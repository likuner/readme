```javascript
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>js-ntive-animation</title>
    <style>
      #box{
        width: 200px;
        height: 100px;
        background-color: lightblue;
        position: absolute;
        z-index: 1;
        top: 10px;
        left: 10px;
      }
    </style>
  </head>
  <body>
    <div id="box">Click</div>
    <script>
      function moveEle(elemID, fin_x, fin_y, interval){
        var elem = document.getElementById(elemID);
        if(!elem.style.left){
          elem.style.left = 10 + 'px';
        }
        if(!elem.style.top){
          elem.style.top = 10 + 'px';
        }
        var xpos = parseInt(elem.style.left);
        var ypos = parseInt(elem.style.top);
        // var xpos = parseFloat(elem.style.left);
        // var ypos = parseFloat(elem.style.top);
        var dist = 0;
        if(elem.movement){
          clearTimeout(elem.movement);
        }
        if(xpos == fin_x && ypos == fin_y){
          console.info('end');
          return true;
        }
        if(xpos < fin_x){
          dist = Math.ceil((fin_x - xpos)/20);
          // dist = (fin_x - xpos)/20;
          xpos += dist;
        }
        if(xpos > fin_x){
          dist = Math.ceil((xpos - fin_x)/20);
          // dist = (xpos - fin_x)/20;
          xpos -= dist;
        }
        if(ypos < fin_y){
          dist = Math.ceil((fin_y - ypos)/20);
          // dist = (fin_y - ypos)/20;
          ypos += dist;
        }
        if(ypos > fin_y){
          dist = Math.ceil((ypos - fin_y)/20);
          // dist = (ypos - fin_y)/20;
          ypos -= dist;
        }
        elem.style.left = xpos + 'px';
        elem.style.top = ypos + 'px';

        var self = this;
        var argus = arguments;
        console.info(self === window);
        elem.movement = setTimeout(function(){
          argus.callee.apply(self, argus);
        }, interval);
      }
      window.onload = function(){
        // moveEle('box', 500, 0, 10);
        document.getElementById('box').onclick = function(){
          moveEle('box', 500, 10, 10);
        }
      }
    </script>
  </body>
</html>
```
