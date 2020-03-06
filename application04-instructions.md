---
title: "Application Task 4"
author: ""
date: ""
output: 
  html_document: 
    keep_md: yes
---



## The Workflow

Due by 11:59 pm Monday, Oct. 28th.

### Overview
The goal of these tasks are to explore a package within R.
You will choose an R package that we haven't already been using in class and use it to do something.

You will be submitting three items: [1] a README.md and [2] a report through GitHub, and [3] a reflection on Bb.

#### Evaluation

Tasks 1 and 3 will be evaluated using the [Meeting Preparation Grading Standards](https://sta518.github.io/syllabus/assessment/#meeting-preparation-1).
Each sub-task in Task 2 will each be evaluated using the [Application Tasks Grading Standards](https://sta518.github.io/syllabus/assessment/#application-tasks-1).

Your overall Application Task 3 grade will be based on the following criteria:

- Excellent (**E**): Each task earned an Excellent of Satisfactory, including one Excellent.
- Satisfactory (**S**): Each task earned a Satisfactory.
- Progressing (**P**): Each task earned a Satisfactory or Progressing.
- Incomplete (**I**): At least one task was not submit.

### Create Your `application04` Repo

GitHub Classroom will automatically make a repository for you, called `application04-your_github_username`, for you to work on your assignment.
Follow these instructions to get the repo:

1. Sign-in to [Bb](https://mybb.gvsu.edu)
2. Go to the **Application Task 4** assignment page.

Here, you will find a url leading to a page on GitHub Classroom.
Visit this page and follow the instructions.
When you obtain your repository, it should contain a copy of this `application04-instructions.md` file, a blank `README.md` file, and a starter `application03Rmd` file.

#### 1. Edit `README.md` 

Your task here is to edit the `README.md` file in your repository to contain a sample of GitHub-flavored markdown features.
Specifically, your README should contain a brief description as to what the repo is, so that an unknown visitor landing on the repo can orient themselves
You should also help the visitor navigate your repository (in whatever way you think is most appropriate).

Remember the resources you were directed to view during your work in the class activities and Meeting Preparations.
These are also organized in the [Additional Resources/Markdown](https://sta518.github.io/resources/markdown/) section of this site.

You can edit the README in your browser like we did in class, but I encourage you to experiment with editing it from within RStudio.
**FYI, this will be a private repo - only you and I will be able to see it.**

#### 2. Pick a package, any package...

... well, not exactly any package.
I provide you with some potential R packages below, but you are also free to use a package not on this list.
If you choose an unlisted package, just run it by me first so that I can confirm that we have not already introduced it in class.
The goal here is to work with a new package and use it to do something.

##### Potential packages (non exhaustive and non exclusive)

###### Packages on CRAN

These packages can be installed with:


```r
install.packages("PACKAGENAME")
```

The package manuals are linked below, however developers of the packages might have additional information on the GitHub repo of the package.

- [`cowsay`](https://cran.r-project.org/web/packages/cowsay/vignettes/cowsay_tutorial.html)
	- Allows printing of character strings as messages/warnings/etc. with ASCII animals, including cats, cows, frogs, chickens, ghosts, and more.
- [`babynames`](https://cran.r-project.org/web/packages/babynames/babynames.pdf)
	- US Baby Names 1880-2015
- [`Lahman`](https://cran.r-project.org/web/packages/Lahman/Lahman.pdf)
	- Provides the tables from the 'Sean Lahman Baseball Database' as a set of R data.frames. It uses the data on pitching, hitting and fielding performance and other tables from 1871 through 2015, as recorded in the 2016 version of the database. 
- [`praise`](https://cran.r-project.org/web/packages/praise/praise.pdf)
	- Build friendly R packages that praise their users if they have done something good, or they just need it to feel better.	
- [`GGally`](https://cran.r-project.org/web/packages/GGally/GGally.pdf)
	- The R package `ggplot2` is a plotting system based on the grammar of graphics. `GGally` extends `ggplot2` by adding several functions to reduce the complexity of combining geometric objects with transformed data. Some of these functions include a pairwise plot matrix, a two group pairwise plot matrix, a parallel coordinates plot, a survival plot, and several functions to plot networks.
- [`ggimage`](https://cran.r-project.org/web/packages/ggimage/vignettes/ggimage.html)
	- Supports image files and graphic objects to be visualized in 'ggplot2' graphic system.
- [`suncalc`](https://cran.r-project.org/web/packages/suncalc/suncalc.pdf)
	- R interface to 'suncalc.js' library, part of the ['SunCalc.net' project](http://suncalc.net), for calculating sun position, sunlight phases (times for sunrise, sunset, dusk, etc.), moon position and lunar phase for the given location and time.
- [`fortunes`](https://cran.r-project.org/web/packages/fortunes/fortunes.pdf)
	- A collection of fortunes from the R community
- [`ttbbeer`](https://cran.r-project.org/web/packages/ttbbeer/ttbbeer.pdf)
	- An R data package of beer statistics from U.S. Department of the Treasury, Alcohol and Tobacco Tax and Trade Bureau (TTB)
	
###### Packages GitHub only

These packages can be installed with:


```r
library(devtools)
install_github("USERNAME/PACKAGENAME")
```

`USERNAME` refers to the user name of the developer of the package. For example, for the first package listed below, `USERNAME` is `hadley` and `PACKAGENAME` is `emo`.

The package manuals are linked below, however developers of the packages might have additional information on the GitHub repo of the package.

- [`emo`](https://github.com/hadley/emo) 
	- The goal of emo(ji) is to make it very easy to insert emoji into R Markdown documents 
- [`gganimate`](https://github.com/dgrtwo/gganimate)
	- Create easy animations with ggplot2 
- [`emokid`](https://github.com/itsrainingdata/emokid)
	- For those times when you're having trouble expressing how you feel about your broken code.
- [`prenoms`](https://github.com/ThinkR-open/prenoms)
	- First names given to babies in metropolitan France between 1900 and 2015.
- [`dadjoke`](https://github.com/jhollist/dadjoke/)
	- The goal of dadjoke is to make you laugh in spite of yourself.
- [`cooking`](https://github.com/krlmlr/cooking)
	- Chopping, peeling, frying, and cooking various ingredients, and combining them to a delicious ragout. Also includes buying them from a local supermarket.
- [`kandinsky`](https://github.com/gsimchoni/kandinsky)
	- Turn any dataset into a Kandinsky paintingy
- [`emoGG`](https://github.com/dill/emoGG)
	- Use emoji in your ggplot2 plots.
- [`lego`](https://github.com/seankross/lego)
	- This R data package contains information about every Lego set manufactured from 1970 to 2015, a total of 6172 sets. 
- [`bingo`](https://github.com/jennybc/bingo)
	- Generate Bingo cards
- [`CatterPlots`](https://github.com/Gibbsdavidl/CatterPlots)
	- Plots with Cats 

##### Task

Install the package that you pick.
Then, load the package with the `library` function.
Finally, do something with the package.
You do not need to do anything too complicated.
Your goal here is to read and understand the package documentation to carry out a simple task.

Edit the R Markdown document and your final submission should include both text and code intertwined.
If you simply recreate the code examples from the documentation and provide a narrative of what it is doing, this would be considered *sufficient*.
Effectively adding your own creative twist, without being distracting, would be considered *excellent*.

As you are creating your R Markdown report be sure to answer these questions:

1. What package are you using?  State the name, whether it was on CRAN or GitHub, and provide the code you used for loading it.
2. What are you doing with the package?  Provide a narrative including code and output.

Knit your completed `.Rmd` file.
Commit and push to GitHub your `.Rmd` file and the `.md` and `application04_files` folder that are automatically created when you knit.

#### 3. Reflection
  
After you have completed Tasks 1 and 2 go back to the **Application Task 4** assignment page on [Bb](https://mybb.gvsu.edu).
You will submit your reflection here that minimally includes:

- A clickable link to your Application Task 4 repository.
- A reflection on what was hard/easy, problems you came across and how you solved them, helpful tutorials you read, etc.
