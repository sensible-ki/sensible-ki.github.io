---
date: 2021-09-27
title: "Hardware Measures"
linkTitle: "Hardware Measures"
type: docs
weight: 4
description: >
  Trusted computing techniques to protect AI applications against attackers
---


# Evaluation Results - Trusted Computing Solutions

## General Overview of Identified Mechanisms
The solutions and mechanisms of Trusted Computing were sorted into two groups, which differ in the way they realize the goals of Trusted Computing. 

The first group, **Trusted Execution Environments** and related Technologies, comprises implementations that use preexisting features of the application processor. Opposed to that, the second group consists of **Tamper Resistant Hardware** and includes hardware modules specifically designed to provide functionality needed to reach the goals of Trusted Computing.  

### Trusted Execution Environments (TEEs) and Frameworks  
#### Underlying Technologies 
The idea of **Trusted Execution Environments (TEEs)** is to achieve the separation of critical processes and their data from any sort of non-trustworthy code. In the case of a TEE the domain of “non-trustworthy code” even includes the normal operating system **(Rich Execution Environment (REE))** and all processes running in it. The TEE has got its own secure operating system and own processes **(Trusted Applications (TAs))**. 

To ensure the separation of the secure domain of the TEE from the non-secure REE, an underlying hardware-based technology is required. Application processors from different manufacturers provide differing technologies to enforce separation which will be described in the following: 

[**TrustZone (TZ)**](https://developer.arm.com/ip-products/security-ip/trustzone/trustzone-for-cortex-a?_ga=2.76035478.2094999520.1624452026-845153957.1615900232) is supported by (some) ARM Cortex-A processors. It supports the separation of resources into a single “Secure World” and a single “Non-Secure World”. The separation is enforced and realized by processor bits signaling the current context, which can be changed by specific instruction set operations that trigger a secure context switch from one world into the other. The resources governed by TrustZone include regions of the main memory, access to certain peripherals and CPU usage. Due to the high prevalence of ARM Cortex-A processors in mobile and embedded systems, TrustZone is supported by many devices in these sectors. 

[**TrustZone-M (TZM)**](https://developer.arm.com/ip-products/security-ip/trustzone/trustzone-for-cortex-m) is the equivalent technology for ARM Cortex-M processors. TZ and TZM work mostly in the same way, except that TZM facilitates the context switches via branch instructions which allows a lower latency. TZM is optimized for low power profiles.

[**Intel SGX**](https://www.trentonsystems.com/blog/what-is-intel-sgx) is an Instruction Set Extension provided by Intel on (some) of its x86 CPUs. Intel SGX allows to separate the main memory into “Enclaves”. The separation is enforced by encryption of the respective memory region. This technology allows an arbitrary number of secure “Enclaves” but does not secure any other resources than the memory. 

[**AMD SEV/PSP**](https://developer.amd.com/sev/): AMD provides a virtualization technology using the AMD Platform Security Processor (PSP), which is itself an ARM chip supporting TrustZone. The PSP generates and manages the cryptographic key material used to encrypt the memory regions and CPU registers belonging to the secured “Guests”. An arbitrary amount of “Guest” can be secured this way.  

[**RISC-V Physical Memory Protection (PMP)**](https://sifive.github.io/freedom-metal-docs/devguide/pmps.html) is an additional module, part of RISC-V architecture, that enforces memory access policies via the application processor. These policies can be used to implement a secure domain for a TEE on a RISC-V processor. 

#### **Implementations**
In the following table, the necessary requirements of the CPU **(Platform)**  have been listed for each solution. In addition, it has been indicated whether the implementation is compliant with the [GlobalPlatform TEE API Specification](https://globalplatform.org/specs-library/tee-internal-core-api-specification/) **(GP Compliance)**.  

<details><summary><strong>Table 1: Commercial / Proprietary Solutions</strong></summary><p>

{{<table "table table-striped">}}

| Name | Platform | GP Compliance | Comments |
| -- | -- | -- | -- |
| [Qualcomm TEE (QTEE / QSEE)](https://www.qualcomm.com/media/documents/files/guard-your-data-with-the-qualcomm-snapdragon-mobile-platform.pdf) | TZ | Yes (SFS API) | QTEE uses the Secure Processing Unit (SPU) on some Qualcomm SoCs next to TrustZone. **Certifications:** [FIPS 140-2 Level 1 (Crypto Lib), FIPS Level 2 (crypto engine core), FIPS Level 1 (PRNG), FIPS Level 1 (Inline Crypto engine)](https://www.qualcomm.com/news/onq/2020/04/16/qualcomm-technologies-product-security-solutions-receive-vital-fips) |
|[Kinibi](https://www.trustonic.com/technology/)|TZ|Yes|[Implementation from Trustonic especially for Exynos Chips.](https://azeria-labs.com/trustonics-kinibi-tee-implementation/). **Certifications:** [Common Criteria (TEE)](https://www.ssi.gouv.fr/uploads/2017/02/anssi_cc-2017_03-cible-publique.pdf) |
|[TEEGRIS](https://developer.samsung.com/teegris/overview.html) |TZ|Yes|For Samsung Exynos, by Samsung. Starting with the Samsung Galaxy S10 TEEGRIS [replaced Kinibi as the TEE implementation on many Samsung smartphones](https://www.riscure.com/blog/tee-security-samsung-teegris-part-1).|
|[iTrustee](https://globalplatform.org/certified-products/huawei-itrustee-v3-0-on-kirin-980/) |TZ |Yes |Huawei’s own implementation. Replaced Huawei’s older solution, Trusted Core, on recent Huawei Smartphones. **Certifications:**  [CC EAL2+](https://www.commoncriteriaportal.org/products/) |
|[Kinibi-M](https://www.trustonic.com/technical-articles/kinibi-m/) |TZM |No info |Implementation by Trustonic for ARM Cortex-M CPUs. Currently only supports Microchips SAML11. |

{{</table>}}

</p></details>&nbsp;

<details><summary><strong>Table 2: Research- and. Open-Source Projects</strong></summary><p>
{{<table "table table-striped">}}

| Name | Platform | GP Compliance | Comments|
| -- | -- | -- | -- |
|[Trusty](https://source.android.com/security/trusty) | TZ, Intel SGX |No | Open-source implementation by Android  | 
|[GoTEE](https://github.com/f-secure-foundry/GoTEE) |TZ |No |Open-source implementation by f-secure. Currently only supports following SoCs: NXP i.MX6ULL, NXP i.MX6ULZ.| 
|[OP-TEE](https://www.op-tee.org/) |TZ |Yes | Open-source implementation by Linaro/TrustedFirmware Project. Target platform is a Linux kernel without external TRH, with a CPU with TZ support. Design goals: Isolation, low memory profile and portability. |
|[uTango](https://arxiv.org/abs/2102.03625) |TZM | No | Open-source project in progress. Targeting IoT devices. Goal is a Multi-World TEE following a Microkernel-Approach and Zero Trust Model: The Trusted Worlds run in TZ Non-Secure Mode. While suspended, their data is stored in the Secure World. The only process running in Secure Mode is the uTango kernel itself. The project’s Trusted Computing Base is, with 6kB, quite small and thus easier to verify.  |
|[Trusted Firmware](https://www.trustedfirmware.org/about/) |TZ, TZM |No |Implementation by Linaro. Serves as a base layer for the creation of TEEs targeting ARM Cortex-A and –M platforms. Supports Secure Boot, various crypto primitives, secure storage and attestation. Provides a reference implementation with Secure Monitor for  TrustZone.  | 
| [Pelagi Enclave](https://penglai-enclave.systems/) | RISC-V (PMP) | No | A [work in progress Open-source project](https://github.com/Penglai-Enclave/Penglai-Enclave) aiming to develop a TEE for RISC-V platforms. Scalable and based on RISC-Vs PMP feature. Currently barely any information available, how exactly the project can be used when finished and what features it will support.   |
|[MultiZone Security](https://hex-five.com/multizone-security-sdk/) |RISC-V (PMP) |No |Open-source implementation by Hex Five. The implementation allows the creation of an arbitrary number of secure environments. The security of each environment can be configured via policies.   | 
|[Keystone](https://keystone-enclave.org/) |RISC-V (PMP) |No | Open-source framework for developing TEEs for RISC-V. Supports monitor-based primitives to create TEEs tailored to needs of differing host platforms (e.g., IoT vs. Server). | 
{{</table>}}

</p></details>&nbsp;

### Tamper Resistant Hardware (TRH) 
#### **Types**
It is hard to cleanly differentiate between the different types of TRH, since there appears to be no universally accepted definition about when which term is applicable. The only type that is officially specified by the Trusted Computing Group (TCG) is the term Trusted Platform Module (TPM).  

To avoid unnecessary confusion, the types used in this document to describe and characterize the identified TRH, will be defined. If a specific module did not fit any of these descriptions or not enough information was available, the term used by the manufacturer was adopted.  

**Trusted Plattform Module (TPM):** Provides secure, tamper resistant on-chip storage, means for key generation and management, a random number generator (RNG) - which does not need to be a True Random Number Generator (TRNG) -, and attestation. Specified by the TCG and in ISO/IEC 11889. The currently “active” Versions of the TPM specification are TPM 1.2 and TPM 2.0 which differ mainly regarding their supported cryptographic primitives. 

**Secure Element (SE):** A module or chip resistant to physical manipulations. Provides key generation and management as well as an unspecified set of cryptographic primitives like hash- or encryption algorithms. On chip-storage is optional.  

#### **Implementations** 
For every TRH the respective **Type** is given (as explained in Section “Types”), as well as – in case of TRH from the mobile sector - the corresponding **Platform**. Some products can be used with arbitrary platforms and are marked accordingly.  

Androids [StrongBox Keymaster API](https://source.android.com/security/keystore) was introduced with Android version 9 and provides functions to check whether key material is stored and managed by a StrongBox compliant Secure Element, providing a separate CPU, secure storage, a TRNG<sup id="fnref:1"><a href="#fn:1" class="footnote-ref" role="doc-noteref">1</a></sup> and tamper resistance. In case of TRH belonging to mobile devices, compliance with StrongBox is given as well **(StrongBox)**.

<details><summary><strong>Table 3: Tamper Resistant Hardware</strong></summary><p>
{{<table "table table-striped">}}

| Name | Type| Platform | StrongBox | Comment|
| -- | -- | -- | -- | -- |
|[Titan M ](https://android-developers.googleblog.com/2018/10/building-titan-better-security-through.html ) |SE |>= Google Pixel 3 |Yes |Separate chip by Google. Verifies the device intergity at boot using a signature stored in the chip. Further, verifies unlock requests of LockScreen, stores keys and supports secure firmware updates. Based on ARM Cortex-A3. Protection against side-channel attacks and provides tamper detection. 64 kB flash available. |
|[Apple Secure Enclave](https://support.apple.com/en-gb/guide/security/sec59b0b31ff/web)|Secure Enclave |iOS, >= iPhone 5s |No info |Integrated security subsystem on Apples system on chips (SoCs). Contains the Apple Secure Enclave Processor (SEP), 4MB internal storage and additional external RAM, that is solely connected to the Secure Enclave and encrypted by the SEP.|
|[Samsung eSE S3K250AF](https://www.samsungmobilepress.com/feature-stories/strengthening-hardware-security-with-galaxy-s20s-secure-processor/)  |SE |>= Samsung Galaxy S20, standalone |Yes |Might be part of the Knox Vault. 252 kB Flash. **Certifications**: [CC EAL 5+](https://news.samsung.com/global/samsung-introduces-best-in-class-data-security-chip-solution-for-mobile-devices) |
|[Samsung eSE S3FV9RR](https://news.samsung.com/global/samsung-elevates-data-protection-for-mobile-devices-with-new-security-chip-solution)  |SE |standalone |No info |1.5/2.0 MB Flash. Might be part of the Knox Vault since Samsung Galaxy S21. **Certifications**: CC EAL 6+ |
|[Knox Vault](https://www.samsungknox.com/en/secured-by-knox) |Tamper Resistant Environment |>= Samsung Galaxy S21 |Yes |Like Apple Secure Enclave, Knox Vault is a security subsystem based on a SE [security subsystem based on a SE](https://docs.samsungknox.com/admin/whitepaper/kpe/knox-vault.htm), which provides, amongst other functions, secure storage for key material and data.|
|[Huawei inSE](https://consumer-img.huawei.com/content/dam/huawei-cbg-site/en/mkt/legal/privacy-policy/EMUI%209.0%20Security%20Technology%20White%20Paper.pdf ) |SE |>= Kirin 960 |No info |Dedicated security chip embedded into the application processor in HiSilicon Kirin 960, 970, 980, 710 (P 30 line, Mate 20 line) **Certifications**: [CFNR Technology Certification of Mobile Financial Service Chip Security, China UnionPay Card Chip Security Specifications, Certificate for Commercial Cipher Product Models, EMVCo (für Kirin 980)](https://www.androidauthority.com/hisilicon-kirin-960-soc-close-look-724326/) |
|[Qualcomm SPU](https://www.qualcomm.com/products/features/mobile-security-solutions)|SE |>= Qualcomm Snapdragon 855 |Yes |Subsystem integrated in some Qualcomm SoCs providing among other functions secure key management, crypto-primitives and –accelerators. **Certifications**:  [EAL 4+](https://www.zdnet.com/article/qualcomm-snapdragon-855-soc-snags-smart-card-security-certificate/) |
|[TPM 1.2](https://trustedcomputinggroup.org/resource/tpm-main-specification/)|TPM |standalone |No (no TRNG) |See section “Types”. Interface for data transmission and other details not covered by the specification are implementation and profile dependent. |
|[TPM 2.0](https://trustedcomputinggroup.org/resource/tpm-library-specification/) | TPM |standalone |No (no TRNG) | See section “Types”. Interface for data transmission and other details not covered by the specification are implementation dependent.  |
|[Microchip ATECC608](https://www.microchip.com/en-us/product/ATECC608B) |SE | standalone | No info | [Secure key storage for up to 16 elements. Provides signature- and hash-alogrithms and AES encryption](https://ww1.microchip.com/downloads/aemDocuments/documents/SCBU/ProductDocuments/DataSheets/ATECC608B-CryptoAuthentication-Device-Summary-Data-Sheet-DS40002239B.pdf) .|
|[NXP EdgeLock SE050](https://www.nxp.com/docs/en/data-sheet/SE050-DATASHEET.pdf) |SE | standalone | No info |Provides signature- and hash-alogrithms, AES encryption and 50kB secure flash. Supported host interface is I2C. **Certifications**:  EAL 6+ |
{{</table>}}
</p></details>&nbsp;

## Criteria of Evaluation 
To evaluate some of the implementations, which seemed promising regarding the goals of the project SENSIBLE-KI, the following criteria of evaluation were chosen:  

- **Accessibility and Usability:**  
The probability that a proposed security mechanism is actually used, is lowered by the direct (financial) and indirect (additional knowledge and time required) cost of this mechanism.   

- **Supported Features:**  
The actual functionality of a specific solution or module is relevant, especially when matching Trusted Computing mechanisms to AI Use-Cases, later on. The evaluated functionality was focused on the supported crypto-primitives and if or how much data can be securely stored by the solution.   

- **Performance:**  
Using any Trusted Computing mechanism will cause additional overhead e.g., from context switches or data transmission to an external module. To gain an overview of the respective performance effects of the solutions, performance measurements were conducted on selected cryptographic functions. The results are relevant when matching Trusted Computing mechanisms to AI Use-Cases, later on. 

- **Market share:**  
The prevalence of a specific implementation is important to rate its relevance in the current economy and was hence – if possible – evaluated.   

## Evaluated Solutions - Mobile devices  
### Choice of Devices 
Choosing devices by Apple and Samsung, we are covering two of the largest smartphone manufacturers on the market. Because of the inherent differences in both soft- and hardware between iOS and Android devices, comparing phones with each operating system is essential. 

Android devices currently cover about 70% of the market in smartphones. Because of this, different Pixel devices by Google were evaluated, since they use an optimized and unedited Android implementation, which does not contain any “bloatware” - meaning third-party apps by the Original Equipment Manufacturer (OEM). 

In each case current high-end devices were picked, because these are sure to contain all of the important functionalities and features provided by the OEM at that time. 

### Note on the Performance Measurements  
8 MB Blocks of random data were used as input for the symmetric crypto algorithms.  

 [The API of the iOS Secure Enclave solely supports the usage of asymmetric cryptography](https://developer.apple.com/documentation/security/seckeyalgorithm/2091899-eciesencryptionstandardx963sha25). Hence, the performance measurements of the AES algorithm were conducted via ECIES decryption with a secp256r1 key (for AES-128-GCM) and a secp521r1 key (for AES-256-GCM) respectively. It must be noted that the performance of AES-GCM via ECIES under iOS is not comparable to the AES-GCM under Android, since key stored in hardware is only used for initial key-derivation when using the ECIES method.  

### Evaluations 
<details><summary><strong>Google Pixel (Android with Tensor SoC and Titan M-/M2-Chip)</strong></summary><p> 

- **Accessibility and Usability:**  
Google provides the freely available Android Security Library, which is high in quality. In addition, developers can rely on the IDE Android Studio, various SDKs, thorough documentation and example-code. Furthermore, a large community of developers exists.  

- **Supported Features:**
The *Android Security Library* provides various mechanisms and algorithms, including many algorithms covering encryption (symmetric and asymmetric), signatures, message digest, key generation and attestation. In addition, the Android KeyStore System API supports functionality to securely store cryptographic keys. On some devices with StrongBox compatible TRH, this hardware can be used with the KeyStore API. The number of keys that can be stored by the keystore is unlimited. 

    Within the Trusted Execution Engine (Tensor Security Core) only the algorithms preloaded by Google can be executed. We assume that the evaluated devices use Androids own TEE implementation *Trusty TEE*. The TEE is used to secure the KeyStore in hardware, if StrongBox cannot be used.  

- **Performance:**<br>
*Table 4: Performance – Pixel 5, Android 12*
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
*Table 5: Performance – Pixel 6 Pro, Android 12* 
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

- **Market share:** 
Google Pixel devices hold a relatively low share of the smartphone market. In 2021 they held about [1,2% of the German market and about 3,8% in the US](https://de.statista.com/infografik/25476/umfrage-zur-nutzung-von-google-smartphones/). 

</p></details>&nbsp;

<details><summary><strong>Samsung Knox (Android)</strong></summary><p>

- **Accessibility and Usability:** 
In addition to the *Andorid Security Library* (see section for Google Pixel), Samsung provides its own freely available security library *Samsung Knox SDK*. The SDK is less thoroughly documented, and the usage is less prevalent than the Android pendant, because they are Samsung exclusive and solely used to access Samsungs own TRH *Samsung Knox Vault*.

- **Supported Features:** 
Next to the Android libraries, Samsung supports the following security functions:    
  - *Weaver* (Android password authentication),  
  - *Credential Storage* (stores keys, biometric data and more) and  
  - *Samsung Attestation Key* (supports firmware and other devices).  
  - The keystore *Knox Vault Storage* can store an arbitrary number of keys. 
  - The Knox Vault Processor solely executes algorithms preloaded by Samsung. We assume that the evaluated devices are equipped with Samsung's own TEE implementation *TEEGRIS*, which was introduced with the Samsung Galaxy S10. *TEEGRIS* can be used to secure the KeyStore in hardware, if StrongBox cannot be used.  

- **Performance:**<br>
*Table 6: Performance – Samsung Galaxy A50, Android 11*
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
*Table 7: Performance – Samsung Galaxy S20FE, Android 11* 
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

- **Market share:** 
In 2021 Samsung came in [second in market dominance](https://www.statista.com/statistics/271496/global-market-share-held-by-smartphone-vendors-since-4th-quarter-2009/), holding [about 20%](https://www.statista.com/statistics/276477/global-market-share-held-by-samsung-smartphones/) of smartphone market shares.

</p></details>&nbsp;

<details><summary><strong>Apple iPhone (Secure Enclave)</strong></summary><p>

- **Accessibility and Usability:** 
Apple provides the free and high-quality Apple CryptoKit library for security features. Additionally, developers can use XCode and a large amount of documentation and code examples. The community of iOS developers is large, due to the prevalence of Apple mobile devices.  

- **Supported Features:** 
*CryptoKit* offers the *SecKey* API (for asymmetric keys), the Common Crypto Library (for symmetric encryption, hash-based MACs, message digest and attestation) and *CryptoTokenKit* (for Smart-Card support). Many ECC-256bit keys can be stored in an exclusive, secure storage unit. Different key formats are not supported. Within the Trusted Execution Engine (Secure Enclave), only the algorithms provided can be executed. Deployment of third-party code is not possible.  

- **Performance:** <br>
*Table 9: Performance – iPhone X* 
{{<table "table table-striped">}}
|Algorithmus / Provider |without Secure Enclave |with Secure Enclave |
|--|--|--|
|AES-128-GCM Decrypt<sup id="fnref:2"><a href="#fn:2" class="footnote-ref" role="doc-noteref">2</a></sup> (ECIES via secp256r1-Schlüssel)|763,26 MB/s |472,95 MB/s |
|AES-256-GCM Decrypt (ECIES via secp521r1-Schlüssel) |495,82 MB/s |n. V. |
|secp256r1 ECDH key exchange |3.892,00 ops/s |135,97 ops/s |secp256r1 keygen |132,88 keys/s |79,77 keys/s |
|secp256r1 ECDSA sign |3.769,10 ops/s |95,36 ops/s |
|secp256r1 ECDSA verify |5.272,65 ops/s |1.492,70 ops/s |
{{</table>}}
*Table 10: Performance – iPhone 12 Pro* 
{{<table "table table-striped">}}
|Algorithmus / Provider |without Secure Enclave |with Secure Enclave |
|--|--|--|
|AES-128-GCM Decrypt (ECIES via secp256r1-Schlüssel) |1.849,27 MB/s |755,34 MB/s |
|AES-256-GCM Decrypt (ECIES via secp521r1-Schlüssel) |1473,18 MB/s |n. V. |
|secp256r1 ECDH key exchange |3.417,93 ops/s |148,43 ops/s |
|secp256r1 keygen |192,37 keys/s |100,93 keys/s| 
|secp256r1 ECDSA sign |3832,87 ops/s |124,64 ops/s|
|secp256r1 ECDSA verify |6416,70 ops/s |2181,78 ops/s| 
{{</table>}}
*Table 11: Performance – iPhone 13 Pro*
{{<table "table table-striped">}}
|Algorithmus / Provider |without Secure Enclave |with Secure Enclave |
|--|--|--|
|AES-128-GCM Decrypt (ECIES via secp256r1-Schlüssel) |1.172,12 MB/s |757,24 MB/s |
|AES-256-GCM Decrypt (ECIES via secp521r1-Schlüssel) |883,49 MB/s |n. V. |
|secp256r1 ECDH key exchange |7.820,13 ops/s |212,38 ops/s |
|secp256r1 keygen |283,47 keys/s |135,35 keys/s| 
|secp256r1 ECDSA sign |6.527,13 ops/s |193,38 ops/s|
|secp256r1 ECDSA verify |7.216,83 ops/s |3.392,44 ops/s |
{{</table>}}
- **Market share:**
  In 2021 Apple was the third largest manufacturer of smartphones worldwide and held a market share of 19,2%.  
</p></details>&nbsp;

###  Results - Overview   

*Table 12: Results Mobile Devices - Overview* 
|Implementation |Accessibility and Usability | Supported Features |Performance |Market share |
|--|--|--|--|--|
|Google Pixel | good | high | High negative performance impact when using Android KeyStore TEE-backed, compared to mere software-based security; Very high negative performance impact when using KeyStore with StrongBox (TRH)  |very low |
|Samsung Knox |good - average |high | High negative performance impact when using Android KeyStore TEE-backed, compared to mere software-based security; Very high negative performance impact when using KeyStore with StrongBox (TRH)  | very high |
|Apple iPhone |good |high |High negative performance impact when using the Secure Enclave  |very high |


## Evaluated Solutions – Embedded Systems  
### Choice of Devices 
*OP-TEE* was chosen as a representative for TEEs on embedded systems with ARM Cortex-A CPUs, because it is open-source and hence one of the few implementations that allows the cost-free implementation and integration of third-party TAs, which was necessary for our experiments. In addition, OP-TEE implements the GlobalPlatform (GP) TEE API, so implemented TAs for OP-TEE can thus be easily ported to other GP conforming TEEs. 

As an alternative TEE, targeting ARM-Cortex M Processors with TrustZone-M, we also chose the commercial implementation *Kinibi-M* by Trustonic. 

The NXP SE050 and the Zymkey 4i by Zymbit both represent Secure Elements and can be used with the Raspberry Pi, which makes them easier to evaluate and ideal for prototyping. The two SEs differ in the available crypto-primitives and the developer target-group. Additionally, a TPM 2.0 implementation by Let’sTrust was picked to cover the group of TPMs. The chosen module too is compatible with the RaspberryPi and implements the TCG TPM 2.0 specification.   

### Note on Performance Measurements  
For the crypto algorithms either the maximum supported buffer size or, in case of no obvious cap, 1MB was used as size for the input buffer. In every case, the time was measured on the lowest possible API level: either right before and after the context switch (TEE) or at the start and end of data transmission to the module (TRH).   

### Evaluations 
<details><summary><strong>OP-TEE (STM32MP157A-DK1)</strong></summary><p>

- **Accessibility and Usability:**  
Next to OP-TEEs open-source code TrustedFirmware also provides developers with documentation, describing the usage and the process to setup a working OP-TEE on a platform. The documentation contains a build-guide and a description of the general architecture of the OS. For more detailed information regarding the different API calls, developers have to consult the respective GP TEE API 1.0. The documentation provided by TrustedFirmware is kept reasonably up-to-date and exhaustive. 
In addition, TrustedFirmware provides various – unfortunately entirely uncommented – example implementations of TAs and a build.git containing an assortment of ready-to-use builds for specific platforms. To use OP-TEE on a platform not covered by the build.git, the setup process is significantly more challenging and requires some experience and knowledge with operating-system development and –architecture, since in that case the image needs to be correctly assembled using the correct elements (op-tee, linux kernel, u-boot, platform specific drivers …) creating the needed Makefiles. 
OP-TEE supports many different platforms, however only a few of them are represented in the build.git.   

- **Supported Features:** 
OP-TEE provides functions according to the GP TEE Specification 1.0 and is thus rich in features. Among others, the TEE supports RSA- and AES-encryption and provides secure storage. Currently OP-TEE does not support remote- or key-attestation. As mentioned above, the implementation of TAs is possible, and OP-TEE even enables developers to secure certain peripherals via “pseudo-TAs” using TrustZones features.  
The STM board used for the experiments includes a TRNG and OP-TEE is, as far as we were able to determine, actually using it, when its random-function is called.   

- **Perfomance:** <br>
*Table 13: Performance – OP-TEE (STM32MP157A-DK1)* 
{{<table "table table-striped">}}
|Algorithm |Performance |
|--|--|
|AES128-CTR Enc |4,56 MB/s |
|AES128-CTR Dec |4,56 MB/s |
|RSA2048-RSAES Enc |2,44 kB/s |
|RSA2048-RSAES Dec |0,16 kB/s |
{{</table>}}

- **Market share:**
No information can be provided on market distribution, as no data is available. OP-TEE is, however, well-known in the community.  

</p></details>&nbsp;

<details><summary><strong>NXP EdgeLock SE050 Development Kit</strong></summary><p> 

- **Accessibility and Usability:**  
  The documentation of the NXP Plug&Trust Middleware is available for download after a cost-free registration on the NXP website. The middleware itself and its source code can be obtained in the same way (a minimal version is also available on GitHub).  
The documentation is structured in a sometimes-confusing way and explanations are brief. All in all, it is, however, complete in regards of relevant information and developers with a certain knowledge of cryptography and SEs that know what they are looking for, will be able to use it without problems. 
The module communicates with the host via I2C and allows, in theory (we’ve only experimented with RaspberryPi 3 as host), the usage with all linux-based host devices with the respective interface.   

- **Supported Features:** 
The SE provides a PRNG conforming with NIST SP800-90A. Both AES- and RSA-encryption are supported, as well as different ECC-algorithms. In general, the API is quite extensive and supports many crypto primitives.  
The device offers 50 kB secured user flash memory, in which Secure Objects like cryptographic keys can be stored. The implemented key store supports key-attestation. The NXP SE050 also offers a second I2C interface that can be used to connect the SE to a sensor which would allow attested sensor data reads from the host via the TRH.   

- **Perfomance:** <br>
  *Table 14: Performance – NXP EdgeLock SE050 Development Kit*
{{<table "table table-striped">}}
|Algorithm|Performance |
|--|--|
|AES128-CBC Enc |2,7 kB/s |
|AES128-CBC Dec |2,7 kB/s |
|HMAC-SHA256 |2,8 kB/s |
|ECDSA-SHA256 Sign |0,5 kB/s |
{{</table>}}

- **Market share:**
No information can be provided on market distribution, as no data is available. The NXP EdgeLock is part of the [Google SE Alliance](https://security.googleblog.com/2021/03/announcing-android-ready-se-alliance.html), which could potentially heighten its prevalence and relevance in the future.   

</p></details>&nbsp;

<details><summary><strong>Zymkey 4i</strong></summary><p> 

- **Accessibility and Usability:**
  The Zymbit API documentation is available on the [Zymbit website](https://docs.zymbit.com/api/) in html and as PDF<sup id="fnref:3"><a href="#fn:3" class="footnote-ref" role="doc-noteref">3</a></sup>. There are three distinct documentations for the C-API, the C++-API and the Python-API. The respective documents are partly inconsistent, especially regarding the descriptions of the equivalent functions in the three different APIs. One would not gain the same information about the device’s abilities and the functionalities of the methods by reading the Python-API than by reading the C-API. Even within the same language-API, different information can be gathered by reading the html version than by reading the PDF. Additionally, each documentation contains function descriptions about all methods supported by the sum of all Zymbit-devices and there is no way to filter them, in order to display only the ones relevant for e.g., the Zymkey 4i. So, for every function one must check the descriptive text, whether it is mentioned that this function is exclusive to a specific device or not. 
However, the reduced feature set, which will be covered in the next section, the available example code and the support of Python, the required pre-existing knowledge is relatively low and even developers that are not familiar with the C programming language, can use the API. 
Usage of the Zymkey 4i is theoretically possible with all devices with a I2C interface, the libraries however, are – at the time of the experiments – solely available as Debian packages and not open-source, so porting them could be difficult.   

- **Supported Features:** 
The Zymkey 4i offers a *lock*-Method, which first encrypts the input data with AES-128 and then signs it with the pre-installed ECDSA-key. 
It is **not** possible to store your own keys in the Zymkey 4i or generate new ones. A key store could only be implemented by encrypting them with the lock-function and storing them in the host memory. We assume that the Zymkey 4i uses the TRNG of the integrated ATECC608 chip, when the respective random-function is called, it was however not possible to verify this given or time and resources. 
Apart from the mentioned lock- and random-methods, the Zymkey supports only one more crypto-function which is ECDSA-SHA256 signatures, where only the signing is conducted on the Zymkey while the SHA digest appears to be calculated on the host device. Although the integrated ATECC608 supports more cryptographic algorithms than that, those are not used and supported by the Zymkey 4i. One would have to use the Zymbit HSM6 which is based on the same chip, in order to use these functions. 
Remote attestation is mentioned as a feature in the Zymkey’s [Product Brief](https://www.zymbit.com/wp-content/uploads/2021/08/Zymbit_ProductBrief_Zymkey4i_04100100_04150911_B1.pdf) , however no information regarding how to use it could be found in the API documentation or the Zymbit forum. 

- **Perfomance:** <br>
*Table 15: Performance – Zymkey 4i* 
{{<table "table table-striped">}}
|Algorithm|Performance |
|--|--|
|“Lock” (AES-128 Enc & ECDSA Sign) |2,61 kB/s| 
|“Unlock” (AES-128 Dec & ECDSA Verify) |2,61 kB/s |
|ECDSA Sign |0,23 kB/s |
{{</table>}}

- **Market share:**
No information can be provided on market distribution, as no data is available.  

</p></details>&nbsp;

<details><summary><strong>Let'sTrust TPM 2.0</strong></summary><p>

- **Accessibility and Usability:**  
  Different implementations of the TPM 2.0 API exist. For our experiments we used [*this*](https://github.com/tpm2-software) stack implementation. To use the API one must refer to the applicable official specification documents provided by the TCG, which is quite complex and extensive. For easier use, a [command line tool](https://github.com/tpm2-software/tpm2-tools) is provided in the above-mentioned GitHub repository. The tool itself is well documented and has examples, while the API implementation itself provides no guidance on how to use it correctly. 
The TPM 2.0 by Let’sTrust connects to the host device via SPI and should be usable with any Linux-based host.  
- **Supported Features:** 
The supported features of the Let’sTrust TPM 2.0 conform with the mandatory features specified by the TCG for the “Mobile Profile”.  The TPM includes a deterministic RNG according to NIST SP800-90A. RSA and different signature algorithms are supported, as well as ECC and ECDH. However, it **does not support AES encryption**, or rather not the respective TPM command *TPM2_EncryptDecrypt*, since it is optional. 
Keys or other critical data can be stored in the 6kB tamper proof flash. At the time of evaluation, there was no way for remote attestation with the Let’sTrust TPM, however there are [there are plans to change that](https://letstrust.de/archives/39-New-Project-EnactTrust.html).  With the *TPM2_Certify* command, the presence of a key on the TPM can be attested, but the command *TPM2_CertifyX509*, which would also attest the attributes of a key/object with a X.509 certificate, is not supported by the module. 
The TPM does not have any other interfaces that would allow to attach further peripherals.
- **Perfomance:** <br>
*Table 16: Performance –Let’sTrust TPM 2.0*
{{<table "table table-striped">}}
|Algorithm|Performance |
|--|--|
|HMAC-SHA256 |4,79 kB/s| 
|RSA2048-RSAES Enc |3,45 kB/s |
|RSA2048-RSAES Dec |0,77 kB/s |
{{</table>}}

- **Market share:**
No information can be provided on market distribution, as no data is available. However, TPM 2.0 implementations are generally widely used.   
</p></details>&nbsp;

<details><summary><strong>Kinibi-M</strong></summary><p>

- **Accessibility and Usability:**  
The Kinibi-M SDK is not open-source and can only be obtained (for free) after registration and request on the Trustonic website. Currently the only supported chip is the Atmel SAML11 (the production SDK is restricted to the SAML11 KPH, that includes the pre-installed unique device key). The SDK includes extensive, well-structured documentation of the API, a step-by-step *Getting Started* guide and several, well-documented code examples that make the SDK accessible.   

- **Supported Features:** 
    The Kinibi-M Crypto API offers, among others, the following relevant functionalities: AES-128 encryption, SHA256 hashing, secure data storage in the *Secure Storage* (1kB on-board data flash) and random number generation. The latter could either be obtaining numbers from the TRNG of the SAML11 or a DRNG implementation. The documentation does not give any information regarding this.  
Key- or remote-attestation, in the sense that those terms are usually used in, is not implemented. Using the features of TrustZone-M, peripherals can be secured and accessed by the TAs. The SDKs intention is to enable developers to create TAs for Kinibi-M, so third party code can be executed.   
- **Perfomance:** 
Since time measurement on SAML11 Xplained Pro would have been incomparably more complex - as well as fundamentally different - than with the Linux-capable other boards, no performance measurements could be carried out on this board in the short time available. 
- **Market share:**
No information can be provided on market distribution, as no data is available. Kinibi-M is currently only available on a single platform and hence the market share is supposedly very low. If more devices based on ARM Cortex-M CPUs with TrustZone-M support emerge, the prevalence of Kinibi-M may increase, due to the former popularity of Kinibi in the mobile sector.  
</p></details>&nbsp;

### Results - Overview  
*Table 12: Results Embedded Devices - Overview* 
|Implementation |Accessibility and Usability  |Supported Features |Performance |Market share  |
|--|--|--|--|--|
|NXP SE050  |average – high |high |low |No info |
|Zymkey 4i  |low - average |low |low |No info |
|Let’sTrust TPM 2.0  |high |high |low |No info |
|OP-TEE  |average – high |high |average – high |No info| 
|Kinibi-M |low |low |No info |No info | 

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
        Since the encryption via ECIES is the only algorithm requiring access to the asymmetric key in the secure enclave, only this specific algorithm was timed. 
				<a href="#fnref:2" class="footnote-backref" role="doc-backlink">&#8617;</a>
			</p>
		</li>
    <li id="fn:3" role="doc-endnote">
			<p>
				https://s3.amazonaws.com/zk-sw-repo/zk_app_utils.py.pdf or https://s3.amazonaws.com/zk-sw-repo/zk_app_utils.c.pdf respectively.
				<a href="#fnref:3" class="footnote-backref" role="doc-backlink">&#8617;</a>
			</p>
		</li>
	</ol>
</div>
