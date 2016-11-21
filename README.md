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

####point animation
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

###ANIMATING PATHS
```
var path = document.querySelector(".path");
var length =path.getTotalLength();
```

###ANIMATING SVG WITH JAVASCRIPT
```
var circle = document.getElementById("orange"), positionX=0;
var interval = setInterval(function(){
   positionX +=0;
   if(positionX>500){
      position=0;
   }
   circle.setAtttribute("cx",positionX);
},20)
```

setInterval isnt ideal for animations because the browser doesnot really optimize it  

requestAnimationFrame (close 60FPS)
##Chapter 8. Some Design Features
###FILTERS
```
.greyscale{
   filter: grayscale(100%);
}
```
filter
```
<filter id="grayscale">
   <feColorMatrix type="saturate" values="0" />
</filter>
```
apply filter via CSS
```
.greyscale-me{
   filter: url("#grayscale");
   filter: url("filters.svg#grayscale"); //use external file 
}
```

filter
```
<g filter="url(#grayscale)">
</g>
```

```
img{
   filter: url("#grayscale");
}
img:hover, img:focus{
   filter: none;
}
```
```
<filter id="blur">
   <feGaussianBlur in="SourceGraphic" stdDeviation="3" y="-" />
</filter>
```

```
<filter id="turbulence">
   <feTurbulence type="fractalNoise" baseFrequency="0.015" numOctaves="2" result="turbulences_3" data-filterId="3"/>
</filter>
```
```
<filter id="turbulence">
   <feTurbulence type="fractalNoise" baseFrequency="0.015" numOctaves="2" result="tub_3" data-filterId="3" />
   <feDisplacementMap xChannelSelector="R" yChannelSelector="G" in="SourceGraphic" in2="tub_3" scale="65" />
</filter>
```
##Chapter 9. Fallbacks
```
<svg width="100%" height="100%">
   <pattern id="pt" x="0" y="0" width="20" height="20" patternUnits="userSpaceOnUse">
   <circle cx="10" cy="10" r="10" fill="#f06060" />
   </pattern>
   <rect x="0" y="0" width="100%" height="100%" fill="url(#pattern-circles)" />  //use this pattern
</svg>
```

