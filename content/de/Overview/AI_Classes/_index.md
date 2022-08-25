---
date: 2021-09-27
title: "KI-Klassen"
linkTitle: "KI-Klassen"
weight: 1
type: docs
description: >
  Systematik von KI-Anwendungen
---

Ziel des Projektes **SENSIBLE-KI** ist es, KI-Anwendungen im eingebetteten und mobilen Bereich zu schützen. Um eine
möglichst standardisierte Absicherung gewährleisten zu können, ist es notwendig, KI-Anwendungen zu systematisieren.
Anhand von diskreten KI-Klassen kann dann der Schutzbedarf ermittelt werden.

Basierend auf der Evaluierung einer großen Anzahl von KI-Anwendungen wurden im Projekt die im Folgenden dargestellten
Klassen identifiziert. Es handelt sich dabei um eine vertikale (d.h. mehrdimensionale) Klassifizierung, welche auf
verschiedenen Eigenschaften der KI-Anwendungen basiert.

Indem eine Anwendung anhand dieser verschiedenen Ebenen eingeteilt wird, kann ihr ganz individueller Schutzbedarf
ermittelt werden.

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
    <th class="tg-ii5f" colspan="2"><h4>Herkunft der Inputdaten</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Woher kommen die Inputdaten?</i></td>
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
    <td class="tg-031e">Sensor</td>
  </tr>

  <tr>
    <th class="tg-ii5f" colspan="2"><h4>Art der Daten</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Was ist das Format der Inputdaten?</i></td>
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
    <th class="tg-ii5f" colspan="2"><h4>Personenbezug</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Enthalten die Inputdaten sensible Informationen?
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
    <th class="tg-ii5f" colspan="2"><h4>Verarbeitung der Inputdaten</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Werden die Inputdaten verarbeitet und wenn ja, wie?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 1:</b></td>
    <td class="tg-031e">nein</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 2:</b></td>
    <td class="tg-031e">ja: automatisiert</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 3:</b></td>
    <td class="tg-031e">ja: manuell</td>
  </tr>



<tr>
    <th class="tg-ii5f" colspan="2"><h4>Vorbereitung der Trainingsdaten</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Womit werden die Trainingsdaten vorbereitet?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 1:</b></td>
    <td class="tg-031e">Data Cleansing</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 2:</b></td>
    <td class="tg-031e">Anonymisierungsmechanismen</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 3:</b></td>
    <td class="tg-031e">Feature Engineering</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4>Trainingszeitpunkte</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Wann bzw. wie oft wird das Modell trainiert?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 1:</b></td>
    <td class="tg-031e">Modell wird einmalig trainiert (offline learning)</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 2:</b></td>
    <td class="tg-031e">Modell wird kontinuierlich trainiert (online learning)</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4>Trainingsort</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Wo wird das Modell trainiert?
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
    <th class="tg-ii5f" colspan="2"><h4>Deployment</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Gibt es angreifbare Kommunikationswege?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 1:</b></td>
    <td class="tg-031e">Anwendungen, die auf dem Gerät selbst deployt sind und nicht mit einem Server kommunizieren
    müssen</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 2:</b></td>
    <td class="tg-031e">Anwendungen, die ein Modell auf dem Server nutzen. Wenn eine Anfrage an die KI auf einem Endgerät kommt, dann wird diese an den Server (über eine API) weitergeleitet und dort beantwortet</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 3:</b></td>
    <td class="tg-031e">Anwendungen, die ihre Modelle von einem Server bekommen</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4>Art des Modells</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Welche Struktur hat das Modell?
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
    <th class="tg-ii5f" colspan="2"><h4>Sicherheitsmaßnahmen</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Wie wird das Modell geschützt?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 1:</b></td>
    <td class="tg-031e">softwareseitig</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 2:</b></td>
    <td class="tg-031e">hardwareseitig</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 3:</b></td>
    <td class="tg-031e">beides</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 4:</b></td>
    <td class="tg-031e">weder noch</td>
  </tr>

<tr>
    <th class="tg-ii5f" colspan="2"><h4>Art des Outputs</h4> </th>
  </tr>
  <tr>
    <td class="tg-031e" colspan="2"><i>Was ist die Aufgabe des Modells?
</i></td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 1:</b></td>
    <td class="tg-031e">Klassifizierung</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 2:</b></td>
    <td class="tg-031e">Regression</td>
  </tr>
  <tr>
    <td class="tg-031e"><b>Klasse 3:</b></td>
    <td class="tg-031e">Datenerzeugung</td>
  </tr>

</table>













