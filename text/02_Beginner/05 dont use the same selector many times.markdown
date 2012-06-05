### Tip #5: Don't repeat the same selector over and over

If you read the previous chapter you know that every selector has a cost, and this cost is paid in time. Every time you use a selector, it takes some time for the jQuery engine to find the element in the page.

When you need to work on the same element many times, it's not very effective to make the engine search for your element again and again. Look at the following code:

@@@ javascript
$('.element:first').click(function(){...});
$('.element:first').addClass("myclass");
$('.element:first').fadeIn('slow');
@@@

Look at the code. It's not very good, right? Why are we making the jQuery engine search for the same element again? We are losing time here! There's a smarter way to do that.

@@@ javascript
first_element = $('.element:first');
first_element.click(function(){...});
first_element.addClass("myclass");
first_element.fadeIn('slow');
@@@

One more line of code, but it's worth it. On the first line we find the element and store it in a variable. Then all we have to do is refer to the variable whenever we want to manipulate that same element again.

In cases where you only want to call a few methods on the same element, there's another way that's even better. Want to know what it is? Come with me to the next chapter!