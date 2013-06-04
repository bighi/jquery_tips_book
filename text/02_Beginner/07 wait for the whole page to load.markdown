### Tip #7: Wait for the whole page to load

When you're using jQuery, most of the time you'll be manipulating DOM elements (those things on the page). Sometimes your JavaScript may load so fast that your code is going to be executed before the page is ready. 

If you try to make that third paragraph blink and spin and zoom before your browser even knows a third paragraph is supposed to be there, you're going to run into trouble.

In these cases, there's a method to make you code wait for the entire page to load before it runs.

@@@ javascript
$(document).ready(function() {
  // INSERT YOUR CODE HERE
});
@@@

Doing it like this, you can be 100% sure all your HTML and CSS content is loaded before your JavaScript does its magic.

There's also a shorter version for the code above. It's not my personal favorite, but here it is in case you like it better:

@@@ javascript
$(function() {
  // INSERT YOUR CODE HERE
});
@@@
