---
title: tblEnumAttribute
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
ms.assetid: 17f8b87e-36a6-4f6a-8630-7c76b61a7595
description: "\"EnumAttribute\" ist eine hardkodierte Tabelle, mit den Attributen \"Visibility\" und \"Behavior\", die in der \"Node\"-Tabelle verwendet werden."
ms.openlocfilehash: 7f55d99a028a7af7979394321bb543db11bb1933
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58628547"
---
# <a name="tblenumattribute"></a>tblEnumAttribute
 
"EnumAttribute" ist eine hardkodierte Tabelle, mit den Attributen "Visibility" und "Behavior", die in der "Node"-Tabelle verwendet werden.
  
**Columns**

|**Spalte**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|Attributeid  <br/> |smallint, nicht NULL  <br/> |ID des Attributs.  <br/> |
|Attributename  <br/> |nvarchar (256), nicht NULL  <br/> |Name des Attributs.  <br/> |
   
**Schlüssel**

|**Spalte**|**Beschreibung**|
|:-----|:-----|
|Attributeid  <br/> |Primärschlüssel  <br/> |
   
**Tabellenwerte**

|**Attributeid**|**Attributename**|
|:-----|:-----|
|1   <br/> |Sichtbarkeit.  <br/> |
|2   <br/> |Verhalten.  <br/> |
   
## <a name="see-also"></a>Siehe auch

[tblNode](tblnode.md)
