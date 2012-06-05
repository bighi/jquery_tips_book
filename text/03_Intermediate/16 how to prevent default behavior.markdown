### Tip #16: How to prevent the default behavior in events

When the user submits a form, he's redirect. If another user clicks on a link she goes to a new page. That's default behavior, right?

But what if you don't want it to happen? You don't want the form submission to redirect the user. You don't want the link to take her to another page (or even reload the same page).

What if you want to prevent the default behavior of the event? Again jQuery comes to the rescue.

First you should know this: when you create a function to handle an event, this function can get the event itself as its argument. You just have to declare it takes an argument, like this:

@@@ javascript
$('a#myLink').on('click', function(event) {
  // Do something
});
@@@

Did you see the `event` parameter over there? It will point to the instance of the event that triggered the function. So if a user clicks on that link, the `event` variable will refer to that exact click.

Now that you know this, you just have to know that every event in jQuery has a method called `preventDefault()`. If you call this method anywhere in your function, the default behavior will not happen.

Example:

@@@ javascript
$('a#myLink').on('click', function(event) {
  event.preventDefault(); // Stops default behavior
  alert('You clicked me!');
});
@@@

By the code above, whenever a user clicks the link he will see the alert and that's it. No page redirect. If you call it on a form's submit event, it will not be submitted. On a link's click event, it will not redirect the user. And so on.

This is the basis of building dynamic user interfaces on your website. You can make links and buttons that do something else instead of redirecting the user somewhere else.