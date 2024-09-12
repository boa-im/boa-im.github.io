---
layout: post
title: Menu Management App
date: 2024-09-10 12:41 -0400
category: [Project, Mobile App]
tags: [Android, Angular, TypeScript, Bootstrap, Web SQL, HTML, Google Map API]
---

## Introduction
---
Menu managment app is an Android app to combine all features into one app for restaurants and customers.

## Research
---
There are 2 app for restaurants.
- Manager app to check the sales and analytics
- Restaurant app to accept orders

And, there are an app for customers.
- Delivery app to order foods

It means if I am owner of a restuarant and I want to order food from my restaurant using delivery app, I need to download 3 apps. I thought it could decrease user experience. That's why I wanted to develeop this app.

## Development Guide
---
To run the app locally, you must have:
- Android Studio
- Angular
- JDK 8.* .  
**Stpes:**
1. Clone the repository:
**_`https://github.com/boa-im/Menu_Management_App.git`_**
2. Run this app using Android Emulator 

## Pages
---
1. Homepage
![homepage](https://github.com/boa-im/Menu_Management_App/blob/master/img/1.png)
In this page, customers can see the restaurant's name, description, and location via **Goolge Maps**.

2. Reservation
![reservation](https://github.com/boa-im/Menu_Management_App/blob/master/img/2.png)
Customers can check their reservations by entering their reservation number.   
And the manager of the restuarant can clear all reservation for memories.

3. Make a reseravtion
![make a reservation](https://github.com/boa-im/Menu_Management_App/blob/master/img/3.png)
Customers need to enter name, email, the number of people, expected date of visit, and time to make a reservation.
After clicking **Add** button, the customer will get an reservation number to modify, check, delete the reservation.

4. Modify the reservation
![modify the reservation](https://github.com/boa-im/Menu_Management_App/blob/master/img/4.png)
If customers enter a right number of reservation, this app will take you this page.
Them, customer can modify all the reservation info or cancle the reservation.

5. Menu
![menu](https://github.com/boa-im/Menu_Management_App/blob/master/img/5.png)
This page is showing all menus added by restaurant's owner.
If customers click the **Order** button, this app will navigate customers to order page

6. Order
![order](https://github.com/boa-im/Menu_Management_App/blob/master/img/6.png)
Customers can select an option like spicy, gluten free, lactose free, etc..
or, can type special instruction!   
**Back to Order** is to cancle to make an order. **Check the Cart** is to check the cart without ordering.

7. Cart
![cart](https://github.com/boa-im/Menu_Management_App/blob/master/img/7.png)
Cutomers can check what they ordered. They can clear the cart and continue to order using buttons.

8. Log In 
![login](https://github.com/boa-im/Menu_Management_App/blob/master/img/8.png)
Mainly, this app is non-login based. But manager of the restaurant have their own account to manage menus.
In this app, the username and password are already set.
If you want to try this you can use with:
- Username: admin
- Password: admin

9. Manage Menus
![manage](https://github.com/boa-im/Menu_Management_App/blob/master/img/9.png)
After successfully logging in as a admin, you can see this page.   
Admin can add a menu using **Add a Menu** buttton, modify the food's name, description and price, and delete a item.

10. Add/Modify a Menu
![add a item](https://github.com/boa-im/Menu_Management_App/blob/master/img/10.png)
Admin can add/modify a menu using this format. Course has 3 options right now; Appeitizers, Main, and Dessert.

## Demo
---
You can watch the demo video. [Click Me!](https://drive.google.com/file/d/1PnR5tDLSYYv5vBsd2ymkVH4h51ItoHrp/view?usp=sharing)

## SWOT Analysis
---

| Strengths | Weaknesses | Opportunities | Threats |
| :-------- | :-------- | :--------- | --------: |
| All-in-one app | Big size app | Growing delivery market | Uber, Doordash, etc.. |
| In app reservation system | Each app for restaurants | No app offers reservation | Open Table App |

## Conclusion
---
While developing this app, I notified there are so many weakness in this app.
For example, customers need to download if they want to order items from different restaurnts
> This means I can't save the storage of my phone.   

But it was really great opportunity to learn the structure of TypeScript and Angular!
My college was focusing on developing web apps more, so I want to use mobile library more like React.js, Vue.js, or Next.js.