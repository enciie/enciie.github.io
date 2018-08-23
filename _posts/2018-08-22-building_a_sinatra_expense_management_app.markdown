---
layout: post
title:      "Building a Sinatra expense management app"
date:       2018-08-23 00:53:26 +0000
permalink:  building_a_sinatra_expense_management_app
---


The initial brainstorming is always a challenge. I like to keep track of expenses especially for trips or any group events. So I decided that I would make a simple expense management app. I named my app after the old calculating tool that was used to perform basic mathematical functions, called the abacus. Where an user can create different groups to keep track of all different expenses. 

I used the **corneal gem** to stub out the structure based on the Model-View-Controller(MVC) pattern. This was a big time saver to get my app started. 

### MODELS

The 'logic' of the web application. This is where date is mmanipulated and/or saved. 
For my app I have a total of 3 different model clases:

** User** has many groups and has many expenses, through groups.

**Group ** has many expenses

**Expenses** belongs to a user and a group

### VIEWS

The "frontend", user-facting part of my web application. This is the only part of the app a user interacts with directly. I created different forms for user sign-in, log-in, and create/edit for the groups and expenses. 

** User**
- sign-in
- log-in
- homepage

**Group **
- View all groups for user
- View single group
- Create group
- Edit group

**Expenses** 
- View single expense
- Create expense
- Edit expense

I implemented the CRUD opertaions Create, Read, Update, and Delete for my groups and expenses.

### CONTROLLERS

This is the go-between for models and views. The controller relays data from the browser to the application, and from the application to the browsers. 

**My controllers:**
User_controller,
Group_controller,
Expense_controller, &
Application_controller


### BUILDING THE APP

The most helpful tool I had for creating my app was `binding.pry` and `shotgun`.  I  built my app step by step, by following the RESTful routes and creating corresponding erb files. I would use `binding.pry` to make sure I was saving and working with the correct params from my forms. I would `shotgun` to make sure all the info from my erb files were working properly. 

There are more features I want to add in the future. I want to be able add features for multiples users to be part of the group and split the expenses equally amongst users in that group. This is a work in progress app and I am excited to be able to continue working on it!


