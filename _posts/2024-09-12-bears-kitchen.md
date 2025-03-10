---
layout: post
title: Bears Kitchen
date: 2024-09-12 00:52 -0400
category: [Project, Web App]
tags: [C#, ASP.NET core, REST API, Swagger, Google Cloud Platform(GCP), OAuth2, YouTube API, Google Vertex AI API, xUnit, Selenium, Microsoft SQL Server]
pin: true
---

## Introduction
---
Worked as: **Back-end Develeoper**   
Bears Kitchen is a web app developed for Conestoga College Capstone Project.

## Research
---
One of our teamates loves cooking. And she told me whenever she finds a recipe in online, she needs to search twice.
I got an idea from her opinion and here is my research.   
1. Youtube
    - Many YouTubers didn't provide text instruction and ingredients list.   
    - We have to watch the entire video from start to finish, which feels like a waste of time.
2. Recipe Websites
    - Most websites don't provide video instructions, so I can't get details of the recipe, like the required heat level.   
    - Some of websites provide a hyperlink to connect with youtube video but it takes me to YouTube.

So we decided to develop an website that provide both content type of text and video in a single page and use AI to transform video's transcript to instruction and ingredients list.

## Development Guide
---
To run the app locally, you must have:
- Visual Studio (for running server)
- Visual Studio Code (for running client)
- Flutter and Dart
- ASP.NET core 7.0
- Microsoft SQL Server

**Stpes:**
1. Clone the repository:
**_`https://github.com/boa-im/bearsKitchen`_**
2. In Visual Studio's NuGet Package Console, execute below command. (Tool -> NuGet Package Manager -> NuGet Package Console)
```shell
$ update-database
```
3. Run the server in visual studio (Ctrl + F5)
4. Run the client in visual studio code

## Pages
---
#### 1. Google Login
![login](https://raw.githubusercontent.com/boa-im/images/main/2.png)
Bears Kitchen is providing **google login system with OAuth2**. User can create a new account via Google or use existing account they already have.

#### 2. Homepage
![homepage](https://raw.githubusercontent.com/boa-im/images/main/1.png)
Once user logged in, user can see the food categories, search bar, and some buttons. Each button navigates user to each page. User can search by keywords or categories.

#### 3. Recipes List
![recipe](https://raw.githubusercontent.com/boa-im/images/main/12.png)
If user clicks one of categories, user can see this page with many recipes. When user clicks one of the videos, **Google Vertex AI** will show user the transformed instruction and ingredients list using the video's transcript. All of the videos are based on YouTube via **YouTube API**.   
To avoid a situation that a video doesn't have any transcript, I added a filter the video must have transcript. The videos can be all languages video. It is because YouTube is already providing transcript translating system. So, I could get the transcript in English.

#### 4. Profile
![profile](https://raw.githubusercontent.com/boa-im/images/main/3.png)
This is the profile page. The profile picture, username, and email came from Google. And User can set the preferences for meal plans. Group Requests button is to check if user gets invitations from groups

#### 5. Group
![group](https://raw.githubusercontent.com/boa-im/images/main/7.png)
This page shows user the groups which the user has joined. It is including group picture, name, and the number of members.

#### 6. Create a New Group
![create](https://raw.githubusercontent.com/boa-im/images/main/5.png)
User can create a new group by entering the group name and selecting the group image.

#### 7. Group Detail
![detail](https://raw.githubusercontent.com/boa-im/images/main/8.png)
Groups are has their own preferneces for group meal plan. User can leave the group or if the user is the leader of the group, user can delete the group as well. To add or remove a member from this group, user needs to click the manage member button.

#### 8. Manage Member
![manage](https://raw.githubusercontent.com/boa-im/images/main/9.png)
In this page, the group leader can see the all group members, and all users list. The group leader can add a new member by clicking Add Member button. If the group leader wants to remove a member from this group, Remove from Group button will work for it.

#### 9. History
![history](https://raw.githubusercontent.com/boa-im/images/main/11.png)
Whenever user clicks a video, the video information will save in the watch history. So user doesn't have to search a video again.

#### 10. Favorites
![favorites](https://raw.githubusercontent.com/boa-im/images/main/10.png)
![youtube](https://raw.githubusercontent.com/boa-im/images/main/13.png)
When user clicks Add to Favorites button in Recipe page, the video information will save the user's favorites list. And, it is because Bears Kitchen is using goolge login system, the first time user added a video into the favorites list, the playlist named Bears Kitchen will be generated in your real YouTube channel.

#### 11. Meal Plans
![mealplan](https://raw.githubusercontent.com/boa-im/images/main/14.png)
Meal plan generating is only for users who has already set the preferences.
Based on the user's preferences, the system will select one random cuisine, and meal type.   
For example, if user's preferences are:
- Tags: Spicy, Vegan, Gluten-Free
- Cuisines: Italian, Korean
- Meal Types: Lunch, Dinner

Then, system select and send ramdomly like **`Spicy, Vegan, Gluten-Free, Korean, Lunch`** or **`Spicy, Vegan, Gluten-Free, Italian, Dinner`** to **Google Vertex AI**. Then AI will generate and show the a meal plan for a week. If users don't like the generated meal plan, they can re-generate meal plan by clicking the 'Regenerate Meal Plan' buttton.

## Demo
---
You can watch the demo video. 
<a href="https://drive.google.com/drive/u/1/folders/1wnBrLqp7wVNte1f0f_RdrCKuvCGyePRt" target="_blank">Click Me!</a>

## Conclusion
---
We ranked on the **Second Place**🏆!!!

Although we had a limited time of 3 months, we could implement a lot of features. I almost worked on this project 40 hrs a week like a full-time job.

It was the most exciting project I've ever done because it was the first time to use **AI**. I didn't know there are so many steps for setting AI, but based on this experience, I could learn how to follow the API documents.   
And the funny story is that at that moment Google only provided example code in Java, Python, and Node.js. So, I had to convert all the code from Java to C#. What a lucky situdation that I already learned Java from college.

Also, this project is mainly my first project that I worked as a team member. Before this project, I almost worked as a full-stack developer or it was my own project. When I first tried to send data using **JSON** and got the 200(OK) resposnse from my team's front-end developer, I almost cried because I was so happy.

I think I could grow up as a software developer and improve my programming skills. Also, I could get great achivement and confident in programming.