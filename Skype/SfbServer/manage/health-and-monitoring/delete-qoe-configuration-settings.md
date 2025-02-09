---
title: Löschen von QoE-Konfigurationseinstellungen in Skype for Business Server
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
ms.assetid: fd0c4c2f-3bfb-42cb-9b6a-f0f8d5aa9e81
description: 'Zusammenfassung: Erfahren Sie, wie Sie QoE-Einstellungen (Quality of Experience) in Skype for Business Server löschen.'
ms.openlocfilehash: e82e844fb217f8c2e71ecb21a6d70e26c4b90ade
ms.sourcegitcommit: efd56988b22189dface73c156f6f8738f273fa61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2021
ms.locfileid: "60014499"
---
# <a name="delete-quality-of-experience-configuration-settings-in-skype-for-business-server"></a>Löschen von QoE-Konfigurationseinstellungen in Skype for Business Server
 
**Zusammenfassung:** Erfahren Sie, wie Sie QoE-Einstellungen (Quality of Experience) in Skype for Business Server löschen.
  
QoE (Quality of Experience)-Metriken dienen der Überwachung der Qualität von Audio- und Videoanrufen in Ihrer Organisation, z. B. der Anzahl der verloren gegangenen Netzwerkpakete, von Hintergrundgeräuschen und der Unterschiede bei Paketverzögerung (Jitter). Diese Metriken werden in einer Datenbank getrennt von anderen Daten (z. B. den Kommunikationsdatensätzen) gespeichert, sodass QoE unabhängig von anderen Datenaufzeichnungen aktiviert und deaktiviert werden kann.
  
Wenn Sie Skype for Business Server installieren, wird eine einzelne, globale Sammlung von QoE-Konfigurationseinstellungen für Sie erstellt. Administratoren können darüber hinaus Auflistungen mit benutzerdefinierten Einstellungen erstellen, die auf die einzelnen Standorte angewendet werden können. Prinzipiell haben Einstellungen auf Standortebene Vorrang vor globalen Einstellungen. Wenn Sie Einstellungen auf Standortebene löschen, wird QoE an diesem Standort mithilfe der globalen Einstellungen verwaltet.
  
Beachten Sie, dass Sie auch die globalen Einstellungen "löschen" können. Diese globalen Einstellungen werden jedoch tatsächlich nicht entfernt. Stattdessen werden alle Eigenschaften in dieser Auflistung auf die Standardwerte zurückgesetzt. Das Löschen ist beispielsweise standardmäßig in einer Auflistung von QoE-Konfigurationseinstellungen aktiviert. Angenommen, Sie ändern die globalen Einstellungen, sodass die Löschung deaktiviert wurde. Wenn Sie später die globalen Einstellungen löschen, werden alle Eigenschaften auf ihre Standardwerte zurückgesetzt. Das bedeutet in diesem Fall, dass die Löschung wieder aktiviert wurde.
  
Sie können QoE-Konfigurationseinstellungen mithilfe der Skype for Business Server Systemsteuerung oder mit dem Cmdlet ["Remove-CsQoEConfiguration"](/powershell/module/skype/remove-csqoeconfiguration?view=skype-ps) entfernen.
  
### <a name="to-delete-qoe-configuration-settings-by-using-skype-for-business-server-control-panel"></a>So löschen Sie QoE-Konfigurationseinstellungen mithilfe Skype for Business Server Systemsteuerung

1.  Melden Sie sich am Computer als Mitglied der Gruppe "RTCUniversalServerAdmins" oder als Mitglied der Rolle "CsVoiceAdministrator", "CsServerAdministrator" oder "CsAdministrator" an. Ausführliche Informationen finden Sie unter **Delegate Setup Permissions**.
    
2. Öffnen Sie ein Browserfenster, und geben Sie dann die Admin-URL ein, um die Skype for Business Server Systemsteuerung zu öffnen.  
    
3. Klicken Sie in der linken Navigationsleiste auf **Überwachung und Archivierung** und dann auf **QoE-Daten**.
    
4. Klicken Sie auf der Seite **"Quality of Experience Data"** auf die gewünschte Richtlinie, klicken Sie auf **"Bearbeiten"** und dann auf **"Löschen".**
    
5. Klicken Sie auf **OK**.
    
## <a name="removing-qoe-configuration-settings-by-using-windows-powershell-cmdlets"></a>Entfernen von QoE-Konfigurations-Einstellungen mithilfe Windows PowerShell Cmdlets

Sie können QoE-Konfigurationseinstellungen mithilfe von Windows PowerShell und dem Cmdlet **"Remove-CsQoEConfiguration"** löschen. Sie können dieses Cmdlet entweder über die Skype for Business Server-Verwaltungsshell oder über eine Remotesitzung von Windows PowerShell ausführen. Ausführliche Informationen zur Verwendung von Remote-Windows PowerShell zum Herstellen einer Verbindung mit Skype for Business Server finden Sie unter [Microsoft Lync Remote PowerShell Administration.](https://blog.insideo365.com/2011/08/remote-lync-powershell-administration/) Der Vorgang ist in Skype for Business Server identisch.
  
### <a name="to-remove-a-specified-collection-of-qoe-configuration-settings"></a>So entfernen Sie eine bestimmte Auflistung von QoE-Konfigurationseinstellungen

 Mit diesem Befehl werden die QoE-Konfigurationseinstellungen entfernt, die auf den Standort Redmond angewendet werden:
    
  ```PowerShell
  Remove-CsQoEConfiguration -Identity "site:Redmond"
  ```

### <a name="to-remove-all-of-the-qoe-configuration-settings-applied-to-the-site-scope"></a>So entfernen Sie alle QoE-Konfigurationseinstellungen, die auf den Standortbereich angewendet wurden

 Mit diesem Befehl werden alle QoE-Konfigurationseinstellungen entfernt, die auf den Standortbereich angewendet werden:
    
  ```PowerShell
  Get-CsQoEConfiguration -Filter "site:*" | Remove-CsQoEConfiguration
  ```

### <a name="to-remove-all-of-the-qoe-configuration-settings-where-qoe-monitoring-is-disabled"></a>So entfernen Sie alle QoE-Konfigurationseinstellungen, in denen die QoE-Überwachung deaktiviert ist

 Mit diesem Befehl werden alle QoE-Konfigurationseinstellungen entfernt, in denen die QoE-Überwachung deaktiviert wurde:
    
  ```PowerShell
  Get-CsQoEConfiguration | Where-Object {$_.EnableQoE -eq $False} | Remove-CsQoEConfiguration
  ```

Ausführliche Informationen finden Sie unter [Remove-CsQoEConfiguration](/powershell/module/skype/remove-csqoeconfiguration?view=skype-ps).
  
## <a name="see-also"></a>Weitere Informationen

[Manuelles Löschen der Datenbanken "Aufzeichnung von Kommunikationsdatensätzen" und "Quality of Experience" in Skype for Business Server](../../deploy/deploy-monitoring/purgecall-detail-recording-and-qoe.md)