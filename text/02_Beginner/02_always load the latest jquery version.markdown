### Tip #2: How to always load jQuery's latest version

This is a quick tip expanding on the last one. if you want to always load the latest version of jQuery, there are some ways to do this.

#### Method 1: Load it from the jQuery website

Just use this script tag:

@@@ html
<script src="http://code.jquery.com/jquery-latest.min.js"></script>
@@@

#### Method 2: Load it from Google

Do you remember what we did in chapter 1? Google allows you to be less specific when picking a version. If you want to load the latest version from the 1.7.x family (anything starting with 1.7), you do:

@@@ html
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.7/jquery.min.js"></script>
@@@

If you want to load the latest version from the 1.x.x family (any version starting with 1), you do:

@@@ html
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js"></script>
@@@