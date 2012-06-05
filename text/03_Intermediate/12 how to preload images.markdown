### Tip #12: How to preload images

In dynamuc you want to dinamically show images to the user, it's a better practice to load the image before adding the <img> element to your page. This way the image will show up instantly, without the loading time.

This is called preloading and is very easy to do.

Whenever a new <img> element is created with a `src` attribute, your browser downloads the image. What's important is that it happens even if the element isn't anywhere in your page. This means we can create an <img> (read tip #12), store it in a variable (read tip #5) and the image will be already download when we finally insert it into our page.

Let's say we want to preload the image of a funny cat and append it to a paragraph when the user clicks on any link. Because every website gets better with cats.

We preload it by doing:

@@@ javascript
var image = $('<img>', {src: '/funny-cat.jpg'});
@@@

And then you can refer to the variable whenever you want to use it. It will already be preloaded.

@@@ javascript
image.appendTo('p:first');
@@@

Now go and make your dynamic images super fast!