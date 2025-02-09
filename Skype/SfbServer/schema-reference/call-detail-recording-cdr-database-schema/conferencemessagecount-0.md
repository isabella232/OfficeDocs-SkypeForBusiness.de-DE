---
title: ConferenceMessageCount-Ansicht
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
ms.assetid: 8ee3ee95-fb78-4d4e-bcdd-6ce5a0a23b44
description: In der ConferenceMessageCount-Ansicht werden Informationen darüber gespeichert, wie viele Nachrichten von einem Benutzer an eine Konferenz gesendet wurden. Diese Ansicht wurde in Microsoft Lync Server 2013 eingeführt.
ms.openlocfilehash: 5b4cadd741eae999a789a51c6adc0400cc8ce45f
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58593429"
---
# <a name="conferencemessagecount-view"></a>ConferenceMessageCount-Ansicht
 
In der ConferenceMessageCount-Ansicht werden Informationen darüber gespeichert, wie viele Nachrichten von einem Benutzer an eine Konferenz gesendet wurden. Diese Ansicht wurde in Microsoft Lync Server 2013 eingeführt.
  
> [!NOTE]
> Die ConferenceMessageCount-Ansicht enthält alle Spalten in der [ConferenceSessionDetails-Ansicht](conferencesessiondetails.md) zusätzlich zu den unten aufgeführten Spalten.
  
|**Spalte**|**Datentyp**|**Details**|
|:-----|:-----|:-----|
|**UserUri** <br/> |nvarchar(450)  <br/> |URI des Benutzers, der die Nachricht gesendet hat.  <br/> |
|**UserUriType** <br/> |nvarchar(256)  <br/> |URI-Typ des Benutzers, der die Nachrichten gesendet hat. Weitere Informationen finden Sie in der [UriTypes-Tabelle.](uritypes.md) <br/> |
|**UserTenant** <br/> |Uniqueidentifier  <br/> |Mandant des Benutzers, der die Nachrichten gesendet hat. Weitere Informationen finden Sie in der [Tabelle "Mandanten".](tenants.md) <br/> |
|**UserMessageCount** <br/> |Smallint  <br/> |Anzahl der Nachrichten, die der Benutzer während der Konferenzsitzung gesendet hat.  <br/> |
   

