---
layout: post
title:      "Creating a Rails App from Scratch"
date:       2019-09-15 23:54:07 -0400
permalink:  creating_a_rails_app_from_scratch
---



When I was a kid, my Mom made a deal with us kids.  You go and pick the black raspberries, and I’ll make you a [black raspberry crisp](https://www.smalltownlivingusa.com/recipe/homemade-black-raspberry-crisp/).  We would bound off and search around our farm in the summer sun and return with containers full of berries.  (The contains would have been more full if we wouldn’t have been popping berries in our mouth as we picked them.)  She would then make us a black raspberry crisp from scratch (soooo tasty!).  Sometimes the best things in life are those made from scratch.  

I just completed an [MVP](https://en.wikipedia.org/wiki/Minimum_viable_product) of a “simple" inventory app for my Rails Project.  It was quite the adventure for sure.  Though it was full of many moments of wanting to rip my hair out, I learned so much from making this Rails app from scratch.  

One of the earliest gleanings was that when you use PostgreSQL for your database in Rails instead of SQLite, the process is a little different to get up and running.  After creating the new rails app with Postgres as the database, I was innocently plugging along at writing up my migrations and then tried to do ``rails db:migrate``.  I got an error.  Huh, that’s weird.  That should have worked.  After tinkering some more and finding my frustration level starting to rise, I then fired up a search engine to see what I could find.  An article from [Medium.com](https://medium.com/@cindyk09/building-a-rails-app-from-scratch-with-postgresql-362e1fd0fb44) came up.  After skimming through the article, I read the following line: 

> “Because of postgresql we need to create the database first so we will run the below in order.  
> ``rake db:create``<br>
> ``rake db:migrate``

Ah ha!  Postgres, you sneeky little guy.  When using the default SQLite for my database in Rails in the past, `rake db:migrate` would automatically create up the db then run the migrations.  I didn’t know that Postgres was little less automagical and that I had to create the database first for it to work —  Lesson learned.  

Next came the major conundrum of my project -- it arose when I had done some significant coding on my locations and items models and controllers.  One functionality I wanted to implement was for items to be available across multiple locations and to track the quantity of item at each location (via a join table called location_items).  So, for example, Roger has a small computer store and is using my app.  He creates up 2 locations - Showroom and Storage Room.  I want Roger to be able to have 2 MacBook Pro's in the Showroom location and 5 MacBook Pro's in the Storage location.  

I then realized that the nested routing and model connections I was using (for example, /locations/2/items/3) were not actually going to work.  Item 3 (in this example) didn’t actually belong to Location 2.  I realized that a row from my join table, location_items, is really what belonged to a location and what kept track of the quantity of the item at that location, not the item itself.  So, my nested route should actually be /locations/2/location_items/5 -- I needed to be displaying instances of the LocationItems model in my nested route, not Items.  When I first realized this, it was slightly horrifying (because I had done so much work already).  But after taking a moment to ponder what needed to be done, I found that it actually wasn’t going to be all that terrible to get it to work the way I wanted it.  I redid my model relationship connections.  Then I set about testing those and reworking some of my previous code for the views and routes to fit this functionality I desired.  In the end, I got it all working!  

This experience taught me a lot about the importance of truly taking the time to think through your model relationships before you get started.  Sometimes an extra hour of thinking about how everything relates can save you hours of coding time.  Sometimes the best lessons in coding life come from those apps that are made from scratch.  

-Jeremiah
