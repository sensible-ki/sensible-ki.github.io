---
date: 2021-09-27
title: "Classes"
linkTitle: "Classes"
weight: 5
type: docs
description: >
  Classes of AI applications
---

# Classification of AI applications
The stated goal of the SENSIBLE-KI project is to secure edge and mobile AI applications.

In order to ensure a standardised security model, it is necessary to define classes of applications which share similarities. 
On the basis of these classes protection needs are determined.
Based on the evaluation of a wide range of AI applications the following classes were identified in this project.

It is a vertical classification which is based on different properties of the AI applications.
The individual protection needs can be determined by categorising the application with these different levels.




<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;}
.tg .tg-ii5f{background-color:#000000;color:#ffffff}
</style>



<table class="tg" style="table-layout: fixed; width: 600px">
<colgroup>
<col style="width: 174px">
<col style="width: 232px">
</colgroup>
  <tr>
    <th class="tg-ii5f" colspan="2"><h4> Classes regarding input </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Where does the data come from?</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">Explicit user input</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">Implicit user input (Tracking)</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 3:</b></td>
    <td class="tg-031e">Sensor data</td>
  </tr>

  <tr>
    <th class="tg-ii5f" colspan="2"><h4> Classes regarding type of data </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Format of user input. Can it be manipulated? How?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">Image</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">Audio</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 3:</b></td>
    <td class="tg-031e">Text</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 4:</b></td>
    <td class="tg-031e">Other</td>
  </tr>
<tr>
    <th class="tg-ii5f" colspan="2"><h4> Classes regarding data with personal connection </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>How worthy of protection is the input?</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">non critical data</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">data with an indirect personal connection</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 3:</b></td>
    <td class="tg-031e">data with an direct personal connection</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4> Classes regarding processing in the pipeline </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>How are the tasks executed?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">Fixed automatic processing pipeline</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">manually processed data</td>
  </tr>


<tr>
    <th class="tg-ii5f" colspan="2"><h4> Classes regarding processing of the training data </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Which measures have been taken?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class1:</b></td>
    <td class="tg-031e">Data Cleansing</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">Anonymisation</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 3:</b></td>
    <td class="tg-031e">Feature Engineering</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4> Classes regarding training time </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>When/ How often?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">Trained once (offline learning)</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">Trained continuous. (online learning)</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 3:</b></td>
    <td class="tg-031e"> Updated to certain times (manually)</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4> Classes regarding training location </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Where has the model been trained?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">decentral und decoupled between diffenrent devices </td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">decentral, peer-to-peer</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 3:</b></td>
    <td class="tg-031e">central on a server</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 4:</b></td>
    <td class="tg-031e">federated</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4> Classes regarding deployment </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Are there communication paths that can be attacked?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">Applications which are deployed on a device and don't have to communicate with a server</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">Applications which use a model on a server</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 3:</b></td>
    <td class="tg-031e">Applications which get their model from a server</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4> Classes regarding access to model </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Which type of access?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">Blackbox</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">Whitebox</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4> Classes regarding algorithm </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Differences between neural networks and classical machine learning?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">classical (transparent) machine learning algorithm</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">Neural networks</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4> Classes regarding taken security measures </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Which measures have been taken?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">Software measures</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">Hardware measures</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 3:</b></td>
    <td class="tg-031e">Both</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 4:</b></td>
    <td class="tg-031e">Neither</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4> Classes regarding types of output</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>How detailled is the output? Only classification or also confidence scores?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">Only classification</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">Only classification and confidence scores</td>
  </tr>

</table>












