---
date: 2021-09-27
title: "AI Classes"
linkTitle: "AI Classes"
weight: 1
type: docs
description: >
  Taxonomy of AI applications
---

# Classification of AI applications
The stated goal of the SENSIBLE-KI project is to secure embedded and mobile AI applications.
In order to ensure a standardized security protection, it is necessary to systematize AI applications.
The specific needs for protection can then be determined by means of discrete AI classes.

Based on the evaluation of a wide range of AI applications, the following classes were identified in this project.
It is a vertical classification which is based on different properties of the AI applications.

The individual protection needs can be determined by categorizing the application with these different levels.

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
    <th class="tg-ii5f" colspan="2"><h4>Source of Input Data</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Where does the input data come from?</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">explicit user input</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">implicit user input (Tracking)</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 3:</b></td>
    <td class="tg-031e">sensory data</td>
  </tr>

  <tr>
    <th class="tg-ii5f" colspan="2"><h4>Type of Input Data</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>What is the format of the input data?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">image</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">audio</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 3:</b></td>
    <td class="tg-031e">text</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 4:</b></td>
    <td class="tg-031e">other</td>
  </tr>
<tr>
    <th class="tg-ii5f" colspan="2"><h4>Personal Reference</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Does the input data contain sensitive information?</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">non-critical</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">indirect personal reference</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 3:</b></td>
    <td class="tg-031e">direct personal reference</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4>Processing of Input Data</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Is the Input Data processed and if yes, how?</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">no</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">yes, automatically</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 3:</b></td>
    <td class="tg-031e">yes, manually</td>
  </tr>


<tr>
    <th class="tg-ii5f" colspan="2"><h4>Preparation of Input Data</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>How is the input data prepared?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class1:</b></td>
    <td class="tg-031e">data cleansing</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">anonymization</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 3:</b></td>
    <td class="tg-031e">feature engineering</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4>Training Time</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>When and how often is the model trained?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">model is trained once (offline learning)</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">model is trained continuously (online learning)</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4>Training Location</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Where is the model trained?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">decentralized und decoupled between different devices</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">decentralized, peer-to-peer</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 3:</b></td>
    <td class="tg-031e">centralized on a server</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 4:</b></td>
    <td class="tg-031e">federated</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4>Deployment</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Are there vulnerable communication paths?
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
    <th class="tg-ii5f" colspan="2"><h4>Type of Model</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>What is the structure of the model?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">classical (transparent) machine learning algorithm</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">neural networks</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4>Protection Measures</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Which measures have been taken?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">software measures</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">hardware measures</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 3:</b></td>
    <td class="tg-031e">both</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 4:</b></td>
    <td class="tg-031e">neither</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4>Type of Output</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>What is the model's task?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 1:</b></td>
    <td class="tg-031e">classification</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 2:</b></td>
    <td class="tg-031e">regression</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Class 3:</b></td>
    <td class="tg-031e">data creation</td>
  </tr>

</table>












