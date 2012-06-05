### Tip #4: Use #id selector to make code faster

jQuery is a fantastic tool that lets you use any CSS3 selector to find HTML elements and some more. But not everyone knows that every selector takes a different time to run.

Let's say you have this HTML element:

@@@ html
<input type="text" id="myid" class="myclass">
@@@

You can find it using many different selectors, like:

@@@ javascript
$('#myid');
$('.myclass')
@@@

Everytime you tell jQuery to find an element it will scan the HTML DOM to find what you want. When you are doing it many times in a row, the time it takes to find your element matter a lot. 

I did a test in my computer to calculate the difference. I ran both selectors 1000 times in a row and logged the time it took my browser to run it.

When I used the *.myclass* selector, it took 5.06 seconds. When I used the *#myid* selector, it took my browser 0.061 seconds to find it one thousand times. That's a **HUGE** difference.

What lesson can we take from this? While you shouldn't go out of your way to make your code faster, but you should use ID to find elements whenever possible.