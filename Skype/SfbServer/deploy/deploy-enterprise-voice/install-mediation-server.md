---
title: Installieren der Dateien für den Vermittlungsserver in Skype for Business Server
ms.reviewer: ''
ms.author: v-cichur
author: cichur
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom: ''
ms.assetid: f0f7dd15-58e1-40fd-aa7e-6db50ceafacd
description: 'Zusammenfassung: Erfahren Sie, wie Sie die Dateien für den Vermittlungsserver in Skype for Business Server installieren.'
ms.openlocfilehash: 5662e4e79534fd469c64005bba98d1c507defff8
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58620501"
---
# <a name="install-the-files-for-mediation-server-in-skype-for-business-server"></a>Installieren der Dateien für den Vermittlungsserver in Skype for Business Server
 
**Zusammenfassung:** Erfahren Sie, wie Sie die Dateien für den Vermittlungsserver in Skype for Business Server installieren.
  
Um dieses Verfahren erfolgreich abzuschließen, sollten Sie mindestens als lokaler Administrator und Domänenbenutzer, der mindestens Mitglied der Gruppe "RTCUniversalReadOnlyAdmins" ist, beim Server angemeldet sein.
  
Führen Sie die Schritte in diesem Thema aus, um Skype for Business Server Bereitstellungs-Assistenten auszuführen, um die Dateien für den Vermittlungsserver auf einem Computer zu installieren, den Sie einem Vermittlungsserverpool hinzugefügt haben, nachdem Sie den Topologie-Generator zum Definieren und Veröffentlichen des Pools verwendet haben. Bei der Installation von Dateien mit Vermittlungsserver installieren und weisen Sie auch das Zertifikat zu, das von jedem Computer in einem Vermittlungsserverpool benötigt wird. 
  
> [!NOTE]
> In diesem Thema wird davon ausgegangen, dass Sie bereits einen eigenständigen Vermittlungsserverpool in Ihrer Topologie definiert und veröffentlicht haben, wie unter [Bereitstellen eines Vermittlungsservers im Topologie-Generator in Skype for Business Server](deploy-a-mediation-server.md)beschrieben. 
  
### <a name="to-install-the-files-for-a-stand-alone-mediation-server-pool"></a>So installieren Sie die Dateien für einen eigenständigen Vermittlungsserverpool

1. Klicken Sie auf dem Installationsmedium mit der rechten Maustaste auf _\<installation media\>_ **\Setup\amd64\Setup.exe,** und klicken Sie dann **auf "Als Administrator ausführen".**
    
2. Klicken Sie auf der Seite **"Installationsspeicherort"** auf **"OK".**
    
3. Klicken Sie auf der Seite **"Endbenutzer-Lizenzvertrag"** auf **"Ich stimme zu"** und dann auf **"OK".** (Erforderlich, um fortzufahren.)
    
4. Klicken Sie auf der Seite **Skype for Business Server Bereitstellungs-Assistenten** auf **Installieren oder Aktualisieren Skype for Business Server Systems.**
    
5. Next to **Step 1: Install Local Configuration Store**, click **Run**, and then follow the instructions on the screen.
    
6. Übernehmen Sie auf der Seite **"Lokales Replikat der zentralen Verwaltung konfigurieren Store"** die Standardeinstellung **"Direkt aus der zentralen Verwaltung abrufen" Store,** und klicken Sie dann auf **"Weiter".**
    
7. Klicken Sie auf der Seite **"Befehle ausführen",** wenn der Aufgabenstatus als **abgeschlossen** angezeigt wird, auf **"Fertig stellen".**
    
8. Next to **Step 2: Setup or Remove Skype for Business Server Components**, click **Run**, and then click **Next**.
    
9. Klicken Sie auf der Seite **"Befehle ausführen",** wenn der Aufgabenstatus als **abgeschlossen** angezeigt wird, auf **"Fertig stellen".**
    
10. Klicken Sie neben **Schritt 3: Anfordern, Installieren oder Zuweisen von Zertifikaten** auf **"Ausführen".** Folgen Sie den Anweisungen auf dem Bildschirm, und akzeptieren Sie die Standardeinstellungen. Der Vermittlungsserver erfordert ein Zertifikat, sodass Sie **Schritt 3** zweimal ausführen: einmal, um das erforderliche Zertifikat auszustellen, und einmal mehr, um es zuzuweisen.
    
11. Wenn das Zertifikat ordnungsgemäß ausgestellt und zugewiesen wurde, klicken Sie neben **Schritt 4: Dienste starten** auf **Ausführen,** und folgen Sie dann den Anweisungen auf dem Bildschirm.
    
12. Wenn **Schritt 4** erfolgreich abgeschlossen wurde, starten Sie den Server neu, und melden Sie sich beim Server als Mitglied der Gruppe "DomainAdmins" an.
    
13. Überprüfen Sie auf dem Computer, auf dem Sie Skype for Business Server Systemsteuerung ausführen, auf der **Topologieseite** Skype for Business Server Systemsteuerung, ob der Dienststatus des Vermittlungsservers als grünes Häkchen angezeigt wird. Wenn stattdessen ein rotes X angezeigt wird, wählen Sie den Vermittlungsserver aus. Klicken Sie im Menü **"Aktion"** auf **"Alle Dienste starten".** 
    
Wenn Sie dem Vermittlungsserverpool mehrere Computer hinzugefügt haben, führen Sie die Schritte in diesem Verfahren auf allen anderen Computern im Vermittlungsserverpool aus. Wenn Sie keine Dateien für den Vermittlungsserver für andere Computer installieren müssen, befolgen Sie die Verfahren unter [Konfigurieren von Trunks in Skype for Business Server,](configure-trunks.md) um Einstellungen für die Trunkverbindung zwischen diesem Vermittlungsserverpool (oder allen Vermittlungsservern an einem Standort) und dem Peer zu konfigurieren.

