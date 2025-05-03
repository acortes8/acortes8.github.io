---
title: Missile Combmand
date: 2025-04-01
categories: [Projects, University]
tags: [projects, university, games, java, javafx]
description: Two dimensional game based on Missile Command, with a bee theme. Written in Java, with the JavaFX library.
---

> The date of this post is not indicative of the date of this project.
{: .prompt-warning }

## Description 
Two dimensional game based on Missile Command. Called Missile *Combmand* as a play-on-words, since it has a bee theme. The player operates a turret to shoot down incoming targets.

## Motivation
This project was also for my event-driven programming class in university. We had another open-ended project, so I again chose to make my project a video game. However for this one I did it in Java, a language that I'm more comfortable than, when compared to Python.

## Features
#### Controllable Player
The player controls a turret at the center-bottom of the screen. Using the left and right arrow keys, the turret can be aimed. Pressing space fires a missile from the turret. This missile flies in a straight line, while in flight the ability to fire another missile is disable, instead by pressing space again, the missile explodes in flight, taking out anything that gets caught in it's blast radius. Once the missile is detonated by the player, or it flies off screen, the ability to fire another missile is restored.

#### Four Lives
In this game you have four "lives", that come in the form of beehives that flank the sides of your turret. Missiles rain from the sky, targeting these beehives. An impact by one of these enemy missiles, destroys the beehive, reducing your lives by one.

#### Enemies
Enemies in this game are red missiles that target your beehives. Four missiles will always be in flight. Meaning, as soon as you destroy one missile, another missile spawns to replace it. The missile objects are instantiated with a randomized x coordinate and the coordinates to a beehive. So every missile comes in at a different angle, depending on which beehive it's targeting and where in the sky the missile spawned from.

When an enemy missile makes contact with one of the beehives, a little blast animation is played, and then the beehive is removed from the game's state.  

#### Win Condition
This game has no win condition, it's purely a survive as long as you can type of game. There's a score tracker at the bottom-right of the screen that tells you how many enemy missiles you've shot down so far.

#### Lose Condition
The player loses in this game by losing all four beehives. When they lose, the canvas is cleared off of all enemy missiles, and a message is painted on the screen to inform the player that they have lost.

## Tech Stack
This project was done in **Java**, using the **JavaFX** library. Additionally, it is packaged using Maven through IntelliJ.

## Challenges
One challenge I had in this project was figuring out the math for moving the turret's barrel. The barrel is simply two sets of coordinates with a line drawn between them. The left and right arrow keys, when pressed, change the set of coordinates for the barrel's end, and then when the canvas is redrawn, the barrel is updated to its new position. That part of the logic was simple, the tricky part was figuring out the math for how the coordinates should be updated. My initial approach worked, but it didn't follow the path of a perfect circle, so it looked strange the closer you positioned the barrel to the horizon.

I reached out to my professor for help with this problem, to see if he had any pointers. Fortunately, he was reading an older book about the code in arcade games at that time, and he sent me this image that helped me with a better arcing-position logic for my code. Implementing this simple formula fixed the issues I had with my previous implementation.  

![Logic Image](assets/img/posts/missile-combmand/missile_combmand_0.jpg)
_Logic Image_

## Media
![Gameplay Image](assets/img/posts/missile-combmand/missile_combmand_1.jpg)
_Intro Card_

![Gameplay Image](assets/img/posts/missile-combmand/missile_combmand_2.jpg)
_Firing a missile_

![Gameplay Image](assets/img/posts/missile-combmand/missile_combmand_3.jpg)
_Detonating a missile_

![Gameplay Image](assets/img/posts/missile-combmand/missile_combmand_4.jpg)
_Losing beehives_

![Gameplay Image](assets/img/posts/missile-combmand/missile_combmand_5.jpg)
_Game over Card_
## Links
You can visit the github repository for this project [here](https://github.com/acortes8/missile_combmand).
