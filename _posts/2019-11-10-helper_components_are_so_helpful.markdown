---
layout: post
title:      "Helper Components are so... Helpful!"
date:       2019-11-10 20:57:59 -0500
permalink:  helper_components_are_so_helpful
---


Profound title -- I know.  This past week I have been working on my final project - a shipment tracking web app named Shipd made with a React frontend and a Ruby on Rails backend.  Now, this shipment tracking app is geared more toward small ebay sellers or a brick and mortar print and ship type shop — it allows you to see all the shipments you have created and run some basic reports over them.  

As I was coding, sometimes one of my React container or component files would be getting really cluttered and/or I’d see the need to reuse some of my logic in one component in another component.  Enter helpers!  I remembered learning that you could have a helper file in React that you can save functions or even variables in, and set it up so you can use these in other files.  Doing this enables you to be able to import those functions and variables just like you import components into your files.  So awesome!  

To do this, you simply create up a new file (and maybe a new folder first called `helpers` to save all your helper files in #keepSeparationOfConcerns).  I categorized mine based on the type of component they were helping.  For example, I created a file called `PackageHelpers.js` to contain functions and variables I wanted to use with anything relating to my package components or containers.  To setup the helper file, you basically need to import React, declare your desired function or variable.  Then on the `export` line, instead of using `default` next, you’ll use `export` then an object containing those function and/or variable names!  That’s it.  You’ll then be able to import those functions and variables into another file by doing something like `import { myFunction, myVar } from ‘./helpers/MyHelperFile.js`  

So let’s look at an example from my project.  In my PackagesHelper.js file, I wanted to add some helpers to conditionally format my sender info, receiver info, and address information for my packages, keep a list of US states for my package creation form, and format how the cost of a package would look.  In the end I had something like this: 

```
import React from 'react'

const senderInfo = (pkg) => {
        //(some logic here for formatting and returning a JSX object.)
}


const receiverInfo = (pkg) => {
       //(…some logic here for formatting and returning a JSX object.)
}


const addressInfo = (shipperObj) => {
       //(…some logic here for formatting and returning a JSX object.)
}


const stateList = 
   [
      "AL", "AK", "AZ", "AR", "CA", "CO", "CT", "DE", "DC", "FL", 
      "GA", "HI", "ID", "IL", "IN", "IA", "KS", "KY", "LA", "ME", 
      "MT", "NE", "NV", "NH", "NJ", "NM", "NY", "NC", "ND", "OH", 
      "OK", "OR", "MD", "MA", "MI", "MN", "MS", "MO", "PA", "RI",
      "SC", "SD",  "TN", "TX", "UT", "VT", "VA", "WA", "WV", "WI", "WY"
   ]

//Format package cost to look like money - have 2 decimal places always
const formattedCost = (costRaw) => parseFloat(costRaw).toFixed(2).toString()

export {
   senderInfo,
   receiverInfo,
   addressInfo,
   stateList,
   formattedCost
}
```

Then I was able to import these into my various files.  One example where I imported some of these was in my Package.js component (which was responsible for rendering out a single package).  The top of my Package.js file looks like so: 

```
import React from 'react';
import { Component } from 'react'
import { Card, Button, Row, Col } from 'react-bootstrap'
import { senderInfo, receiverInfo, formattedCost } from '../../helpers/PackageHelpers’  
// the line above imports some of the helpers from PackageHelpers!
```

After importing them, I could utilize them by simply using their imported name.  

```
<Row>
     <Col style={{width: 13}} className="text-center">{senderInfo(this.props.pkg)}</Col>
     <Col style={{width: 13}} className="text-center">{receiverInfo(this.props.pkg)}</Col>
</Row>
```

Ahhhhh. That looks much better and is reusable in other files too!  The further I worked on my project this past week, the more helpers I implemented so that my code could be more DRY.  I hope this little example from my gleanings while coding helps you along the way in your coding journey! 

—Jeremiah
