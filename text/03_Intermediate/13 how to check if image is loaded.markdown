### Tip #13: Do something when an image has been loaded

In tip #12 you learned how to dynamically preload images. But there is more to it. There are cases when you want to run a piece of code when the image is loaded. I once needed it myself when trying to make an image gallery and the solution is not very easy to find. So here I am to help you.

Images can fire a `load` event when they have been loaded, but you have to bind a callback to the event BEFORE you set the image's src. It's not technically necessary to do this, but some internet connections these days are so fast they may download the image before you are able to hook your function to that callback. 
So follow my advice and set your callback first.

You can do this by using the `on` method like you would with any other method binding. If you learned jQuery in the old days, you may be using `bind` to do the same. If you do, please stop using `bind` and start to use `on`. It's the new default. Now to the code:

@@@ javascript
// We create an empty image element and store it in a variable
var image = $('<img>');

// We bind a function to the load event
image.on('load', function() { 
    console.log("It's alive!!"); // Just a log to make sure it's working
});

// We use jQuery's attr() method to change the src attribute.
image.attr('src', './funny-cat.jpg');
@@@

When we set the `src` attribute the image will be loaded and our function will be called.