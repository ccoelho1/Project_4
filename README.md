##Website Performance Optimization portfolio project- ccoelho1 8/7/2015

###File Index.html
###File Project_2048.html
###File project-mobile.html
###File project-webperf.html

1. inlined style.css
2. added media print to script so this will only run when requested to print
3. Compresses images
4. customized file with new pictures and change headings.
5. Added async to the scripts to avoid the completion of one to go to another
6. Check page on Page speed insights and have >90

###File View/css/Style.css

1. added font size to h1, h2 & h3

###File View/pizza.html

1. inlined View/css/style.css
2. Added async to the scripts to avoid the completion of one to go to another

###File view/js/main.js

1. Added the 'use strict' tag through out main.js ;

2. function changePizzaSizes(size) {

         function changePizzaSizes(size) {
         'use strict'
         //took all 3 statements out of the loop
         //also changed from document.querySelectorAll to document.getElementsByClassName
         var changePizzaSizes = document.getElementsByClassName("randomPizzaContainer");
         var dx = determineDx(changePizzaSizes[0], size);
         var newwidth = (changePizzaSizes[0].offsetWidth + dx) + 'px';
          //change code per recommendation 
         for (var i = 0, len = changePizzaSizes.length; i < len; i++) {
            changePizzaSizes[i].style.width = newwidth;
            }

Checked console.log and less than 5 milliseconds

3. Move complete pizzaDiv statement out of the loop

         var pizzasDiv = document.getElementById("randomPizzas");
         for (var i = 2; i < 100; i++) {
            pizzasDiv.appendChild(pizzaElementGenerator(i));
         }

4. function updatePositions()
         function updatePositions() { 
         'use strict'
          frame++; 
         window.performance.mark("mark_start_frame");
         //changed from document.querySelectorAll('.mover') to document.getElementsByClassName("mover") 
          var items = document.getElementsByClassName("mover");
         // remove scrolltop from loop 
         var scroll = (document.body.scrollTop / 1250);
        //changed code to recommended by reviewer, but I still see a problem with greater than 60 fps
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

         for (var i = 0; i < pizzaLength; i++) {
            phase = Math.sin(scroll + (i % 5));
            items[i].style.left = items[i].basicLeft + 100 * phase + 'px';
    }
5. document.addEventListener('DOMContentLoaded', function() {

         document.addEventListener('DOMContentLoaded', function() {
         'use strict'
         var cols = 8;
         var s = 256;
         //Took these statements out of the loop 
         var elem;
         var movingPizzas = document.getElementById('movingPizzas1');
         //changed from 200 to 50
         for (var i = 0; i < 50; i++) {
            elem = document.createElement('img');
            elem.className = 'mover';
            elem.src = "images/pizza.png";
            elem.style.height = "100px";
            elem.style.width = "73.333px";
            elem.basicLeft = (i % cols) * s;
            elem.style.top = (Math.floor(i / cols) * s) + 'px';
            movingPizzas.appendChild(elem);
         }
         updatePositions();
      });
   
6. All office hours were reviewed and comments taken into consideration
