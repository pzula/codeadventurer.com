---
layout: post
title: "Keeping Things DRY Without Complecting: Table Inheritance"
published: false
date: 2014-11-11 08:49
comments: true
categories: architecture
---

### Keeping Things DRY Without Complecting: Table Inheritance

When dealing with architecture, we find ourselves often dealing with concepts that are similar, yet just slightly different. In an effort to keep our code DRY, we might reach for an abstraction of these concepts all the way down to the data layer, in order to squeeze out more re-use within our codebase. But sometimes, our abstractions can lead to more complexity down the road. I'd like to exploire this concept to see how an abstraction can morph over time, and what sort of decisions along the way can help an abstraction become easier or harder to use.

In the following example, we're going to assume that we are building a type of storage and logic system for content types in a small, hosted content-management system.

A content management system can have many kinds of content -- including polls, blog posts, articles, events and so on. When a user opens an account, they are given a few of these default content types to use and customize.

As the engineer, we know that the types of content that our product offers to users will grow as our product grows, so we take a close look at what the content types have in common in order to try to tease out the similarities and build an abstraction that will allow us to easily add more content types in the future.

We find that each kind of content has a lot of the same ideas: we have sections, and each section can have instructions on what to use that section for, and each section can have many different input types.

There could be a problem, though: when a user modifies one of the content types by adding or removing parts, we can end up with data loss if they've used that content type prior to the modification. For example, by removing the field for author in the future, all prior posts that had an author entry will no longer have that data.

After some thought, we find a way around the problem of data loss. We will create
Templates for each type of content. The template is where a user can customize
how they want to be able to use this input form, from naming the template to
adding, editing and deleting fields and text within sections. Sections can also
be added, edited, or deleted. Some users might want to have a mood input field in
their blog posts. Others might want to have a 'Related Articles' section
available when they add new acticles.  We also want to offer the ability to
bring back anything that has been removed from the template in the past, so each
template will have a 'Deleted' section, where inputs and sections can be
retreived for later use.

However, the Template is only used for storing the structure of how the user
wants to interact with that type of content. When a user actually wants to
create a new piece of content, we will duplicate the structure of the Template
and turn it into a Document object. This Document is a snapshot of the Template at that
point in time, and also contains the data entered by the user (such as an article or a blog post). If the Template for that content types gets modified
in the future, it will not affect a Document that has been created for that
content type, because they are different objects and the data resides in different tables in our database.

In order to implement the solution, we build up our database migrations and our models. We want to keep things simple from a data perspective, as everything shares the same sort of structure, so we create these migrations and models:

```ruby

class CreateContentTypes < ActiveRecord::Migration
  def change
    create_table :content_types do |t|
      t.string :name

      t.timestamps
    end
  end
end

```

```ruby

class CreateContentTemplates < ActiveRecord::Migration
  def change
    create_table :content_templates do |t|
      t.string :name
      t.integer :content_type_id
      t.integer :account_id
      t.integer :created_by_id
      t.integer :modified_by_id

      t.timestamps
    end
  end
end

```

```ruby

class CreateContentDocuments < ActiveRecord::Migration
  def change
    create_table :content_documents do |t|
      t.string :name
      t.integer :content_type_id
      t.integer :account_id
      t.integer :user_id
      t.datetime :published_at
      t.integer :created_by_id
      t.integer :modified_by_id

      t.timestamps
    end
  end
end

```

```ruby

class CreateContentSections < ActiveRecord::Migration
  def change
    create_table :content_sections do |t|
      t.string :name
      t.integer :created_by_id
      t.integer :modified_by_id

      t.timestamps
    end
  end
end

```

```ruby

class CreateContentInputs < ActiveRecord::Migration
  def change
    create_table :content_inputs do |t|
      t.string :description
      t.integer :content_data_id
      t.integer :interview_type_id
      t.integer :account_id
      t.integer :created_by_id
      t.integer :modified_by_id

      t.timestamps
    end
  end
end

```

```ruby

class CreateContentDatas < ActiveRecord::Migration
  def change
    create_table :content_datas do |t|
      t.string :data
      t.integer :created_by_id
      t.integer :modified_by_id

      t.timestamps
    end
  end
end

```

```
class ContentType < ActiveRecord::Base

  POLL_ID = 1
  BLOG_POST_ID = 2
  ARTICLE_ID = 3

  scope :poll,      => { find(POLL_ID) }
  scope :blog_post, => { find(BLOG_POST_ID) }
  scope :article,   => { find(ARTICLE_ID) }

end
```

```
class ContentTemplate < ActiveRecord::Base

  has_many :content_template_sections
  has_many :content_sections

  belongs_to :content_type
  belongs_to :account
  belongs_to :modified_by, :class_name => User
  belongs_to :created_by, :class_name => User

end

```

```
class ContentDocument < ActiveRecord::Base

  belongs_to :content_type
  belongs_to :account
  belongs_to :modified_by, :class_name => User
  belongs_to :created_by, :class_name => User

end
```

```
class ContentSection < ActiveRecord::Base

  has_many :content_template_sections
  has_many :content_templates, :through => :content_template_sections

  has_many :content_section_inputs
  has_many :content_inputs, :through => :content_section_inputs

  belongs_to :created_by, :class_name => User

  amoeba do
    enable
    exclude_field [:content_templates, :content_template_sections]
    clone [:content_inputs]
  end
end
```

```
class ContentInput

  has_many :content_section_inputs
  has_many :content_sections, :through => :content_section_inputs

  has_many :content_input_datas
  has_many :content_datas, :through => :content_input_datas

  belongs_to :account
  belongs_to :content_type

end
```

```
class ContentData

  belongs_to :created_by, :class => User
  belongs_to :modified_by, :class => User

end

```


