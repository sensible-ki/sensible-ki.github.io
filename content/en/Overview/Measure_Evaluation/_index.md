---
date: 2023-03-01
title: "Measure Evaluation"
linkTitle: "Measure Evaluation"
type: docs
weight: 6
description: >
  Evaluation of Protection Measures
---

Software-based and hardware-based protection measures can be evaluated by means
of different criteria. Some important criteria are
- **Accuracy** (proportion of correct predictions on test data)
- **Robustness** (accuracy on manipulated data)
- **Privacy** (effectiveness of membership inference attacks)
- **Training Time** (duration of the model's training process)

To interpret an evaluation adequately, it should be compared to the evaluation
of the same AI application without any protection measure.

In the following, the evaluation results of some protection measures on
exemplary AI applications are depicted.

## Software Measures

### MNIST Dataset

| Protection Measure   | Accuracy | Robustness | Privacy | Training Time |
|:---------------------|---------:|-----------:|--------:|--------------:|
| no                   |   98,3 % |     11,9 % |    0,45 |          72 s |
| DP-SGD               |   94,2 % |      4,8 % |   < 0,1 |          98 s |
| Anomaly Detection    |   98,3 % |      4,4 % |   < 0,1 |          65 s |
| Adversarial Training |   98,9 % |     76,8 % |    0,12 |         286 s |

### CIFAR10 Dataset

| Protection Measure   | Accuracy | Robustness |  Privacy | Training Time |
|:---------------------|---------:|-----------:|---------:|--------------:|
| no                   |   81,6 % |     18,4 % |     0,31 |         373 s |
| DP-SGD               |   63,9 % |     54,5 % |    < 0,1 |        1061 s |
| Anomaly Detection    |   79,4 % |     17,6 % |      0,4 |         313 s |
| Adversarial Training |   71,9 % |     23,1 % |     22,0 |        2930 s |

## Hardware Measures

| Protection Measure       |      Delay | Power Consumption |                                                                          Device / Setup |
|:-------------------------|-----------:|------------------:|----------------------------------------------------------------------------------------:|
| Modell-Signierung        |     282 ms |          < 0,01 W |                                                 Jetson Nano / Raspberry Pi 3, Zymkey 4i |
| Modell-Signierung        |      12 ms |            mittel |                                                                Huawei P20 Pro (Android) |
| Sensordaten-Attestierung |      77 ms |            0,15 W | Raspberry Pi 3, NXP SE050 Edge Lock, 3-Axis Accelerometer, Burst-Read (6 Byte, I2C API) |
| Sensordaten-Attestierung |   0,221 ms |            gering |                                                                Huawei P20 Pro (Android) |
| Verschlüsselung (AES128) |  2,68 kB/s |     0,07 - 0,15 W |                                          Raspberry Pi 3, NXP SE050 Edge Lock (CBC Mode) |
| Verschlüsselung (AES128) | 2,617 kB/s |          < 0,01 W |                               Raspberry Pi 3, Zymkey 4i (ECDSA Signature, Mode unknown) |
| Verschlüsselung (AES128) |  4566 kB/s |     0,07 - 0,14 W |                                                             OP-TEE, STM32MP1 (CTR Mode) |
| Verschlüsselung (AES128) |   0,095 ms |            gering |                                                                Huawei P20 Pro (Android) |
