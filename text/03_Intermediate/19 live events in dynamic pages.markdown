### Tip #19: Live events can bind to elements in the future

The regular way to bind functions to events is nice, but it only affects elements that are already on the page when the binding happens. If you're working on a dynamic website where stuff gets added after the page is loaded, you need some way to make sure you're binding events of elements that will appear some time in the future.

Let's say you have a Task List website where tasks are added by javascript and you want to capture not only the events of existing tasks, but of every task yet to be added. Let's explore the `on()` method to know how to do that.

Since jQuery 1.7, the `on()` method is the default recommended method of binding events to functions. A regular binding of the click event works like this:

@@@ javascript
$('a.task').on('click', function() { 
    alert('I was clicked!');
});
@@@

As we saw earlier, this is not enough to capture events of element in the future. To do what we want, it's important to first learn about event bubbling.

#### Event Bubbling

Inside browsers, any uncaptured event bubbles up. Imagine you have the following HTML code:

@@@ html
<div>
    <p>
        <a>Go to Disney!</a>
    </p>
</div>
@@@

When the user clicks on the link, a `click` event is fired. If there's nothing set up to capture click events in the `<a>` element, it will bubble up to our `<p>` element. If nothing captures the event, it will again bubble up to the `<div>` element. And it will keep going up the element tree, up to `<body>`, then `<html>` and then, if it's still not captured, it will fade away.

Why is this important? Because of event delegation!

#### Delegating events

How do we set up code to capture events on **any** task in our task list, including future ones? We tell its parent element to watch out for events! That's event delegation.

And how do we do this in jQuery? Look at the code below:

This is our HTML:

@@@ html
<ul>
    <li><a>Task One</a></li>
    <li><a>Task Two</a></li>
    <li><a>Task Three</a></li>
</ul>
@@@

And our javascript:

@@@ javascript
$('ul li').on('click', 'a', function() {
    alert('a task was clicked!');
});
@@@

If you look closely at the `on()` method, this time I used 3 parameters instead of just 2. Let me break it down and explain it bit by bit.

First of all I'm using the `on()` method on the `<li>` element. He will be the one watching for click events.

As the second parameter I used `'a'` to tell the `<li>` element it will be watching for click events on `<a>` elements. In the background, the following will happen: anytime an event bubbles up to our `<li>`, it will check where it originate from. If it came from any `<a>`, the function will be called.

This means it does not matter how many tasks I add to my list and when I add them, because the `<li>` will watch out for events in **any** `<a>` inside it.
