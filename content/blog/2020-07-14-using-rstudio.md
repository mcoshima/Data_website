---
title: Using RStudio
author: Meg
date: '2020-07-14'
slug: using-rstudio
image: images/blog/RStudio-Logo-Flat.png
categories:
  - r
tags: []
---

The purpose of this tutorial is to share some "hidden" tricks in RStudio that can improve coding efficiency and overall user experience.    

### Customizing your Console  
You can customize your RStudio setup and layout in the Global Options. You can control everything from the arrangement of your windows, to the font color, to the default working directory and more. Here are just a few examples of settings you can change that may improve the look of your RStudio sessions. Go into Tools -> Global Options and start on the General tab. This is where you can change the default working directory, and control what shows up when you start a new session or saves at the end of a session.  
![](/blog/usingRStudio/General-Preferences.png)


Under the next tab, Code, we can specify formatting styles we want to use. For example, wrap text helps make code more readable by automatically moving text to the next line when it reaches the edge of the window. This also where you can specify autocompletion functions that make coding faster.  

![](/blog/usingRStudio/Code-Preferences.png)


The next tab, Appearance, is where you can change the color scheme of your script. 

![](/blog/usingRStudio/Format-Preferences.png)

Click through some of the other tabs and familiarize yourself with some of the other things you can customize.  
  
### Tools in RStudio  
The history pane shows a searchable list of previously run commands. You can also access them in the console by hitting the `Up` arrow until you find it. The arrow key is good for code that was recently run, while the history pane is better for code that was run earlier in the session.       
  
![](/blog/usingRStudio/History.png)

Names of functions, arguments, objects, and files can be autofilled using tab. To autofill a function, begin typing the name (ie fun) and when you see a drop down box of functions hit tab. This is a snippet and it provides the skeleton for commonly used functions. To import a file, the tab button can help find the file. Begin typing the filepath and hit `Tab` to see a drop down list of files. Scroll through the options using the `Up` and `Down` arrows  and hit `Enter` to select the file or folder you want.    

![](/blog/usingRStudio/tab-autofill-file-search.png)

  
If you want to rename a variable, you can use Rename in Scope. Just highlight the name you want to change, go to Code -> Rename in Scope and it will highlight all occurrences of that exact name so you can edit them all at once.    

![](/blog/usingRStudio/Rename-in-Scope.png)

Sections of code can be folded, or hid, to make it easier to navigate through the script and focus on one section at a time. Braced code (ie functions or loops), code chunks (RMarkdown style), text sections between headers within RMarkdown documents, and code sections are foldable. Sections can be defined in three ways:

    # Style one ---------------------------

    # Style two ===========================

    ### Style three #######################

You can use the Jump To menu at the bottom of the editor window or the outline view at top of the editor window. This shows the section names and you can quickly go to any one you choose.     


![](/blog/usingRStudio/Jumpto-box.png)

### Keyboard Shortcuts  
`Alt` + `-` Assignment arrow  
`Ctrl` + `Alt` + `Shift` + `M` Highlights all occurrences of a word  
`Ctrl` + `Alt` + `Shift` + `Arrow` Creates a second cursor that you can move to lines above or below original 
`Ctrl` + `Shift` + `R`  Inserts new section  
`Ctrl` + `Shift` + `m` Pipping symbol  
`Ctrl` + `Shift` + `F` search for text in all files in a specified folder  
`Ctrl` + `Shift` + `A` Reformats highlighted section to improve readability  
`Ctrl` + `.` Go to file  
`Ctrl` + `Shift` + `C` Comments or uncomments a line
`Alt` + `Shift` + `Down Arrow` Copies entire line or mulitple lines (highlighted) below

For Macs, replace `Ctrl` with `Cmd`

### Organizing Your Script  
It is important to keep your scripts organized and annotated to help you and others remember and understand what lines of code are doing. Well organized scripts save time by making it easy to find what you need and prevent you from having to things repeatedly. Here are a few guidelines for writing nice script.  
  
* Use comments to explain what you are doing in a line or section. 

* Use sections for chunks of code. They can be run as a group, are searchable in the outline view, and can be hidden when not needed to make scrolling through the script eaiser. 

* Use descriptive names when naming scripts, nothing generic or vague like code_01.R. This makes it much easier to go back and find later.

* Put functions into individual scripts so you can easily source them later.

* Keep everything organized and together by projects. 

### How to Use .RProjects  
RProjects are a tool to organize your work and make it completely self-contained and transportable. This is ideal for when you are collaborating with others and working on code together. When a project is created, a file is created that holds the files associated with that project, including temporary files and the environment. When you open a project, the working directory is set to the project directory, the .RHistory file is loaded, previously loaded scripts are in the editor window, and the global environment is loaded. One way to open a new project is to open RStudio and click the create new project button.    

![](/blog/usingRStudio/New-Project.png)
  
You can work with multiple projects at a time in different windows. Another way to create a project is with the package ProjectTemplate. It creates a project directory with pre-defined subfolders to help organize your materials.  

#### Advantages of using ProjectTemplate package    
When you load a project, it searches through the data directory for files and automatically loads any .csv or .sql files it finds.
There is a libraries function that will automatically load the necessary libraries when you load the project. First you need to make sure in the `config/global.dcf` file the `load_libraries: TRUE`. Then check the `libraries` it will print out a list of the ones that will be loaded.  

    install.packages("ProjectTemplate")
    library(ProjectTemplate)
    create.project("SWT_RStudio")
    setwd("./SWT_RStudio") #current working directory /SWT_RStudio
    load.project()

For this example we will be using the mtcars dataset.

    data("mtcars")
    save(mtcars, file = "./data/mtcars.csv")

We saved the dataframe in the data folder. Now when we load the project, it will automatically be read into our environment. Now any scripts that we write with code associated with this project can be saved in the src folder.  You can also load libraries automatically when the project opens. First, open the `config/global.dcf` document in a texteditor and set `load_libraries` to `TRUE`. If there are specific libraries you need for your analysis, you can add them to the next section, libraries.  
Let's try creating a new dataframe of any three variables you want. 

    mtcars_sub <- mtcars[,c(1,2,4)]
    save(mtcars_sub, file = "./data/mtcars_sub.csv")
    
These tricks are small things that can make your coding life easier and more efficient. Projects are really great for work that you are sharing or collaborating on, big projects that involve multiple scripts and files, and a good way to practice organization.   
  
  
*This workshop was taught as part of the 2018 Student Workshop Training Series at USM GCRL.*  