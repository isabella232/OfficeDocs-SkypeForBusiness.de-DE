---
title: SessionCorrelation-Tabelle
ms.reviewer: ''
ms.author: v-cichur
author: cichur
manager: serdars
ms.date: 2/1/2018
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 041705e1-7290-464f-95f8-96256cfa2e3e
description: Die SessionCorrelation-Tabelle ist eine Unterstützende Tabelle. Jeder Datensatz stellt eine CorrelationID dar, die verwendet wird, um mehrere Sitzungen zu korrelieren.
ms.openlocfilehash: a0ec0a2e1435aab02ba1733530271b2ad648869e
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58634119"
---
# <a name="sessioncorrelation-table"></a>SessionCorrelation-Tabelle
 
Die SessionCorrelation-Tabelle ist eine Unterstützende Tabelle. Jeder Datensatz stellt eine CorrelationID dar, die verwendet wird, um mehrere Sitzungen zu korrelieren. 
  
|**Spalte**|**Datentyp**|**Schlüssel/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**Prüfsumme** <br/> |int  <br/> |||
|**CorrelationKey** <br/> |int  <br/> |Primary  <br/> |Eindeutige Nummer, die diesen A/V-Konferenzserver identifiziert.  <br/> |
|**Correlationid** <br/> |nvarchar(256)  <br/> |Eigen  <br/> |Sitzungen, die korreliert sind, haben dieselbe Korrelations-ID.  <br/> |
|**NextUpdateTS** <br/> |Datum/Uhrzeit  <br/> | <br/> |Ausschließlich für interne Zwecke.  <br/> |
   

