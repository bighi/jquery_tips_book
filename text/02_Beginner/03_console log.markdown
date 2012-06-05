### Tip #3: Use console.log() to see what's wrong

During the development of JavaScript code there are surely those moments where you need to check the value of something. Maybe you need to check if a function is being called, or what the hell is being saved on that variable.

For those moments, console.log() is a gift from heavens, brought to you by Zeus himself.

Every modern browser has a JavaScript console, where errors and warnings go to die. In Chrome, for example, you can open it by clicking on the wench icon, then going to the Tools submenu and then clicking on JavaScript Console.

Every message you log using the console.log() command is shown on your browser's JavaScript Console. It's not a jQuery tip *per se*, but this a great tool when you're doing something complex and error-prone.

You use it like this:

@@@ javascript
console.log("Hello World");
@@@

But error messages are not all. The console is so powerful it can help you inspect HTML elements and JavaScript functions. You can inspect a jQuery selector to see if it's capturing the correct element (or elements).

Example:

@@@ javascript
element = $('.complex-selector:not(.simple)');
console.log(element);
@@@

Then you can see what HTML the variable contains (if any), check the element's properties, etc. If you pass it an object, you can see everything about the object.

So, remember console.log() whenever something is not working as intended. It may save your life! (If your life is the price for not finishing your work in time, I mean)