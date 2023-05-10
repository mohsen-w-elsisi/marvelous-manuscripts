---
title: "How Minecraft has Infinite Worlds"
date: 2023-05-06T13:38:52+03:00
draft: true
---

Many of us have played games that have an infinite amount of worlds" or "procedurally generated terrain", but what does that mean? I mean surely someone didn't sit down and make the 18 quintillion (18,000,000,000,000,000,000) planets of no man's sky, so how does procedural generation work?

## the definition
There are many for using procedural generation, but they all fall under one general definition: **an algorithm with certain constraints tasked with the creation of content**. let's break down this definition:

- **an algorithm:** as described by the oxford dictionary, an algoritm is "a process or set of rules to be followed in calculations or other problem-solving operations, especially by a computer". basically a program.
- **with certain constraints:** this algorithm needs to given a set of rules that it will follow to give the result that we want. for example: "you can only put sand next to water" or "snow can only be on tall mountains".
- **tasked with the creation of content:** this algorithm in the end produces a planet to discover or an enemy fight or a thousand different pictures of monkeys to sell as NFTs.

## ain't that AI ?
No, it isn't. The way popular AI models work is they analyze massive amounts of the content, then try to create content which vaguely looks like what they were trained on. 

Most of the effort that it would take to make an AI model is in gathering the data that will be used to train the model, while when programming a procedural generation engine, effort goes in to tweaking the limitations manually to try to get it to do what you want.

The quality of an AI depends almost completely on the quality and quantity of its training data. Getting data is hard, especially if you want to make something in a specific style. So for a lone game developer making a thousand worlds and then training an AI on them is more work than coding an algorithm from scratch.

## how it works in Minecraft
As stated before, there are many ways of implementing procedural generation, but the method I'm gonna be exploring to make terrain is one that is very commonly used: **Perlin noise**.

### what is Perlin noise?
Have you ever opened up your TV while the signal was bad and saw something that looked like this...

![noise](../images/noise.jpg)

This is called noise. it's made by giving each pixel (tiny square) in the image a number from 0 to 1. 0 is white, while 1 is black all the decimals in between are different shades of gray. However this is too messy to make a world out of, so in comes Ken Perlin with his famous algorithm (which is a whole nother can of worms) that can generate so called _perlin noise:_

![perlin noise](../images/perlin-noise.jpg)

Here the shifts are gradual, and that's the key thing, because we are gonna use this image as a _height map_

### height map???
The blacker a part of an image is (how high the number assigned is), the higher the elevation of that spot in our world. In other words: imagine each black spot as a tall mountain, and each white spot as a deep ocean.

### finally, we draw the world!
Now we have the noise map which tells us which places of our world are mountains which are flat plains and which are seas, let's make the world:

1. create a cube for each value in the noise map
2. set the height of the cube to match the value it maps to
3. chnge the color of the cube to match what it's supposed to be. ex: green for plains, white for the tops of mountains

*note: for oceans which correspond to very low values, having them drawn at the height they match to will make it so their's a big hole and then water at the very bottom... not what we want. Instead we will ignore the height value when drawing oceans, and instead draw them at the height of gruond next to them*

### the result 
Implementing the method i described above the result is this:

///////////////////// add Iframe ////////////////////////////////////

## conclusion
Procedural generation is quite famous among all game developers for a reason. It allows us to do more with less.

---

## scources

- 


