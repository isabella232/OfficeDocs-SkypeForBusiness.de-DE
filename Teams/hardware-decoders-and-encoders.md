---
title: Empfehlungen für Hardware Decoder und Encoder-Treiber
ms.reviewer: ''
author: SerdarSoysal
ms.author: serdars
manager: serdars
ms.date: 06/06/2019
audience: Admin
ms.topic: reference
ms.service: msteams
ms.collection:
- M365-voice
ms.localizationpriority: medium
search.appverid: MET150
description: Listet die Kombinationen von Betriebssystem, Modell und Treibern auf, die aufgrund von Treiberproblemen nicht für die Hardwarebeschleunigung aktiviert sind.
f1.keywords:
- CSH
ms.custom:
- NewAdminCenter_Update
appliesto:
- Microsoft Teams
ms.openlocfilehash: 8d483f914c486c9912f608f16de5ab421d0fa47e
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58632119"
---
# <a name="hardware-decoder-and-encoder-driver-recommendations"></a>Empfehlungen für Hardware Decoder und Encoder-Treiber

Microsoft unterstützt alle Decoder und Encoder mit Ausnahme der in diesem Artikel aufgeführten.

## <a name="hardware-decoder-driver-recommendations---intel"></a>Empfehlungen für Hardwaredecoder-Treiber – Intel

Die folgenden Kombinationen aus Betriebssystem, Modell und Treiber sind aufgrund verschiedener Treiberprobleme nicht für die Hardwarebeschleunigung aktiviert.

|Betriebssystem           | Modell (Device_id) | Treiber/Bereich |
|---------------------------|-------------------|--------------|
|Windows 07.Windows 8.Windows 8.1.Windows 10 | 0x0116 | [2,0,11,929] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | 0x0126 | [0.0.0.0] - [8.15.10.2418] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | alle | [0.0.0.0] - [8.15.10.2753] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | 0x2772 | [8.15.10.1749] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | 0x0162, 0x0166 | [0.0.0.0] - [9.17.10.2850] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | alle | [9.17.10.2867] - [9.17.10.4459] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 |0x1616 | [9.18.7.9] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | alle | [10.18.10.3431] - [10.18.10.4425] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | alle | [10.18.14.4280] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | 0x1616 |[10.18.15.4256] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | 0x1916 |[10.18.15.4293] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | alle |[10.18.15.4281] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | alle |[20.19.15.4390] - [20.19.15.4444] |
|Windows 10 | alle | [21.20.16.4541] |
|Windows 10 | alle | [22.20.16.4811] |
|Windows 10 | alle | [24.20.100.6293] |

## <a name="hardware-decoder-driver-recommendations---nvidia"></a>Empfehlungen für Den Hardwaredecoder-Treiber – Nvidia

Die folgenden Kombinationen aus Betriebssystem, Modell und Treiber sind aufgrund verschiedener Treiberprobleme nicht für die Hardwarebeschleunigung aktiviert.

|Betriebssystem           | Modell (Device_id) | Treiber/Bereich |
|---------------------------|-------------------|--------------|
|Windows 07.Windows 8.Windows 8.1.Windows 10 | 0x0540 | [8.15.1.1243] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | 0x0A20 | [8.15.11.8627], [8.15.11.8634], [8.15.11.8642] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | 0x0A34 | [8.15.11.8631], [8.15.11.8636], [8.15.11.8652], [8.15.11.8662], [8.15.11.8664], [8.16.11.8691] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | 0x0A74 | [8.15.11.8636], [8.15.11.8652], [8.15.11.8688] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | 0x0A28 | [8.15.11.8644] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | 0x0A69 | [8.16.11.8691] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | 0x0A3C | [0.0.0.0] - [8.17.12.6721] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | 0x0873 | [8.17.12.8562] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | 0x040C, 0x0429, 0x06FD | [0.0.0.0] - [8.17.12.9670] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | alle | [8.17.11.9745], [8.17.12.5738] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | 0x0A2B | [0.0.0.0] - [9.18.13.282] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | 0x087D | [9.18.13.697] |
|Windows 07.Windows 8.Windows 8.1.Windows 10 | 0x1040 |[0.0.0.0] - [9.18.13.1106] |
|Windows 10 | alle | [10.18.13.5891] - [10.18.13.6881] |
|Windows 10 | alle | [21.21.13.6909], [21.21.13.7570] |
|Windows 7 | alle | [21,21,13,4201] |

## <a name="hardware-decoder-driver-recommendations---amd"></a>Empfehlungen für Hardwaredecoder-Treiber – AMD

Bei älteren Betriebssystemen sind nur die folgenden Device_ids hardwarebeschleunigung aktiviert.

|Betriebssystem           | Modell (Device_id) |
|---------------------------|-------------------|
|Windows 7/<br>Windows 8/<br>Windows 8,1 | 0x9874, 0x9851, 0x9853, 0x9854, 0x9855, 0x9856, 0x9857, 0x9858, 0x9857, 0x9858, 0x9859, 0x985A, 0x985B, 0x985C, 0x985D, 0x985E, 0x985F, 0x98E4, 0x67DF, 0x67C0, 0x67C2, 0x67C4, 0x67C7, 0x67D0, 0x67EF, 0x67FF, 0x67E0, 0x67E1, 0x67E8, 0x67E9, 0x67EB, 0x67DF, 0x67EF, 0x67FF, 0x6981, 0x6987, 0x6900, 0x694C, 0x694E, 0x694F, 0x6860, 0x6861, 0x6862, 0x6863, 0x6864, 0x6867, 0x6868, 0x6869, 0x686A, 0x686B, 0x686C, 0x686D, 0x686E, 0x687F, 0x69A0, 0x69A1,  0x69A2, 0x69A3, 0x69AF, 0x66A0, 0x66A1, 0x66A2, 0x66AF |

Die folgenden Kombinationen aus Betriebssystem, Modell und Treiber sind aufgrund verschiedener Treiberprobleme nicht für die Hardwarebeschleunigung aktiviert.

|Betriebssystem           | Modell (Device_id) | Treiber/Bereich |
|---------------------------|-------------------|--------------|
|Windows 07.07.Windows 8/Windows 8.1/Windows 10 | alle | [0.0.0.0] – [25.20.15017.1009] |

## <a name="hardware-encoder-driver-recommendations---intel"></a>Empfehlungen für Treiber für Hardware encoder – Intel

Die folgenden Kombinationen aus Betriebssystem, Modell und Treiber sind aufgrund verschiedener Treiberprobleme nicht für die Hardwarebeschleunigung aktiviert.

|Betriebssystem           | Modell (Device_id) | Treiber/Bereich |
|---------------------------|-------------------|--------------|
|Windows 7 | alle | [8.15.10.2200] - [8.15.10.2600] |
|Windows 07.07.Windows 8/Windows 8.1/Windows 10 | alle | [8.15.10.2653] - [8.15.10.2827] |
|Windows 07.07.Windows 8/Windows 8.1/Windows 10 | alle | [9.14.3.1176] - [9.14.3.1177] |
|Windows 07.07.Windows 8/Windows 8.1/Windows 10 | alle | [9.17.10.2800] - [9.17.10.9999] |
|Windows 07.07.Windows 8/Windows 8.1/Windows 10 | alle | [9.18.10.3222] |
|Windows 7 | alle | [9.18.10.3234] |
|Windows 7 | alle | [9.18.10.3272] |
|Windows 7 | alle | [10.18.10.3242] - [10.18.10.9999] |
|Windows 8/Windows 8.1/Windows 10 | alle | [10.18.10.0000] - [10.18.10.9999] |
|Windows 07.07.Windows 8/Windows 8.1/Windows 10 | alle | [10.18.14.4153] - [10.18.14.4161] |
|Windows 07.07.Windows 8/Windows 8.1/Windows 10 | alle | [10.18.14.4264] |
|Windows 7 | alle | [10.18.14.4578] |
|Windows 7 | alle | [10.18.14.4889] |
|Windows 7 | alle | [10.18.14.5057] |
|Windows 07.07.Windows 8/Windows 8.1/Windows 10 | alle | [20.19.15.4300] - [20.19.15.4444] |
|Windows 7 | alle | [20.19.15.4474] |

## <a name="hardware-encoder-driver-recommendations---nvidia"></a>Empfehlungen für Den Hardware encoder-Treiber – Nvidia

Die folgenden Kombinationen aus Betriebssystem, Modell und Treiber sind aufgrund verschiedener Treiberprobleme nicht für die Hardwarebeschleunigung aktiviert.

|Betriebssystem           | Modell (Device_id) | Treiber/Bereich |
|---------------------------|-------------------|--------------|
|Windows 07.07.Windows 8/Windows 8.1/Windows 10 | alle | [0.0.0.0] - [21.21.13.7848] |

## <a name="hardware-encoder-driver-recommendations---amd"></a>Empfehlungen für Den Hardware encoder-Treiber – AMD

Bei älteren Betriebssystemen sind nur die folgenden Device_ids hardwarebeschleunigung aktiviert.

|Betriebssystem           | Modell (Device_id) |
|---------------------------|-------------------|
|Windows 7 | 0x9874, 0x9850, 0x9851, 0x9852, 0x9853, 0x9854, 0x9855, 0x9856, 0x9857, 0x9858, 0x9859, 0x985A, 0x985B, 0x985C, 0x985D, 0x985E, 0x985F, 0x98E4, 0x67C0, 0x67C1, 0x67C2, 0x67C3, 0x67C4, 0x67C5, 0x67C6, 0x67C7, 0x67C8, 0x67C9, 0x67CA, 0x67CB, 0x67CC, 0x67CD, 0x67CE, 0x67CF, 0x67D0, 0x67D1, 0x67D2, 0x67D3, 0x67D4, 0x67D5, 0x67D6, 0x67D7, 0x67D8, 0x67D9, 0x67D9, 0x6 7DA, 0x67DB, 0x67DC, 0x67DD, 0x67DE, 0x67DF, 0x67E0, 0x67E1, 0x67E2, 0x67E3, 0x67E4, 0x67E5,  0x67E6, 0x67E7, 0x67E8, 0x67E9, 0x67EA, 0x67EB, 0x67EC, 0x67ED, 0x67EE, 0x67EF, 0x67F0, 0x67F1, 0x67F2, 0x67F3, 0x67F4, 0x67F5, 0x67F6, 0x67F7, 0x67F8, 0x67F9, 0x67FA, 0x67FB, 0x67FC, 0x67FD, 0x67FE, 0x67FF, 0x1304, 0x1305, 0x1306, 0x1306, 0x1307, 0x1308, 0x1309, 0x130A, 0x130B, 0x130C, 0x130D, 0x130E, 0x130F, 0x1310, 0x1311, 0x1312, 0x1313, 0x1314, 0x1315, 0x1316, 0x1317, 0x1318, 0x1319, 0x131A, 0x131B, 0x131C, 0x131D, 0x131E, 0x131F, 0x66A0, 0x66A1,  0x66A2, 0x66A3, 0x66A4, 0x66A7, 0x66AF, 0x6860, 0x6861, 0x6862, 0x6863, 0x6864, 0x6867, 0x6868, 0x6869, 0x686A, 0x686B, 0x686D, 0x686E, 0x687F, 0x69A0, 0x69A1, 0x69A2, 0x69A3, 0x69AF

Die folgenden Kombinationen aus Betriebssystem, Modell und Treiber sind aufgrund verschiedener Treiberprobleme nicht für die Hardwarebeschleunigung aktiviert.

|Betriebssystem           | Modell (Device_id) | Treiber/Bereich |
|---------------------------|-------------------|--------------|
|Windows 07.07.Windows 8/Windows 8.1/Windows 10 | 0x674a | [0.0.0.0] – [99.9999.9999.9999] |
|Windows 7 | alle | [0.0.0.0] - [16.199.9999.9999] |
|Windows 07.07.Windows 8/Windows 8.1/Windows 10 | alle | [15.21.0.0] - [16.199.9999.9999] |
|Windows 07.07.Windows 8/Windows 8.1/Windows 10 | alle | [15.201.1101.0] |
|Windows 07.07.Windows 8/Windows 8.1/Windows 10 | alle | [21.19.137.1] |

## <a name="related-topics"></a>Verwandte Themen

[Hardwareanforderungen für die Teams-App](hardware-requirements-for-the-teams-app.md).
