---
layout: post
title:      "Rails Portfolio Project"
date:       2018-11-30 07:08:42 +0000
permalink:  rails_portfolio_project
---


I did it! I finally completed my Rails Portfolio Project. I faced a lot of struggles with this project, but I feel so accomplished now that I have completed it.

I created a yelp-like app called NYC Restaurant Reviewer, in which users can review and see other user reviews of restaurants in NYC. For this app, I created A LOT of seed files in order for the app to be functional. Luckily it wasn't much of a struggle, it was just very tedious.

The app has five models: user, review, restaurant, cuisine, and neighborhood. A user has_many reviews and has_many restaurants through reviews. A review belongs to a user and a restaurant. Both a neighborhood and cuisine has_many restaurants. And finally, a restaurant has_many reviews and has_many users through reviews.

The first major problem I encountered involved my create method in my reviews_controller. I tried doing "@review = Review.new", but it kept giving me errors. I actually got help when I went to a Flatiron coding meetup (shoutout to Ruth!) and my problem was solved. I was supposed to put "@review = @user.reviews.build(review_params)". This is because my app is heavily based on seed files. I'm not creating a review on a new restaurant, I'm creating a review for a restaurant that already exists. ".new" does not retain the object in memory like ".build".

One of the biggest errors that took me forever to solve was the "validates_uniqueness_of :restaurant_id" validation in the Review model. I wanted my app to only allow a user to review a restaurant only once. When I added this validation, it made it as though if a restaurant has been reviewed by any user already, it cannot be reviewed. After hysterically searching the internet for answers, I finally found that I simply had to add ":scope => :user_id". The entire line of code was supposed to be "validates_uniqueness_of :restaurant_id, :scope => :user_id". This finally allowed for the app to prevent a user from reviewing the same restaurant twice. This checked that the user_id is unique within all rows with the same restaurant_id as the record that is being inserted.

A huge error I faced was in the reviews show page. I don't really know how to explain it in words, but I'll try to explain the best way I can. So for example, if a user whose user_id = 1 creates a review that has an id of 1, the route would look like this: http://localhost:3000/users/1/reviews/1. However, if you change the user_id in the link, for example, http://localhost:3000/users/3/reviews/1, it will show the review as it belongs to the user with the user_id of 3. This error also applies when you change the review id. Basically, what I'm trying to say is, the user_id and the review_id have to match. The user should only be able to open the review that they made. To solve this issue, I had to put this code: 

  def show
    @set_review = Review.find(params[:id])
		@current_user ||= User.find_by(id: session[:user_id])
		@find_user = User.find_by(id: params[:user_id])
		if @current_user != @find_user || @set_review.user_id != @current_user.id
      redirect_to user_reviews_path(@user)
    end
  end

By doing this, I made sure that the routes are accessible only if the review id belongs to the user_id.

Working with CSS was also a struggle in this project. I have not done it in a while and I did not implement CSS in my Sinatra project. I am happy with how my project looks like, but I know I can do a lot more. In future updates, I am planning to rearrange certain aspects and change the font sizes.

Although I faced so many struggles in making this project, I have learned so much. I feel more confident in my skills as a programmer and despite all the challenges and frustrations, I had a lot of fun and feel so accomplished. Overall, I am proud of myself for getting though this and I'm glad I persevered.




