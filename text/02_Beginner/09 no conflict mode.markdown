### Tip #9: Use no-conflict mode to avoid... guess what... conflict!

When you load jQuery, it creates a super mega powerful $ variable. It's short to type, it's visually different from the rest of the code, it's great.

The problem is that other some JavaScript frameworks are jealous and fat and decided to use the same $ variable. If you load jQuery and one of the other drunk and bald frameworks on the same page, both are claiming the $ variable as their own and then you've got a conflict.

As jQuery is a gentleman framework, it has a "no-conflict mode". When you load it in this mode it will not try to claim $, so other frameworks can do their jobs uninterrupted.

To activate no-conflict mode, you have to use the following code as soon as possible:

@@@ javascript
jQuery.noConflict();
@@@

It will make jQuery let go of the $ variable. Also, if some other framework had claimed $ before jQuery was loaded, jQuery will give back $ to that other framework as it were before jQuery was loaded. So remember, after you activate no-conflict mode, the $ variable will no more point to jQuery.

In these cases you can use the jQuery variable instead of $. If you go back to any example from previous chapters, you can safely replace every instance of `$` for `jQuery` and it will work just the same.

An example of code using jQuery instead of $:

@@@ javascript
jQuery('div#myid').addClass('myClass');
jQuery.ajax({...});
@@@

Now you can go ahead and use any other framework you want along jQuery and there'll be no conflict between them.