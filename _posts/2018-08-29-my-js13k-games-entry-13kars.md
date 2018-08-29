---
layout:       post
title:        "My JS13K Games 2018 Entry: 13Kars"
description:  "I made a simple car game for JS13K Games 2018."
date:         2018-08-29 21:21:21
categories:   javascript js js13k game foss
image:        /images/2018-08-29-13kars.png
---
**[JS13K Games][js13k]** is a JavaScript coding competition that limits your
game file size to 13 kilobytes. Theme for this year is **offline** even thought
there is a server category. I wrote [13Kars][13kars] for desktop category.

## Motivation
JS13K has been there for few years but this is the first time I heard about it.
File size limit of 13 kilobytes was my main motivation to start writing
something. I thought since it's so small, I can write something small and silly
without spending lot of time.

## Tools
I used [Kontra.js][kontra], a lightweight JavaScript game engine. Rest of the
code is pure JavaScript, CSS and HTML5. Since I had enough space to include
some sound effects, I used [jsfxr][jsfxr] to generate them.

[![13Kars](/images/2018-08-29-13kars.png "13Kars")][13kars]

## Takeaways
With all those fancy game engines it is really easy to start developing games.
You don't have to be good with arts, there are great resources like
[OpenGameArt][opengameart] project which offers graphics and music under free
licenses. But in 13Kars, I choose not to use any. :)

When ever I had to use JavaScript/HTML/CSS in my day to day work, I usually use
jQuery and Bootstrap. With this project I had to avoid both. Using pure
JavaScript instead of jQuery isn't a problem. But getting a good responsive
design without Bootstrap was a major pain. That's when I start learning about
[CSS grid][css-grid]. It's amazing.

But that's not the only CSS skill that I acquired.
**[Dynamic CSS][dynamic-css]** is fun to work with. Opens up lots of
possibilities.

## 13Kars
I didn't had any idea on what sort of game I should design. I just started
playing around with Kontra.js. and the result was [13Kars][13kars]. 13kars is a
simple car game where you drive against incoming traffic. Colour theme is
grayscale and all the graphics in that game is computer generated dynamic
graphics. Player's car is controlled by keyboard and objective of the game is
to avoid hitting incoming cars and drive on to fuel cells to keep your car
running.

## Conclusion
I spend mostly a half of my weekend developing this game. With all the skills
that I learned doing that, I'm pretty happy with my effort.

## References
* [Github repository][github-13kars]
* [JS13K Games entry][js13k-13kars]

[js13k]:         https://2018.js13kgames.com/
[13kars]:        https://13kars.fq.nz/
[kontra]:        https://straker.github.io/kontra/
[jsfxr]:         http://github.grumdrig.com/jsfxr/
[opengameart]:   https://opengameart.org/
[css-grid]:      https://css-tricks.com/snippets/css/complete-guide-grid/
[dynamic-css]:   https://css-tricks.com/making-custom-properties-css-variables-dynamic/
[github-13kars]: https://github.com/kesara/13kars/
[js13k-13kars]:  https://2018.js13kgames.com/entries/13kars
