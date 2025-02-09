---
title: Ausführen einer Abfrage
ms.reviewer: ''
ms.author: v-cichur
author: cichur
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: IT_Skype16
ms.assetid: 45a77f7e-b137-462b-9146-3a0f43d8e0c7
description: 'Zusammenfassung: Erfahren Sie mehr über den Vorgang "Abfrage ausführen", der Teil der Daten-API für das Anrufqualitätsdashboard ist. Das Anrufqualitäts-Dashboard ist ein Tool für Skype for Business Server.'
ms.openlocfilehash: 814b602631b3699b2b802adaee931e4ab0a780a6
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58626627"
---
# <a name="run-query"></a>Ausführen einer Abfrage

**Zusammenfassung:** Erfahren Sie mehr über den Vorgang "Abfrage ausführen", der Teil der Daten-API für das Anrufqualitätsdashboard ist. Das Anrufqualitäts-Dashboard ist ein Tool für Skype for Business Server.

Der Vorgang "Abfrage ausführen" ist Teil der Daten-API für das Anrufqualitäts-Dashboard.

## <a name="run-query"></a>Ausführen einer Abfrage

Der Vorgang "Abfrage ausführen" bietet die Möglichkeit, eine Abfrage für den Cube basierend auf angegebenen Dimensionen, Maßangaben und Filtern auszuführen und die Daten zurückzugeben.


|**Methode**|**Anforderungs-URI**|**HTTP-Version**|
|:-----|:-----|:-----|
|POST  <br/> |https:// \<portal\> /QoEDataService/RunQuery  <br/> |HTTP/1.1  <br/> |

 **URI-Parameter** : Keine.

 **Anforderungsheader** – keine zusätzlichen Kopfzeilen.

 **Anforderungstext** – Hier ist eine Beispielanforderungsnutzlast in JSON. Es enthält Dimensionen, Filter und Maßangaben, die für eine Abfrage erforderlich sind.

```json
{
"Filters": [{
"DataModelName": "[StartDate].[Month]",
"Caption": "July 2013",
"Value": "[2015-03-01T00:00:00]",
"Operand": 0,
"UnionGroup": ""
}],
"Dimensions": [{
"DataModelName": "[StartDate].[Month]"
}],
"Measurements": [{
"DataModelName": "[Measures].[Audio Good Streams Count]"
},
{
"DataModelName": "[Measures].[Audio UnClassified Streams Count]"
},
{
"DataModelName": "[Measures].[Audio Poor Streams Count]"
},
{
"DataModelName": "[Measures].[AudioPoorPercentage]"
}],
"Trend": {
"EnableTrend": true,
"SpanCount": 7,
"TrendDate": "2015-3",
"Type": 0
}
}
```

 *Filter*  – Eine Liste der anzuwendenden Filterausdrücke, sodass der resultierende Datensatz nur die Teilmenge der daten wiedergibt, die von Interesse sind.

 *Dimensionen*  – Eine Liste der Dimensionen, die zum Aggregieren der Daten verwendet werden. Mindestens eine Dimension ist erforderlich, es können jedoch mehrere Dimensionen angegeben werden, um zusätzliche Unteraggregationenebenen zu erhalten.

 *Maßangaben*  – eine Liste von Messungen, auch als Fakten bezeichnet, bei denen es sich um die gewünschten Metriken handelt, die basierend auf den angegebenen Dimensionen aggregiert werden sollen.

 *Trend*  – Zusätzliche Steuerungsanweisungen zum Anpassen der Ergebnisdaten.

 **Antwort** : Die Antwort enthält einen HTTP-Statuscode und eine Reihe von Antwortheadern.

 **Statuscode** : Ein erfolgreicher Vorgang gibt den Statuscode 200 (OK) zurück.

 **Antwortheader** – keine zusätzlichen Kopfzeilen.

 **Antworttext** : Unten sehen Sie eine Beispielantwortnutzlast in JSON. Sie enthält eine Datentabelle, die die Daten enthält, außerdem enthält sie metadaten, die die Ausführungszeit der Abfrage anzeigen und angeben, ob die Daten aus dem Cache stammen oder nicht.

```json
{
"ExecutionTime": "00:00:00.2102630",
"DataResult": [["September 2014",
        1792,
        34,
        78,
        4.171],
        ["October 2014",
        37017,
        1731,
        3305,
        8.197],
        ["November 2014",
        79184,
        3033,
        5556,
        6.557],
        ["December 2014",
        122253,
        4050,
        5444,
        4.263],
        ["January 2015",
        31246,
        1069,
        1342,
        4.118]],
"ResultIsFromCache": false,
"ErrorType": 0
}
```

 *Ausführungszeit*  – Die Gesamtzeit, die der Server für die Rückgabe der Daten benötigte. Dies kann den Cache beinhalten oder nicht.

 *Datenergebnis*  – Das Ergebnis der Abfrage. Es handelt sich um ein zweidimensionales Array, das alle Permutationen der Elemente der Dimensionen und jedes Element mit den Elementnamen der Dimensionen sowie die aggregierten Werte der angegebenen Maßeinheiten enthält.

 *Ergebnis aus Cache*  – für Diagnose. Gibt an, ob das Ergebnis aus dem Cache oder aus dem QoE-Cube stammt.
