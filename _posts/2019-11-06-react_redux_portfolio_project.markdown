---
layout: post
title:      "React/Redux Portfolio Project"
date:       2019-11-06 14:05:20 -0500
permalink:  react_redux_portfolio_project
---


At long last! I have finally completed the final portfolio project for the Flatiron School! 

For my final project, I decided to create a luxury fragrance web application, which shows a list of perfumes and allows users to "like" and leave a comment on specific perfumes. I love fragrances was inspired by fragrantica.com, and decided to make a much simpler version of it.

For the Rails backend, I created my own seed files. I initially wanted to create this project with an external API, but I found it to be much simpler creating my own backend API. Setting up the backend was actually an easy task for me. I knew exactly how I wanted my application to be structured.

The biggest challenge I faced when doing the frontend was the implementation of the "like" button. At first, the error was it would not recognize what was being iterated. Then after some fixing, it would increment but only show during page refresh. To simplify the problem, I created a separate LikePerfumeButton component instead of putting the button in the CommentsForm. I then realized that I was running `perfumeId` as opposed to `perfume_id` (which is the correct attribute name in the backend for a comment) when running `this.state` in my CommentsForm. I also had to change `method: "POST"` to `method: "PUT"`, since it was an update and not a post. 

The two pieces of advice that really helped me with this project were 1.) Keep the project simple & 2.) Build the actions and reducers first. I initially wanted to do a MyVidster clone, in which users can search for YouTube videos and save it to their favorites. I found it too challenging because I needed to use an external API and I did not know whether to put it in the frontend or in the rails backend. Luckily, I had the perfumes idea as a backup and it was much simpler and easier to create, since I did not need to create users or use an external API. Building the actions and reducers first helped me get a sense of how I want the application to work and be structured. Because of the naming conventions using words like "set", "fetch", and "create", it helped greatly with setting up the components and how I wanted them to operate.

Overall, I learned a lot from this project and actually had fun doing it. I came into this project with a different mindset than the other projects; I approached it with a lot less pressure and instead maintained a positive outlook. This project really allowed me to be more confident with my skills as a programmer, and I'm very excited to keep improving. 

