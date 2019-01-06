---
layout: post
title:      "React, Redux, Rejoice..."
date:       2019-01-06 02:18:24 +0000
permalink:  react_redux_rejoice
---


I find that building and creating my own code is the best method for me to learn material. The labs are great but you don't get the flexibility to be creative with them. All the months of studying and digesting code has finally paid off. I am finally finished with my final project for Flatiron school but by no means my last project. I created a community driven platform for users to share their travel adventures. It's a simple CRUD application, where a user can CREATE, READ, UPDATE, and DELETE trips. 

So let's begin with the basic principles of a react/redux application. The most important thing to keep in mind is how the data flows through the application. React is a JS library that helps us to divide up our app into multiple components but doesn't doesn't specify  how we should keep track of the data and the events. This is where Redux comes in to play. Redux provides a way to delagate the state and actions to the different components. When connecting your rails api backend to the frontend client side application with Redux, you must create a store which will handle storing all the state object from each component. 

**Redux**
- A single source of truth, the state of your whole application is stored in an object tree within a single store.
- State is read-only
- Changes are made with pure functions.

**Action Creator**
- Are in charge of creatig actions, which is the path that all changes and interactions should go through. Any time you want to change the state of the app or have the view render differently, we have to go through the action creator
- Example: Add or create new trips or delete comments. 
- the action creatror creates an action with a type and payload
- Exmaple of an action would be like CREATE_TRIP or DELETE_COMMENT
- once we get the action payload, we pass that action off to the dispatcher
- If you are having any errors you can check to see what data we are actually reciving from the backend. 
- It's important to make sure your backend rails API is working properly. 
 

**Disptacher**
- It's the connective tissue between the action/reducers and the store. 
- Dispatch alllows you to render data from the store as props. 
- Need to make sure that the data we are rendering is correct. 

**The store**
- This is where all te state of the application is held. The store is the ontainer and state lives in the container. 

**Reducers**
- Reducers are pure functions that take the previous state and an action, and return the next state. 

Redux helps by giving each React component tht exact piece of state it needs. Understanding how all the connections work together will help  to debug and write better code. Once I understood the flow, I was able to follow it up from the child component and up the tree. It'll take some practice so don't give up!





