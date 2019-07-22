---
layout: post
title:      "Rails w/ JS Portfolio Project"
date:       2019-07-22 20:44:18 +0000
permalink:  rails_w_js_portfolio_project
---


After months of struggle, I finally completed my Rails w/ JS Portfolio Project! It was definitely not an easy journey. I worked very hard on my Rails project. I made it to be very direct and user-friendly. It was hard to come up with what else to add and how JavaScript could make the already existing portfolio project better.

A big hurdle I had to overcome was my data appearing as an array that showed `[object object]`. I wanted to render a list of restaurants of a particular cuisine. A restaurant belongs to a cuisine, and a cuisine has many restaurants. I was so confused as to why this kept appearing on my cuisines show page. I solved this problem by adding `const restaurant = this.restaurants.map(restaurant => restaurant.name);` within the Cuisine.prototype.formatShow function. This allowed an array of the names of the restaurants to render as opposed to `[object object]`.

I also struggled fulfilling the form requirement. My form is in a nested route; `/users/${this.user}/reviews/`. A user has many reviews and a review belongs to a user. I kept getting errors because I was doing my construction function wrong. I initially did `this.user = review.user`. I solved the problem by changing it to `this.user = review.user.id`, as I had to specify that the id of the user is what needs to be passed in.

Rendering issues also occured when submitting a form. When submitting a form, sometimes it would render what I wanted, but other times it would render the JSON of the object. I could not figure out why. Dahlia pointed out to me that it was because I had turbolinks in my project. When clicking a link, Turbolinks automatically fetches the page, swaps in its <body>, and merges its <head>, all without incurring the cost of a full page load. This interfered with the rendering. Once I removed turbolinks from my applications.js, layouts index, and gemfile, my form started to work perfectly.

Although it took me ages to finish, I feel very accomplished in completing the project. I learned a lot in making this project and I feel this enhanced my skills even further. I can't wait to get to the React unit and finally graduate!
