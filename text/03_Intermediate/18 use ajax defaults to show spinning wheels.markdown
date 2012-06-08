### Tip #18: Set ajax defaults to standardize ajax requests

I was once in a project where there was many different asynchronous interfaces on the same page. Any time the user clicked on something an ajax request was done and it would show a spinning wheel. I was not very experienced in jQuery at that time and I used many times the same code to show the wheel while waiting and then hide it again when the process was completed.

There's a smarter way. There are 3 very handy methods to deal with ajax requests: `ajaxSetup()`, `ajaxStart()` and `ajaxComplete()`.

#### Use ajaxSetup() to set defaults

You can use the `ajaxSetup()` method to set defaults that any ajax method will follow. You can pass it any parameter a normal ajax request would take, and then these parameters will be passed to any ajax method you call.

Look at the example:

@@@ javascript
$.ajaxSetup({
    url: 'http://disney.com', // Mickey likes ajax requests
    dataType: 'json' // I want JSON unless I tell it otherwise
});
@@@

Now every ajax request I do on this page will have these two parameters as default. If I want a different dataType in one request, for example, I give it its own dataType parameter.

#### ajaxStart() and ajaxComplete()

These other two methods let you do something at the **beginning** and the **end** of ajax requests, respectively. Let's pretend we have a method `showIndicator()` to show a spinning wheel and another method called `disableButtons` that... well... disable buttons.

I want to disable buttons and show a spinning wheel while the request is pending. I want to revert it (hide wheel, enable buttons) when it's complete. Instead of repeating the code inside every request, I can do the following:

@@@ javascript
$.ajaxStart(function() {
    showIndicator();
    disableButtons();
});

$.ajaxComplete(function() {
    enableButtons();
    hideIndicator();
});
@@@

That's nice and easy, right? You should be using these methods to save you some time when doing a lot of similar requests.

Some other similar methods you might find useful: `ajaxStop()`, `ajaxError()`, `ajaxSuccess`, `ajaxSend`.