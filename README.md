# Icon fonts guide (WIP)

## Table of contents

- [Goal](#goal)
- [Packages](#packages)
    - [Full package](#full-package)
    - [Component package](#component-package)
    - [Custom package](#custom-package)
- [How to use in your project](#how-to-use-in-your-project)

## Goal
This brief document seeks to **optimize the use of icons**, make easier their implementation and improve the performance of each project. Its main goal is that **each project uses only the icons that they really need**.

## Packages
Following this goal, the icon library was reviewed and three different packages were arranged:

### 1. Full package

Includes all the icons that we use in MercadoLibre. Most of them are courtesy of [Font Awesome](http://fortawesome.github.io/Font-Awesome/cheatsheet/) however are a few exceptions: 

- `icon-user` and `icon-users` are from **MFG Labs** library.
- `icon-offical-store`, `icon-card`, `icon-cash`, `icon-motorcycle` and `icon-trash` are custom so you must import their corresponding **SVG file** provided in this repo. To do this, simply drag and drop your files into [Fontello](http://www.fontello.com). 

You can use the full package from (…)

### 2. Component package

Includes only the icons that a particular component need. Eg.: Navigation Component (header + footer), Feedback Component, Reputation Component, etc.

You can download packages from (…)

### 3. Custom package

Includes only the icons that a particular project needs. You can create your own package following this simple steps: 

- Go to [Fontello](http://www.fontello.com)
- Choose the icons you need from the list or include your own svg files provided in this repo.
- Name your font from the upper right corner of the browser. 
- If you included custom svg files, remember to name them from the "Customize names" tab.
- In "Customize codes" setup your characters codes.
- Finally, **download** your font and include it to your project. 

## How to use in your project
WIP
