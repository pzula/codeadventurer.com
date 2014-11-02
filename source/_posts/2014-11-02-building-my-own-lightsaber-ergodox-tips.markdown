---
layout: post
title: "Building My Own Lightsaber: Ergodox Tips"
date: 2014-11-02 11:08
comments: true
categories: projects
---

Building a keyboard can be likened to building a lightsaber. I set off on an adventure, found some plans, and somehow found the confidence to give it a try.

This is not an endeavor that happens without trepidation. When I first decided to spring for an Ergodox kit on [Massdrop](http://massdrop.com), I knew that I wouldn't be getting the parts in the mail for months. I figured I knew how to do a little soldering (thanks to the [Concococtory's](http://concoctory.com/) beginner class), and it wouldn't be a big deal. But once the kit was on my front porch, months later, I started to doubt my abilities to complete this project.

<!-- more -->

I opened up the package and found ~100 diodes to be surface-mounted, two PCBs, two USB cables, three LED's, two TRSS connectors, one I/O expanders, an I/O expansion cable, mechanical key switches, keycaps, and a case.

I found the instructions to build the kit online, and got everything in place to begin the process. I messed up on a few counts, but I finished it, and I wanted to provide resources for other people to be able to build their own without as many hiccups as I encountered.

## Things you will need (learned the hard way)


#### 1. A Good Soldering Iron


Before you get your ErgoDox kit, get a [50 watt, variable temperature soldering iron](https://www.sparkfun.com/products/10707) from SparkFun

I started this project with a cheap RadioShack soldering iron. It got too hot too fast, and couldn't maintain a reasonable temperature for soldering SMDs onto a PCB. I had to stop construction in order to get a proper variable-temperature iron in the mail.

#### 2. Soldering and De-soldering consumables


You're going to need a good, thin solder for the work you will be doing on the Ergodox. [This one](http://www.amazon.com/Amico-0-3mm-Rosin-Solder-Soldering/dp/B008DEYEAW) is a good choice.
You're also going to need a few things to help you when you mess up. I recommend some [desoldering wick](https://www.amazon.com/gp/product/B003E48ERU), and a good [flux pen](https://www.amazon.com/gp/product/B0089EQGW0).

#### 3. A small electronics tool kit


The tools I found I got the most use out of for this project were:

- [Reverse-action tweezers](http://www.amazon.com/Testors-8942T-Reverse-Action-Tweezers/dp/B003ZD1148) (used for placing the SMD's)
- Needle-nose pliers
- Wire cutters
- A sharp pocket knife
- Solder sucker
- A magnifying glass, preferably one with a built in light (like [this one](http://www.amazon.com/3-5x12x-Helping-Magnifying-Soldering-Magnifier/dp/B009NOG9TA))
- Voltmeter


#### 4. A workspace


- Big enough to leave everything spread out
- Safe from pets and kids who might want to play with the parts
- Good lighting
- Well-ventilated (for soldering)



#### 5. A few practice projects


If you are new to soldering (or haven't soldered in a while), it's best to do a little bit of practice before you undertake this.

You should practice both your through-hole soldering, and your surface-mount soldering. SparkFun sells kits for this. This [Weevil kit](https://www.sparkfun.com/products/10723) is a great through-hole project (make sure to read the instructions and tips), and the [Simon Says](https://www.sparkfun.com/products/10935) project is an excellent surface-mount project to practice with.


#### 6. Some decent instructional videos


I found [this video](https://www.youtube.com/watch?v=3NN7UGWYmBY) to be helpful for learning how to do SMD soldering without needing more equipment.

I found [this video](https://www.youtube.com/watch?v=tlSY1uaw0GA) helpful for learning how to desolder something that you surface-mounted. I had a couple of mishaps throughout the process and needed to use this technique a few times.

I also had a few switched that I needed to replace (due to my own poor soldering jobs, not due to Massdrop's shipment), and needed to know how to desolder the through-hole joints. [Here is a video that is helpful](https://www.youtube.com/watch?v=Z38WsZFmq8E) for that task.

#### 7. Get going!

Once you get your Massdrop order of parts, make sure you open it and count all of the pieces. I did not do this, and ended up with a few missing parts. It was a few weeks after the drop arrived, however, so I had to aquire the missing parts on my own.

Give yourself at least one weekend to do this project -- after you have taken the time to get all of the things I have listed above, and also after you have practiced your soldering. Make sure you follow the order of instructions in the [Massdrop assembly instructions](https://www.massdrop.com/ext/ergodox/assembly.php), and you should come out on the other side of your weekend with a shiny new keyboard!

#### Common Problems


I encountered a lot of common problems along the way, and I thought I should list them here in case you have similar issues.

- Keyboard stops working after pressing a key

This is likely due to a diode having a lose connection, or being damaged. Check across diodes with a voltmeter to see if any indicate the connection is not made. Use SMD desoldering skills that you learned to remove the offending diode, and if you removed it cleanly, re-solder the same diode to the board. If you have damaged the diode (either in placing it, or removing it), use a new one to ensure the problem will not persist.

- A key is not working when pressed

This is likely due to a poor solder job around the key-switch. Flip the board over and check your joint. If it needs to be re-soldered, revisit the de-soldering a through-hole video to get proper instruction on how to remove the part, clean the through-hole, and re-solder the switch. This is often the better option than adding more solder, as the solder can overflow to the other side if you use too much, and cause damage to the board or the switch. There was only one switch I had that was actually malfunctioning after trying to remove and re-solder it. In that case, remove the switch completely using desoldering techniques, and use a spare provided by Massdrop.

- An entire column of keys do not work

This is likely due to a poor solder job on the Teensy or the I/O expander. Check that every connection point is free of excess solder that may be connecting multiple together. Yes, these are small components, but careful soldering around these two will ensure that you don't run into this problem.

- Keys aren't all aligned well, causing issues with the keycaps not sitting in place well.

This problem I could have avoided had I had experience with using a PCB and acrylic together. Although the solder on the other side should help keep your key-switches snugly in place (if you placed them in straight), if you ever do any modifications to your key-switches in the future (such as replacing what kind of springs you are using in your Cherry MX keys), you are at risk of damaging your solder job. To prevent this from happening, I recommend using a hot glue gun to place your key-switches in place on the acrylic **before** you place it through the PCB, and **before** you solder your key-switches in place. I'm working on a second keyboard project at the moment and realize how much of a difference this makes now.



## The Review


The Ergodox is a great keyboard for someone who is looking for a do-it-yourself alternative to matrix-style split keyboards. I found it a little difficult to get used to with the blank keycaps, so I joined in on a [GeekHack](http://www.geekhack.org) group buy to buy keycaps for the ErgoDox. It took several months to get them, and in that time period I wasn't using the ErgoDox because of the learning curve. Once I got the keycaps, I still felt slow. I put the ErgoDox away for a while, as I wasn't fast enough with it yet to use it daily at work, and I wasn't working on side projects in the evenings. These past few weeks, my Apple Wireless keyboard died, and the only other keyboard I had around was the ErgoDox. I dusted it off, and within a few weeks got better at using it. I'm still not fast enough with special characters that I use daily in programming, so it is a bit cumbersome. I feel that with a few months of practice, someone can bring their typing speed back up to par, and with a lot less wrist pain than a traditional keyboard.


## Photos of my project


![Placing diodes using the magnifiying glass](/images/ergodox/ergodox_diodes.jpg)

<p class="caption">Placing diodes using the magnifying glass</p>

![Placing keyswitches on acrylic](/images/ergodox/keyswitches_on_acrylic.jpg)

<p class="caption">Placing keyswitches on acrylic</p>


![Placing keyswitches on PCB](/images/ergodox/keyswitches_and_pcb.jpg)

<p class="caption">Placing keyswitches on PCB</p>

![Soldering of switches](/images/ergodox/switches_and_diodes.jpg)

<p class="caption">Soldering on switches after the diodes</p>

![Finished, with missing keycap](/images/ergodox/missing_keycap.jpg)

<p class="caption">Missing a keycap from the drop</p>

![Finished, with new keycaps](/images/ergodox/with_new_keycaps.jpg)

<p class="caption">The Ergodox today</p>
