---
title: Hive Invaders
date: 2025-03-26
categories: [Projects]
tags: [projects, university, games, python, tkinter]
---

> The date of this post is not indicative of the date of this project. 
{: .prompt-tip }

## Description 
Two dimensional game based on Space Invaders. The player controls a yellow bee at the bottom of the screen that can shoot projectiles, while red and blue enemy bees come down from the top of the screen towards you. 

## Motivation
This project was for my event-driven programming class in university. We had very open-ended requirements from our professor for the projects of this class, so it was very enjoyable being able to work on something with a lot of freedom of choice. While we learned a lot of subtopics in that class, the unit we did on games as a medium of event-driven programming was one that I found the most enjoyable, so I decided to make a version of Space Invaders.

## Features
### Controllable Player
The player controls a yellow bee that starts at the bottom-center of the screen. Using the left and right arrow keys, the bee can move side to side. Pressing the space bar fires a projectile from the yellow bee.
### Enemies
Enemies in this game are also bees, but they're either red or blue, and they start at the top of the screen. They move side to side automatically, and every time any of them hit the edge of the screen, all of them will move down the screen a certain distance, and switch their direction towards the other side of the screen, in unison. 
### Win Condition
The player can win by using their projectiles to destroy the incoming wave of enemies. A message box pops up to let you know that you won, and prompts you to either play again, or quit the application.
### Lose Condition
The player can lose by letting any enemies reach the bottom of the screen. A message box pops up to let you know that you lost, and prompts you to either play again, or quit the application. 
### Second Difficulty
After the player wins, if they select to play again in the message box prompt, the game will change up a bit. A restart function resets the game's canvas and spawns in the enemies again, but this time it initializes the enemies with different speeds depending on their color, making them trickier to shoot down.


## Tech Stack
This project was done in **Python**, using the **TKinter** library. 

## Challenges
One challenge in this project was figuring how to approach the enemy logic for moving down the screen. At first I tied that logic into each individual enemy instance, so that they wouldn't move down the screen until they hit the edge of the screen themselves.

When I tested that version though it was slightly unpleasing on the eyes, as the enemies would clip into each other as they switched directions. 

I figured it was better visually if I made all instances of the enemy switch their direction whenever even one instance of the enemy touched the edge. That change would prevent them from clipping into each other all the time, while also making the enemy seem more hive-minded, like bees should be, fixing that issue.

## Media
![Gameplay Image](../..assets/lib/hive-invaders/hive_invaders_demo_0.png)
_Gameplay Image_

![Gameplay Image](../../assets/lib/hive-invaders/hive_invaders_demo_1.png)
_Gameplay Image_

## Links
You can visit the github repository for this project [here](https://github.com/acortes8/hive_invaders/tree/main).
