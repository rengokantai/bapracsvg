# bapracsvg
##Introduction
Imagine doubling the size of an image from 100 by 100 pixels to 200 by 200 pixels(2x), then that’s not twice as much pixel data; it’s four times as much. 
Four times as much data being sent across the network. Four times as much memory used to display it. Four times the bandwidth...

##Chapter 1. The Basics of Using SVG
Three ways:
1:
```
<img src="pic.svg">
```
2:
```
.class {
   background-image: url(pic.svg);
}
```
3:
inline-svg
##Chapter 2. Software
online:[Mondrian](mondrian.io)
##Chapter 3. Building an Icon System
make svg sprites
##Chapter 4. Build Tools
##Chapter 5. Optimizing SVG
##Chapter 6. Sizing and Scaling SVG

```
<svg class="logo">
   <g class="magic">
   </g>
   <g class="walt">
   </g>
   <g class="disney">
      <path class="d">
   </g>
</svg>
```
```
@media(max-width:1000px){
   .magic{
      display:none;
   }
}
@media(max-width:800px){
   .walt{
      display:none;
   }
}
@media(max-width:600px){
   .disney > *:not(.d){
      display:none;
   }
}
```
##Chapter 7. Animating SVG
SMIL (pronounced smile) sychronized multimedia integration language
```
<circle r="30" cx="50" cy="50" fill="orange">
   <animate attributeName="cx" from="50" to="50" dur="1s" begin="click" fill="freeze">
</circle>
```

fill:optional freeze/remove. like animation-fill-mode  

#####point animation
```
<polygon points=" points .... ">
<animate id="id" attributeName="points"
dur="500ms"
to=" new points"/>
</polygon>
```

animateTransform
```
<animateTransform attributeName="transform" type="rotate" from="0 60 70" to="360 60 70" dur="10s" />
```

####ANIMATING PATHS
```
var path = document.querySelector(".path");
var length =path.getTotalLength();
```
##Chapter 8. Some Design Features
##Chapter 9. Fallbacks

