### Tip #1: Use jQuery from Google's Servers

You all know how to include the jQuery script in your page. But did you know you can get a little weight off your server by including jquery.js from Google’s servers?

All you have to do is use this script tag:

@@@ html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js"></script> 
@@@

This is the path to include version 1.7.2. Change to number to point to whatever version you want to load.

This little trick will make it load faster (Google has better servers than you do) and also save you some bandwidth.

You can also include jQuery-UI by using this script tag:

@@@ html
<script src="https://ajax.googleapis.com/ajax/libs/jqueryui/1.8.18/jquery-ui.min.js"></script> 
@@@

Just remember you can change version number to whatever version you want to load.

In case you’re interested in finding out what other libraries you can use from Google’s servers, you can check the Google Libraries API website: https://developers.google.com/speed/libraries/devguide.