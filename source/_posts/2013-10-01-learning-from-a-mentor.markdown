---
layout: post
title: "Turtles & Mentors"
date: 2013-10-04 20:41
comments: true
categories: journey
---
Our most recent project at gSchool, called [SalesEngine](http://tutorials.jumpstartlab.com/projects/sales_engine.html), was quite a stretch for a lot of us in the class. <!-- more --> Beyond the complexity of EventReporter, we had not had any time to recover from that project, overview the lessons learned, and reinforce the most important concepts from from the project. Instead, we jumped right into the next project, some of us without even having touched EventReporter, others with only half of the project completed.

With our new pairs, we dove into the requirements. The project looked massive at first glance, but slowly we started to follow through the requirements (with very handy method and class name requirement) and made progress.

Our progress skidded to a halt once we hit the relationships piece. Although I understand databases, foreign key relationships and how to get my data in and out of MySQL using PHP, I had no idea how to get my objects to pass around stored information to each other in Ruby.

My partner was equally confused. We stepped through an explanation with Jorge on Friday, and spent the weekend putting it together. We took the approach of calling our main interface class, SalesEngine, from every other piece of the program, so that we could reach through SalesEngine down into our data storage collections (called Repositories in this project). Apparently, we didn't understand the Object Model, but then again we haven't talked much about the Object Model except for the fact that everything is an object.

Having completed our relationships piece exactly the wrong way, we were on to building the pieces of business intelligence into the program. Suddenly we had to actually make our idea of the relationships make sense in our heads to get these pieces working, and suddenly everything seemed to be running in circles. On Monday, our instructor Katrina helped us understand where we went wrong, and showed us how to pass through a copy of SalesEngine (by using `self`) to each repository, and in turn to each individual piece of the program. 

We spent a good deal of time of Monday refactoring our relationship model, and finally were back to our original issue: how do we grab and compare data stored in different places in the application?

After some nudging and help from various instructors, we started to understand how things were supposed to work. On Tuesday, with two days to go, we got to building the first few pieces of business intelligence. I sat down to read the piece on the first item, and this is what my psuedocode looked like: 

``` ruby
 def test_it_can_find_the_merchant_with_the_most_x_revenue
    engine = SalesEngine.new("./test/fixtures")
    # find all invoices by merchant_id
    # then find each invoice id for the merchant_id
    # use invoice_id to call invoice_items that match
    # compare these invoice_id's to tranactions invoice_id 
    # only use the ids that have result == success
    # take the quantitiy of the items & multiply by the price
    # process the price into BigDecimal (don't use Float)
    # store that in an array
    # sort the array on .sort or some similar array method
 end 
```

In the end, this pseudocode actually didn't help me out at all. It wasn't until I stepped back and read through
all of the requirements that I realized that starting at the top of the list would not get us to the final endpoint. In order to report the top `x` merchants based on revenue, we would have to create helper classes associated with invoices and transactions. 

Eventually, by the end of the night we had tested and created methods for our individual `Merchant`, `Invoice`, `Transaction`, and `MerchantRepository` classes to help us get some sort of response from the system.

But there was a bug. And that it turns out that wherever there is one bug, there are many more in hiding. It was 4:30, and the instructors were leaving for the day, and we were stuck. 

Thankfully, [Cory LaNou](https://twitter.com/corylanou) and [Levi Cook](https://twitter.com/levicook), founders and developers at [SupportLocal](http://www.supportlocal.com/), offer their time and energy for help on Tuesday evenings to gSchool students. 

Cory spent four hours with my partner and I that night, showing us how to debug a program, and exploring with us where things were going wrong. Besides various errors that we have made using core methods, we also discovered that our test data set was completely useless without our foreign keys matching up. It took us that fours hours to get two tests to pass.

I couldn't believe how much time he had spent with us, going around in circles, walking us through debugging, and helping us find the issues in our program. I would love it if every mentor out there were as patient as Cory.

Although in the end we did not finish SalesEngine, I believe the lessons we learned from Cory about debugging, and the persistence needed when tracking down issues, were monumental, and very important to the success of our future projects.