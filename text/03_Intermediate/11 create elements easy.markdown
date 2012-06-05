### Tip #11: Create elements on the fly with ease

There are moments when you need to create a new element and insert it into your page. You can do it the old JavaScript way (that's the way old people do, and it's ugly and wordy) or you can do it the beautiful way. If you prefer the latter, come with to the next paragraphs.

The first thing you should know is that you're going to use the same old $() function. Surprised, right? No? OK.

Let's pretend you have a need to insert a new link in your page. How do you create a new `<a>` element?

@@@ javascript
$('<a>');
@@@

Voilá! That small code is enough to tell jQuery you want to create an `<a>` tag. If you're a perceptive person you'll see this element is being created and discarded, because it's not being inserted anywhere in the page. Let's fix this.

@@@ javascript
$('<a>').appendTo('p:first');
@@@

Ah, now we're on to something. We are creating a new empty `<a>` tag and inserting it at the end (`appendTo()`) of the first paragraph. You could use `prependTo()` to insert it at the beginning.

But our link is empty and boring! *How do I put stuff in my link?* you may ask. Stick with me and you'll see. To be continued...

...right now. We want to add at least 2 things to our link: a text and an address. Let's first do it the basic way.

@@@ javascript
$('<a href="http://disney.com">Here be Mickey</a>').appendTo('p:first');
@@@

See what I did there? I just declared an HTML tag inside $() just like I would do in HTML code. That's the most basic way of telling jQuery to create a new element. But there are two issues. First, when you want to create an element with a lot of attributes, this is going to become a very long line of code. Second, if you want to define programatically the value of these attributes, this is going to become a mess of string concatenation.

Being jQuery the beautiful framework it is, it gives us a better way to do this. Let's do again the previous `<a>` tag, this time with an id and a class, using the second method:

@@@ javascript
$('<a>', {
  href: 'http://disney.com',
  text: 'Here be Mickey',
  class: 'linkClass',
  id: 'mickey'
}).appendTo('p:first');
@@@

That is nicer, right? And it's easier to use a variable as the content of any attribute. To create your elements like this you just pass a second parameter, an anonymous object (also called a hash) containing the attributes you want it to be created with.