---
date: 2021-09-27
title: "AI Examples"
linkTitle: "AI Examples"
weight: 5
type: docs
description: >
  Examples of AI applications
---



In order to categorize AI mobile and edge applications into several classes regarding their security goals, a functional
evaluation was performed for numerous existing AI applications in this project. The evaluated applications originate
from a wide scope (biometry, smart home, smart living, smart devices, etc.), to identify a general classification that
suits a variety of applications. From this functional evaluation several [classes]({{< relref "AI_Classes" >}}) were
derived.

Below, four different applications will be evaluated along with its determined classes, showing how a classification can
be achieved and to validate that the determined classes may be applied to numerous AI applications.




<style>

<!-- CSS Tabellen -->
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-abx8{background-color:#c0c0c0;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-1wig{font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-lqy6{text-align:right;vertical-align:top}
.tg .tg-0lax{text-align:left;vertical-align:top}
.tg .tg-y6fn{background-color:#c0c0c0;text-align:left;vertical-align:top}
.tg .tg-ufyb{font-style:italic;text-align:right;vertical-align:top}  


<!-- Slideshow CSS -->
* {box-sizing: border-box}
.mySlides {display: none}


/* Slideshow container */
.slideshow-container {
  max-width: 1000px;
  position: relative;
  margin: auto;
}



/* Next & previous buttons */
.prev, .next {
  cursor: pointer;
  position: absolute;
  top: 50%;
  width: auto;
  padding: 16px;
  margin-top: -22px;
  color: black;
  font-weight: bold;
  font-size: 18px;
  transition: 0.6s ease;
  border-radius: 0 3px 3px 0;
  user-select: none;
}


/* Position the "next button" to the right */
.next {
  right: 0;
  border-radius: 3px 0 0 3px;
}

.prev {
  left: 0;
  border-radius: 3px 0 0 3px;
}



/* On hover, add a black background color with a little bit see-through */
.prev:hover, .next:hover {
  background-color: rgba(0,0,0,0.8);
}




/* The dots/bullets/indicators */
.dot {
  cursor: pointer;
  
  height: 15px;
  width: 15px;
  margin: 0 2px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
  transition: background-color 0.6s ease;
}

.dot:hover{
  background-color: #717171;
}




</style>

<!-- Header -->



<!-- Grafik Hierarchie KI-Beispiele -->

<img src="ai_hierarchy.png" />
<br><br><br>

<!-- KI-Beispiele -->


<div class="slideshow-container">
<div class="mySlides">

<table class="tg" style="undefined;table-layout: fixed; width: 543px; height:650px">
<colgroup>
<col style="width: 157px">
<col style="width: 386px">
</colgroup>
<thead>
  <tr>
    <th class="tg-lqy6" colspan="2"><span style="font-weight:bold ; font-size:20px"> Gang-Authentifizierung (Seamless.me) </span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">Category</td>
    <td class="tg-y6fn">Partial aspect</td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Input</td>
    <td class="tg-0lax"><span style="font-weight:bold">Where does the data come from? <ul><li> <span style="font-weight:normal"> Sensors </span></li></ul></span><span style="font-weight:bold">Number of data classes? <ul><li> <span style="font-weight:normal"> One Class Classification / Novelty Detection </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-y6fn"><span style="font-weight:bold">Type of data? <ul><li> <span style="font-weight:normal"> Sensor data </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Training</td>
    <td class="tg-0lax"><span style="font-weight:bold">Where does training take place? <ul><li> <span style="font-weight:normal"> decentral, decoupled </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-abx8">When is new training data added? <ul><li> <span style="font-weight:normal"> continuous (online learning) </span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Modell</td>
    <td class="tg-1wig">Where is the model deployed? <ul><li> <span style="font-weight:normal"> on-device </span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-abx8">What is known?<ul><li> <span style="font-weight:normal"> Supervised Learning </span></li><li> <span style="font-weight:normal"> own histogramm-based novelty detector  </span></li><li> <span style="font-weight:normal"> Scikit-learn framework </span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-ufyb">Output</td>
    <td class="tg-1wig">What does the output look like?  <ul><li> <span style="font-weight:normal"> Probability Scores </span></li></ul> </td>
  </tr>
</tbody>
</table>

</div>



<div class="mySlides">

<table class="tg" style="undefined;table-layout: fixed; width: 543px; height:650px">
<colgroup>
<col style="width: 157px">
<col style="width: 386px">
</colgroup>
<thead>
  <tr>
    <th class="tg-lqy6" colspan="2"><span style="font-weight:bold ; font-size:20px"> ArcFace: Additive Angular Margin Loss for Deep Face Recognition </span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">Category</td>
    <td class="tg-y6fn">Partial aspect</td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Input</td>
    <td class="tg-0lax"><span style="font-weight:bold">Where does the data come from? <ul><li> <span style="font-weight:normal"> Sensors </span></li></ul></span><span style="font-weight:bold">Number of data classes? <ul><li> <span style="font-weight:normal"> Multiclass </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-y6fn"><span style="font-weight:bold">Type of data? <ul><li> <span style="font-weight:normal"> Image </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Training</td>
    <td class="tg-0lax"><span style="font-weight:bold">Where does training take place? <ul><li> <span style="font-weight:normal"> decentral, decoupled </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-abx8">When is new training data added? <ul><li> <span style="font-weight:normal"> once when model is deployed </span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Modell</td>
    <td class="tg-1wig">Where is the model deployed? <ul><li> <span style="font-weight:normal"> on-device </span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-abx8">What is known? <ul><li> <span style="font-weight:normal"> Supervised Learning </span></li><li> <span style="font-weight:normal"> GAN </span></li><li> <span style="font-weight:normal"> Tensorflow </span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-ufyb">Output</td>
    <td class="tg-1wig">What does the output look like? <ul><li> <span style="font-weight:normal"> Image, Generation Simularity Score </span></li></ul> </td>
  </tr>
</tbody>
</table>


</div>



<div class="mySlides">

<table class="tg" style="undefined;table-layout: fixed; width: 543px; height:650px">
<colgroup>
<col style="width: 157px">
<col style="width: 386px">
</colgroup>
<thead>
  <tr>
    <th class="tg-lqy6" colspan="2"><span style="font-weight:bold ; font-size:20px"> Realtime Object Recognition (YOLObile) </span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">Category</td>
    <td class="tg-y6fn">Partial aspect</td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Input</td>
    <td class="tg-0lax"><span style="font-weight:bold">Where does the data come from?  <ul><li> <span style="font-weight:normal"> explicit user input </span></li></ul></span><span style="font-weight:bold">Number of data classes? <ul><li> <span style="font-weight:normal"> Multiclass </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-y6fn"><span style="font-weight:bold">Type of data? <ul><li> <span style="font-weight:normal"> Image </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Training</td>
    <td class="tg-0lax"><span style="font-weight:bold">Where does training take place? <ul><li> <span style="font-weight:normal">zentral</span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-abx8">When is new training data added? <ul><li> <span style="font-weight:normal"> once when model is deployed</span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Modell</td>
    <td class="tg-1wig">Where is the model deployed? <ul><li> <span style="font-weight:normal"> on-device </span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-abx8">What is known?<ul><li> <span style="font-weight:normal"> Supervised Learning </span></li><li> <span style="font-weight:normal"> DNN, group
Lasso method </span></li><li> <span style="font-weight:normal"> YOLOv4  </span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-ufyb">Output</td>
    <td class="tg-1wig">What does the output look like?  <ul><li> <span style="font-weight:normal"> Klassifizierung und Bounding Boxes </span></li></ul> </td>
  </tr>
</tbody>
</table>

</div>



<div class="mySlides">
<table class="tg" style="undefined;table-layout: fixed; width: 543px; height:650px">
<colgroup>
<col style="width: 157px">
<col style="width: 386px">
</colgroup>
<thead>
  <tr>
    <th class="tg-lqy6" colspan="2"><span style="font-weight:bold ; font-size:20px"> Object Detection (R-CNN) </span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">Category</td>
    <td class="tg-y6fn">Partial aspect</td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Input</td>
    <td class="tg-0lax"><span style="font-weight:bold">Where does the data come from? <ul><li> <span style="font-weight:normal"> explicit user input </span></li></ul></span><span style="font-weight:bold">Number of data classes? <ul><li> <span style="font-weight:normal"> Multiclass </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-y6fn"><span style="font-weight:bold">Type of data? <ul><li> <span style="font-weight:normal"> Image </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Training</td>
    <td class="tg-0lax"><span style="font-weight:bold">Where does training take place? <ul><li> <span style="font-weight:normal"> - </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-abx8">When is new training data added? <ul><li> <span style="font-weight:normal"> once when model is deployed</span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Modell</td>
    <td class="tg-1wig">Where is the model deployed? <ul><li> <span style="font-weight:normal"> on-device </span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-abx8">What is known?<ul><li> <span style="font-weight:normal"> Supervised Learning </span></li><li> <span style="font-weight:normal"> CNN </span></li><li> <span style="font-weight:normal"> Tensorflow </span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-ufyb">Output</td>
    <td class="tg-1wig">What does the output look like?  <ul><li> <span style="font-weight:normal"> classification </span></li></ul> </td>
  </tr>
</tbody>
</table>
</div>



<a class="prev" onclick="plusSlides(-1)">&#10094;</a>
<a class="next" onclick="plusSlides(1)">&#10095;</a>


</div>
<div style="text-align:center">
  <span class="dot" onclick="currentSlide(1)"></span> 
  <span class="dot" onclick="currentSlide(2)"></span> 
  <span class="dot" onclick="currentSlide(3)"></span> 
  <span class="dot" onclick="currentSlide(4)"></span> 
</div>



<!-- Javascript -->
<script language="javascript" type="text/javascript">


var slideIndex = 1;
showSlides(slideIndex);

function plusSlides(n) {
  showSlides(slideIndex += n);
}

function currentSlide(n) {
  showSlides(slideIndex = n);
}

function showSlides(n) {
  var i;
  var slides = document.getElementsByClassName("mySlides");
  var dots = document.getElementsByClassName("dot");
  if (n > slides.length) {slideIndex = 1}    
  if (n < 1) {slideIndex = slides.length}
  for (i = 0; i < slides.length; i++) {
      slides[i].style.display = "none";  
  }
  for (i = 0; i < dots.length; i++) {
      dots[i].className = dots[i].className.replace(" active", "");
  }
  slides[slideIndex-1].style.display = "block";  
  dots[slideIndex-1].className += " active";
}


</script>