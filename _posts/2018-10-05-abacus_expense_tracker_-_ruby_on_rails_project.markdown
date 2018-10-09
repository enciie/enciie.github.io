---
layout: post
title:      "Abacus Expense Tracker - Ruby On Rails Project"
date:       2018-10-05 05:41:47 -0400
permalink:  abacus_expense_tracker_-_ruby_on_rails_project
---


For my ruby on rails project, I decided to continue to improve and build upon my Sinatra application. Abacus is a personal expense tracker that allows a user to create and manage their own expenses. The app uses four models: Users, Groups, Expenses, and Categories, with Expenses acting as the join table for groups and users.

**My rails project application has the following features:**

1. User login with authentification and authorization. 

2. User can sign-up and log-in with Github using omniauth gem

3. User can view all groups they created

4. User can edit  a group's status as active or inactive

5. User can create, read, update and delete a group

6. User can create, read, update, and delete an expense in a group

7. User can create or choose existing categories for each expense


### Challenges:

**Helper Methods**

Initially, I had a hard time trying to understand helper methods. But after doing some research the answer was pretty straightforward. Methods that are built in the controller do not permeate to your ActionVIew, unless you explicitly tell it by calling it a helper method. 


```
  def current_user
    @current_user ||= User.find(session[:user_id]) if session[:user_id]
  end
	helper_method :current_user
	```

Now that current_user is set as a helper method, I can use it in my view pages without any issues.
In my layout/application.html.erb view, I used it to display the current user's username. 

```
logged in as:<%= current_user.username  %>
```


**Partial with locals**

I didn't know what to do with partials until I realized I really needed one! My group table code was redudant and long which was a big indiactor that I needed to DRY it up.  My group index page lists a users "active" and "inactive" groups in two separate tables. The tables are pretty much identical but the only difference is status column, which is either "active" or "inactive". So I moved the redundant code into it's own partial under *views/groups/table.html.erb*.

```
<table class="table">
  <thead>
    <tr>
      <th colspan = "5"></th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td><strong>Name</strong></td>
      <td><strong>Status</strong></td>
      <td><strong>View</strong></td>
      <td><strong>Edit</strong></td>
      <td><strong>Delete</strong></td>
    </tr>

    <% groups.each do |group| %>
      <tr>
        <td><%= group.name%></td>
        <td><%= group.group_status %></td>
        <td><%= link_to "View Group", group_expenses_path(group)%></td>
        <td><%= link_to "Edit Group", edit_group_path(group)%></td>
        <td><%= link_to "Delete Group", group_path(group), method: :delete, data: { confirm: "Are you sure?" } %></td>
      </tr>
    <% end %>
  </tbody>
</table>
```

The collection "groups" is set as the variable name and for each table it will be set to a different value. 

*views/groups/index.html.erb
*
```
<%= render partial: 'table', locals: {groups: @groups.active_groups }%>

<%= render partial: 'table', locals: {groups: @groups.inactive_groups }%>
```


To break down the code:

`table`  is the name of the parital to render _table.html.erb


`groups`  is the  variable name that will store the different collection

`@groups.active_groups` is the collection for all the user's active groups
 
`@groups.inactive_groups` is the collection for all the user's inactive groups

Using the partial, I only needed to create the table once and not have to duplicate any code. Using the locals key I was able to set the value to different collections to create the proper tables. 


**Refactoring and Single Responsibility Principle**

I think the toughest challenge I had with this project is where I should place the logic. I tried my best to DRY (Don't Repeat Yourself) up my code as much as possible. I know as time goes on it will become second nature. 




