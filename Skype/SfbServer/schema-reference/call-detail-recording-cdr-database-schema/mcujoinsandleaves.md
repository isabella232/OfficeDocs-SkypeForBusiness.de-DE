---
title: McuJoinsAndLeaves-Tabelle in Skype for Business Server 2015
ms.reviewer: ''
ms.author: v-cichur
author: cichur
manager: serdars
ms.date: 7/15/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 4e073366-0b5d-45b4-a3f6-d63dd5fd9f25
description: Jeder Datensatz in dieser Tabelle enthält Anrufdetails zu einer Kombination aus einem Benutzerbeitritt oder -verlassen und einem Konferenzserver. Wenn ein Benutzer beispielsweise einer Konferenz beitritt, die Webkonferenzen und Audio-/Videoelemente enthält, wird ein Datensatz für den Webkonferenzbeitritt dieses Benutzers und ein weiterer Datensatz für die Audio-/Videokonferenzteilnahme des Benutzers erstellt.
ms.openlocfilehash: 5d01781dd0d16abb3f03cdc8f6021981e7ebfff7
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58629467"
---
# <a name="mcujoinsandleaves-table-in-skype-for-business-server-2015"></a>McuJoinsAndLeaves-Tabelle in Skype for Business Server 2015
 
Jeder Datensatz in dieser Tabelle enthält Anrufdetails zu einer Kombination aus einem Benutzerbeitritt oder -verlassen und einem Konferenzserver. Wenn ein Benutzer beispielsweise einer Konferenz beitritt, die Webkonferenzen und Audio-/Videoelemente enthält, wird ein Datensatz für den Webkonferenzbeitritt dieses Benutzers und ein weiterer Datensatz für die Audio-/Videokonferenzteilnahme des Benutzers erstellt.
  
|**Spalte**|**Datentyp**|**Schlüssel/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SessionIdTime** <br/> |Datum/Uhrzeit  <br/> |Primär, Fremd  <br/> |Zeitpunkt der Konferenzinstanz. Wird in Verbindung mit **SessionIdSeq** verwendet, um eine Konferenzinstanz eindeutig zu identifizieren. Weitere Informationen finden Sie in der [Tabelle "Konferenzen" in Skype for Business Server 2015.](conferences.md) <br/> |
|**SessionIdSeq** <br/> |int  <br/> |Primär, Fremd  <br/> |ID zur Identifikation der Konferenzinstanz. Wird in Verbindung mit **SessionIdTime** verwendet, um eine Konferenzinstanz eindeutig zu identifizieren. Weitere Informationen finden Sie in der [Tabelle "Konferenzen" in Skype for Business Server 2015.](conferences.md) <br/> |
|**UserId** <br/> |int  <br/> |Primär, Fremd  <br/> |Eindeutige Zahl, die diesen Benutzer identifiziert. Weitere Informationen finden Sie in der [Tabelle "Benutzer".](users.md) <br/> |
|**McuUserInstance** <br/> |int  <br/> |Primary  <br/> |Wenn ein Benutzer auf mehreren Computern oder Geräten gleichzeitig angemeldet ist, identifiziert McuUserInstance die Kombination aus Benutzer und Gerät eindeutig.  <br/> |
|**IsFromPstn** <br/> |Bit  <br/> | <br/> |Gibt an, ob der Benutzer aus einem PSTN beitritt oder nicht.  <br/> |
|**McuId** <br/> |int  <br/> |Primär, Fremd  <br/> |Eindeutige Nummer, die diesen Konferenzserver identifiziert. Weitere Informationen finden Sie in der [Mcus-Tabelle in Skype for Business Server 2015.](mcus.md) <br/> |
|**DialogSessionIdTime** <br/> |Datum/Uhrzeit  <br/> |Ausländisch  <br/> |Zeitpunkt der Sitzungsanforderung. Wird zusammen mit **SessionIdSeq** verwendet, um eine Sitzung eindeutig zu identifizieren. Weitere Informationen finden Sie in der [Dialogs-Tabelle in Skype for Business Server 2015.](dialogs.md) <br/> |
|**DialogSessionIdSeq** <br/> |int  <br/> |Ausländisch  <br/> |ID zur Identifikation der Sitzung. Wird zusammen mit **SessionIdTime** verwendet, um eine Sitzung eindeutig zu identifizieren. Weitere Informationen finden Sie in der [Dialogs-Tabelle in Skype for Business Server 2015.](dialogs.md) <br/> |
|**UserJoinTime** <br/> |Datum/Uhrzeit  <br/> | <br/> |Der Zeitpunkt, zu dem dieser Benutzer diesem Konferenzserver beitritt.  <br/> |
|**UserLeaveTime** <br/> |Datum/Uhrzeit  <br/> | <br/> |Die Zeit, zu der dieser Benutzer diesen Konferenzserver verlässt.  <br/> |
|**ClientVerId** <br/> |int  <br/> |Ausländisch  <br/> |Bezeichner, der die Versionsnummer der in der Konferenz verwendeten Clientsoftware angibt. Weitere Informationen finden Sie in der [Tabelle "ClientVersions" in Skype for Business Server 2015.](clientversions.md) <br/> Dieses Feld wurde in Microsoft Lync Server 2013 eingeführt.  <br/> |
|**LastModifiedTime** <br/> |Datetime  <br/> ||Für die interne Verwendung durch den Überwachungsdienst.  <br/> Dieses Feld wurde in Skype for Business Server 2015 eingeführt.  <br/> |
   

