# Countdown-Timer
This is a countdown timer written in HTML, CSS and JS.
<!DOCTYPE html>
<html lang="en">
<head>
<meta content="text/html;charset=utf-8" http-equiv="Content-Type">
<meta content="utf-8" http-equiv="encoding">
<meta name="author" content="Peter Fralick">
<title>Countdown Timer</title>
<div class="top">Countdown Timer</div>
</head>

<style>
body{
	background-color: grey;
}
.top{
	display: block;
	margin: auto;
	width: 67%;
	text-align: center;
	font-size: 26px;
	font-family: tahoma, serif;
	background-color: tomato;
}
canvas{
	display: block;
	margin: auto;
	background-color: white;
}
h1{
	display: block;
	margin: auto;
	width: 50%;
	text-align: center;
	font-size: 20px;
	font-family: tahoma, serif;
	color: black;
	padding: 5px;
}
.button{
	display: block;
	margin-top: 10px;
	width: 45%;
	text-align: center;
	font-size: 26px;
	font-family: tahoma, serif;
	background-color: DodgerBlue;
	font-family: tahoma, serif;
	cursor: pointer;
}
button{
	display: block;
	margin: auto;
	width: 35%;
	text-align: center;
	font-size: 26px;
	font-family: tahoma, serif;
	background-color: DodgerBlue;
	font-family: tahoma, serif;
	cursor: pointer;
}
input{
	display: block;
	margin: auto;
	padding: 10px;
	width: 30%;
	text-align: center;
	font-size: 30px;
	cursor: pointer;
}
a:hover, button:hover{
		color: red;
}
a {
	text-decoration: none;
	color: black;
}
</style>

<body>
<br>
<br>
<h1>Enter your timer duration (min) and press the Start button.</h1>
<br>
<br>
<input type="number" id="myNumber" placeholder="(min)">

<button onclick="timerFunction()">Start</button>
<!-- <div id="demo"></div> seconds. -->
<canvas id="timerCanvas" width="400" height="100"></canvas>  <!-- countdown timer window -->

<script>
var audio = new Audio('chime.wav');
var framesPerSecondForTimer = 1;

function timerFunction() {
    var sec = Math.floor(60*(document.getElementById("myNumber").value));
	
    // document.getElementById("demo").innerHTML = sec;
	canvas = document.getElementById('timerCanvas');
	canvasContext = canvas.getContext('2d');

	// create a countdown timer 
	
	setInterval(function() {
	drawEverything(sec);
	sec--;
}, 1000/framesPerSecondForTimer);
}

function colorRect(topLeftX, topLeftY, boxWidth, boxHeight, fillColor) {
	canvasContext.fillStyle = fillColor;
	canvasContext.fillRect(topLeftX, topLeftY, boxWidth, boxHeight);
} 
function drawEverything(sec) {
	var tmin = Math.floor(sec/60);
	var min = tmin.toFixed(0);
	var tsec = sec-(tmin*60);
	

	
	colorRect(0, 0, canvas.width, canvas.height, 'white'); // clear screen
	canvasContext.fillStyle = 'black';
	canvasContext.font="30px Arial";
	console.log("This is a countdown timer.", min, sec, tsec, tmin);
	
	if (sec > 0) {
		canvasContext.fillText("Countdown: " + min + " min " + tsec + " sec", 10, 40);	
		
	}  else if(sec==0){
		canvasContext.fillText("Countdown: " + min + " min " + tsec + " sec", 10, 40);
		canvasContext.fillText("Time Expired!", 10, 80);
		audio.play(); // play chime sound, by FreeSound.org
		
	} else if(sec < 0){
		canvasContext.fillText("Countdown: 0 min 0 sec", 10, 40);
		canvasContext.fillText("Time Expired!", 10, 80);
	}
	
}
</script>
<br>
<br>
 <button class="button"><a href="http://www.pfwebdev.com/CountdownTimer.html">Reset Timer</button>
 <button class="button"><a href="http://www.pfwebdev.com/index.php">Return to PFWebDev</button>
</body>
</html>
