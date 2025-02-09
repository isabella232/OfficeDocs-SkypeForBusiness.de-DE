---
title: tblADUpdates
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
ms.assetid: ba19fa16-4d2d-4635-ac32-f93e09469546
description: tblADUpdates enthält Active Directory Domain Services-Änderungen, die noch nicht von den späteren Active Directory-Synchronisierungsschritten verarbeitet wurden.
ms.openlocfilehash: 5d98ccd69b5a4213484c5dbbf4baf88f35106867
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58586803"
---
# <a name="tbladupdates"></a>tblADUpdates
 
tblADUpdates enthält Active Directory Domain Services-Änderungen, die noch nicht von den späteren Active Directory-Synchronisierungsschritten verarbeitet wurden.
  
**Columns**

|**Spalte**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|prinGuid  <br/> |GUID, nicht NULL  <br/> |Prinzipal-GUID des geänderten Objekts.  <br/> |
|prinADPath  <br/> |nvarchar (384), nicht NULL  <br/> |Distinguished Name (DN) des Objekts.  <br/> |
|prinAttributesChanged  <br/> |bit, nicht NULL  <br/> |TRUE, wenn sich mindestens ein Attribut des Objekts geändert hat.  <br/> |
|prinMembersChanged  <br/> |bit, nicht NULL  <br/> |TRUE, wenn sich die Mitgliedschaft geändert hat.  <br/> |
|prinAffiliationsChanged  <br/> |bit, nicht NULL  <br/> |Nicht verwendet.  <br/> |
|prinDeleted  <br/> |bit, nicht NULL  <br/> |TRUE, wenn das Objekt gelöscht wurde.  <br/> |
|lastUpdated  <br/> |datetime, nicht NULL  <br/> |Zeitstempel für den Zeitpunkt, an dem die Zeile eingefügt wurde.  <br/> |
   

