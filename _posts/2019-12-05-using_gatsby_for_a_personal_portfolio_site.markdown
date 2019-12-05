---
layout: post
title:      "Using Gatsby for a Personal Portfolio Site"
date:       2019-12-05 17:40:18 -0500
permalink:  using_gatsby_for_a_personal_portfolio_site
---

After graduating from Flatiron School recently, I wanted to create a personal portfolio site.  With a desire to keep my skills sharp, I decided to see how I could make up a portfolio site using React.  As I was poking through [the React documentation](https://reactjs.org/docs/create-a-new-react-app.html), I found that it recommended trying out [Gatsby](https://www.gatsbyjs.org) for static content-oriented sites.  This seemed right up my ally for making up a MVP portfolio website… and onward the learning journey continued!  

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAxMDYgMjgiIGZvY3VzYWJsZT0iZmFsc2UiPgogIDxwYXRoIGQ9Ik02Mi45IDEyaDIuOHYxMGgtMi44di0xLjNjLTEgMS41LTIuMyAxLjYtMy4xIDEuNi0zLjEgMC01LjEtMi40LTUuMS01LjMgMC0zIDItNS4zIDQuOS01LjMuOCAwIDIuMy4xIDMuMiAxLjZWMTJ6bS01LjIgNWMwIDEuNiAxLjEgMi44IDIuOCAyLjggMS42IDAgMi44LTEuMiAyLjgtMi44IDAtMS42LTEuMS0yLjgtMi44LTIuOC0xLjYgMC0yLjggMS4yLTIuOCAyLjh6bTEzLjUtMi42VjIyaC0yLjh2LTcuNmgtMS4xVjEyaDEuMVY4LjZoMi44VjEyaDEuOXYyLjRoLTEuOXptOC41IDBjLS43LS42LTEuMy0uNy0xLjYtLjctLjcgMC0xLjEuMy0xLjEuOCAwIC4zLjEuNi45LjlsLjcuMmMuOC4zIDIgLjYgMi41IDEuNC4zLjQuNSAxIC41IDEuNyAwIC45LS4zIDEuOC0xLjEgMi41cy0xLjggMS4xLTMgMS4xYy0yLjEgMC0zLjItMS0zLjktMS43bDEuNS0xLjdjLjYuNiAxLjQgMS4yIDIuMiAxLjIuOCAwIDEuNC0uNCAxLjQtMS4xIDAtLjYtLjUtLjktLjktMWwtLjYtLjJjLS43LS4zLTEuNS0uNi0yLjEtMS4yLS41LS41LS44LTEuMS0uOC0xLjkgMC0xIC41LTEuOCAxLTIuMy44LS42IDEuOC0uNyAyLjYtLjcuNyAwIDEuOS4xIDMuMiAxLjFsLTEuNCAxLjZ6bTYuMS0xLjFjMS0xLjQgMi40LTEuNiAzLjItMS42IDIuOSAwIDQuOSAyLjMgNC45IDUuM3MtMiA1LjMtNSA1LjNjLS42IDAtMi4xLS4xLTMuMi0xLjZWMjJIODNWNS4yaDIuOHY4LjF6bS0uMyAzLjdjMCAxLjYgMS4xIDIuOCAyLjggMi44IDEuNiAwIDIuOC0xLjIgMi44LTIuOCAwLTEuNi0xLjEtMi44LTIuOC0yLjgtMS43IDAtMi44IDEuMi0yLjggMi44em0xMyAzLjVMOTMuNyAxMkg5N2wzLjEgNS43IDIuOC01LjdoMy4ybC04IDE1LjNoLTMuMmwzLjYtNi44ek01NCAxMy43aC03djIuOGgzLjdjLS42IDEuOS0yIDMuMi00LjYgMy4yLTIuOSAwLTUtMi40LTUtNS4zUzQzLjEgOSA0NiA5YzEuNiAwIDMuMi44IDQuMiAyLjFsMi4zLTEuNUM1MSA3LjUgNDguNiA2LjMgNDYgNi4zYy00LjQgMC04IDMuNi04IDguMXMzLjQgOC4xIDggOC4xIDgtMy42IDgtOC4xYy4xLS4zIDAtLjUgMC0uN3oiLz4KICA8cGF0aCBkPSJNMjUgMTRoLTd2Mmg0LjhjLS43IDMtMi45IDUuNS01LjggNi41TDUuNSAxMWMxLjItMy41IDQuNi02IDguNS02IDMgMCA1LjcgMS41IDcuNCAzLjhsMS41LTEuM0MyMC45IDQuOCAxNy43IDMgMTQgMyA4LjggMyA0LjQgNi43IDMuMyAxMS42bDEzLjIgMTMuMkMyMS4zIDIzLjYgMjUgMTkuMiAyNSAxNHptLTIyIC4xYzAgMi44IDEuMSA1LjUgMy4yIDcuNiAyLjEgMi4xIDQuOSAzLjIgNy42IDMuMkwzIDE0LjF6IiBmaWxsPSIjZmZmIi8+CiAgPHBhdGggZD0iTTE0IDBDNi4zIDAgMCA2LjMgMCAxNHM2LjMgMTQgMTQgMTQgMTQtNi4zIDE0LTE0UzIxLjcgMCAxNCAwek02LjIgMjEuOEM0LjEgMTkuNyAzIDE2LjkgMyAxNC4yTDEzLjkgMjVjLTIuOC0uMS01LjYtMS4xLTcuNy0zLjJ6bTEwLjIgMi45TDMuMyAxMS42QzQuNCA2LjcgOC44IDMgMTQgM2MzLjcgMCA2LjkgMS44IDguOSA0LjVsLTEuNSAxLjNDMTkuNyA2LjUgMTcgNSAxNCA1Yy0zLjkgMC03LjIgMi41LTguNSA2TDE3IDIyLjVjMi45LTEgNS4xLTMuNSA1LjgtNi41SDE4di0yaDdjMCA1LjItMy43IDkuNi04LjYgMTAuN3oiIGZpbGw9IiM2MzkiLz4KPC9zdmc+Cg==" width="200px" height="75px">

So what is Gatsby?  According to gatsbyjs.org, "Gatsby is a free and open source framework based on React that helps developers build blazing fast websites and apps... Gatsby.js builds your site as “static” files which can be deployed easily on dozens of services.”  Cool.  So far, Gatsby has been pretty easy to pick up -- when they say it only takes a few minutes to get up and running, they're not joking!  Gatsby has a multitude of what they call “starters” or template sites you can use to get up and going fast.  You can have a look at them [here](https://www.gatsbyjs.org/starters/?v=2).   After looking through some starters that I wanted to use for my site, I picked this [one]( https://www.gatsbyjs.org/starters/JohnJKerr/gatsby-creative) by [John J Kerr](https://github.com/JohnJKerr) for its clean and beautiful look (nice work John!  Thanks for sharing.)  In this post, I'll describe the process so you can follow along too!

Toward the bottom of the Gatsby starter’s page, you’ll see it even gives you the Gatsby CLI command to get going with that specific starter!  We’ll be using that in just a second.  But before we do that, we’ll need to make sure we have Gatsby’s CLI installed first on our local machine.  Simply use `npm` from your terminal to install it globally
```
npm install -g gatsby-cli
```

Well, that was easy.  

Then we’ll go ahead and run the command found at the bottom of the Gatsby starter page.  You can chose to name the project folder something else besides the default that is given.  In my case, I replaced `gatsby-creative` with `roddendev-brand`.  Also, if you selected a different starter, be sure to replace the github repo link (`https://github.com/JohnJKerr/gatsby-creative`) with the appropriate repo link for your starter. 

Default command at the bottom of the Gatsby starter page:
```
gatsby new gatsby-creative https://github.com/JohnJKerr/gatsby-creative
```

What I used:
```
gatsby new roddendev-brand https://github.com/JohnJKerr/gatsby-creative
```

Now, `cd` into the new directory - in my case `roddendev-brand`:
```
cd roddendev-brand
```

Alright, now we can start our development server
```
gatsby develop
```

Sweet.  Now we can navigate in our internet browser to `http://localhost:8000` and we’ll see the starter site.  Piece of cake!  

You can then proceed to open up the project folder with your favorite text editor (I use VS Code so from the terminal with the roddendev-brand opened, I can simply type `code .`

We definitely want version control so lets put this on Github.  (You can open a terminal in VS Code using Ctrl + \` on a Mac or go to the View menu then select Terminal.  You also can just use another regular terminal window.)  To prep the new project folder for Github, run these three commands one right after the other.
```
git init 
git add . 
git commit -m “Initial Commit"
```
Next open up your browser and navigate to github.com/new (If you are logged in, this will take you directly to the Create New Repository page; otherwise, login and then go to the + button next to your avatar in the upper right and select New Repository)

Go ahead and give your repo a name.  I typically like to call it the same as what the project folder name is, so in my case I set it to `roddendev-brand` and then click on “Create repository”

Github will now give you instructions.  You’ll want to copy the commands from the “push an existing repository from the command line” section.  

Keeping with my example, the two commands to run would be: 
```
git remote add origin git@github.com:jrodden1/roddendev-brand.git
git push -u origin master
```

Go back to the same terminal window you were entering in the git commands before and run those two commands.  

If all is well, you should be able to run `git remote -v` and see 

```
origin    git@github.com:jrodden1/roddendev-brand.git (fetch)
origin    git@github.com:jrodden1/roddendev-brand.git (push)
```
(except it will be your repo name in there now)

Alright, then we’ll push our initial commit to github using
```
git push
```

Awesome! Now, let the customization begin!  At this point go to town personalizing your starter.  In my case I customized this starter fit my personal brand needs.  

In conclusion, Gatsby is pretty neat!  They also have really good tutorials on their site.  If you are not as inexperienced with coding, I suggest you start with this [tutorial](https://www.gatsbyjs.org/tutorial/part-zero/) and for the more experienced, this [tutorial](https://www.gatsbyjs.org/docs/quick-start/).  Once you are ready to publish, head on over to the [Deploying & Hosting](https://www.gatsbyjs.org/docs/deploying-and-hosting/) section of Gatsby's documentation.  I ended up using their Heroku directions, and it was easy peasy to get it running.  Feel free to have a look at my repo [here](https://github.com/jrodden1/roddendev-brand).

May this post help you in your journey of being a growing coder!

Jeremiah

