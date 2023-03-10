---
date: 2023-03-01
title: "Maßnahmen-Evaluierung"
linkTitle: "Maßnahmen-Evaluierung"
type: docs
weight: 6
description: >
  Evaluierung der Schutzmaßnahmen
---

Software- und Hardware-seitige Schutzmaßnahmen können anhand verschiedener
Kriterien bewertet werden. Wichtige Kriterien sind

- **Genauigkeit** (Anteil korrekter Vorhersagen auf Testdaten)
- **Robustheit** (Genauigkeit auf manipulierten Daten)
- **Privatsphärerisiko** (Wirksamkeit von Membership-Inference-Attacken)
- **Trainingszeit** (Dauer des Modelltrainingsprozesses)

Für eine sinnvolle Interpretation der Bewertung sollte diese mit der Bewertung
derselben KI-Anwendung ohne Schutzmaßnahme verglichen werden.

Im folgenden werden die Evaluationsergebnisse einiger Schutzmaßnahmen für
beispielhafte KI-Anwendungen dargestellt.

## Software-Maßnahmen

Die Robustheit beschreibt das Verhältnis der Genauigkeit mit normalen Eingangsdaten zu der Genauigkeit mit bösartig manipulierten (adversarial) Eingangsdaten.

Das Privatsphärerisiko wird berechnet als der Vorteil eines Angreifers mit Membership-Inference-Angriffen (True Positive Rate / False Positive Rate - 1).

### MNIST-Datensatz

| Maßnahme             | Genauigkeit | Robustheit | Privatsphärerisiko | Training Time |
| :------------------- | ----------: | ---------: | -----------------: | ------------: |
| keine                |      98,3 % |     11,9 % |               0,45 |          72 s |
| DP-SGD               |      94,2 % |      4,8 % |              < 0,1 |          98 s |
| Anomaly Detection    |      98,3 % |      4,4 % |              < 0,1 |          65 s |
| Adversarial Training |      98,9 % |     76,8 % |               0,12 |         286 s |

### CIFAR10-Datensatz

| Maßnahme             | Genauigkeit | Robustheit | Privatsphärerisiko | Training Time |
| :------------------- | ----------: | ---------: | -----------------: | ------------: |
| keine                |      81,6 % |     18,4 % |               0,31 |         373 s |
| DP-SGD               |      63,9 % |     54,5 % |              < 0,1 |        1061 s |
| Anomaly Detection    |      79,4 % |     17,6 % |                0,4 |         313 s |
| Adversarial Training |      71,9 % |     23,1 % |               22,0 |        2930 s |

## Hardware-Maßnahmen

| Maßnahme                 | Verzögerung | Stromverbrauch |                                                                           Gerät / Setup |
| :----------------------- | ----------: | -------------: | --------------------------------------------------------------------------------------: |
| Modell-Signierung        |      282 ms |       < 0,01 W |                                                 Jetson Nano / Raspberry Pi 3, Zymkey 4i |
| Modell-Signierung        |       12 ms |         mittel |                                                                Huawei P20 Pro (Android) |
| Sensordaten-Attestierung |       77 ms |         0,15 W | Raspberry Pi 3, NXP SE050 Edge Lock, 3-Axis Accelerometer, Burst-Read (6 Byte, I2C API) |
| Sensordaten-Attestierung |    0,221 ms |         gering |                                                                Huawei P20 Pro (Android) |
| Verschlüsselung (AES128) |   2,68 kB/s |  0,07 - 0,15 W |                                          Raspberry Pi 3, NXP SE050 Edge Lock (CBC Mode) |
| Verschlüsselung (AES128) |  2,617 kB/s |       < 0,01 W |                              Raspberry Pi 3, Zymkey 4i (ECDSA Signatur, Mode unbekannt) |
| Verschlüsselung (AES128) |   4566 kB/s |  0,07 - 0,14 W |                                                             OP-TEE, STM32MP1 (CTR Mode) |
| Verschlüsselung (AES128) |    0,095 ms |         gering |                                                                Huawei P20 Pro (Android) |
