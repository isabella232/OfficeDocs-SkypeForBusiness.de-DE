---
title: Archivierungsrichtlinie
ms.reviewer: ''
ms.author: v-cichur
author: cichur
manager: serdars
ms.date: 3/27/2015
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.lscp.MonArchPolicyMain
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.assetid: 9b69f1fa-8f3b-450e-aa89-91fd462f198d
description: 'Sie verwenden Archivierungsrichtlinien, um die Archivierung für Benutzer zu aktivieren und zu deaktivieren, die auf Skype for Business Server verwaltet werden. In einer Archivierungsrichtlinie können Sie die Archivierung jeweils für eine oder beide der folgenden Kommunikationsarten aktivieren oder deaktivieren:'
ms.openlocfilehash: dd0bd831aeb408862ee16b9f09e2c5247f205e82
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58591579"
---
# <a name="archiving-policy"></a>Archivierungsrichtlinie
 
Sie verwenden Archivierungsrichtlinien, um die Archivierung für Benutzer zu aktivieren und zu deaktivieren, die auf Skype for Business Server verwaltet werden. In einer Archivierungsrichtlinie können Sie die Archivierung jeweils für eine oder beide der folgenden Kommunikationsarten aktivieren oder deaktivieren:
  
- Interne Kommunikation
    
- Externe Kommunikation (mit mindestens einem Benutzer außerhalb des internen Netzwerks)
    
Zu den Archivierungsrichtlinien gehören die globale Richtlinie und optional eine oder mehrere Archivierungsrichtlinien für Standorte und Benutzer:
  
- **Globale Richtlinie** Die globale Richtlinie wird in allen Bereitstellungen standardmäßig erstellt. Sie können die globale Richtlinie bearbeiten, aber Sie können diese Richtlinie nicht löschen. Wenn Sie versuchen, das Löschen durchzuführen, werden alle Optionen auf die Standardwerte zurückgesetzt.
    
- **Standortrichtlinie (optional)** Sie können eine oder mehrere Archivierungsrichtlinien für Standorte angeben, die Sie jeweils so konfigurieren können, dass die Archivierung der internen oder externen Kommunikation für einen einzelnen Standort aktiviert und deaktiviert wird. Eine Standortrichtlinie setzt die globale Richtlinie außer Kraft, jedoch nur für die in den Archivierungsstandortrichtlinien angegebenen Standorte. Sie können Standortrichtlinien bearbeiten oder löschen.
    
- **Benutzerrichtlinie (optional)** Sie können eine oder mehrere Archivierungsrichtlinien für Benutzer angeben, die Sie jeweils so konfigurieren können, dass die Archivierung der internen oder externen Kommunikation für einen bestimmten Benutzer oder eine bestimmte Benutzergruppe aktiviert und deaktiviert wird. Eine Benutzerrichtlinie setzt die globale Richtlinie und die Standortrichtlinien außer Kraft, jedoch nur für die Benutzer und Benutzergruppen, denen Sie Archivierungsrichtlinien auf Benutzerebene zuweisen. Sie können Benutzerrichtlinien bearbeiten oder löschen.
    
> [!NOTE]
> Archivierungsrichtlinien gelten nur für Benutzer, die auf Skype for Business Server verwaltet werden. Wenn Sie Exchange Integration zum Speichern von Archivierungsdaten in Microsoft Exchange verwenden, steuern Exchange 2013-Richtlinien die Archivierung für Benutzer, die am Exchange 2013 verwaltet werden. Um die Archivierung für diese Benutzer zu aktivieren, muss das Postfach des Benutzers in In-Place Haltebereich gesetzt werden. 
  
Auf der Seite **Archivierungsrichtlinie** sind die einzelnen Archivierungsrichtlinien aufgeführt, die für die Bereitstellung konfiguriert sind. Außerdem werden der Richtlinienname und -bereich (global, Standort oder Benutzer) sowie die für eine Archivierungsrichtlinie aktivierten Archivierungsoptionen angezeigt. Auf der Seite **Archivierungsrichtlinie** haben Sie die folgenden Möglichkeiten:
- **Neu** Sie können eine oder mehrere der folgenden optionalen Archivierungsrichtlinien hinzufügen:
    
  - Standortrichtlinie
    
  - Benutzerrichtlinie
    
- **Bearbeiten** Sie können die Optionen aller auf der Seite aufgeführten Archivierungsrichtlinien ändern. Mit dieser Option haben Sie folgende Möglichkeiten:
    
  - **Details anzeigen**   Mit dieser Option öffnen Sie ein Dialogfeld, in dem Sie die Archivierungsoptionen für eine Archivierungsrichtlinie ändern können.
    
  - **Alles auswählen** Mit dieser Option werden alle Archivierungsrichtlinien der Liste ausgewählt.
    
  - **Löschen**   Mit dieser Option werden alle ausgewählten Archivierungsrichtlinien gelöscht.
    
- **Aktion** Sie können diese Option verwenden, um die Archivierung der internen oder externen Kommunikation in allen auf der Seite aufgeführten Richtlinien schnell zu aktivieren oder zu deaktivieren, anstatt die Richtlinie zu bearbeiten. Die unter **Aktion** verfügbaren Optionen richten sich danach, welche Option in der Archivierungsrichtlinie momentan angegeben ist. Alle Optionen sind verfügbar, mit Ausnahme der Option, die für die Archivierungsrichtlinie derzeit wirksam ist. Folgende Optionen sind vorhanden:
    
  - **Archivierung interner Kommunikation aktivieren**
    
  - **Archivierung interner Kommunikation deaktivieren**
    
  - **Archivierung externer Kommunikation aktivieren**
    
  - **Archivierung externer Kommunikation deaktivieren**
    
- **Aktualisieren** Sie können die Seite **"Archivierungsrichtlinie"** aktualisieren, um den Status der Optionen aller Archivierungsrichtlinien zu überprüfen.
    
Ausführliche Informationen zu den Archivierungsfeatures und -funktionen, einschließlich Exchange Integration, finden Sie unter [Plan for archiving in Skype for Business Server 2015,](../../plan-your-deployment/archiving/archiving.md)Deploy archiving for Skype for Business Server [2015](../../deploy/deploy-archiving/deploy-archiving.md)und [Manage archiving in Skype for Business Server 2015.](../../manage/archiving/archiving.md)

