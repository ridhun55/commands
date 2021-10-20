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

============================================

# jQuery Selectors

```shell
1. The element Selector 

  $("button").click(function(){
      $("p").hide();
  });
    
2. The #id Selector

  $("button").click(function(){
    $("#test").hide();
  });

3. The .class Selector

  $("button").click(function(){
    $(".test").hide();
  });
```

# Other jQuery Selectors
```shell
$("*")                  - Selects all elements
$(this)	                - Selects the current HTML element
$("p.xyz")	            - Selects all <p> elements with class="xyz"
$("p:first")	          - Selects the first <p> element
$("ul li:first")        - Selects the first <li> element of the first <ul>
$("a[target='_blank']") - Selects all <a> elements with a target attribute value equal to "_blank"
```

============================================
# jQuery Event Methods

<table class="ws-table-all notranslate">
<tbody><tr>
<th style="width:23%">Mouse Events</th>
<th style="width:25%">Keyboard Events</th>
<th style="width:22%">Form Events</th>
<th>Document/Window Events</th>
</tr>
<tr>
<td>click</td>
<td>keypress</td>
<td>submit</td>
<td>load</td>
</tr>
<tr>
<td>dblclick</td>
<td>keydown</td>
<td>change</td>
<td>resize</td>
</tr>
<tr>
<td>mouseenter</td>
<td>keyup</td>
<td>focus</td>
<td>scroll</td>
</tr>
<tr>
<td>mouseleave</td>
<td>&nbsp;</td>
<td>blur</td>
<td>unload</td>
</tr>
</tbody></table>
  
  
  
  
  
  
