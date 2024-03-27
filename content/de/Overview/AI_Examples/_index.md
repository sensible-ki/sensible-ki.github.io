---
date: 2021-09-27
title: "KI-Beispiele"
linkTitle: "KI-Beispiele"
weight: 2
type: docs
description: >
  Beispiele eingebetteter und mobiler KI-Anwendungen
---

Um KI-Anwendungen im mobilen und eingebetteten Bereich in einzelne Klassen bezüglich ihres Schutzbedarfes einzuteilen, 
wurden im Projekt zahlreiche existierende KI-Anwendungen funktional evaluiert. Die evaluierten Anwendungen stammen aus
einer großen Bandbreite von Anwendungsbereichen (Biometrie, Smart Home, Smart Living, Smart Devices, etc.), um eine
möglichst allgemeine und auf eine Vielzahl von Anwendungen passende Klassifizierung zu ermitteln. Aus dieser
funktionalen Evaluierung wurden im Projekt dann die einzelnen [Klassen]({{< relref "AI_Classes" >}}) abgeleitet.

Im Folgenden werden vier unterschiedliche Anwendungen anhand der ermittelten Klassen evaluiert, um beispielhaft
aufzuzeigen, wie eine Klassifizierung erfolgen kann, und um zu beispielhaft zu validieren, dass die ermittelten Klassen
auf solch vielfältige Anwendungen anwendbar sind.

<link rel="stylesheet" href="/css/style.css">
<!-- Header -->



<!-- Grafik Hierarchie AI_Examples -->

<img src="KI_hierarchie.png" />
<br><br><br>

<!-- AI_Examples -->


<div class="slideshow-container" style="margin: auto">

<div class="mySlides">
<table class="tg" style="table-layout: fixed; width: 543px; height:650px">
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
    <td class="tg-0lax">Einordnung</td>
    <td class="tg-y6fn">Teilaspekte</td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Input</td>
    <td class="tg-0lax"><span style="font-weight:bold">Woher kommen die Daten? <ul><li> <span style="font-weight:normal"> Sensoren </span></li></ul></span><span style="font-weight:bold">Anzahl der Datenklassen? <ul><li> <span style="font-weight:normal"> One Class Classification / Novelty Detection </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-y6fn"><span style="font-weight:bold">Art der Daten? <ul><li> <span style="font-weight:normal"> Sensordaten </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Training</td>
    <td class="tg-0lax"><span style="font-weight:bold">Wo findet das Training statt? <ul><li> <span style="font-weight:normal"> dezentral, entkoppelt </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-abx8">Wann kommen neue Trainingsdaten hinzu? <ul><li> <span style="font-weight:normal"> Kontinuierlich (online learning) </span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Modell</td>
    <td class="tg-1wig">Wo ist das Modell deployt? <ul><li> <span style="font-weight:normal"> on-device </span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-abx8">Was ist bekannt? <ul><li> <span style="font-weight:normal"> Supervised Learning </span></li><li> <span style="font-weight:normal"> Eigener Histogramm-basierter Novelty Detector  </span></li><li> <span style="font-weight:normal"> Scikit-learn framework </span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-ufyb">Output</td>
    <td class="tg-1wig">Wie sieht der Output aus? <ul><li> <span style="font-weight:normal"> Probability Scores </span></li></ul> </td>
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
    <td class="tg-0lax">Einordnung</td>
    <td class="tg-y6fn">Teilaspekte</td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Input</td>
    <td class="tg-0lax"><span style="font-weight:bold">Woher kommen die Daten? <ul><li> <span style="font-weight:normal"> Sensoren </span></li></ul></span><span style="font-weight:bold">Anzahl der Datenklassen? <ul><li> <span style="font-weight:normal"> Multiclass </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-y6fn"><span style="font-weight:bold">Art der Daten? <ul><li> <span style="font-weight:normal"> Bilddateien </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Training</td>
    <td class="tg-0lax"><span style="font-weight:bold">Wo findet das Training statt? <ul><li> <span style="font-weight:normal"> dezentral, entkoppelt </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-abx8">Wann kommen neue Trainingsdaten hinzu? <ul><li> <span style="font-weight:normal"> Einmalig zum Deployen des Modells</span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Modell</td>
    <td class="tg-1wig">Wo ist das Modell deployt? <ul><li> <span style="font-weight:normal"> on-device </span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-abx8">Was ist bekannt? <ul><li> <span style="font-weight:normal"> Supervised Learning </span></li><li> <span style="font-weight:normal"> GAN </span></li><li> <span style="font-weight:normal"> Tensorflow </span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-ufyb">Output</td>
    <td class="tg-1wig">Wie sieht der Output aus? <ul><li> <span style="font-weight:normal"> Bild, Generation Simularity Score </span></li></ul> </td>
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
    <th class="tg-lqy6" colspan="2"><span style="font-weight:bold ; font-size:20px"> Echtzeit Objekterkennung (YOLObile) </span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">Einordnung</td>
    <td class="tg-y6fn">Teilaspekte</td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Input</td>
    <td class="tg-0lax"><span style="font-weight:bold">Woher kommen die Daten? <ul><li> <span style="font-weight:normal"> Explizite Benutzereingabe </span></li></ul></span><span style="font-weight:bold">Anzahl der Datenklassen? <ul><li> <span style="font-weight:normal"> Multiclass </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-y6fn"><span style="font-weight:bold">Art der Daten? <ul><li> <span style="font-weight:normal"> Bilddateien </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Training</td>
    <td class="tg-0lax"><span style="font-weight:bold">Wo findet das Training statt? <ul><li> <span style="font-weight:normal">zentral</span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-abx8">Wann kommen neue Trainingsdaten hinzu? <ul><li> <span style="font-weight:normal"> Einmalig zum Deployen des Modells</span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Modell</td>
    <td class="tg-1wig">Wo ist das Modell deployt? <ul><li> <span style="font-weight:normal"> on-device </span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-abx8">Was ist bekannt? <ul><li> <span style="font-weight:normal"> Supervised Learning </span></li><li> <span style="font-weight:normal"> DNN, group
Lasso method </span></li><li> <span style="font-weight:normal"> YOLOv4  </span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-ufyb">Output</td>
    <td class="tg-1wig">Wie sieht der Output aus? <ul><li> <span style="font-weight:normal"> Klassifizierung und Bounding Boxes </span></li></ul> </td>
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
    <th class="tg-lqy6" colspan="2"><span style="font-weight:bold ; font-size:20px"> Objekterkennung (R-CNN) </span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">Einordnung</td>
    <td class="tg-y6fn">Teilaspekte</td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Input</td>
    <td class="tg-0lax"><span style="font-weight:bold">Woher kommen die Daten? <ul><li> <span style="font-weight:normal"> Explizite Benutzereingabe </span></li></ul></span><span style="font-weight:bold">Anzahl der Datenklassen? <ul><li> <span style="font-weight:normal"> Multiclass </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-y6fn"><span style="font-weight:bold">Art der Daten? <ul><li> <span style="font-weight:normal"> Bilddateien </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Training</td>
    <td class="tg-0lax"><span style="font-weight:bold">Wo findet das Training statt? <ul><li> <span style="font-weight:normal"> keine Angabe </span></li></ul></span></td>
  </tr>
  <tr>
    <td class="tg-abx8">Wann kommen neue Traininfsdaten hinzu? <ul><li> <span style="font-weight:normal"> Einmalig zum Deployen des Modells</span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-ufyb" rowspan="2">Modell</td>
    <td class="tg-1wig">Wo ist das Modell deployt? <ul><li> <span style="font-weight:normal"> on-device </span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-abx8">Was ist bekannt? <ul><li> <span style="font-weight:normal"> Supervised Learning </span></li><li> <span style="font-weight:normal"> CNN </span></li><li> <span style="font-weight:normal"> Tensorflow </span></li></ul></td>
  </tr>
  <tr>
    <td class="tg-ufyb">Output</td>
    <td class="tg-1wig">Wie sieht der Output aus? <ul><li> <span style="font-weight:normal"> Klassifizierung </span></li></ul> </td>
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