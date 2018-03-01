---
layout: post
title:      "Rewards Credit Card CLI Data Gem Project"
date:       2018-03-01 16:54:28 -0500
permalink:  rewards_credit_card_cli_data_gem_project
---


The CLI Data Gem Project was one of the most challenging and rewarding projects I've ever done. I have been on hiatus from November to January, which started right before I was supposed to do this project. When I resumed the course again in the end of January, I had to review the entire OO Ruby unit just to make sure I am still on track. I was both very excited and nervous about starting. This is the first portfolio project and I felt extremely nervous because I wanted to do well.


**Starting**

The first step was deciding what I want my project to be. Luckily for me, I knew exactly what I wanted my project to be and the site I wanted to scrape: https://www.nerdwallet.com/the-best-credit-cards. I wanted to do a project based on credit cards. Initially, I wanted to scrape all the credit cards for all the different categories. However, that task was too complex, so I decided to only focus on the best rewards credit card.


**Struggling**

The biggest struggle I faced with this project is the scraping. I was so excited that the site I found was built with a Rails framework and is very organized, but I realized that it is also heavily based on React. The scraper was only giving me the category of "Best Offers for February 2018" as opposed to the one I wanted, which is "Best Rewards Credit Cards". I even tried to use another scraper, Poltergeist, but it was giving me the same thing as Nokogiri was. After a lot of agonizing, I decided to scrape the part of the website that is dedicated to the best rewards credit cards: https://www.nerdwallet.com/blog/top-credit-cards/nerdwallets-best-rewards-credit-cards/. Although I had to change the scraper method since I was scraping a new site, it was quite easy because at that point I was much more comfortable with scraping and the layout was not that much different from the other page. 


**Working with child components**

The hardest part of the scraping was trying to get the Intro APR, Regular APR, and Annual Fee. They all had the same details, down to the ul and li classes. I never worked with scraping "children" before, so thankfully I was able to attend office hours to get help as well as get educated in that concept. I always knew about children components, I just never knew how to scrape them. Here is how I was able to do it:

      card.intro_apr = x.css("ul.card-details li:first-child p.card-details__content").text
      card.regular_apr = x.css("ul.card-details li:nth-child(2) p.card-details__content").text
      card.annual_fee = x.css("ul.card-details li:nth-child(3) p.card-details__content").text


**Layout**

I had a very clear idea as to how I wanted this project to look like. First, I wanted it to welcome the user and provide a numbered list of spending categories. Once the user selects a category by inputting the corresponding number, the gem will show the name of the credit card, the benefits, Intro APR, Regular APR, Annual Fee, and Recommended Credit Score. I laid it out to be as easy to read as possible. To make the gem easier to read and more vibrant to look at, I installed the colorize gem and implemented it in my code.


**Final thoughts**

The CLI Data Gem Project made me struggle A LOT. There were certain points in which I was ready to cry. Once I completed it however, I felt so accomplished and proud of myself. I believe this project also allowed me to become a more competent and confident coder. 


https://github.com/jomaejercito/rewards_credit_card
