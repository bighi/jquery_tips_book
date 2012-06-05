### Tip #6: Use chained methods to shorten your code

On the previous chapter we saw it's a good think to avoid repeating the same selector many times. We learned how to store the element in a variable. But when you want to call many short methods on the same element, there's an even better way to do it. A way that will spare you some lines of code.

Let's recall the code from the previous example:

@@@ javascript
first_element = $('.element:first');
first_element.click(function(){...});
first_element.addClass("myclass");
first_element.fadeIn('slow');
@@@

Most jQuery methods return the element (or collection of elements) we gave it. This means we can simply call a new method right after the previous one. This is what the professional ninja experts call "chaining methods".

If you chain methods on your first selector, you don't even need to store the element in a variable. Let's try.

@@@ javascript
$('element:first').click(function(){...}).addClass('myClass').fadeIn('slow');
@@@

Just one single line of code! That's like magic! Why don't you use it every time? The problem of working like this is that you may end up with very very long lines of code. It makes your code ugly, and ugly code is not good.

If you still want to chain methods without storing the element and don't want a huge code, there's another option. You can break the line right before the dot. Let's try chaining methods with creating a huge line of code.

@@@ javascript
$('element:first')
  .click(function(){...})
  .addClass('myClass')
  .fadeIn('slow');
@@@

Between this and the method from the previous chapter you can use both, depending on the situation. Sometimes you will need a variable. Sometimes you can just chain them like you're getting a dollar for every chained method. Pick whatever makes your code easier to read and understand.