# lab-preview

## Introduction

This is a website John Thorp made in September 2021 to centralize and document the various opportunities for undergraduates in the department, primarily concerning RA recruitment across all the main labs and any other labs from across Columbia that want in on the haul.

Being a github site under the cu-psych-computing domain is intended to make it flexible and easy to update, at least relative to it being on any official Columbia page. I hope this README helps make that the case.

## Tutorials
Check out Emily's great [workshop](https://cu-psych-computing.github.io/cu-psych-comp-tutorial/tutorials/r-extra/website-github-r/) if you're super new to using hugo and blogdown, like I was. There are a few version difference things that make my instructions here slightly different (mostly you just need build_site() now).

## Software

In Terminal, navigate to an empty folder and type ```git clone https://github.com/cu-psych-computing/lab-preview```, press enter. This should clone the repo onto your computer.

All editing is done in RStudio (R version = 4.0.3) using the blogdown package (version = 1.4). You will need to call the install_hugo function to install hugo on your machine. I used version 0.87.0 of hugo.

I also used kableExtra (version = 1.3.4) to make the tables a little prettier.

## Website organization

The master branch is the only branch you'll be working with. This is how blogdown creates a site when you run new_site(). 
Most pertinent folders are:
### content/
this is where all of pages of the website are stored. ```_index.Rmd``` is the main landing page, every other page is the individual lab pages.
### static/
this is where the .txt tables of lab information are stored, and is where you'd stick any images if you want to load an image.
### public/
this is where the actual site is stored, that is, what you will push to the gh-pages branch and what github will post to the web.

## A typical workflow

These are your first steps.

1. Open lab-preview.Rproj
2. Run ```blogdown::serve_site()```
  * serve_site() automatically detects changes in your .Rmd documents and knits them into the .html docs that will make up the website
  * it also renders your website in the viewer on the bottom right of Rstudio, which you can pop out into your web browser using the button to the right of the broomstick
3. Make changes to existing .Rmd / save as an existing .Rmd to make a new page. 
  * Let's say I'm adding a new page for the Pat Benatar Lab. I would save any of the existing pages as benatar.Rmd, then change the title of the page to "The Heartbreaker Cognition Lab", the slug to benatar, and make any other relevant changes.
4. Make pertinent changes to static/psych-labs.txt or static/other-labs.txt
  * Those documents are where the tables on the welcome page are read from. I would open them in Excel, enter the pertinent info, then sort them alphabetically based on the first column.
5. Run ```blogdown::build_site()``` to render any changes into the public folder (which is what the actual website is).
5. ```git add``` and ```git commit``` any changes.
6. ```git push``` changes to remote.
7. ```git subtree push --prefix public origin gh-pages``` pushes the public folder to gh-pages. This is what actually updates the website.

## Making changes

Every page has a few characteristics that all have to be the same (if I were smarter I would've set every page up to read these variables off a table, which you are welcome to do but wouldn't really save any time anyway).

### Title
The very first line, should be the name of the lab.

### Slug
The name of the page, should be the name of the .Rmd and the second-to-last column in the psych-labs.txt table.

### Video CSS
The frames the videos are in needed a bit of CSS so that they resize with the screen. If you can figure out how to get the tables on the welcome page to resize with the screen and dynamically wrap text you'll be my hero.

### Recruitment text
Every lab is either recruiting or not recruiting RAs. If they are recruiting RAs, this should read:
```<span style="color:green">
**The Heartbreaker Cognition Lab is currently seeking research assistants**
</span
```
If they are not recruiting RAs, this should read:
```<span style="color:red">
**The Heartbreaker Cognition Lab is not currently seeking research assistants**
</span
```

### Video embedding
The best solution I could figure out for the videos was to upload them to my own YouTube account and embed them here. You can get the embed link by clicking "Share" on youtube and replacing the youtube link here. This might make sense to be posted on the Psychology PhD account than on mine, or if there's really any official Columbia YouTube account. I really wish our LionMail accounts could share public links but they explicitly can't do that, so uploading to Google Drive wouldn't work.

### Contact Information Table
See shohamy.Rmd if you need an example of how to put multiple rows into that table.

## Contact Me
If you're stuck just make John Thorp (jnt2136@columbia.edu) do it, this website ain't nobody's fault but mine.

