### Tip #8: How to check if an element exists

Sometimes you want to do something but you don't know if an element exists. Since you can't manipulate the nothing, there are times when it's needed to check for the existence of an element.

Everytime you use a jQuery selector it sets a length property equal to the number of elements found. So if you want to know if an element exists you have to check if your selector found at least one.

@@@ javascript
if ($('.myclass').length > 0) {
    // DO SOMETHING HERE
}
@@@

In JavaScript, every number different from zero validates as true. This means you can leave out the `> 0` part.

@@@ javascript
if ($('.myclass').length) {
    // DO SOMETHING HERE
}
@@@