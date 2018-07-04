---
layout: post
title:      "Best National Park CLI Project "
date:       2018-07-04 18:59:17 +0000
permalink:  best_national_park_cli_project
---


I struggled a bit in the beginning to get my project off the ground. I felt inadequate and didn't even know where to start. Staring at a blank screen was intimidating to say the least. It's reassuring to know that most students are on the same boat. We all have to start somewhere!

I was lucky enough to come across a previous student's post that helped give a clear step-by-step on how to create a brand new project with the IDE.
[Getting Started](http://https://sillhouette.github.io/crowder_news_data_gem). 
This is exactly what I needed to finally start this project. YAY! 

Now that I had all my files up and running and watched and followed along Avi's tutorial. This was really helpful to see his thought process and he created the daily deal gem. It gave me ideas on how to build my own gem.

It is important to commit early and often. I had to constantly remind myself to commit my code to github. I had to learn the hard way by losing code along the way because I forgot to commit! Now that I've finished my project, the below commands are second nature now.


```
git add .
git status
git commit -m "commit message"
git push
```


So for my CLI project I decided to scrape a website to list the best National Park per state. I really enjoyed creating the CLI class and adding the different functionalities. 

The initial part is a greeting and a prompt asking if the user "Are you ready for go on an adventure?"

```
************************************************************
*                                                          *
*          WELCOME TO THE BEST NATIONAL PARKS CLI          *
*                                                          *
*             This app allows you to explore               *
*             the best National park per state             *
*                                                          *
************************************************************
            Are you ready to go on an adventure?
                    Please enter Y or N:
```

If the user enters "Y" it would then list all the 50 states for the user to choose from and the below menu options. 

```
Which State would you like to explore?
Enter a valid number 1-50 or State Name:
Or enter 'list' to view list
Or enter 'exit' to end
```

The user is able to choose a state by entering the corresponding number or the state name. 
The next level would be the State's National Park information. 

```
* NATIONAL PARK *
Yosemite, California

* DESCRIPTION *
Yosemite (one of the most well known rock climbing destinations in the country thanks to its iconic wall, El Capitan) has enough outdoor recreation opportunities and breathtaking scenery for everyone to enjoy. Both Yosemite Falls and Half-Dome are extremely picturesque—landscape photographers around the world travel for an opportunity to shoot in this park. Consider exploring the Tuolumne meadows area on the west side of the park for a more private experience.
```


I'm excited to finish my first project and also grateful to be able to learn from this process. I'm looking forward to my next adventure now!


