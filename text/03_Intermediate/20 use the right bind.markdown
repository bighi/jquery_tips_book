### Tip #20: Use data() to store any data in an element

When I learned this last tip I thought to myself "I will never use this". Oh, how wrong I was. Read this tip, learn it, save it for the future. When you need it you will be thankful.

HTML5 offers us a way to store arbritary data inside elements, using `data-` attributes. You can create any attribute you want as long as the name starts with `data-`. Just like `data-order`, `data-full-name` and `data-price-with-discount`. The value of these attributes are always strings.

Example:

@@@ html
<li class="task" data-order="4" data-created-at="2012/05/17">Do something</li>
@@@

jQuery builds upon it and offers you a way to store anything in an element by the use of the `data()` method. The first parameter is the name of the attribute to store (with the `data-` part). The second attribute is optional. You give it a second parameter, it you will change its value. If no second parameter is passed, the value of the data attribute is returned.

Let's see it in action:

@@@ javascript
$('li.task:first').data('order', '1'); // Here I store the value 1 at the data-order attribute
$('li.task:first').data('order'); // Here I recover out the value of data-order
@@@

Here starts the magic. The `data()` method allows us to store **anything**, including functions and objects. Look at the example below, where I store a function inside an element.

@@@ javascript
// Store an anonymous function inside an element
$('li.task:first').data('method', function() {
    console.log("This function is INSIDE the element");
});
@@@

This opens up a sea of possibilities! You could store numbers, strings, functions, objects. You could store a different function inside every element, and then just call it without having to know which function it is. Polymorfism working in a weird and abstract way.