---
date: 2021-09-27
title: "AI Examples"
linkTitle: "AI Examples"
weight: 2
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




<link rel="stylesheet" href="/css/style.css">

<!-- Header -->



<!-- Grafik Hierarchie AI_Examples -->

<img src="ai_hierarchy.png" />
<br><br><br>

<!-- AI_Examples -->


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