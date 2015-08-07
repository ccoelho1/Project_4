File Index.html
File Project_2048.html
File project-mobile.html
File project-webperf.html


1. inlined style.css
2. added media print to script <link href="css/print.css" rel="stylesheet" media="print"> so this will only run when requested to print
3. Compresses images 
4. customized file with new pictures and change headings.
5. Added async to the scripts to avoid the completion of one to go to another
<script async src="http://www.google-analytics.com/analytics.js"></script> 
<script async src="js/perfmatters.js"></script>
6. Check page on Page speed insights and have >90 


File View/css/Style.css

1. added font size to h1, h2 & h3

File View/pizza.html

1. inlined View/css/style.css
2. Added async to the scripts to avoid the completion of one to go to another
<script type="text/javascript" aync src="js/main.js"></script>

File view/js/main.js

1. function changePizzaSizes(size)

 	  //took all 3 statements out of the loop
      //also changed from document.querySelectorAll to document.getElementsByClassName

      Checked console.log and less than 5 milliseconds 1.8 ms

2. move PizzaDiv out of the loop     


3. function updatePositions()
changed from document.querySelectorAll('.mover') to document.getElementsByClassName("mover")

remove scrolltop from loop
var scroll = (document.body.scrollTop / 1250); 

changed code to recommended by reviewer, but I still see a problem with greater than 60 fps

/*var phase = []; 
 for (var i = 0; i < 5; i++) {
    phase.push(Math.sin(scroll + i) * 100);
}
for (var i = 0, max = items.length; i < max; i++) {
    items[i].style.left = items[i].basicLeft + phase[i%5] + 'px';
}*/

//going back to original code but remove items.length and phase from loop
var pizzaLength = items.length;
var phase;

document.addEventListener('DOMContentLoaded', function() {
//changed from 200 to 50
  for (var i = 0; i < 50; i++) {

