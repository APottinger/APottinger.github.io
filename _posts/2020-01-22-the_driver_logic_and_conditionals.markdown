---
layout: post
title:      "the driver: logic and conditionals"
date:       2020-01-23 02:10:17 +0000
permalink:  the_driver_logic_and_conditionals
---


Logic and Conditionals is exactly as it sounds. Logic, our capacity to comprehend and connect pieces of information towards an understanding of a whole concept and conditionals which through evaluation of the root word “condition”, we see that it is some enaction based on a fulfilled requirement. Sounds like gibberish, right? Well, for computers this is quite simple to synthesize; however, it only gets complicated if we the glorious creators and controllers of all machine-kind – mess up. See, we want the data that we code into our programs to make the right decisions. We want them to follow the path we clearly marked out for them; to stop when the light turns red and to race full speed ahead when it turns green! As programmers, we guide the computer’s interpretation of data through conditionals.


Conditionals can be a tricky subject to nail because of the depth at which it can complicate itself. To gain a better understanding of conditionals, let’s imagine our program as a car driving down a path with a destination marked hundreds of miles away. Every 10 miles the car approaches a split in the road and must ask, “Should I go left or right?” and consider which path will lead to the destination. Depending on the *condition* of the road, the car will go down a path that best leads toward the goal.



With that in mind, lets jump into our code. When the data is confronted with some “problem” or conditional, the conditional will inform the data where and how to proceed. In Ruby, conditionals are commonly denoted by statements: if, else, elsif, and unless. Additionally, they are marked by many familiar comparison and logical operators we learned during grade school ( <, > ) and others commont to programming:

`== - equal to`

`<= - less than or equal to`

`>= - greater than or equal to`

`&& - AND`

`|| - OR`


These operators and statement are in place for code to react to them. For example, if the website I code only allows adults, then anyone under the age of eighteen cannot access it due to the age condition coded into the program. In written code, If `age =< 18`, the program would likely output, “You are not old enough to access the site!” `If age == eighteen`, the reaction the code would likely output on screen would display, “Sign in below. If you do not have an account, create one!”


Conditional statements in conjunction with logical operators follow the reasoning of the world. There can be many reasonings and metrics in which a single program can be held accountable for based on time period, the geographic location, height, or even as far as the rationality of the programmer allows! This can sometimes make for a complicated and oversaturation of else/if statements and operatorsto keep up and that can make your code look – well, plain ugly. As Ruby programmers, the appearance of your code should be mirror you: simple and lazy (haha). Yet graceful and smooth! There are ways to accomplish this feat through using the ternary operator (?:). This gives you the advantage of compacting if/else statements into one line of code through asking a question first with two possible outcomes depending on the truthiness of an answer. For example,
`number_of_songs <= ? 3 :skip_playlist: :listen_to_playlist`

Logic and Conditionals can be a tough cookie sometimes; however, the logic and conditionals also have conditions and those conditions are set by you and I. As programmers, the data that is interpreted is solely controlled by what we input. Remember that car driving down the road? Well, from here on out think of yourself as the driver.

