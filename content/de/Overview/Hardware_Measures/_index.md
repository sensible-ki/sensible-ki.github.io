---
date: 2021-09-27
title: "Hardware-Maßnahmen"
linkTitle: "Hardware-Maßnahmen"
type: docs
weight: 4
description: >
  Techniken des Trusted-Computing zum Schutz von KI-Anwendungen gegen Angreifer
---


# Evaluierungsübersicht – Trusted Computing Verfahren 

## Gruppierung und allgemeine Übersicht 
Die Verfahren des Trusted Computing wurden in zwei Gruppen unterteilt, die sich in der Umsetzung der Ziele des Trusted Computing unterschieden. Der Gruppe **Trusted Execution Environments** und verwandte Technologien sind Implementierungen zugeordnet, die dazu Technologien des vorhandenen Anwendungsprozessors nutzen. Die Gruppe **Tamper Resistant Hardware** hingegen bildet spezifische Hardware-Module ab, die die Ziele des Trusted Computing umsetzen bzw. deren Umsetzung ermöglichen. 

### Trusted Execution Environments (TEEs) und Frameworks 
#### **Basis Technologien** 
Die Idee eines **Trusted Execution Environments (TEE)** ist die Trennung sicherheitskritischer Prozesse und ihrer Daten von nicht-vertrauenswürdigem Code. Im Falle von TEEs umfasst Letzterer auch das reguläre Betriebssystem mit all seinen Prozessen **(Rich Execution Environment (REE))**. Das TEE hat also sein eigenes Betriebssystem und eigene Prozesse **(Trusted Applications (TAs))**. Um diese Trennung sicherzustellen und den Bereich des TEE auch vor den Eingriffen des REEs zu schützen, muss eine hardwarebasierte unterliegende Technologie genutzt werden. Im Folgenden werden die dafür von verschiedenen Hardwareherstellern bereitgestellten Technologien beschrieben: 

[**TrustZone (TZ)**](https://developer.arm.com/ip-products/security-ip/trustzone/trustzone-for-cortex-a?_ga=2.76035478.2094999520.1624452026-845153957.1615900232) ist eine Technologie, die auf (manchen) ARM Cortex-A Prozessoren verfügbar ist. Sie ermöglicht die Trennung von Ressourcen in eine “Secure World” und eine “Non-Secure World”. Diese Trennung wird durch bestimmte Prozessorbits und sichere Kontextwechsel umgesetzt. Die von TrustZone kontrollierten Ressourcen umfassen den Hauptspeicher, bestimmte Peripheriezugriffe und die Ausführungszeit. Wegen der hohen Verbreitung von ARM Cortex-A Prozessoren in den Bereichen der Mobilgeräte und der eingebetteten Systeme ist diese Technologie auf vielen Embedded- und Mobilgeräten verfügbar. 

[**TrustZone-M (TZM)**](https://developer.arm.com/ip-products/security-ip/trustzone/trustzone-for-cortex-m) ist die entsprechende Technologie für ARM Cortex-M Prozessoren mit dem Unterschied, dass hierbei die Kontextwechsel mittels Branch Instructions ablaufen. Dadurch verursachen diese eine geringere Verzögerung. TrustZone-M ist optimiert für Geräte mit Low Power Profilen. 

[**Intel SGX**](https://www.trentonsystems.com/blog/what-is-intel-sgx) ist eine Instruction Set Extension, verfügbar auf einigen Intel x86 Prozessoren, zur Separation des Speichers in sogenannte "Enclaves". Diese Enclaves werden verschlüsselt, um illegitime Zugriffe zu verhindern. Intel SGX kann mehrere sichere Bereiche in Form der Enclaves bereitstellen, kontrolliert jedoch nur den Zugriff auf deren Speicher. Eine zusätzliche Absicherung von Peripherie ist nicht vorgesehen. 

[**AMD SEV/PSP**](https://developer.amd.com/sev/) ist die Virtualisierungstechnologie von AMD. Sie nutzt den AMD Platform Security Processor (PSP), welcher wiederum ein ARM Chip mit TrustZone ist. Der PSP ist zuständig für die Generation und Verwaltung von Schlüsselmaterial, welches für die Verschlüsselung der Speicherbereiche sowie der CPU-Register der sicheren “Guests” genutzt wird. 

[**RISC-V Physical Memory Protection (PMP)**](https://sifive.github.io/freedom-metal-docs/devguide/pmps.html) ist ein Modul der RISC-V Architektur, mit welchem Speicherzugriff-Policies über den Prozessor umgesetzt werden können. Die Absicherung von Speicherbereichen kann bei RISC-V basierten TEEs zum Schutz der “sicheren Welten” genutzt werden. 

#### **Implementierungen**
Beschrieben werden pro Lösung jeweils die notwendigen Voraussetzungen des Anwendungsprozessors bzw. des genutzten Gerätes **(Plattform)** und ob die Implementierung mit der [GlobalPlatform TEE API Specification](https://globalplatform.org/specs-library/tee-internal-core-api-specification/) konform ist **(GP Compliance)**.  

<details><summary><strong>Tabelle 1: Kommerzielle / Proprietäre Lösungen</strong></summary><p>

{{<table "table table-striped">}}

| Name | Plattform |  GP Compliance | Kommentar|
| --   | --        | --            | --       |
| [Qualcomm TEE (QTEE / QSEE)](https://www.qualcomm.com/media/documents/files/guard-your-data-with-the-qualcomm-snapdragon-mobile-platform.pdf) | TZ | Ja (SFS API) | Nutzt neben TrustZone auch die Secure Processing Unit (SPU) (mancher) Qualcomm SoCs.  **Zertifizierungen:** [FIPS 140-2 Level 1 (Crypto Lib), FIPS Level 2 (crypto engine core), FIPS Level 1 (PRNG), FIPS Level 1 (Inline Crypto engine)](https://www.qualcomm.com/news/onq/2020/04/16/qualcomm-technologies-product-security-solutions-receive-vital-fips) |
|[Kinibi](https://www.trustonic.com/technology/)|TZ|Ja|[Implementierung für Exynos Chips von Trustonic](https://azeria-labs.com/trustonics-kinibi-tee-implementation/). **Zertifizierungen:** [Common Criteria (TEE)](https://www.ssi.gouv.fr/uploads/2017/02/anssi_cc-2017_03-cible-publique.pdf) |
|[TEEGRIS](https://developer.samsung.com/teegris/overview.html) | TZ |Ja|Für Samsung Exynos. TEEGRIS hat ab dem Samsung Galaxy S10 Kinibi [auf vielen Samsung-Smartphones abgelöst](https://www.riscure.com/blog/tee-security-samsung-teegris-part-1).|
|[iTrustee](https://globalplatform.org/certified-products/huawei-itrustee-v3-0-on-kirin-980/) |TZ |Ja |Implementierung von Huawei. Hat Huaweis vorherige Implementierung, Trusted Core, auf neuen Huawei-Smartphones abgelöst. **Zertifizierungen:** [CC EAL2+](https://www.commoncriteriaportal.org/products/) |
|[Kinibi-M](https://www.trustonic.com/technical-articles/kinibi-m/) |TZM |k. A. |Implementierung für Arm Cortex-M Prozessoren von Trustonic. Momentan nur für Microchips SAM L11 verfügbar. |

{{</table>}}

</p></details>&nbsp;

<details><summary><strong>Tabelle 2: Forschungs- bzw. Open-Source-Projekte</strong></summary><p>
{{<table "table table-striped">}}

| Name | Plattform | GP Compliance | Kommentar|
| -- | -- | -- | -- |
|[Trusty](https://source.android.com/security/trusty) | TZ, Intel SGX |Nein | Open-Source-Implementierung von Android | 
|[GoTEE](https://github.com/f-secure-foundry/GoTEE) |TZ |Nein |Open-Source-Implementierung von f-secure. Bisher nur für folgende SoCs: NXP i.MX6ULL, NXP i.MX6ULZ.| 
|[OP-TEE](https://www.op-tee.org/) |TZ |Ja | Open-Source-Implementierung von Linaro bzw. dem TrustedFirmware-Projekt.Die Zielplattform ist ein Linux-Kernel ohne externe TRH mittels TrustZone. Designziele umfassen: Isolation, geringer Speicherverbrauch und Portabilität. |
|[uTango](https://arxiv.org/abs/2102.03625) |TZM | Nein | Open-Source-Projekt in Entwicklung. Zielplattformen sind IoT Geräte. Ziel ist ein Multi-World TEE mit Mikrokernel-Ansatz und Zero Trust Model: Die Trusted Worlds laufen in TZ Non-Secure Mode. Wenn sie nicht laufen, werden die Daten in der Secure World gespeichert. Nur uTango selbst läuft im Secure Mode. Das Projekt hat eine kleine Trusted Computing Base von 6KB, die sich durch ihre geringe Größe leichter verifizieren lässt. |
|[Trusted Firmware](https://www.trustedfirmware.org/about/) |TZ, TZM |Nein |Implementierung von Linaro und dient als Basis für TEEs auf ARM Cortex-A und -M Plattformen. Ermöglicht Secure Boot, verschiedene Crypto-Funktionen, sicheren Speicher und Attestation. Referenzimplementierung mit Secure Monitor für TrustZone und damit nutzbar als Basis für TEE-Implementierungen auf ARM Prozessoren.| 
| [Pelagi Enclave](https://penglai-enclave.systems/) | RISC-V (PMP) | Nein | Ein [laufendes Open-Source-Projekt](https://github.com/Penglai-Enclave/Penglai-Enclave) mit dem Ziel, ein TEE für RISC-V Plattformen zu entwickeln. Skalierbar und basiert auf RISC-Vs PMP Feature. Bisher sind kaum Informationen verfügbar, wie genau Pelagi Enclave eingestezt werden soll bzw. was es genau ist und welche Features bereitgestellt werden. |
|[MultiZone Security](https://hex-five.com/multizone-security-sdk/) |RISC-V (PMP) |Nein |Open-Source Implementierung von Hex Five. Die Implementierung ermöglicht unbegrenzt viele sichere Umgebungen parallel und ist konfigurierbar durch Policies. | 
|[Keystone](https://keystone-enclave.org/) |RISC-V (PMP) |Nein | Open-Source-Framework zum Entwickeln von TEEs für RISC-V Prozessoren. Bietet monitorbasierte Primitive zum Entwickeln von, auf Bedürfnisse verschiedener Umgebungen (z. B. IoT vs. Server) angepasste, TEEs. | 

{{</table>}}

</p></details>&nbsp;

### Tamper Resistant Hardware (TRH) 
#### **Typen**
Die verschiedenen Typen von TRH sind schwierig voneinander abzugrenzen, da kein Konsens zu herrschen scheint, wann welcher Begriff genutzt wird. Lediglich Trusted Plattform Modules (TPMs) sind durch die Trusted Computing Group (TCG) fest spezifiziert. Im Folgenden werden deshalb die Typen, wie sie in diesem Dokument genutzt werden, beschrieben. Wenn die Implementierung keiner dieser Beschreibungen entspricht, wurde in der Auflistung die Herstellerbezeichnung verwendet. 

**Trusted Plattform Module (TPM):** Verfügt über sicheren Speicher, Funktionen zur Schlüsselgeneration und -verwaltung, einen Random Number Generator (per Spezifikation ist *kein* True Random Number Generator (TRNG) nötig) und Attestation-Funktionen. Spezifiziert von TCG und standardisiert in ISO/IEC 11889. TPM 1.2 und 2.0 sind die aktuell existierenden Versionen, wobei sich die beiden Varianten in Details unterschieden.  

**Secure Element (SE):** Vor physischen Manipulationen geschütztes Modul mit eigenem Prozessor, welches Möglichkeiten zur Schlüsselgeneration und -verwaltung sowie Crypto-Primitive wie Hash-Funktionen und Verschlüsselungsfunktionen bietet. Eigener Speicher ist optional und implementierungsabhängig. 

#### **Implementierungen** 
Für jede TRH ist jeweils der **Typ** analog zur obigen Beschreibung angegeben, sowie – im Falle der Mobilgeräte – die **Plattform**, in welche die Lösung integriert ist. Bei “stand-alone” Produkten, die je nach Schnittstelle mit beliebigen Plattformen genutzt werden können, ist dies entsprechend vermerkt. 

[StrongBox Keymaster API](https://source.android.com/security/keystore) von Android ist eine mit Android Version 9 eingeführte API, die es Anwendungsentwicklern ermöglicht sicherzugehen, dass ihr Schlüsselmaterial von einem mit den StrongBox Anforderungen (separate CPU, sicherer Speicher, ein TRNG<sup id="fnref:1"><a href="#fn:1" class="footnote-ref" role="doc-noteref">1</a></sup>, Maßnahmen gegen Manipulationen) konformen Secure Element verwaltet und gespeichert wird. Bei TRH aus dem Mobilbereich ist deshalb angegeben, ob die jeweilige Lösung mit der StrongBox API genutzt werden kann **(StrongBox)**. 

<details><summary><strong>Tabelle 3: Tamper Resistant Hardware</strong></summary><p>
{{<table "table table-striped">}}

| Name | Typ| Plattform | StrongBox | Kommentar|
| -- | -- | -- | -- | -- |
|[Titan M ](https://android-developers.googleblog.com/2018/10/building-titan-better-security-through.html ) |SE |>= Google Pixel 3 |Ja |Separater Chip von Google, der vor dem Boot mithilfe einer im Chip gespeicherten Signatur verifiziert, ob das Gerät manipuliert wurde. Übernimmt die Verifizierung der LockScreen-Entsperrung, Schlüsselspeicherung und si-chert Firmwareupdates ab. Basiert auf einem ARM Cortex-A3.  Bietet Schutz vor Side-Channel-Angriffen und hat eine Tamper Detection.  64 KB Flash Speicher verfügbar.|
|[Apple Secure Enclave](https://support.apple.com/en-gb/guide/security/sec59b0b31ff/web)|Secure Enclave |iOS, >= iPhone 5s |k. A. |Sicherheits-Subsystem integ-riert in Apple systems on chip (SoCs).  Umfasst den Apple Secure Enclave Processor (SEP), 4 MB internen Speicher und externen, direkt angebunde-nen, durch den SEP verschlüsselten, RAM. |
|[Samsung eSE S3K250AF](https://www.samsungmobilepress.com/feature-stories/strengthening-hardware-security-with-galaxy-s20s-secure-processor/)  |SE |>= Samsung Galaxy S20, standalone |Ja |Vermutlich ein Teil der Knox Vault. 252 kB Flash.  **Zertifizierungen:** [CC EAL 5+](https://news.samsung.com/global/samsung-introduces-best-in-class-data-security-chip-solution-for-mobile-devices) |
|[Samsung eSE S3FV9RR](https://news.samsung.com/global/samsung-elevates-data-protection-for-mobile-devices-with-new-security-chip-solution)  |SE |standalone |k. A. |1.5 / 2.0 MB Flash. Möglicherweise Teil der Knox Vault ab Samsung Galaxy S21. **Zertifizierungen:** CC EAL 6+ |
|[Knox Vault](https://www.samsungknox.com/en/secured-by-knox) |Tamper Resistant Environment |>= Samsung Galaxy S21 |Ja |Ähnlich wie Apple Secure Enclave ist die Knox Vault ein [Sicherheits-Subsystem basierend auf einem SE](https://docs.samsungknox.com/admin/whitepaper/kpe/knox-vault.htm) und bietet u. A. sicheren Speicher für Schlüsselmaterial und Daten. |
|[Huawei inSE](https://consumer-img.huawei.com/content/dam/huawei-cbg-site/en/mkt/legal/privacy-policy/EMUI%209.0%20Security%20Technology%20White%20Paper.pdf ) |SE |>= Kirin 960 |k. A. |Security Chip eingebettet in den AP in HiSilicon Kirin 960, 970, 980, 710 (P 30 line, Mate 20 line). **Zertifizierungen:** [CFNR Technology Certification of Mobile Financial Service Chip Security, China UnionPay Card Chip Security Specifications, Certificate for Commercial Cipher Product Models, EMVCo (für Kirin 980)](https://www.androidauthority.com/hisilicon-kirin-960-soc-close-look-724326/) |
|[Qualcomm SPU](https://www.qualcomm.com/products/features/mobile-security-solutions)|SE |>= Qualcomm Snapdragon 855 |Ja |Integriertes Sub-System auf einigen Qualcomm SoCs mit u. A. Schlüsselverwaltung, Crypto-Funktionen und -Beschleunigern. **Zertifizierungen:** [EAL 4+](https://www.zdnet.com/article/qualcomm-snapdragon-855-soc-snags-smart-card-security-certificate/) |
|[TPM 1.2](https://trustedcomputinggroup.org/resource/tpm-main-specification/)|TPM |standalone |Nein (kein TRNG) |Siehe Abschnitt “Typen”. Schnittstelle und andere nicht spezifizierte Details implementationsabhängig.|
|[TPM 2.0](https://trustedcomputinggroup.org/resource/tpm-library-specification/) | TPM |standalone |Nein (kein TRNG) | Siehe Abschnitt “Typen”. Schnittstelle und andere nicht spezifizierte Details implementations- und profilabhängig. |
|[Microchip ATECC608](https://www.microchip.com/en-us/product/ATECC608B) |SE | standalone | k. A. | [Sicherer Schlüsselspeicher für bis zu 16 Elemente. Bietet Signatur- und Hash-Operationen und AES-Verschlüsselung](https://ww1.microchip.com/downloads/aemDocuments/documents/SCBU/ProductDocuments/DataSheets/ATECC608B-CryptoAuthentication-Device-Summary-Data-Sheet-DS40002239B.pdf) .|
|[NXP EdgeLock SE050](https://www.nxp.com/docs/en/data-sheet/SE050-DATASHEET.pdf) |SE | standalone | k. A. | Bietet Signatur- und Hash-Funktionen, AES-Verschlüsselung und 50kB sicheren Flash. Verbindung mit dem Host via I2C Interface. **Zertifizierungen:** EAL 6+ |
{{</table>}}
</p></details>&nbsp;

## Evaluierungskriterien
Zur Evaluation einiger, für das Projekt SENSIBLE-KI vielversprechend erscheinenden Implementierungen wurden die folgenden Evaluierungskriterien festgelegt: 

- **Zugänglichkeit bzw. Einstiegshürden:**  
Die Attraktivität für Entwickler bzw. die Wahrscheinlichkeit der tatsächlichen Nutzung der Verfahren wird durch hohe Einstiegshürden und ggf. mit dem Einsatz dieser, verbundene Kosten negativ beeinflusst.  

- **Funktionsumfang:**  
Der tatsächliche Funktionsumfang der konkreten Verfahren ist vor allem für die spätere Zuordnung der Verfahren zu den KI-Anwendungsfällen relevant. Untersucht wurden hier z. B. welche Crypto-Funktionen umgesetzt wurden und welche Datenmengen mit dem Verfahren abgesichert werden können.  

- **Performance:**  
Die Nutzung jedes Trusted Computing Verfahrens führt zu zusätzlichem Overhead für beispielsweise Kontextwechsel oder Datenübertragung an ein externes Modul. Um diesen Overhead besser einschätzen zu können, wurden Performance-Messungen für ausgewählte Funktionen des Verfahrens durchgeführt. Diese Ergebnisse sind für die spätere Zuordnung zu den Anwendungsfällen bzw. zur Bewertung der allgemeinen Eignung des Verfahrens wichtig. 

- **Marktverbreitung:**  
Die Verbreitung einer Lösung hilft bei der Bewertung der Relevanz in der Wirtschaft und wird deshalb – falls möglich – erfasst.  

## Evaluierte Verfahren - Mobilgeräte 
### Begründung der Auswahl
Mit Apple und Samsung decken wir zwei der größten Gerätehersteller weltweit ab. Da sich zwischen iOS- und Android-Geräten sowohl Software als auch Hardware stark unterscheiden, ist diese Gegenüberstellung unverzichtbar.  

Android-Geräte machen 70% des Smartphone-Marktes aus. Deshalb wurden stellvertretend verschiedene Pixel-Geräte vom Hersteller Google evaluiert, da dort eine optimierte und unveränderte Android Implementierung zur Verfügung steht, welche keine zusätzlichen Hersteller-Apps (sog. Bloatware) enthält. 

Von jedem Hersteller wurden High-End Geräte gewählt, da diese jeweils über alle wichtigen, durch den Hersteller zum Zeitpunkt der Evaluierung bereitgestellten, Funktionen verfügen. 

### Anmerkung zur Performance-Messung
Als Input für die symmetrischen Crypto-Funktionen wurden jeweils Blöcke zufälliger Daten mit einer Größe von 8 MB verwendet. 

Da die [API für die iOS Secure Enclave nur die Verwendung von asymmetrischer Kryptografie erlaubt](https://developer.apple.com/documentation/security/seckeyalgorithm/2091899-eciesencryptionstandardx963sha25) , wurde die Performance von AES-Algorithmen via ECIES-Entschlüsselung mit einem secp256r1 –Schlüssel (für AES-128-GCM) bzw. einem secp521r1-Schlüssel (für AES-256-GCM) aus der SE erhoben. Dabei ist zu bemerken, dass die Performance von AES-GCM via ECIES unter iOS nicht mit der Performance von AES-GCM unter Android verglichen werden sollte: beim ECIES-Verfahren wird der in der Hardware gespeicherte Schlüssel nur für die initiale Schlüsselableitung benötigt. 

### Evaluierungen 

<details><summary><strong>Google Pixel (Android mit Tensor SoC und Titan M- bzw. M2-Chip)</strong></summary><p>

- **Zugänglichkeit:**  
Google stellt die vollumfängliche, frei verfügbare *Android Security Library* zur Verfügung, welche eine hohe Qualität aufweist. Außerdem werden Entwickler durch Android-Studio, SDKs sowie große Mengen an Dokumentation und Implementierungsbeispielen unterstützt.  Daneben gibt es eine große Community von Android-Entwicklern. 

- **Funktionsumfang:**
Die *Android Security Library* stellt eine Vielzahl an Verfahren und Algorithmen bereit. Es existieren zahlreiche Algorithmen u.A. für Verschlüsselung (symmetrisch/asymmetrisch), Signaturen, Message Digest, Schlüsselgenerierung, Attestation. Zudem gibt es mit dem Android Keystore System eine API zur sicheren Verwahrung von Schlüsseln. Diese kann auf einigen Geräten mit StrongBox, einem integrierten HSM, genutzt werden. Die Anzahl der speicherbaren Schlüssel ist nicht begrenzt. In der Trusted Execution Engine (Tensor Security Core) können nur die von Google bereitgestellten Algorithmen ausgeführt werden. Auf den evaluierten Geräten wird mit großer Wahrscheinlichkeit Googles eigenes TEE Trusty TEE verwendet, um den Android KeyStore abzusichern, wenn StrongBox nicht genutzt wird bzw. nicht genutzt werden kann. 

- **Performance:**<br>
*Tabelle 4: Performance – Pixel 5, Android 12*
{{<table "table table-striped">}}
|Algorithmus / Provider | BouncyCastle | AndroidKeyStore (Trusty TEE) |AndroidKeyStore + StrongBox |
|--|--|--|--|	
|AES-128-GCM |645.28 MB/s |6.77 MB/s |0.01 MB/s |
|AES-256-GCM |599,19 MB/s |6,68 MB/s |0,01 MB/s |
|HMAC-SHA-256 |1.398,10 MB/s |15,36 MB/s |0,02 MB/s |
|secp256r1 keygen |1.666,67 keys/s |39,35 keys/s |4,25 keys/s |
secp256r1 ECDSA sign |5.882,35 ops/s |77,16 ops/s |9,54 ops/s |	
|secp256r1 ECDSA verify |2.500,00 ops/s |2.500,00 ops/s |833,33 ops/s |
{{</table>}}
*Tabelle 5: Performance – Pixel 6 Pro, Android 12* 
{{<table "table table-striped">}}
|Algorithmus / Provider | BouncyCastle | AndroidKeyStore (Trusty TEE) |AndroidKeyStore + StrongBox |
|--|--|--|--|
|AES-128-GCM |838.86 MB/s |3.4 MB/s |0.04 MB/s|
|AES-256-GCM |762,60 MB/s |4,86 MB/s |0,05 MB/s |
|HMAC-SHA-256 |1.677,72 MB/s |9,07 MB/s |0,05 MB/s |
|secp256r1 keygen |2.777,78 keys/s |112,23 keys/s |11,50 keys/s |
|secp256r1 ECDSA sign |7.692,31 ops/s |190,48 ops/s |22,64 ops/s |
|secp256r1 ECDSA verify| 4.761,90 ops/s |1.694,92 ops/s |714,29 ops/s |
{{</table>}}

- **Marktverbreitung:** 
Google Pixel Geräte sind eher gering verbreitet. 2021 lag der Marktanteil in Deutschland [bei etwa 1,2% und 3,8%](https://de.statista.com/infografik/25476/umfrage-zur-nutzung-von-google-smartphones/) in den USA. 

</p></details>&nbsp;

<details><summary><strong>Samsung Knox (Android)</strong></summary><p>
 
- **Zugänglichkeit:** 
Samsung stellt neben der *Android Security Library* (siehe Google Pixel) eigene freie Bibliotheken unter dem Namen *Samsung Knox SDK* zur Verfügung. Diese sind weniger umfangreich dokumentiert und weniger stark verbreitet, da sie nur exklusiv für Samsung-Geräte zur Verfügung stehen. Diese machen die hauseigene Hardware *Samsung Knox Vault* nutzbar. 

- **Funktionsumfang:** 
Zusätzlich zur Android-Bibliotheken stellt Samsung folgende Funktionen zur Verfügung:  
  - *Weaver* (Android-Passwortauthentifizierung),  
  - *Credential Storage* (speichert Schlüssel, biometrische Daten usw.) und  
  - *Samsung Attestation Key* (unterstützt auch Firmware und weitere Geräte).  
  - Der Schlüsselspeicher *Knox Vault Storage* speichert eine unbegrenzte Anzahl an Schlüsseln.
  - Der *Knox Vault Processor* führt ausschließlich von Samsung zur Verfügung gestellte Algorithmen aus. Auf den evaluierten Geräten wird mit großer Wahrscheinlichkeit Samsungs eigenes TEE TEEGRIS verwendet, welches mit dem Samsung Galaxy S10 eingeführt wurde, um den Android KeyStore abzusichern, wenn StrongBox nicht genutzt wird bzw. nicht genutzt werden kann.  

- **Performance:** <br>
*Tabelle 6: Performance – Samsung Galaxy A50, Android 11*
{{<table "table table-striped">}}
|Algorithmus / Provider | BouncyCastle | AndroidKeyStore (TEEGRIS) |AndroidKeyStore + StrongBox |
|--|--|--|--|
|AES-128-GCM |399.46 MB/s |5.89 MB/s |n.V. |
|AES-256-GCM |399.46 MB/s |5.78 MB/s |n.V. |
|HMAC-SHA-256 |1198.37 MB/s |14.39 MB/s |n.V.|
|secp256r1 keygen |694.44 keys/s |15.89 keys/s |n.V.|
|secp256r1 ECDSA sign |4000 ops/s |63.29 ops/s |n.V.|
|secp256r1 ECDSA verify |1724.14 ops/s |1298.7 ops/s |n.V. |
{{</table>}}
*Tabelle 7: Performance – Samsung Galaxy S20FE, Android 11* 
{{<table "table table-striped">}}
|Algorithmus / Provider | BouncyCastle | AndroidKeyStore (TEEGRIS) |AndroidKeyStore + StrongBox |
|--|--|--|--|
|AES-128-GCM |838,86 MB/s |7,9 MB/s |0,18 MB/s| 
|AES-256-GCM |838,86 MB/s |8,62 MB/s |0,18 MB/s|
|HMAC-SHA-256 |1.677,72 MB/s |21,51 MB/s |0,37 MB/s|
|secp256r1 keygen |2.000 keys/s |11,06 keys/s |0,96 keys/s |
|secp256r1 ECDSA sign |11.111,11 ops/s |74,85 ops/s |12,17 ops/s |
|secp256r1 ECDSA verify |4.545,45 ops/s |1.960,78 ops/s|1.204,82 ops/s| 
{{</table>}}

- **Marktverbreitung:** 
Samsung hatte 2021 einen Marktanteil von [ca. 20%](https://www.statista.com/statistics/276477/global-market-share-held-by-samsung-smartphones/) und ist damit der [zweitgrößte Smartphone-Hersteller weltweit](https://www.statista.com/statistics/271496/global-market-share-held-by-smartphone-vendors-since-4th-quarter-2009/).

</p></details>&nbsp;

<details><summary><strong>Apple iPhone (Secure Enclave)</strong></summary><p>

- **Zugänglichkeit:** 
Apple stellt die frei verfügbare Bibliothek *Apple CryptoKit* zur Verfügung, welche eine hohe Qualität aufweist. Außerdem werden Entwickler durch XCode sowie große Mengen an Dokumentation und Implementierungsbeispielen unterstützt. Daneben gibt es eine große Community von iOS-Entwicklern. 

- **Funktionsumfang:** 
*CryptoKit* bietet die Module *SecKey* API (für asymmetrische Schlüssel), Common Crypto Library (symmetrische Verschlüsselung, hashbasierte MACs, Message Digests, Attestation) und *CryptoTokenKit* (für Smart-Card-Support).  Es kann eine hohe Anzahl an ECC-256Bit-Schlüsseln in einem exklusiven Speicherbereich gespeichert werden. Andere Schlüsselformate werden nicht zur Verfügung gestellt. In der Trusted Execution Engine (Secure Enclave) können nur die von Apple bereitgestellten Algorithmen, also keine eigenen Applikationen, ausgeführt werden. 

- **Performance:** <br>
*Tabelle 9: Performance – iPhone X* 
{{<table "table table-striped">}}
|Algorithmus / Provider |ohne Secure Enclave |mit Secure Enclave |
|--|--|--|
|AES-128-GCM Decrypt<sup id="fnref:2"><a href="#fn:2" class="footnote-ref" role="doc-noteref">2</a></sup> (ECIES via secp256r1-Schlüssel) |763,26 MB/s |472,95 MB/s|
|AES-256-GCM Decrypt (ECIES via secp521r1-Schlüssel) |495,82 MB/s |n. V. |
|secp256r1 ECDH key exchange |3.892,00 ops/s |135,97 ops/s |secp256r1 keygen |132,88 keys/s |79,77 keys/s |
|secp256r1 ECDSA sign |3.769,10 ops/s |95,36 ops/s |
|secp256r1 ECDSA verify |5.272,65 ops/s |1.492,70 ops/s |
{{</table>}}
*Tabelle 10: Performance – iPhone 12 Pro* 
{{<table "table table-striped">}}
|Algorithmus / Provider |ohne Secure Enclave |mit Secure Enclave |
|--|--|--|
|AES-128-GCM Decrypt (ECIES via secp256r1-Schlüssel) |1.849,27 MB/s |755,34 MB/s |
|AES-256-GCM Decrypt (ECIES via secp521r1-Schlüssel) |1473,18 MB/s |n. V. |
|secp256r1 ECDH key exchange |3.417,93 ops/s |148,43 ops/s |
|secp256r1 keygen |192,37 keys/s |100,93 keys/s| 
|secp256r1 ECDSA sign |3832,87 ops/s |124,64 ops/s|
|secp256r1 ECDSA verify |6416,70 ops/s |2181,78 ops/s| 
{{</table>}}
*Tabelle 11: Performance – iPhone 13 Pro*
{{<table "table table-striped">}}
|Algorithmus / Provider |ohne Secure Enclave |mit Secure Enclave |
|--|--|--|
|AES-128-GCM Decrypt (ECIES via secp256r1-Schlüssel) |1.172,12 MB/s |757,24 MB/s |
|AES-256-GCM Decrypt (ECIES via secp521r1-Schlüssel) |883,49 MB/s |n. V. |
|secp256r1 ECDH key exchange |7.820,13 ops/s |212,38 ops/s |
|secp256r1 keygen |283,47 keys/s |135,35 keys/s| 
|secp256r1 ECDSA sign |6.527,13 ops/s |193,38 ops/s|
|secp256r1 ECDSA verify |7.216,83 ops/s |3.392,44 ops/s |
{{</table>}}
- **Marktverbreitung:**
  Apple hatte 2021 einen Marktanteil von 19,2% und ist damit der drittgrößter Smartphone-Hersteller weltweit. 
</p></details>&nbsp;

### Übersicht der Ergebnisse  

*Tabelle 12: Übersicht der Ergebnisse für Mobilgeräte* 
|Verfahren |Zugänglichkeit | Funktionalität|Performance |Marktverbreitung |
|--|--|--|--|--|
|Google Pixel | gut | hoch | starke Performance-Einbußen bei Verwendung der “AndroidKeyStore”-TEE gegenüber der Software-Implementierung; sehr starke Einbußen bei Verwendung des “StrongBox”-SE |sehr gering |
|Samsung Knox |gut / mittel |hoch | starke Performance-Einbußen bei Verwendung der “AndroidKeyStore”-TEE gegenüber der Software-Implementierung; sehr starke Einbußen bei Verwendung des “StrongBox”-SE | sehr hoch |
|Apple iPhone |gut |hoch |starke Performance-Einbußen bei Verwendung der Secure Enclave |sehr hoch |


## Evaluierte Verfahren – Eingebettete Systeme 
### Begründung der Auswahl
Als TEE wurde OP-TEE gewählt, da es sich um eine Opensource-Lösung handelt und somit eine der wenigen, auf die problemloser Zugriff möglich ist. Außerdem ist OP-TEE kompatibel mit der GlobalPlatform (GP) TEE API und dementsprechend geeignet für Entwicklung von TAs für alle GP kompatiblen TEEs.  

Kinibi-M auf dem *SAML11 Evaluation Kit* wurde gewählt, um Arm-Cortex M Prozessoren mit TrustZone-M Unterstützung abzudecken. 

Der NXP SE050 und der Zymkey 4i von Zymbit sind beide Secure Elements, kompatibel mit dem RasperryPi und somit leicht zu evaluieren und gut für die Entwicklung von Prototypen einzusetzen. Die SEs unterschieden sich in den verfügbaren Crypto-Funktionen und der Zielgruppe. Zudem wurde als TRH das TPM 2.0 Modul von Let’sTrust gewählt. Dieses ist ebenfalls kompatibel mit dem RaspberryPi und implementiert die TPM 2.0 Spezifikation.  

### Anmerkung zur Performance-Messung 
Als Inputgröße für die Crypto-Funktionen wurde jeweils entweder die maximal unterstützte Buffergröße oder, bei keiner offenkundigen Begrenzung, 1MB verwendet. Es wurde jeweils der letzte API-Call vor einem Wechsel in entweder die Schnittstellenübertragung zur TRH bei externen Modulen oder einem Kontextwechsel in die sichere Welt bei TEEs gemessen.  

<details><summary><strong>OP-TEE (STM32MP157A-DK1)</strong></summary><p>

- **Zugänglichkeit:**  
Es sind sowohl Open-Source Quellcode als auch Dokumentation zur Nutzung und “Installation” von OP-TEE verfügbar. Es existieren ein Build-Guide und eine Architekturbeschreibung. Die zugehörige API Doku ist die offizielle GlobalPlatform TEE API 1.0. Die Dokumentation von Linaro/TrustedFirmware ist ausreichend aktuell und vollständig. <br>
Es existieren verschiedene – leider unkommentierte – Code-Beispiele in C und ein build.git mit fertigen Builds für bestimmte Plattformen. Soll OP-TEE auf einer dort nicht enthaltenen Plattform genutzt werden, ist dies deutlich anspruchsvoller und erfordert Erfahrung oder Kenntnisse im Bereich der Betriebssystementwicklung und Betriebssystemstruktur, da hier der Build aus verschiedenen Bestandteilen (op-tee, linux, u-boot, Plattform-spezifische Treiber…) mit entsprechenden Makefiles selbst erstellt werden muss. Die Nutzung von OP-TEE ist mit einer Menge verschiedener Plattformen möglich, jedoch sind nur einige davon vorhanden im build-git.  

- **Funktionsumfang:** 
Der Funktionsumfang entspricht der GlobalPlattform TEE Spezifikation und ist dementsprechend umfangreich. Unter anderem unterstützt wird RSA- und AES-Verschlüsselung und sicherer Speicher. Bisher bietet OP-TEE keinen Support für Remote- oder Key-Attestation. Da es sich um ein Open-Source TEE handelt, ist die Erstellung und Einbindung eigener TAs kein Problem und es besteht über OP-TEE mittels Pseudo TAs die Möglichkeit, bestimmte Peripherie mittels TrustZone abzusichern.  
Das genutzte Board verfügt über einen TRNG und dieser wird von OP-TEE, soweit überprüfbar, auch genutzt.  

- **Perfomance:** 
*Tabelle 13: Performance – OP-TEE (STM32MP157A-DK1)* 
{{<table "table table-striped">}}
|Funktion |Performance |
|--|--|
|AES128-CTR Enc |4,56 MB/s |
|AES128-CTR Dec |4,56 MB/s |
|RSA2048-RSAES Enc |2,44 kB/s |
|RSA2048-RSAES Dec |0,16 kB/s |
{{</table>}}

- **Marktverbreitung:**
Bezüglich der Marktverbreitung sind keine Angaben möglich, da es keine Daten gibt. OP-TEE verfügt jedoch über einen hohen Bekanntheitsgrad. 

</p></details>&nbsp;

<details><summary><strong>NXP EdgeLock SE050 Development Kit</strong></summary><p> 
- **Zugänglichkeit:**  
  Die Dokumentation ist nur über einen Download nach Anmeldung auf der Webseite des Herstellers verfügbar. Gleiches gilt für die gesamte Middleware (eine reduzierte Version der Middleware ist auch auf GitHub verfügbar). Der Quellcode wird mitausgeliefert. Die Dokumentation ist teils unerwartet strukturiert und stellenweise sehr knapp. Alles in allem ist die Doku in Bezug auf die relevanten Informationen vollständig und für Personen, die sich etwas mit der Materie (also SEs und kryptografischen Funktionen) auskennen und wissen, wonach sie suchen müssen, gut nutzbar.
   Die Anbindung mittels I2C ermöglicht theoretisch die Nutzung mit allen Linux-fähigen Geräten mit einer entsprechenden Schnittstelle – getestet wurde jedoch nur mit dem RaspberryPi 3. 

- **Funktionsumfang:** 
Das SE hat einen nach NIST SP800-90A implementierten PRNG. Es werden sowohl AES- und RSA-Verschlüsselung als auch verschiedene ECC-Methoden unterstützt. Generell ist die API recht umfangreich und unterstützt viele Crypto-Primitive. Das Gerät verfügt über 50 kB *secured user flash memory*, in welchem *Secure Object* wie bspw. Schlüssel gespeichert werden können. Der implementierte Key Store unterstützt Key-Attestation. Der NXP SE050 bietet eine zweite I2C Schnittstelle, an die ein externes Gerät – wie beispielsweise ein Sensor – angeschlossen werden kann, was ein attestiertes Auslesen der Sensor-Daten über das SE ermöglicht.   

- **Perfomance:** 
  *Tabelle 14: Performance – NXP EdgeLock SE050 Development Kit*
{{<table "table table-striped">}}
|Funktion |Performance |
|--|--|
|AES128-CBC Enc |2,7 kB/s |
|AES128-CBC Dec |2,7 kB/s |
|HMAC-SHA256 |2,8 kB/s |
|ECDSA-SHA256 Sign |0,5 kB/s |
{{</table>}}

- **Marktverbreitung:**
  Zur Markverbreitung sind keine Angaben möglich, da keine Daten verfügbar sind. Der NXP EdgeLock ist Teil der [Google SE Alliance](https://security.googleblog.com/2021/03/announcing-android-ready-se-alliance.html), wodurch zukünftig eine erhöhte Verbreitung möglich ist. 

</p></details>&nbsp;

<details><summary><strong>Zymkey 4i</strong></summary><p> 

- **Zugänglichkeit:**
  Die Dokumentation der Zymbit API ist sowohl auf der [Herstellerseite](https://docs.zymbit.com/api/) als auch als PDF-Version<sup id="fnref:3"><a href="#fn:3" class="footnote-ref" role="doc-noteref">3</a></sup> verfügbar. Es gibt eine C-API, eine C++-API und eine Python-API. Die jeweiligen Dokumentationen sind – insbesondere bezüglich der Methodenbeschreibungen in den unterschiedlichen APIs – an einigen Stellen inkonsistent. Man erhält also durch das Lesen der Python-API nicht dieselben Informationen über das Gerät und die Methoden, wie durch das Lesen der C-API. Auch die API auf der Herstellerseite unterscheidet sich von der PDF-Version. Weiterhin sind in der Dokumentation alle Funktionen für alle Zymbit-Geräte enthalten. Da die Funktionen keiner direkt erkennbaren Sortierung in Bezug auf die Verfügbarkeit auf den einzelnen Geräten folgt, muss dadurch bei jeder Funktion in der Beschreibung dieser überprüft werden, ob diese überhaupt auf dem Zymkey 4i unterstützt wird. Grundsätzlich wird jedoch durch den geringen Umfang an Funktionen bereitgestellten Beispielcode und die vorhandene Python-API die Nutzung auf für nicht-C-Programmierer eine Nutzung stark erleichtert. 
  Die Nutzung des Zymkey ist theoretisch mit allen I2C-fähigen Geräten möglich, jedoch sind die Libraries zur Nutzung – zum Zeitpunkt der Evaluation – nur als Debian Pakete verfügbar, sodass eine Portierung erschwert wird.  

- **Funktionsumfang:** 
  Der Zymkey 4i bietet eine *lock*-Methode, welche Daten mittels AES-128 verschlüsselt und mit einem vom Hersteller vorinstallierten, einzigartigen ECDSA-Key signiert. Es können **keine eigenen** Schlüssel gespeichert oder neue generiert werden. Ein Schlüsselspeicher kann also nur in vom Zymkey verschlüsseltem Speicher des Hostgerätes realisiert werden. Der Zymkey 4i nutzt – vermutlich – den TRNG des integrierten ATECC608 Chips für die Generation von Zufallszahlen. Abgesehen von besagter lock-Methode und der Generation von Zufallszahlen unterstützt der Zymkey lediglich eine weitere Krypto-Funktion: ECDSA-SHA256 Signaturen, wobei der SHA256 Hash scheinbar nicht durch den Zymkey, sondern auf dem Host-Gerät berechnet wird. Obwohl der ATECC608 weitere kryptographische Operationen unterstützt, werden diese durch die API beim Zymkey 4i nicht angeboten. Dazu müsste man auf das Zymbit HSM6 (das über denselben Chip verfügt) zurückgreifen. Remote Attestation wird im [Product Brief](https://www.zymbit.com/wp-content/uploads/2021/08/Zymbit_ProductBrief_Zymkey4i_04100100_04150911_B1.pdf) des Zymkey 4i als Feature angepriesen, allerdings lässt sich dazu weder etwas in der API Doku noch im zugehörigen Forum finden, wie diese genau umgesetzt werden kann.

- **Perfomance:** 
*Tabelle 15: Performance – Zymkey 4i* 
{{<table "table table-striped">}}
|Funktion |Performance |
|--|--|
|“Lock” (AES-128 Enc & ECDSA Sign) |2,61 kB/s| 
|“Unlock” (AES-128 Dec & ECDSA Verify) |2,61 kB/s |
|ECDSA Sign |0,23 kB/s |
{{</table>}}

- **Marktverbreitung:**
Zur Markverbreitung sind keine Angaben möglich, da keine Daten verfügbar sind. 

</p></details>&nbsp;

<details><summary><strong>Let'sTrust TPM 2.0</strong></summary><p> 

- **Zugänglichkeit:**  
  Es existieren verschiedene Implementierungen der TPM 2.0 API. Für die experimentelle Evaluierung wurde [*diese*](https://github.com/tpm2-software) genutzt. Dokumentation ist in Form mehrerer Spezifikations-Dokumente von der Trusted Computing Group (TCG) vorhanden. Diese sind sehr umfangreich und komplex. Außerdem existiert für die referenzierte Implementierung ein [Tool](https://github.com/tpm2-software/tpm2-tools), mit dem die TPM2-API leicht von der Kommandozeile des Hostgerätes aus genutzt werden kann. Das Tool selbst ist ausreichend gut dokumentiert. Für die TPM2-API Implementierung selbst existiert hingegen scheinbar kein Beispielcode, an dem Einsteiger sich bzgl. der Nutzung der API orientieren könnten.   <br> Das Let’sTrust TPM kann über eine SPI Schnittstelle und mittels der Code-Libraries leicht mit jedem Linux-fähigen Gerät mit einer solchen Schnittstelle genutzt werden.  
- **Funktionsumfang:** 
  Der Funktionsumfang des Let’sTrust TPM 2.0 entspricht dem erforderlichen (mandatory) Funktionsumfang der TPM 2.0 Spezifikation. Das TPM verfügt über einen Deterministischen-RNG nach NIST SP800-90A, für die Generation von Zufallszahlen. Das TPM unterstützt RSA Ver- und Entschlüsselung und verschiedene Signatur-Methoden sowie Elliptic Curve Cryptography  und unterstützt Elliptic Curve Diffie Hellman, jedoch **keine AES Verschlüsselung** bzw. nicht den entsprechenden, optionalen, TPM Command *TPM2_EncryptDecrypt*. Schlüssel oder andere zu sichernde Daten können in den 6kB Speicher des TPMs vor Manipulationen geschützt gespeichert werden. Aktuell gibt es noch keine Möglichkeit zur Remote Attestation mit dem Let’sTrust TPM, [jedoch ist sie in Planung](https://letstrust.de/archives/39-New-Project-EnactTrust.html). Über die Methode *TPM2_Certify* kann attestiert werden, dass ein Key auf dem TPM gespeichert ist, jedoch unterstützt das evaluierte Board **nicht** die *TPM2_CertifyX509* Methode, mich welcher auch die Attribute eines Keys/Objekts mit einem X.509 Zertifikat attestiert werden würden. Das TPM verfügt über keine weiteren Schnittstellen zum Anschließen anderer Peripherie.  
- **Perfomance:** 
*Tabelle 16: Performance –Let’sTrust TPM 2.0*
{{<table "table table-striped">}}
|Funktion |Performance |
|--|--|
|HMAC-SHA256 |4,79 kB/s| 
|RSA2048-RSAES Enc |3,45 kB/s |
|RSA2048-RSAES Dec |0,77 kB/s |
{{</table>}}
- **Marktverbreitung:**
  Zur Markverbreitung sind keine Angaben möglich, da keine Daten verfügbar sind. TPM 2.0 Implementierungen im Allgemeinen jedoch verbreitet eingesetzt.

</p></details>&nbsp;

<details><summary><strong>Kinibi-M</strong></summary><p> 

- **Zugänglichkeit:**  
  Das Kinibi-M SDK ist nicht Open-Source und kann nur nach Anmeldung und Anfrage bei Trustonic über einen Link heruntergeladen werden. Bisher wird Kinibi-M nur für den Atmel SAML11 (das Production SDK nur für den SAML11 KPH mit einzigartigem Key) angeboten. Die Dokumentation wird mit dem SDK ausgeliefert und ist sehr umfangreich und gut strukturiert. Neben der reinen API-Dokumentation existieren noch ein *Getting Started* Dokument und der *Kinibi-M Developer’s Guide*, die den Einstieg erleichtern. Zusätzlich dazu liefert das SDK einige Code Samples, anhand deren die Nutzung von Kinibi-M leicht zu erschließen ist. 

- **Funktionsumfang:** 
    Die Kinibi-M Crypto API bietet u. A. die folgenden relevanten Funktionen: AES-128 Ver- und Entschlüsselung, Hashberechnung mit SHA256, Speichern von Daten im Secure Storage (1kB Data Flash auf dem Board verfügbar) und Zufallszahlengeneration. Es ist anhand der Dokumentation nicht ersichtlich, ob Kinibi-M den TRNG des SAML11 nutzt oder einen DRNG (ggf. auf Basis des TRNG) implementiert. Eine Key- oder Remote-Attestation nach klassischer Definition ist nicht implementiert. Über die Möglichkeiten von TrustZone-M kann Peripherie abgesichert werden bzw. kann sichere Peripherie aus der TA heraus genutzt werden. TAs für Kinibi-M können leicht mit dem SDK entwickelt werden.  
- **Perfomance:** 
  Leider konnten in der Kürze der Zeit keine Performance-Messungen mit dem SAML11 Xplained Pro durchgeführt werden, da eine Zeitmessung auf diesem Board ungleich komplexer – und auch grundverschieden – durchzuführen wäre als mit den Linux-fähigen anderen Boards.  
- **Marktverbreitung:**
    Zur Markverbreitung sind keine Angaben möglich, da bisher keine Daten verfügbar sind. Da Kinibi-M bisher nur für eine einzige Plattform verfügbar ist, vermutlich sehr niedrig. Wenn mehr ARM Cortex-M Prozessoren mit TrustZone-M eingesetzt werden sollten, wird die Verbreitung vermutlich aufgrund des Bekanntheitsgrads von Kinibi steigen.  
</p></details>&nbsp;

### Übersicht der Ergebnisse  
*Tabelle 17: Übersicht der Ergebnisse für eingebettete Systeme*
|Implementierung |Einstiegshürden |Umgesetzte Funktionalität |Performance |Markt-verbreitung |
|--|--|--|--|--|
|NXP SE050  |mittel – hoch |hoch |gering |k. A. |
|Zymkey 4i  |gering - mittel |gering |gering |k. A. |
|Let’sTrust TPM 2.0  |hoch |hoch |gering |k. A. |
|OP-TEE  |mittel – hoch |hoch |mittel – hoch |k. A.| 
|Kinibi-M |gering |gering |k. A. |k. A. | 


<div class="footnotes" role="doc-endnotes">
	<hr />
	<ol>
		<li id="fn:1" role="doc-endnote">
			<p>
				True Random Number Generator.
				<a href="#fnref:1" class="footnote-backref" role="doc-backlink">&#8617;</a>
			</p>
		</li>
		<li id="fn:2" role="doc-endnote">
			<p>
				Hier wurde spezifisch das Entschlüsseln per ECIES gemessen, da nur dabei auf den asymmetrischen Schlüssel in der Secure Enclave zugegriffen werden muss.
				<a href="#fnref:2" class="footnote-backref" role="doc-backlink">&#8617;</a>
			</p>
		</li>
    <li id="fn:3" role="doc-endnote">
			<p>
				https://s3.amazonaws.com/zk-sw-repo/zk_app_utils.py.pdf bzw. https://s3.amazonaws.com/zk-sw-repo/zk_app_utils.c.pdf
				<a href="#fnref:3" class="footnote-backref" role="doc-backlink">&#8617;</a>
			</p>
		</li>
	</ol>
</div>
