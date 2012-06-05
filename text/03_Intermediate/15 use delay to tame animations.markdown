### Tip #15: Use delay to create sequences of animations

In our previous tip we saw how to create an animation composed of one or more attribute change. But these changes happen at the same time. If you want to do two or more animations in sequence, you can't just call `animate()` after `animate()`.

Everytime you call `animate()`, a new animation **starts**. Take a look of the following code:

@@@ javascript
$('#myDiv').animate({"height": 400},"slow").animate({width: 700}, "fast");
@@@

The code above is similar to what many people do when trying to chain animations for the first time. But the results are not the expected. You are telling jQuery to begin the first animation and right after you tell it to begin the second one. Both animations will be happening at the same time and it's possible the second one may finish first (because it's `"fast"`).

This is not the result you want.

If you want the second animation to start only after the first one ends, there are two ways.

#### First Method: Function as a parameter of animate()

The `animate()` method accepts a function. If you do pass one, it will call the function as soon as the animation stops. Look at the example below, where we get the effect we want:

@@@ javascript
$('#myDiv').animate({"height": 400, "slow", function() {
  animate({"width": 700}, "fast");
}});
@@@

#### Second Method: Use delay()

There are moments when you want to delay the second animation but you don't want it to begin exactly when the first one stops. Maybe you want it to begin a little sooner or later. The `delay()` method comes in handy.

This method takes a number as a parameter to define how many milliseconds it should delay execution of the next animation.

Let's say we want the first animation to have a duration of 3 seconds, and we want the second animation to begin half a second BEFORE the other one stops. Here's the code.

@@@ javascript
// Method chaining in several lines as seen on tip #6
$('#myDiv').animate({"height": 400}, 3000) // First animation starts with 3s length
  .delay(2500) // We wait 2.5s
  .animate({"width": 700}, "fast"); // Second animation starts
@@@

You can chain several `delay()` and `animate()` as you wish to create very complex multi-step animations.