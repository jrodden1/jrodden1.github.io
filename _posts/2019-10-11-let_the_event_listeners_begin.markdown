---
layout: post
title:      "Let the Event(Listeners) Begin! "
date:       2019-10-11 17:42:10 +0000
permalink:  let_the_event_listeners_begin
---

One of the neatest things about Javascript is how event based it can be.  Over the last few weeks as I dove into Javascript, I have really enjoyed how I can now do so much with manipulating DOM elements based on events that happen.  One of the challenges I ran into during my latest project (a JS SPA frontend with a Ruby on Rails backend), was around using a modal to display my “create new…” type forms.  

My app is called Auto Maintainer.  It allows the user to create up vehicles and then log maintenance events against those vehicles.  I used MaterializeCSS for styling and thought that the modals looked really slick.  The modal html for the forms was added to the base index.html of my app and then simply gets trigged by special class names attached to buttons.  

After coding up a significant portion of my frontend JS I realized that the modal for my create new maintenance event form didn’t have any idea which vehicle it was creating the maintenance event for (in the words of Scooby-Doo, “Ruh Roh!”).  🤔 How could I make the modal to know the id of the vehicle it was creating the new maintenance event for?   After some pondering, I had a hunch.  What if I add a hidden input to the create-new-maintenance-event form for the vehicle’s id, then when the user clicks on the Create New Maintenance Event button, run a function that sets the hidden vehicle-id input on the modal to the id of the vehicle that the Create New Maintenance button resides in?  

```
<li id="data-vehicle-12" class="active">
   <div class="collapsible-header"><strong>2018 Ford Mustang GT</strong></div>
   <div class="collapsible-body">
	    <a class="btn red modal-trigger" href="#modal2">Create New Maintenance Event</a>
   </div>
</li>
```

Above is a simplified HTML code snippet from my app.  In the HTML, the 2018 Ford Mustang GT vehicle HTML starts with a `<li>` that has a data attribute indicating its vehicle-id (12 in this case).  Since each vehicle has its own Create New Maintenance Event button (for that vehicle) as a (grand)child element, when I click it, I can go to the grandparent `<li>` HTML element and grab that data attribute and now I have the vehicle id I need to tell to the New Maintenance Event form that lives in the modal!  Then from there, I can select the New Maintenance Event form's hidden vehicle id input and set it's value to the correct id.  Awesome!  I think that will work.  

So, I then wrote up a function that would snag the grandparent's data attribute content that contained the vehicle id and then write it to the hidden vehicle-id input on the form inside the modal right when the user clicks on the Create New Maintenance Event button (which also triggers the modal to open).  Next I proceeded to add an event listener to the Create New Maintenance Event button during the creation of the vehicle html (when the Create New Maintenance Event button itself gets created) that would trigger the setting of the vehicle id on the create new form on the modal when clicked.  

Now, the moment of truth (try it out)!  As I refreshed the page, and clicked on one of the Create New Maintenance Event buttons, nothing looked different thus far - the New Maintenance Event form inside the modal popped up (...but that was expected I suppose — I did just set a hidden input).  Now to inspect the form element on the New Maintenance Event form inside the modal to see if the hidden vehicle-id input was set correctly and…. it was!  Yay!  It worked.  Then came that sense of satisfaction — the satisfaction of after thinking through a problem, trying a solution, and then having that solve the problem (on the first try in this case!).  Good times.  

I’ll leave you with something a friend of mine (a former US Special Forces man) taught me about when you run into a problematic situation (in his case he was speaking of wilderness survival, but it applies here too!): 

**S.T.O.P.**

**S** - Stop what your doing, acknowledge you need to address a problem<br>
**T** - Think about what to do<br>
**O** - Observe (what do I have around I can make use of)<br>
**P** - Plan what I’m going to do (and then proceed) <br>

In my case, I wasn’t thinking about how to get food or shelter to survive, but rather I realized I had a problem and needed to **stop** (I need to get the vehicle id sent to the modal form dynamically).  Then I **thought** about what I could do to solve the problem (What can I do to fix this issue?  Well I could create a hidden input field and set it based on a trigger…).  Next, I **observed** what information I already had in my html that I could pull from to get the vehicle id dynamically.  After finding that data attribute with the vehicle-id on the grandparent element of the Create New Maintenance Event button, I **planned** out a fix (add an event listener to the button, and create a callback function to grab the vehicle id and then set it on the modal) then proceeded with the potential solution.  This process worked out well and I was able to get the functionality I wanted!  I hope this helps you in your coding journey too.   

Happy Coding!

Jeremiah
