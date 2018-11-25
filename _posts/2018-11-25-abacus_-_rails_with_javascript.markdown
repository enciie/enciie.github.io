---
layout: post
title:      "Abacus - Rails with JavaScript"
date:       2018-11-25 04:51:44 -0500
permalink:  abacus_-_rails_with_javascript
---


My application is a simple expense tracker that allows a user can create and save groups and create multiple expenses for each group. 

While working on my project and watching the videos on learn.co I came across an awesome cheatsheet for Jquery!  

[jQuery cheatsheet ](https://oscarotero.com/jquery/)



Requirement 1&2: Render at least one index page via JavaScript and an Active Model Serialization JSON Backend. Render at least one show page via JavaScript and an Active Model Serialization JSON Backend.

I fulfilled the above requirement by rendering the expense index page on the group's show page. 
So the group's show page will list all the expenses for that particular group. I used an AJAX GET request to fetch all the expenses. 

The expenses were rendered in JSON format and I used Active Model Serialization to extract and organize the data I needed. I was able to render the has_many relationship between my categories and expenses. 

```
[
{
id: 3,
description: "Beanies",
amount: 20,
created_at: "2018-10-12T00:10:56.984Z",
category: {
name: "Accessories"
},
{
id: 2,
description: "Jeans",
amount: 87.45,
created_at: "2018-10-12T00:10:42.359Z",
category: {
name: "Clothing"
},
},
```

Then I posted to data into a table in the group's show page.


**Delegated event handler to the rescue! **

On my group's show page I included a "create new group form" that would submit a newly created group dynamically to the page. When a new group was created it would be added to a table which would also include a edit and delete link as well. I had difficulty attaching the event listeners to those links. Luckily, after some googling I came across the solution, delegated event handlers. 

Delegated event handlers have the advantage that they can process events from descendant elements that are added to the document at a later time. By picking an element that is guaranteed to be present at the time the delegated event handler is attached, you can use delegated events to avoid the need to frequently attach and remove event handlers.

The issue I was having with my original code was that when a new group was created, the pencil-icon was not originally present at the time the delegated event handler was attached on  $document.ready. 

```
$("a#pencil-icon").on("click", (e)=> {
    e.preventDefault();
    let $pencilIcon = e.target
    let url = $pencilIcon.href
    $.get(url, function(response){
      $(".group-form").hide();
      $(".edit-group").html(response)
    })
  })
	```


NEW CODE:
This allows me to attach the event handler to all the newly created pencil elements based on the closest parent element .

```
$("div.groups-container").on("click", "a#pencil-icon", (e)=> {
    e.preventDefault();
    let $pencilIcon = e.target
    let url = $pencilIcon.href
    $.get(url, function(response){
      $(".group-form").hide();
      $(".edit-group").html(response)
    })
  })
	```


