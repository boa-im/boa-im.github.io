---
layout: post
title: Tip Calculator
date: 2024-09-12 11:16 -0400
category: [Project, Web App]
tags: [C#, Windows Forms]
pin: true
---

## Introduction
---
Worked as: **Full Stack Develeoper**   
Tip Calculator is a Windows Forms app to automate tip settlement process.

## Background Knowledge
---
1. I'm working as a server at a restaurant.
2. Servers user to calculate their tip by hand.
3. It took about 30 minuties and they made mistakes many times.

## Development Guide
---
To run the app locally, you must follow below steps:

**Stpes:**
1. Download setup.exe from 
**_`https://github.com/boa-im/Tip_Calculator`_**
2. Execute the setup.exe file and allow the permission.
3. Run the downloaded program.

Or, to modify the card tax, server tip, or kitchen tip percentage:

**Stpes:**
1. Clone the repository:
**_`https://github.com/boa-im/Tip_Calculator`_**
2. Open the Tip.V2/form1.cs file and change below part to what you want.
```shell
    // Please modify card tax persent. 
    // If servers can take 95% of the card tip, TaxPercent needs to be 5.
    public int TaxPercent = 5;

    // Please modify the ratio servers and kitchen tip.
    // If servers can take 60% of total tips and kitchen workers take 40%, 
    // ServerTipPercent and KitchenTipPercent need to be 60, 40 each.
    public int ServerTipPercent = 60;
    public int KitchenTipPercent = 40;
```
3. Run the program (ctrl + F5)

## Tip Settlement Process Diagram
---
![diagram](https://raw.githubusercontent.com/boa-im/Tip_Calculator/main/img/chart.jpeg)
This is a diagram to make it easy to understand how the tip will be calculated.

## Program
---
![program](https://raw.githubusercontent.com/boa-im/Tip_Calculator/main/img/form.png){: width="400"}   
Here is how this program looks like. Servers need to enter the amount of tip and the number of servers.
Then the total kitchen tip would be calculated. And if servers enter the hours for cooks, the total tip is going to be devided based on their working hours.

## Demo
---
You can watch the demo video. 
<a href="https://drive.google.com/file/d/115LefJ6f5BESvEeZrR3p-vLnDd_b-H5q/view?usp=sharing" target="_blank">Click Me!</a>

## Conclusion
---
I sold this project to my boss for $100💰

My coworkers and I use this program every night. So, I'm still getiing feedback from them. Basically, the reason this project named V2, is that I upgraded this project in July 2024.
While using previous app, We faced 2 problems.
1. Part 4 was needed.   
For example, 1 server worked between 11am to 4pm, another server worked between 4pm to 6pm, 2 servers worked between 6pm to 9pm, and 1 server work 9pm to 11pm.
2. If I pressed 'Tab' to go next text box, the cursor went somewhere that I didn't want to go.

To solve this problems:
1. I added one more part. So, there are 4 parts now!
2. I changed TabIndex in each tool's properties tab.

Based on this experience, I felt now I became a real software developer. Now I'm thinking to develop a new android app using Vue.js and Nest.js. Please share your idea in commnets if you have!