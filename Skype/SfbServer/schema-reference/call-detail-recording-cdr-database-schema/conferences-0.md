---
title: Konferenzansicht
ms.reviewer: ''
ms.author: v-cichur
author: cichur
manager: serdars
ms.date: 3/9/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: c0e5c4db-c135-401f-9296-e9a49f6499a1
description: Die Konferenzansicht enthält Informationen zu den Konferenzen. Diese Ansicht wurde in Microsoft Lync Server 2013 eingeführt.
ms.openlocfilehash: c61a0d9d2d7e1985aa63256be16d9268138ddd83
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58620901"
---
# <a name="conferences-view"></a>Konferenzansicht
 
Die Konferenzansicht enthält Informationen zu den Konferenzen. Diese Ansicht wurde in Microsoft Lync Server 2013 eingeführt.
  
|**Spalte**|**Datentyp**|**Details**|
|:-----|:-----|:-----|
|**SessionIdTime** <br/> |Datum/Uhrzeit  <br/> |Zeitpunkt der Sitzungsanforderung. Wird zusammen mit SessionIdSeq verwendet, um eine Sitzung eindeutig zu identifizieren.. Weitere Informationen finden Sie in der [Dialogs-Tabelle in Skype for Business Server 2015.](dialogs.md) <br/> |
|**SessionIdSeq** <br/> |int  <br/> |ID zur Identifikation der Sitzung. Wird zusammen mit SessionIdTime verwendet, um eine Konferenzinstanz eindeutig zu identifizieren. Weitere Informationen finden Sie in der [Dialogs-Tabelle in Skype for Business Server 2015.](dialogs.md) <br/> |
|**ConferenceUri** <br/> |nvarchar(450)  <br/> |Der URI für die Konferenz.  <br/> |
|**ConferenceUriType** <br/> |nvarchar(256)  <br/> |Der Typ des Konferenz-URI. Weitere Informationen finden Sie in der [UriTypes-Tabelle.](uritypes.md) <br/> |
|**ConfInstance** <br/> |Uniqueidentifier  <br/> |Wird für wiederkehrende Konferenzen verwendet. Jede Instanz einer wiederkehrenden Konferenz hat die gleiche ConferenceUri, aber eine andere ConfInstance.  <br/> |
|**ConferenceStartTime** <br/> |Datum/Uhrzeit  <br/> |Die Startzeit für die Konferenz.  <br/> |
|**ConferenceEndTime** <br/> |Datum/Uhrzeit  <br/> |Die Endzeit für die Konferenz.  <br/> |
|**OrganizerUri** <br/> |nvarchar(450)  <br/> |Der URI des Benutzers, der die Sitzung organisiert hat.  <br/> |
|**OrganizerType** <br/> |nvarchar(256)  <br/> |Der URI-Typ des Benutzers, der die Konferenz organisiert hat. Weitere Informationen finden Sie in der [UriTypes-Tabelle.](uritypes.md) <br/> |
|**OrganizerTenant** <br/> |nvarchar(256)  <br/> |Der Mandant des Benutzers, der die Konferenz organisiert hat. Weitere Informationen finden Sie in der [Tabelle "Mandanten".](tenants.md) <br/> |
|**Pool** <br/> |nvarchar(256)  <br/> |Der vollqualifizierte Domänenname des Pools, von dem die Konferenz gehostet wurde.  <br/> |
|**Wert** <br/> |Smallint  <br/> |Eine Bitmaske, die Konferenzattribute enthält. Mögliche Werte sind:  <br/> 0X01 – Synthetische Transaktion  <br/> |
   

