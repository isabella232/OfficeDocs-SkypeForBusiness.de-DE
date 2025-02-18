---
title: Löschen einer Standort- oder Benutzerrichtlinie für den externen Benutzerzugriff
ms.reviewer: ''
ms:assetid: 6d907507-825b-4354-9c03-337a459f72de
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg521013(v=OCS.15)
ms:contentKeyID: 48184455
mtps_version: v=OCS.15
ms.author: v-cichur
author: cichur
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
description: Sie können alle Website- oder Benutzerrichtlinien löschen, die in der Systemsteuerung Skype for Business Server auf der Seite "Richtlinie für den externen Zugriff" aufgeführt sind.
ms.openlocfilehash: dc8ebdd0fc37d638f4d129dd995ebd2f179b0026
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58582759"
---
# <a name="delete-a-site-or-user-policy-for-external-user-access"></a>Löschen einer Standort- oder Benutzerrichtlinie für den externen Benutzerzugriff

Wenn Sie richtlinien für den externen Benutzerzugriff erstellt oder konfiguriert haben, die Sie nicht mehr verwenden möchten, können Sie die folgende Methode ausführen:

  - Löschen Sie alle Website- oder Benutzerrichtlinien, die Sie erstellt haben.

  - Setzen Sie die globale Richtlinie auf die Standardeinstellungen zurück. Die standardmäßigen globalen Richtlinieneinstellungen verweigern externen Benutzern den Zugriff. Die globale Richtlinie kann nicht gelöscht werden.


Sie können alle Website- oder Benutzerrichtlinien löschen, die in der Skype for Business Server Systemsteuerung auf der Seite **"Richtlinie für den externen Zugriff"** aufgeführt sind. Durch das Löschen der globalen Richtlinie wird sie nicht tatsächlich gelöscht, sondern nur auf die Standardeinstellungen zurückgesetzt, die keine Unterstützung für Zugriffsoptionen für externe Benutzer enthalten. Ausführliche Informationen zum Zurücksetzen der globalen Richtlinie finden Sie unter ["Zurücksetzen der globalen Richtlinie für den externen Benutzerzugriff".](reset-the-global-policy-for-external-user-access.md)


## <a name="to-delete-a-site-or-user-policy-for-external-user-access"></a>So löschen Sie eine Standort- oder Benutzerrichtlinie für den externen Benutzerzugriff

1.  Melden Sie sich über ein Benutzerkonto, das Mitglied der Gruppe "RTCUniversalServerAdmins" ist (oder über gleichwertige Benutzerrechte verfügt) oder der Rolle "CsAdministrator" zugewiesen ist, bei einem beliebigen Computer in Ihrer internen Bereitstellung an.

2.  Öffnen Sie ein Browserfenster, und geben Sie dann die Admin-URL ein, um die Skype for Business Server Systemsteuerung zu öffnen. 

3.  Klicken Sie auf **Externer Benutzerzugriff** und dann auf **Richtlinie für den externen Zugriff**.

4.  Klicken Sie auf der Registerkarte **Richtlinie für den externen Zugriff** auf die zu löschende Standort- oder Benutzerrichtlinie, klicken Sie auf **Bearbeiten** und dann auf **Löschen**.

5.  Klicken Sie zum Bestätigen des Löschvorgangs auf **OK**.


## <a name="removing-pin-policies-by-using-windows-powershell-cmdlets"></a>Entfernen von PIN-Richtlinien mithilfe Windows PowerShell Cmdlets

Richtlinien für den externen Zugriff können mithilfe von Windows PowerShell und dem Cmdlet Remove-CsExternalAccessPolicy gelöscht werden. Dieses Cmdlet kann entweder über die Skype for Business Server Verwaltungsshell oder über eine Remotesitzung von Windows PowerShell ausgeführt werden. 


## <a name="to-remove-a-specific-external-access-policy"></a>So entfernen Sie eine bestimmte Richtlinie für den externen Zugriff

  - Dieser Befehl entfernt die Richtlinie für den externen Zugriff, die auf den Standort "Redmond" angewendet werden:<br/><br/>Remove-CsExternalAccessPolicy -Identity "site:Redmond"


## <a name="to-remove-all-the-external-access-policies-applied-to-the-per-user-scope"></a>So entfernen Sie alle externen Zugriffsrichtlinien, die auf den Benutzerbereich angewendet werden

  - Dieser Befehl entfernt alle Richtlinien für den externen Zugriff, die auf Benutzerbasis konfiguriert wurden:<br/><br/>Get-CsExternalAccessPolicy -Filter "tag:*" | Remove-CsExternalAccessPolicy


## <a name="to-remove-all-the-external-access-policies-where-outside-user-access-is-disabled"></a>So entfernen Sie alle Richtlinien für den externen Zugriff, bei denen der Externe Benutzerzugriff deaktiviert ist

  - Dieser Befehl löscht alle Richtlinien für den externen Zugriff, für die der externe Benutzerzugriff deaktiviert ist:<br/><br/>Get-CsExternalAccessPolicy | Where-Object {$_. EnableOutsideAccess -eq $False}-| Remove-CsExternalAccessPolicy


Weitere Informationen finden Sie im Hilfethema zum [Cmdlet "Remove-CsExternalAccessPolicy".](/powershell/module/skype/Remove-CsExternalAccessPolicy)
