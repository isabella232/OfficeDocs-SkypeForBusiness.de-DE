---
title: Verwalten von Konfigurationseinstellungen für Konferenzserver in Skype for Business Server
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
ms.assetid: 36bed690-6e22-4e11-88c1-b40a20836c6a
description: 'Zusammenfassung: Erfahren Sie, wie Sie die Konfigurationseinstellungen für Konferenzserver in Skype for Business Server verwalten.'
ms.openlocfilehash: 7ba225920fd511d70efe1e063cb77dbd77d9721f
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58623727"
---
# <a name="manage-conferencing-server-configuration-settings-in-skype-for-business-server"></a>Verwalten von Konfigurationseinstellungen für Konferenzserver in Skype for Business Server
 
**Zusammenfassung:** Erfahren Sie, wie Sie die Konfigurationseinstellungen für Konferenzserver in Skype for Business Server verwalten.
  
In diesem Thema wird das Verwalten von Konferenzkonfigurationseinstellungen beschrieben. Weitere Informationen zum Planen und Bereitstellen von Konferenzen finden Sie unter [Plan for conferencing in Skype for Business Server](../../plan-your-deployment/conferencing/conferencing.md) and Deploy [conferencing in Skype for Business Server.](../../deploy/deploy-conferencing/deploy-conferencing.md)
  
Die Konferenzkonfigurationseinstellungen bestimmen z. B. die maximal zulässige Größe für Besprechungsinhalte und Handzettel; maximale Bandbreite für den Konferenzdienst für anwendungsfreigabe; Speicherlimits und Ablaufzeiten; die URLs für die internen und externen Downloads des unterstützten Clients; Zeiger auf interne und externe URLs, in denen Benutzer Hilfe und Ressourcen für Konferenzen erhalten können; und die Ports für Anwendungsfreigabe, Clientaudio, Dateiübertragungen und Mediendatenverkehr. Mit diesen Einstellungen können Sie die eigentlichen Server selbst verwalten. Diese Einstellungen können mithilfe Skype for Business Server Verwaltungsshell festgelegt werden.
  
Wenn Sie Skype for Business Server installieren, stellt das System eine einzige Sammlung von Konferenzkonfigurationseinstellungen (die globale Auflistung) bereit. Wenn Sie benutzerdefinierte Einstellungen für einen Standort oder Dienst erstellen müssen, können Sie dies mit dem Cmdlet **New-CsConferencingConfiguration** tun. Beachten Sie, dass neue Einstellungen nur auf Standort- oder Dienstebene angewendet werden können. Sie können keine neue globale Auflistung von Konferenzkonfigurationseinstellungen erstellen, aber Sie können die globale Auflistung mithilfe des Cmdlets **"Set-CsConferencingConfiguration"** ändern. Darüber hinaus kann kein Standort oder Dienst mehr als eine Auflistung von Einstellungen hosten. Wenn Sie versuchen, neue Einstellungen für den Standort Redmond zu erstellen, und der Standort Redmond bereits eine Sammlung von Konferenzkonfigurationseinstellungen hostet, schlägt der Befehl fehl.
  
## <a name="manage-conferencing-configuration-settings-by-using-skype-for-business-server-management-shell"></a>Verwalten von Konferenzkonfigurationseinstellungen mithilfe Skype for Business Server Verwaltungsshell

Verwenden Sie die folgenden Cmdlets, um Konferenzkonfigurationseinstellungen mithilfe Skype for Business Server Verwaltungsshell zu verwalten:
  
**Konfigurationseinstellungen für Konferenzen**

|**Cmdlet**|**Beschreibung**|
|:-----|:-----|
|[Get-CsConferencingConfiguration](/powershell/module/skype/get-csconferencingconfiguration?view=skype-ps) <br/> |Gibt Informationen zu den Konferenzkonfigurationseinstellungen für Ihre Organisation zurück.  <br/> |
|[New-CsConferencingConfiguration](/powershell/module/skype/new-csconferencingconfiguration?view=skype-ps) <br/> |Erstellt eine neue Auflistung von Konferenzkonfigurationseinstellungen.  <br/> |
|[Remove-CsConferencingConfiguration](/powershell/module/skype/remove-csconferencingconfiguration?view=skype-ps) <br/> |Entfernt die angegebene Auflistung von Konferenzkonfigurationseinstellungen.  <br/> |
|[Set-CsConferencingConfiguration](/powershell/module/skype/set-csconferencingconfiguration?view=skype-ps) <br/> |Ändert eine vorhandene Auflistung von Konfigurationseinstellungen für Konferenzen.  <br/> |
   
Mit dem folgenden Befehl wird eine neue Auflistung von Konferenzkonfigurationseinstellungen für den Standort Redmond (site:Redmond) erstellt. In diesem Beispiel ist ein zusätzlicher Parameter (Organization) enthalten, der verwendet wird, um den Wert der Organization-Eigenschaft auf Litwareinc festzulegen: 
  
```PowerShell
New-CsConferencingConfiguration -Identity site:Redmond -Organization Litwareinc
```

Beachten Sie, dass Sie nur eine solche Sammlung pro Standort haben können. Dieser Befehl würde daher fehlschlagen, wenn der Standort Redmond bereits über eine Sammlung von Konferenzkonfigurationseinstellungen verfügt. 
  
Im nächsten Beispiel wird eine neue Auflistung von Konferenzkonfigurationseinstellungen definiert, die zunächst im Arbeitsspeicher gespeichert und dann zu einem späteren Zeitpunkt auf den Standort Redmond angewendet werden. 
  
Der erste Befehl verwendet das Cmdlet **"New-CsConferencingConfiguration",** um eine neue Speicherauflistung von Einstellungen zu erstellen, die in der Variablen $x gespeichert sind. Der InMemory-Parameter gibt an, dass die Auflistung im Arbeitsspeicher erstellt werden soll, anstatt sie sofort auf den Standort Redmond anzuwenden.
  
Nachdem die Auflistung erstellt wurde, wird mit dem zweiten Befehl der Wert für die Eigenschaft "Organization" auf "Litwareinc" festgelegt. 
  
Schließlich verwendet der dritte Befehl das Cmdlet **"Set-CsConferencingConfiguration",** um die neuen Einstellungen tatsächlich auf den Standort Redmond anzuwenden:
  
```PowerShell
$x = New-CsConferencingConfiguration -Identity site:Redmond -InMemory
$x.Organization = "Litwareinc"
Set-CsConferencingConfiguration -Instance $x
```

Wenn Sie das Cmdlet **"Set-CsConferencingConfiguration"** nicht aufrufen, werden die neuen Einstellungen nie wirksam. Stattdessen werden sie ausgeblendet, sobald Sie Ihre Windows PowerShell Sitzung beenden oder die Variable $x löschen.
