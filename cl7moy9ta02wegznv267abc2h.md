## Rainyday.js - Raindrops effect with Js & Canvas

Today, i came across an awesome animation js library which gives rain drops effects using js. So i wanted to share this with you. 

### Rainyday.js

A simple script for simulating raindrops falling on a glass surface. Features a clear API to easily control most of the script variables in order to achieve the most realistic effect - either specify the rain intensity and draw a static picture or run it as an animation with collision detection and complete rain physics.

The first step of the approach is to draw the original picture on the HTML5 canvas and applying the blur effect¹. In the next phase a second (transparent) canvas is added to the DOM over the original one in order to emulate the glass surface. Randomly distributed raindrops are then placed on the glass. The effect is improved by having the drops take irregular shapes as well as a reflection of the original image in the raindrop, based on previously calculated miniatures.

- Author: https://github.com/konstantinos-tsatsarounos
- Github: https://github.com/konstantinos-tsatsarounos/rainyday.js
- Updated Version: https://github.com/mubaidr/rainyday.js
- Docs: https://mubaidr.js.org/rainyday.js/


Example: 

<iframe src="https://mubaidr.js.org/rainyday.js/demo2.html" style="height:500px;width:100%;" title="Rainyday.js demo link"></iframe>



