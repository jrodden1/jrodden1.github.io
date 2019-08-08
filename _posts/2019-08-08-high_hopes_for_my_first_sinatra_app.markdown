---
layout: post
title:      "High Hopes for my first Sinatra App"
date:       2019-08-08 21:43:37 +0000
permalink:  high_hopes_for_my_first_sinatra_app
---

My eyes must have shone with excitement as I sat down to write my first webapp.  In the words of Rhino the Hampster (from the movie Bolt), "All of my training has prepared me for this moment."

But first, the backstory.  A few days prior, I had been pondering what to do for my Sinatra app project that would meet the requirements laid out for me.  I thought, "What would be something I would like to keep better track of that I currently don't have a good system for?"  Necessity is the mother of invention.  I had noticed that I didn't really have a great organized way to keep track of my bills (what bills still needed to be paid and which were already paid for this month).  Thus, the idea for *Bill Tracker* was born.  

To start the planning process, I began whiteboarding out the concept of Bill Tracker.  What will be the *has_many* and *belongs_to* relationships? 

Hmm, well... 
* A User has many Months.  
* A Month has many bills associated with it.  
* A User has many Bills through Months
* Bills belong to a Month 
* A Month belongs to a User. 

Awesome.  That makes sense.  With that in mind, I began planning out my MVC -- I detailed out my Models (User, Month, and Bill) with what attributes each model would have, then my Controller routes, and then Views.  All of this so far had been done without writing any code.  So, as I sat down to start coding my project, it was immensly helpful to have planned out my app before I started coding.   There were many references back to my original my plan when I would get to a spot when coding and say, "Ok... What do I need to do next?"  This plan also helped me from getting overwhelmed by everything that needed to be done.  Just take the next step, make sure that step works, then move on.  

During the code writing process, there was definitely some smelly code that was written, but it worked and got me moving on to the next thing.  Later on, I came back to these areas after most of my app was written and refactored away the smelliness.  

At times I was tempted to make the most perfect app ever (on the first try!).  Then, instruction from a former (wise) CTO (Matt Powell) I worked for came back to my mind.  

It went something like this (I'm paraphrasing): 
> Shoot for an MVP (Minimum Viable Product).  Get something out there (even if it is buggy) to your users, then iterate, iterate, iterate **based on actual user feedback not what you perceive the user will want**. Otherwise, if you don't get something out there, you'll overthink and code something to death, adding in a bunch of features and spending all this extra time and money developing features **that users may not want in the end**.  

Thank you for that reminder, Matt.  One can think of this tempting tendency to make the perfect app on the first go as "feature fever."   Something I found helpful to get over "feature fever" was to just take note of those feature ideas and improvements in a file that I saved in my repo.

Then finally that exciting moment came after much toil and failure, when I tried out my app from start to finish and everything **worked**.  Wohoo!  Status of Desire to Create: Satiated...(for now. 😉)  Euphoria of Creating Experienced?: Yes. 😄 

I think one of the key takeaways from this project was that having a plan for how to execute your specs **helps majorly**.  Also, don't forget those wise words from Dr. Howard Hendricks, "Failure is a necessary part of the learning process."  Learn to laugh at yourself.  Well, this is all I have for now.  😊 May these gleanings help you grow up into a better coder too! 

-Jeremiah


(And for those of you who may not have noticed the reference I made in my title, should check out this [link](https://youtu.be/A_HvBDorpzE). 😉
