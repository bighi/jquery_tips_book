### Tip #14: Use animate() to change attributes with style

Not many people know this, but you can easily create an animation whenever you change visual CSS attributes of an element. Any numeric attribute change that can be visually perceived by the user can be animated.

Let's say you want to expand a div from 200px wide to 400px wide. Instead of just changing it, you can create a progressive animation where the width grows from 200 to 400.

Just look at the code below:

@@@ javascript
$('#myDiv').animate({"width": 400}, "slow");
@@@

That's it. A simple code that animates my width growth slowly. You can use "normal" or "fast" instead of "slow". You can also use a number to define a duration in milliseconds.

@@@ javascript
$('#myDiv').animate({"width": 400}, "fast");
// OR
$('#myDiv').animate({"width": 400}, 3000); // The animation will take 3 seconds to finish
@@@

If you want to animate multiple attributes at the same time, just declare more attributes inside the hash. Like this:

@@@ javascript
$('#myDiv').animate({"width": 400, "height": 500, "opacity": 0.8}, "slow");
@@@

Any CSS numeric attribute can be animated. Width, height, opacity, font size, etc. The list goes on and on. 

It's important to note again that this only works on numeric attributes. Width is numeric, font-family is not. Background-color and font-color also cannot be animated unless you use a plugin.

Have fun!