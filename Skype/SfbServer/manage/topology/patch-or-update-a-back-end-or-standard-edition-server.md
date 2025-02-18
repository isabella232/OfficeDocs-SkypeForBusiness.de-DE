---
title: Patchen oder Aktualisieren eines Back-End-Servers oder Standard Edition Servers in Skype for Business Server
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
ms.assetid: f95f8d3a-e039-484e-97bd-d727db21a12b
description: 'Zusammenfassung: Erfahren Sie, wie Sie ein Update oder einen Patch auf einem Back-End-Server in Skype for Business Server installieren.'
ms.openlocfilehash: 2b7292b71f57d7396c5b90bce3746b73b98f6f43
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58619751"
---
# <a name="patch-or-update-a-back-end-server-or-standard-edition-server-in-skype-for-business-server"></a>Patchen oder Aktualisieren eines Back-End-Servers oder Standard Edition Servers in Skype for Business Server
 
**Zusammenfassung:** Erfahren Sie, wie Sie ein Update oder patchen auf einem Back-End-Server in Skype for Business Server installieren.
  
In diesem Thema wird erläutert, wie Sie ein Update auf einem Enterprise Edition Back-End-Server oder einem Standard Edition-Server installieren.
  
Wenn ein Back-End-Server während des Upgrades mindestens 30 Minuten ausgefallen ist, können Benutzer in den Ausfallsicherheitsmodus wechseln. Wenn das Upgrade abgeschlossen ist und die Back-End-Server erneut mit den Front-End-Servern im Pool verbunden sind, erhalten die Benutzer die volle Funktionalität. Wenn das Upgrade weniger als 30 Minuten dauert, sind die Benutzer nicht betroffen.
  
### <a name="to-update-a-back-end-server-or-standard-edition-server"></a>So aktualisieren Sie einen Back-End-Server oder Standard Edition Server

1. Melden Sie sich am Server, für den Sie das Upgrade vornehmen, als Mitglied der Rolle "CsAdministrator" an.
    
2. Laden Sie das Update herunter, und extrahieren Sie es auf die lokale Festplatte.
    
3. Starten Sie die Skype for Business Server Verwaltungsshell: Klicken Sie auf **"Start",** auf **"Alle Programme",** auf **Skype for Business** und dann auf **Skype for Business Server Verwaltungsshell.**
    
4. Beenden Sie Skype for Business Server Dienste. Geben Sie in die Befehlszeile Folgendes ein:
    
    ```PowerShell
    Stop-CsWindowsService
    ```

5. Beenden Sie den WWW-Dienst (World Wide Web). Geben Sie an der Befehlszeile Folgendes ein:
    
    ```PowerShell
    net stop w3svc
   ```

6. Schließen Sie alle Fenster Skype for Business Server Verwaltungsshell.
    
7. Installieren Sie das Update.
    
8. Starten Sie die Skype for Business Server Verwaltungsshell: Klicken Sie auf **"Start",** auf **"Alle Programme",** auf **Skype for Business** und dann auf **Skype for Business Server Verwaltungsshell.**
    
9. Beenden Sie Skype for Business Server Dienste erneut, um GAC-D-Assemblys (Global Assembly Cache) abzufangen. Geben Sie an der Eingabeaufforderung Folgendes ein:
    
    ```PowerShell
    Stop-CsWindowsService
    ```

10. Starten Sie den WWW-Dienst neu. Geben Sie an der Befehlszeile Folgendes ein:
    
    ```PowerShell
    net start w3svc
    ```

11. Wenden Sie die Änderungen an den SQL Server Datenbanken an, indem Sie eine der folgenden Aktionen ausführen:
    
    - Wenn es sich um einen Enterprise Edition Back-End-Server handelt und keine verbundenen Datenbanken auf diesem Server vorhanden sind, z. B. Archivierungs- oder Überwachungsdatenbanken, geben Sie Folgendes in einer Befehlszeile ein:
    
    ```PowerShell
    Install-CsDatabase -Update -ConfiguredDatabases -SqlServerFqdn <SQL Server FQDN>
    ```

    - Wenn es sich um einen Enterprise Edition Back-End-Server handelt und auf diesem Server verbundenen Datenbanken vorhanden sind, geben Sie An einer Befehlszeile Folgendes ein:
    
    ```PowerShell
    Install-CsDatabase -Update -ConfiguredDatabases -SqlServerFqdn <SQL Server FQDN>  -ExcludeCollocatedStores
    ```

    - Wenn es sich um einen Standard Edition Server handelt, geben Sie Folgendes an einer Befehlszeile ein:
    
    ```PowerShell
    Install-CsDatabase -Update -LocalDatabases

    ```
