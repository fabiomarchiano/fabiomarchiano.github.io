---
layout: page
title: Wave Clock
description: Processing + p5.js
img: /assets/img/WaveClock.jpg
---

Had some fun messing around with the artwork *Wave Clock* (2009) by Matt Pearson.
That's a cool starting point to reason about what **randomness** is and its meaning when associated with computer's calculations. We can use Perlin noise (developed in the ‘80 by Ken Perlin), as we did in this case, to simulate a more “naturalist” variance.
Good to know that we can already obtain cool and unexpected results by applying some randomness to basic shapes!  
<br>

<script src="/assets/js/processing.js"></script>
<script src="/assets/js/p5.min.js"></script>

<div id="sketch"> </div>

<script>

//global variables
let _angnoise;
let _radiusnoise;
let _xnoise;
let _ynoise;
let _angle;
let _radius;
let _strokeCol;
let _strokeChange;

function setup() {

  width = $(window).width();
  height = $(window).height();
  if(width>720){
  	width = 720;
  	height = 480;
  }
if( /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent) ) {
	width = 300;
  	height = 300;
 
}
  let canvas = createCanvas(width, height);
  canvas.parent("sketch");
  smooth();
  frameRate(20);
  background(255);
  noFill();
  _strokeCol = 254;
  _strokeChange = -1;
  _angle = -PI/2;
  _radiusnoise=0;
  _radius=0;
  _angnoise=0;
  _xnoise=0;
  _ynoise=0;

}

function draw(){

  //add some noise to the radius
  _radiusnoise += 0.005;
  _radius += (noise(_radiusnoise)*550)+1;

  //add som noise to the angle
  _angnoise += 0.005; 
  _angle += (noise(_angnoise)*6)-3;
  
  if(_angle>360){_angle -= 360;}
  if(_angle<0){_angle += 360;}
  
  //add some noise to the center position
  _xnoise+=0.01;
  _ynoise+=0.01;
  let centerX=width/2 + (noise(_xnoise)*100)-50;
  let centerY=height/2 + (noise(_ynoise)*100)-50;
  
  //compute points opposite to the center
  let rad = radians(_angle);
  let x1= centerX+(_radius*cos(rad));
  let y1= centerY+(_radius*sin(rad));
  
  let opprad = rad + PI;
  let x2= centerX+(_radius*cos(opprad));
  let y2= centerY+(_radius*sin(opprad));
  
  //compute stroke color
  _strokeCol += _strokeChange;
  if(_strokeCol>240){_strokeChange = -1;}
  if(_strokeCol<40){_strokeChange = 1;}
  
  //draw
  stroke(_strokeCol,60);
  strokeWeight(1);
  line(x1,y1,x2,y2);

}

function keyPressed() {

	if (keyCode === ENTER) {
	saveCanvas(canvas, 'WaveClock_FabioMarchiano', 'jpg');
	}

	if (key == 'r') {
		
		let randCol=random(255);
		background(randCol);
	}else{
    alert("r and ENTER are the only input allowed for this project!:)");
  }


}

function touchStarted() {


  let randCol=random(255);

	background(randCol);

 }


</script>

<br>

Press 'r' if you want the clock to restart with a random background.<br>
If you like what you see save it pressing ENTER.

If you are from the phone, touch on the screen to restart with a random background.