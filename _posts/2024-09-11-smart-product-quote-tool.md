---
layout: post
title: Smart Product Quote Tool
date: 2024-09-11 01:34 -0400
category: [Project, Web App]
tags: [C#, ASP.NET core, Microsoft SQL Server, Bootstrap]
---

## Introduction
---
Worked as: **Leader, Full Stack Develeoper**   
Smart Product Quote Tool is a web app developed for [**Smart Cities Hackathon**](https://2023.senecahackathon.com) from Seneca College. This project is made for [**Mircom**](https://mircom.com) that only have offline shopping mall.

## Background Knowledge
---
1. Each user has the own discount percentage based on the number of they ordered before.
2. All items are assigned a level.
3. If a customer wants to buy level 3 item, then that customer must have level 1 and 2 items.
4. Customers can buy only one item in each level.

## Development Guide
---
To run the app locally, you must have:
- Visual Studio
- .NET 6.0

**Stpes:**
1. Clone the repository:
**_`https://github.com/boa-im/SmartProductQuoteTool_TeamK.git`_**
2. In NuGet Package Console, execute below command. (Tool -> NuGet Package Manager -> NuGet Package Console)
```shell
$ update-database
```
3. Run the program. (Ctrl+F5)
4. You can check the database in 'View -> SQL Server Object Explorer'

## Pages
---
#### Log In
![login](https://raw.githubusercontent.com/boa-im/SmartProductQuoteTool_TeamK/master/img/4.png)
Customers can log in with provided username and password.
By clicking the check box **'Remember Me'** then it would automatically type your username and password when you sign out and want to log in again.

#### Items List
![login](https://raw.githubusercontent.com/boa-im/SmartProductQuoteTool_TeamK/master/img/2.png)
After loggin in, the customer can see the item name, description, original price and discounted price.
Items can be added into the customer's cart via **Add to cart** button.

#### Cart
![login](https://raw.githubusercontent.com/boa-im/SmartProductQuoteTool_TeamK/master/img/3.png)
In the cart page, the customer can modify the quantity of the item or delete the item.
It is because this customer added a level 2 item, this system is suggesting this customer level 3 items.

#### Admin Log In
![login](https://raw.githubusercontent.com/boa-im/SmartProductQuoteTool_TeamK/master/img/5.png)
By loggin in as a admin, the **'Admin'** button is now visable at the top right.
Admin can add a new model, edit the existing item, and delete the item.

#### Add/Edit Model
![login](https://raw.githubusercontent.com/boa-im/SmartProductQuoteTool_TeamK/master/img/6.png)
Admin can add a new model with level, name, description, list price, PV Code, and Quantity.
Or they can edit the existing model.
In this page, quantity means how many items admin can sell (how many item admin have in stock).

## Demo
---
You can watch the demo video. 
<a href="https://drive.google.com/file/d/1ilFOvAYVsRdKsSZs-_MuO7e9DQVa_HgY/view?usp=sharing" target="_blank">Click Me!</a>

## Conclusion
---
It was my first hackathon!!! And we ranked on the final list (**Top 7%**)🏆!!!

I faced so many difficult situation. For example, after my team decided to use C# ASP.NET framework to develop this website, one of my teammates kept saying she has never learned C# before. So, my teammates and I told her we can study together. But on the first day, she said 'I want to give up this hackathon because I can't follow you'. I noticed that I gave her some hard task. So I re-assigned the tasks which are suitable for each level as a leader. So finally she could do her task and also my teammates and I did very well. I think this is why we racked on the final list because we did great job!

And it was really impressing experience to watch the winners' presentations. I could learn how to introduce my project's strength and how to promote my project.   
1. Compare with competitors
: By researching the existing apps, I can share the reason I wanted to make this project.
2. SWOT Analysis
: It is really powerful to get fund from investors.
3. Impressing Demo
: I don't have to show all the features of my project. Just show the main feature that I want to emphasize.

If I have a chance to present my project, I will definitely follow their flow.