---
title: Überprüfen der Replikation in der Domäne
ms.reviewer: ''
ms.author: v-cichur
author: cichur
manager: serdars
ms.date: 3/26/2015
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.dep.DeployMainVerifyDomainPrep
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.assetid: 4846b787-d55e-4364-bdcd-2dee33f0251c
description: 'Um die Replikation der in Schritt 1: Vorbereiten des Schemas durchgeführten Domänenvorbereitung zu überprüfen, müssen Sie ein Cmdlet aus der Skype for Business Server Verwaltungsshell lync Server-Verwaltungsshell ausführen. Um das Cmdlet Windows PowerShell auszuführen, melden Sie sich bei einem Computer an, der Mitglied der von Ihnen vorbereiteten Domäne ist, und als Mitglied der Gruppe "Domänenadministratoren". Gehen Sie wie folgt vor:'
ms.openlocfilehash: 1715ef902b4c0812b98ff6e37c8ea31eab5489ec
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58596919"
---
# <a name="verify-replication-in-the-domain"></a>Überprüfen der Replikation in der Domäne
 
Um die Replikation der in **Schritt 1: Vorbereiten** des Schemas durchgeführten Domänenvorbereitung zu überprüfen, müssen Sie ein Cmdlet aus der Skype for Business Server Verwaltungsshell Lync Server-Verwaltungsshell ausführen. Um das Cmdlet Windows PowerShell auszuführen, melden Sie sich bei einem Computer an, der Mitglied der von Ihnen vorbereiteten Domäne ist, und als Mitglied der Gruppe "Domänenadministratoren". Gehen Sie wie folgt vor:
  
1. Starten Sie die Skype for Business Server Verwaltungsshell: Klicken Sie auf **"Start",** auf **"Alle Programme",** auf **Skype for Business 2015** und dann auf **Skype for Business Server Verwaltungsshell.**
    
2. Geben Sie in Windows PowerShell Folgendes ein:
    
   ```PowerShell
   Get-CsAdDomain [-Domain <Fqdn>] [-DomainController <Fqdn>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>]
   ```

    Beispiel:
    
   ```PowerShell
   Get-CsAdDomain -Domain domain1.contoso.net -GlobalSettingsDomainController dc01.domain1.contoso.com
   ```

    > [!NOTE]
    > Über den Parameter "GlobalSettingsDomainController" können Sie den Speicherort der globalen Einstellungen angeben. Wenn Ihre Einstellungen im Systemcontainer gespeichert sind (was bei Upgradebereitstellungen typisch ist, bei denen die globale Einstellung nicht zum Konfigurationscontainer migriert wurde), definieren Sie einen Domänencontroller im Stammverzeichnis der Active Directory Domain Services-Gesamtstruktur. Wenn sich die globalen Einstellungen im Konfigurationscontainer befinden (dies ist bei neuen Bereitstellungen oder Upgradebereitstellungen typisch, bei denen die Einstellungen zum Konfigurationscontainer migriert wurden), definieren Sie einen beliebigen Domänencontroller in der Gesamtstruktur. Wenn Sie diesen Parameter nicht angeben, geht das Cmdlet davon aus, dass die Einstellungen im Konfigurationscontainer gespeichert sind und bezieht sich auf einen beliebigen Domänencontroller in Active Directory. 
  
    Wenn Sie den Parameter "Domain" nicht angeben, wird die lokale Domäne verwendet. Bei erfolgreicher Domänenvorbereitung gibt dieses Cmdlet den Wert **LC_DOMAIN_SETTINGS_STATE_READY** zurück.
    

