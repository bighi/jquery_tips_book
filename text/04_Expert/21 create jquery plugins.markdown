### Tip #21: Create jQuery plugins

Ok, now you're an advanced jQuery user. What's the next step? You develop your own plugin! And it's so easy you'll start to make a lot of plugins every year. Trust me, I know what I'm talking about.

This is the basis of it all, just pay attention:

**To make your own jQuery function, all you have to do it creating a new function inside `$.fn`**

@@@ javascript
$.fn.removeAndAlert = function() {
    $(this).remove();
    alert('Your element was removed. This plugin works');
};
@@@

Then you use you new method by calling:

@@@ javascript
$('#some_element').removeAndAlert();
@@@

How does it work? The `$()` function passes the matched element to our `removeAndAlert()` function as the `this` variable. If you look at our plugin code, you'll see we use $(this) to refer to the matched element.

It works, but it's not very well done. We have a few problems with this code and we can make it way better by following the best practices of jQuery plugins. First, we're calling $ but we can never make sure that the $ symbol refers to the jQuery variable. There are other javascript frameworks claiming the $ variable.

The second problem is that jQuery functions operate over the selector, but the selector my have matched more than one element.

To solve our first problem, we must make sure that the `$` variable points to jQuery. We do this by encapsulating our plugin function inside an anonymous function in javascript. This sounds as comething complicated, but it's actually very easy. Look at the code below:

@@@ javascript
(function($){
    $.fn.removeAndAlert = function() {
        $(this).remove();
        alert('Your element was removed. This plugin works');
    };
})(jQuery);
@@@

What have we added here? There's an outer function containing our plugin. This function declares one argument called `$`. The we call this function (last line of code) passing the jQuery variable. This means we're 100% sure our `$` variable references `jQuery` when inside the containing function.

How do we solve our second problem? We want to make sure our function will do it's magic inside **each** matched element. To do this you won't just refer to `this`as if it's one single element. We're gonna iterate over it.

Let's redo our code one more time.

@@@ javascript
(function($){
    $.fn.removeAndAlert = function() {
        $(this).each(function() {
            // The each() function changes the meaning of $(this)
            // Now $(this) references the current element being iterated,
            // not the whole collection of matched elements.
            $(this).remove();
        });
        alert('Your element(s) have been destroyed! The plugin works!');
    };
})(jQuery);
@@@

The $(this).each() function will iterate over your collection of matched elements. It doesn't matter if there's 1, 3, 10 or even 0 elements in the collection. The function inside `each()` will be called once for each matched element. This way we can remove them all!

The code below uses our new function to remove every link (`<a>`) in the page and then alert.

@@@ javascript
$('a').removeAndAlert();
@@@

The $('a') selector will match ANY link inside your page, so it'll probably match more than 1. But now our function is smart enough to handle these cases.

Our plugin is looking very good right now. It works as expected and has no bugs. But it's not perfect yet. There's one little detail still missing.

Most jQuery functions allow you to chain them to do many things over the selector. [See tip #6][] for more details on chaining. Our current code won't allow it, but it's something very easy to do. The trick to make chaining work is that your function must return the matched elements. To do that, we'll add the word `return` before our `$(this).each()` call.

This is the final version of the code:

@@@ javascript
(function($){
    $.fn.removeAndAlert = function() {
        return $(this).each(function() {
            // The each() function changes the meaning of $(this)
            // Now $(this) references the current element being iterated,
            // not the whole collection of matched elements.
            $(this).remove();
        });
        alert('Your element(s) have been destroyed! The plugin works!');
    };
})(jQuery);
@@@

Just save your code in a `.js` file and your plugin is ready!