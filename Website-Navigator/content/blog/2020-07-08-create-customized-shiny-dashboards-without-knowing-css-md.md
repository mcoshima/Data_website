---
title: 'Create Customized Shiny Dashboards: Without Knowing CSS!'
author: Meg
date: '2020-07-08'
image: images/blog/dashboard.jpg
slug: create-customized-shiny-dashboards-without-knowing-css-md
categories:
  - r
  - dashboards
  - shiny
tags: 
  -R
  -Shiny
---
## Problem

Recently, I was making a Shiny Dashboard that I wanted to look nice but I wasn't satisfied with any of available themes and designs. The easiest way to customize a dashboard is to change the color of the skin but you are limited to the pre-selected colors (blue, black, purple, green, red, and yellow). Additionally you can use 3rd party packages such as `semantic.dashboard` or the `shinythemes` to use a Bootstrap theme. All of these look better than the generic "out-of-the-box" dashboard theme, however, I wanted to use a specific color scheme for my dashboard. At first, it seemed like I would need to write a custom style file (in CSS) or add HTML and CSS code in the app, both of which are difficult for someone who is not very familiar with either language. I also wanted to avoid the second option because (this is purely for aesthetics), I found that the extra text made it more difficult to read through and the script overall looked "messy".

## Solution

After a deep Google search, I came upon a fairly new package `dashboardthemes`. In this package, there are 7 pre-made dashboard themes you can use, but it also allows you to easily create your own custom theme *without* writing any CSS or HTML!! This package is exactly what I was looking for. 

### Pre-Made themes:

![](/blog/dashboardthemes/pre-made_themes.png)

## My Theme

The theme I built was based on the [Nord color palette](https://www.nordtheme.com/docs/colors-and-palettes)  
<center>
![](/blog/dashboardthemes/polar_night.png)  
![](/blog/dashboardthemes/snow_storm.png)  
![](/blog/dashboardthemes/frost.png)  
![](/blog/dashboardthemes/aurora.png) 
</center>
and is a "dark-mode" version.  

### General  
I created a new script 'theme_diy.R' and used the function `shinyDashboardThemeDIY()` to create the object `nord_theme`.  The first section is the general section which icludes the font family you want to use, the color of your text, the color of the background for the body of the page, and the font colors that will be used for each status (primary, info, success, warning, and danger). Allowing different font colors for different statuses is nice because sometimes certain colors look better with a dark font rather than a light font. To specify the color, I used the hex code but you can also use the `rgb()` function.  

    theme_nord <- shinyDashboardThemeDIY(
      
      ### general
      appFontFamily = "Arial"
      ,appFontColor = "#D8DEE9"
      ,primaryFontColor = "#434C5E"
      ,infoFontColor = "#434C5E"
      ,successFontColor = "#434C5E"
      ,warningFontColor = "#434C5E"
      ,dangerFontColor = "#434C5E"
      ,bodyBackColor = "#2E3440"

### Header
The second section customizes the header part of the dashboard. You can change the color of the bar, the color of buttons and icons, and the color of them when you hover over them. You can also add a shadow boarder around the header to give it a 3d-dimensional look. I chose not too have a shadow to give it a flat look.  

    ### header
    ,logoBackColor = "#3B4252"
    
    ,headerButtonBackColor = "#3B4252"
    ,headerButtonIconColor = "#4C566A"
    ,headerButtonBackColorHover = "#3B4252"
    ,headerButtonIconColorHover = "#81A1C1"
    
    ,headerBackColor = "#3B4252"
    ,headerBoxShadowColor = ""
    ,headerBoxShadowSize = "0px 0px 0px"
    

The next section is for the sidebar. You can add spacing around objects (padding), shadow boxes, and change the color of the menu background, search bar, and tabs. There are a lot of options for tabs, you can change text color and size, the boarder around a tab, the colors for selected tabs or hovering over one (if you don't want it to be different just set it to the same color as the normal tab color).  

    ### sidebar
      ,sidebarBackColor = "#434C5E"
      ,sidebarPadding = 0
      
      ,sidebarMenuBackColor = "transparent"
      ,sidebarMenuPadding = 0
      ,sidebarMenuBorderRadius = 0
      
      ,sidebarShadowRadius = ""
      ,sidebarShadowColor = "0px 0px 0px"
      
      ,sidebarUserTextColor = "#D8DEE9"
      
      ,sidebarSearchBackColor = "#4C566A"
      ,sidebarSearchIconColor = "#E5E9F0"
      ,sidebarSearchBorderColor = "#4C566A"
      
      ,sidebarTabTextColor = "#ECEFF4"
      ,sidebarTabTextSize = 14
      ,sidebarTabBorderStyle = "none"
      ,sidebarTabBorderColor = "none"
      ,sidebarTabBorderWidth = 0
      
      ,sidebarTabBackColorSelected = "#3B4252"
      ,sidebarTabTextColorSelected = "#ECEFF4"
      ,sidebarTabRadiusSelected = "5px"
      
      ,sidebarTabBackColorHover = "#3B4252"
      ,sidebarTabTextColorHover = "#81A1C1"
      ,sidebarTabBorderStyleHover = "none"
      ,sidebarTabBorderColorHover = "none"
      ,sidebarTabBorderWidthHover = 0
      ,sidebarTabRadiusHover = "5px"

### Boxes  
This section sets the colors for various types of boxes you can use in a dashboard. The `boxBackColor` is for a basic box. Again, I chose not to add a shadow border because I wanted the flat look. I increased the font size so that titles of boxes are 18 pt. You can also set colors for the status options. I chose the following colors:  
![](/blog/dashboardthemes/box_colors.png){width=800px height=200px}


You can also adjust the color of the boxes of a tab, I made mine the same other box backgrounds.  

    ### boxes
      ,boxBackColor = "#434C5E"
      ,boxBorderRadius = 5
      ,boxShadowSize = "0px 0px 0px"
      ,boxShadowColor = ""
      ,boxTitleSize = 18
      ,boxDefaultColor = "#434C5E"
      ,boxPrimaryColor = "#88C0D0"
      ,boxInfoColor = "#8FBCBB"
      ,boxSuccessColor = "#A3BE8C"
      ,boxWarningColor = "#EBCB8B"
      ,boxDangerColor = "#BF616A"
      
      ,tabBoxTabColor = "#434C5E"
      ,tabBoxTabTextSize = 16
      ,tabBoxTabTextColor = "#D8DEE9"
      ,tabBoxTabTextColorSelected = "#D8DEE9"
      ,tabBoxBackColor = "#434C5E"
      ,tabBoxHighlightColor = "#4C566A"
      ,tabBoxBorderRadius = 5 

### Inputs and Tables
The last two sections are where you customize the buttons, text boxes, and tables. You can change the color of the button when you hover over it, and you can adjust the radius of the border. The text box back color changes text boxes and dropdown menu colors. You can change a table's background color, border color and border thickness.  

      ### inputs
      ,buttonBackColor = "#D8DEE9"
      ,buttonTextColor = "#2E3440"
      ,buttonBorderColor = "#2E3440"
      ,buttonBorderRadius = 5
      
      ,buttonBackColorHover = "#E5E9F0"
      ,buttonTextColorHover = "#3B4252"
      ,buttonBorderColorHover = "#2E3440"
      
      ,textboxBackColor = "#4C566A"
      ,textboxBorderColor = "#2E3440"
      ,textboxBorderRadius = 5
      ,textboxBackColorSelect = "#3B4252"
      ,textboxBorderColorSelect = "#2E3440"
      
      ### tables
      ,tableBackColor = "#4C566A"
      ,tableBorderColor = "#2E3440"
      ,tableBorderTopSize = 1
      ,tableBorderRowSize = 1
      
    )


After you have finished setting everything up, you will call your custom theme in the app.R file. At the top of the file, I read in the theme with `source("theme_diy.R")`. Then in the UI body call that theme. 

    ui <- dashboardPage(
      dashboardHeader(),
      dashboardBody(
        theme_nord,
        
        ### the rest of body elements
      )
    )

### Custom Logo  
The theme does not change the logo part of the dashboard. The logo is your dashboard's name or the section in the top left above the side bar. To change this, use the function `shinyDashboardLogoDIY()`. I included this in the same script as the theme. You can specify which text is bold and which is not (boldText and mainText), the size of the text, and add a badge if you want. I did not include a badge in mine and I achieved this by setting `badgeText=""`.  

    logo_nord <- shinyDashboardLogoDIY(
      boldText = "COVID-19"
      ,mainText = "in Your State"
      ,textSize = 18
      ,badgeText = ""
      ,badgeTextColor = ""
      ,badgeTextSize = 0
      ,badgeBackColor = "#3B4252"
      ,badgeBorderRadius = 0
    )


To use your custom logo in your dashboard, source the script at the top of the app.R file, then add it into the UI section.  

     ui <- dashboardPage(
          
          ### ui header
          dashboardHeader(
        
            ### changing logo
            title = logo_nord
            ...
          )
     )

## Final Theme  
![](/blog/2020-07-08-create-customized-shiny-dashboards-without-knowing-css_files/final_theme.PNG)  

### Lessons Learned
Look at the script of a template theme and match the current color to what items it correspondeds to if you are unsure what the argument refers to.  

Save the changes as you go and reload your shiny app each time. 

Follow the guidelines for using the Nord palette (or the palette of your choice) to inform which colors are used for each item.   

Overall, I am extremely satisfied with the theme I made and this package makes it easy to make as many as I desire. Next, I will probably make a "light-mode" Nord theme.