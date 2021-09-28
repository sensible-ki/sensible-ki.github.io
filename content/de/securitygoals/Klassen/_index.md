---
date: 2021-09-27
title: "Klassen"
linkTitle: "Klassen"
weight: 5
type: docs
description: >
  Klassen von KI-Anwendungen
---

# Klassifizierung von KI-Anwendungen
Ziel des Projektes Sensible-KI ist es, KI-Anwendungen im eingebetteten und mobilen Bereich zu sichern.
Um eine möglichst standardisierte Absicherung zu gewährleisten, ist es notwendig, Klassen von Anwendungen zu definieren, welche Gemeinsamkeiten teilen.
Anhand dieser Klassen kann dann der Schutzbedarf ermittelt werden.

Basierend auf der Evaluierung einer großen Anzahl von KI-Anwendungen wurden im Projekt die im Folgenden dargestellten Klassen identifiziert.
Es handelt sich dabei um eine vertikale Klassifizierung, welche auf verschiedenen Eigenschaften der KI-Anwendungen basiert. 

Indem eine Anwendung anhand dieser verschiedenen Ebenen eingeteilt wird, kann ihr ganz individueller Schutzbedarf ermittelt werden.

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
    <th class="tg-ii5f" colspan="2"><h4> Klassen nach Input </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Woher kommen die Daten?</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 1:</b></td>
    <td class="tg-031e">Explizite Nutzereingabe</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 2:</b></td>
    <td class="tg-031e">Implizite Nutzereingabe (z.B. Tracking)</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 3:</b></td>
    <td class="tg-031e">Sensordaten</td>
  </tr>

  <tr>
    <th class="tg-ii5f" colspan="2"><h4> Klassen nach Art der Daten </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Format der Nutzereingabe. Können diese manipuliert werden? Wie? (z.B. versteckte Sprachbefehle)
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 1:</b></td>
    <td class="tg-031e">Bild</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 2:</b></td>
    <td class="tg-031e">Audio</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 3:</b></td>
    <td class="tg-031e">Text</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 4:</b></td>
    <td class="tg-031e">Sonstiges</td>
  </tr>
<tr>
    <th class="tg-ii5f" colspan="2"><h4> Klassen nach Personenbezug </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Wie schützenswert sind die Nutzereingaben? Enthalten sie Daten, die auf eine Privatperson oder andere sensible Informationen Rückschlüsse zulässt?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 1:</b></td>
    <td class="tg-031e">Unkritische Daten</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 2:</b></td>
    <td class="tg-031e">Daten mit indirektem Personenbezug</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 3:</b></td>
    <td class="tg-031e">Daten mit direktem Personenbezug</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4> Klasse nach Verarbeitung in der Pipeline </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Wie werden die Maßnahmen auf den Daten ausgeführt?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 1:</b></td>
    <td class="tg-031e">Feststehende automatisierte Datenverarbeitungspipeline</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 2:</b></td>
    <td class="tg-031e">Manuelle Datenbearbeitung und ggf. manuelles Hinzufügen</td>
  </tr>



<tr>
    <th class="tg-ii5f" colspan="2"><h4> Klasse nach Verarbeitung der Trainingsdaten </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Wo wird das Modell trainiert?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 1:</b></td>
    <td class="tg-031e">Data Cleansing</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 2:</b></td>
    <td class="tg-031e">Anonymisierungemechanismen</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 3:</b></td>
    <td class="tg-031e">Feature Engineering</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4> Klassen nach Trainingszeitpunkten </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Wann/ Wie oft?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 1:</b></td>
    <td class="tg-031e">Modell wird einmalig trainiert (offline learning)</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 2:</b></td>
    <td class="tg-031e">Modell wird kontinuierlich trainiert. (online learning)</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 3:</b></td>
    <td class="tg-031e">Modell wird zu bestimmten Zeitpunkten aktualisiert (manuell)</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4> Klasse nach Trainingsort </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Welche Art Maßnahmen werden auf den Daten ausgeführt?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 1:</b></td>
    <td class="tg-031e">dezentral und entkoppelt zwischen verschiedenen Geräten</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 2:</b></td>
    <td class="tg-031e">dezentral und z.B. peer-to-peer zwischen Geräten</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 3:</b></td>
    <td class="tg-031e">zentral auf Server</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 4:</b></td>
    <td class="tg-031e">federated</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4> Klassen nach Deployment </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Gibt es evtl. Kommunikationswege, die angegriffen werden können?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 1:</b></td>
    <td class="tg-031e">Anwendungen, die auf dem Gerät selbst deployt sind und nicht mit einem Server kommunizieren müssen.</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 2:</b></td>
    <td class="tg-031e">Anwendungen, die die ein Modell auf dem Server nutzen. Wenn eine Anfrage an die KI auf einem Endgerät kommt, dann wird diese an den Server (über eine API) weitergeleitet und dort beantwortet</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 3:</b></td>
    <td class="tg-031e">Anwendungen, die ihre Modelle von einem Server bekommen</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4> Klassen nach Modellzugriff </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Welche Art Modellzugriff?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 1:</b></td>
    <td class="tg-031e">Blackbox</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 2:</b></td>
    <td class="tg-031e">Whitebox</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4> Klassen nach Algorithmen </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Eventuell verschiedene Maßnahmen bei Neuronalen Netzwerken als klassischem Machine Learning?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 1:</b></td>
    <td class="tg-031e">Klassische (nachvollziehbarere) Machine Learning Algorithmen</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 2:</b></td>
    <td class="tg-031e">Neuronale Netze</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4> Klasse nach vorgenommenen Sicherheitsmaßnahmen </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Welche Art Maßnahmen bestehen bereits?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 1:</b></td>
    <td class="tg-031e">Softwareseitig</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 2:</b></td>
    <td class="tg-031e">Hardwareseitig</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 3:</b></td>
    <td class="tg-031e">Beides</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 4:</b></td>
    <td class="tg-031e">Weder noch</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4> Klassen nach Art des Outputs </h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Wie detailliert ist der Output? Nur Klassifizierung oder auch Confidence Scores?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 1:</b></td>
    <td class="tg-031e">Nur Klassifizierung</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 2:</b></td>
    <td class="tg-031e">Klassifizierung und Confidence Score</td>
  </tr>

</table>













