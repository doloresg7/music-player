# music-player
Music player using JavaScript,HTML
//html

<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <link href="projectdemo.css" type="text/css" rel="stylesheet"/>
  <title> Demo trying to make a player</title>

</head>
<body onload>
  <script src="projectdemo.js"></script>
<div class="audio-player" >
  <div class="logo">
    <img src="audioicon.png" width="100" height="100"/>
  </div>
  <div class="player">
    <div id="songtitle" class="song-title">

  </div>
</div>
    <input id="songSlider" class="song-slider" type="range" min="0" max="" step="1" onchange="seekSong()"/>
    <div>
      <div id="currentTime" class="currentTime"> 00:00 </div>

  </div>
  <div class="controllers">
    <input type="button" id="play" value="play" width="40px" onclick="play()"/>
    <input type="button" id="backwards" value="backwards" width="40px" onclcik="backward()" />
    <input type="button" id="playPause" value="play/pause" width="40px" onclick="playOrPause()"/>
    <input type="button" id="forward" value="forward" width="40px" onclick="forward()"/>
    <input type="button" id="next" value="next" width="40px" onclick="next()"/>

  </div>
  </body>
</html>

//javascript
var songs= ["johnnewman.mp3","ladygaga.mp3","katyperry.mp3","zhu.mp3"];

var songtitle= document.getElementById("songtitle");
var songSlider= document.getElementById("songSlider");
var currentTime=document.getElementById("currentTime");
var duration= document.getElementById("duration");
var title= document.getElementById("songtitle");


var song = new Audio();
var currentSong=0;
var text;
window.onload=loadSong;

function loadSong(){

song.src="songs/" + songs[currentSong];

song.play();
setTimeout(duration,1000);
}
title.innerHTML =songs[currentSong];


function convertTime(secs){
  var min= Math.floor(secs/60);
  var sec= secs % 60;
  min= (min<10);
  sec= (sec<10);
  return (min+ ":" + sec);
}



function playOrPause(){
  if (song.paused){
    song.play();

  }else {
    song.pause();
  }
}

function next(){
currentSong= currentSong +1 % songs.length;
loadSong();

}
