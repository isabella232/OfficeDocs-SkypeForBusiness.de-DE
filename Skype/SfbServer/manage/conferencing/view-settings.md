---
title: Anzeigen von Besprechungskonfigurationseinstellungen in Skype for Business Server
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
ms.assetid: 932c7e2d-6de3-4176-ac6e-ec230f8230f2
description: 'Zusammenfassung: Erfahren Sie, wie Sie Besprechungskonfigurationseinstellungen in Skype for Business Server anzeigen.'
ms.openlocfilehash: 79a05b35d5bdac952d009445b92c9f1b30883027
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58578819"
---
# <a name="view-meeting-configuration-settings-in-skype-for-business-server"></a>Anzeigen von Besprechungskonfigurationseinstellungen in Skype for Business Server
 
**Zusammenfassung:** Erfahren Sie, wie Sie Besprechungskonfigurationseinstellungen in Skype for Business Server anzeigen.
  
Sie können Besprechungskonfigurationseinstellungen mithilfe Skype for Business Server Systemsteuerung oder mithilfe Skype for Business Server Verwaltungsshell anzeigen.
  
## <a name="view-meeting-configuration-settings-by-using-skype-for-business-server-control-panel"></a>Anzeigen von Besprechungskonfigurationseinstellungen mithilfe Skype for Business Server Systemsteuerung
<a name="BKMK_ViewJoinSettings"> </a>

1. Melden Sie sich mit einem Benutzerkonto, dem die Rolle CsUserAdministrator oder CsAdministrator zugewiesen ist, an einem beliebigen Computer in Ihrer internen Bereitstellung an.
    
2.  Öffnen Sie Skype for Business Server Systemsteuerung.
    
3. Klicken Sie in der linken Navigationsleiste auf **"Konferenzen",** und klicken Sie dann auf **"Besprechungskonfiguration".**
    
4. Klicken Sie auf der Seite **"Besprechungskonfiguration"** auf die Besprechungskonfiguration, die Sie anzeigen möchten.
    
5. Aktivieren Sie im **Filter "Datei bearbeiten"** das Kontrollkästchen **"Details anzeigen".**
    
    **Besprechungskonfiguration \<policy\> bearbeiten –** öffnet die Anzeige der Einstellungen für die ausgewählte Richtlinie.
    
    Ausführliche Informationen zum Konfigurieren der Einstellungen finden Sie unter [Erstellen von Besprechungskonfigurationseinstellungen in Skype for Business Server.](create-settings.md)
    
## <a name="view-meeting-configuration-settings-by-using-skype-for-business-server-management-shell"></a>Anzeigen von Besprechungskonfigurationseinstellungen mithilfe Skype for Business Server Verwaltungsshell
<a name="BKMK_ViewJoinSettings"> </a>

Verwenden Sie das Cmdlet **"Get-CsMeetingConfiguration",** um Informationen zu allen Besprechungskonfigurationseinstellungen anzuzeigen:
  
```
Get-CsMeetingConfiguration
```

Dieser Befehl gibt Informationen wie die folgenden zurück:
  
<pre>
Identity                        : Global
PstnCallersBypassLobby          : True
EnableAssignedConferenceType    : True
DesignateAsPresenter            : Company
AssignedConferenceTypeByDefault : True
AdmitAnonymousUsersByDefault    : True
RequireRoomSystemsAuthorization : False
LogoURL                         :
LegalURL                        :
HelpURL                         :
CustomFooterText                :
AllowConferenceRecording        : True
</pre>

Weitere Informationen, einschließlich einer vollständigen Liste von Parametern, finden Sie unter ["Get-CsMeetingConfiguration".](/powershell/module/skype/get-csmeetingconfiguration?view=skype-ps)
