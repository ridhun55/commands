# Adding jQuery to Your Web Pages
1. Download the jQuery library from jQuery.com
```shell
<head>
  <script src="jquery-3.5.1.min.js"></script>
</head>
```
2. Include jQuery from a CDN, like Google
```shell
<head>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
</head>
```

# jQuery Syntax
The jQuery syntax is tailor-made for selecting HTML elements and performing some action on the element(s).<br/>
Basic syntax is: $(selector).action()<br/>
<br/>
A $ sign to define/access jQuery<br/>
A (selector) to "query (or find)" HTML elements<br/>
A jQuery action() to be performed on the element(s)<br/>
<br/>
Examples:<br/>
<br/>
$(this).hide() - hides the current element.<br/>
$("p").hide() - hides all &lt;p&gt; elements.<br/>
$(".test").hide() - hides all elements with class="test".<br/>
$("#test").hide() - hides the element with id="test".<br/>

# Document Ready Event
used to prevent any jQuery code running before the document is finished loading
```shell
$(document).ready(function(){

  // jQuery methods go here...

});

in short hand methord

$(function(){

  // jQuery methods go here...

});
```

# Example : 1

```shell
<!DOCTYPE html>
<html>
   <head>
      <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
      <script>
         $(document).ready(function()
         {
           $("button").click(function()
           {
             $("h2").hide();
           });
         });
      </script>
   </head>
   <body>
      <h2>This is a heading</h2>
      <button>Click me to hide heading</button>
   </body>
</html>
```

