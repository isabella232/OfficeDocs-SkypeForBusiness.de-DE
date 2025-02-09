---
title: tblPrincipalAffiliations
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
ms.assetid: 45fd8484-5837-44d2-85bb-45c83546607c
description: tblPrincipalAffiliations enthält die Prinzipalmitgliedschaften, die Mitgliedschaften an Standorten beschreiben, einschließlich Active Directory Domain Services-Sicherheitsgruppen, in Active Directory-Containern in Domänen.
ms.openlocfilehash: 6126fb32b6b56c9a3ec142ad1b1186763f28d045
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58580379"
---
# <a name="tblprincipalaffiliations"></a>tblPrincipalAffiliations
 
tblPrincipalAffiliations enthält die Prinzipalmitgliedschaften, die Mitgliedschaften an Standorten beschreiben, einschließlich Active Directory Domain Services-Sicherheitsgruppen, in Active Directory-Containern in Domänen.
  
**Columns**

|**Spalte**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|principalID  <br/> |int, nicht NULL  <br/> |ID des zugeordneten Prinzipals.  <br/> |
|affiliationID  <br/> |int, nicht NULL  <br/> |ID des Prinzipals, die für die Zuordnung steht. Jeder Prinzipal (ausgenommen system-user-types) verfügt auch über eine Selbstzuordnung.  <br/> |
|Index  <br/> |int, nicht NULL  <br/> |Index. Der Wert für Selbstmitgliedschaften ist -1, und für die anderen Mitgliedschaften erhöht er sich sequenziell von 1 innerhalb jedes \<principalID, affiliationId\> Buckets.  <br/> |
|updatedBy  <br/> |int, nicht NULL  <br/> |Prinzipal, der die letzte Aktualisierung durchführte. Der Wert ist in der Regel 1, was der Active Directory-Synchronisierung entspricht.  <br/> |
   
**Keys**

|**Columns**|**Beschreibung**|
|:-----|:-----|
|\<principalID, index, affiliationID\>  <br/> |Primärschlüssel  <br/> |
|principalID  <br/> |Fremdschlüssel mit Abfrage der tblPrincipal.prinID-Tabelle  <br/> |
|affiliationID  <br/> |Fremdschlüssel mit Abfrage der tblPrincipal.prinID-Tabelle  <br/> |
   

