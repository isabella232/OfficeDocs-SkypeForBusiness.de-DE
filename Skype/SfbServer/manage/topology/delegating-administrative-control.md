---
title: Delegieren der administrativen Kontrolle über Skype for Business Server
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
description: ''
ms.openlocfilehash: 580a0c31d3321564d76f248408facaffa4f399a2
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58580519"
---
# <a name="delegate-administrative-control-of-skype-for-business-server"></a>Delegieren der administrativen Kontrolle über Skype for Business Server 

In Skype for Business Server werden administrative Aufgaben mithilfe des Features für die rollenbasierte Zugriffssteuerung (RBAC) an Benutzer delegiert. Wenn Sie Skype for Business Server installieren, werden eine Reihe von RBAC-Rollen für Sie erstellt. Diese Rollen entsprechen universellen Sicherheitsgruppen in Active Directory Domain Services. Die RBAC-Rolle "CsHelpDesk" entspricht beispielsweise der Gruppe "CsHelpDesk", die sich im Container "Benutzer" in active Directory Domain Services befindet. Darüber hinaus ist jede RBAC-Rolle einer Reihe von Skype for Business ServerWindows PowerShell Cmdlets zugeordnet.   Diese Cmdlets stellen die Aufgaben dar, die von Benutzern ausgeführt werden können, denen die angegebene RBAC-Rolle zugewiesen wurde. Beispielsweise wurde der Rolle "CsHelpDesk" die Cmdlets Lock-CsClientPin und UnlockCsClientPin zugewiesen. Das bedeutet, dass Benutzer, denen die CsHelpDesk-Rolle zugewiesen wurde, Benutzer-PIN-Nummern sperren und entsperren können. Der Rolle "CsHelpDesk" wurde jedoch nicht das Cmdlet New-CsVoicePolicy zugewiesen. Das bedeutet, dass Benutzer, denen die Rolle "CsHelpDesk" zugewiesen wurde, keine neuen VoIP-Richtlinien erstellen können.

## <a name="viewing-information-about-rbac-roles"></a>Anzeigen von Informationen zu RBAC-Rollen

Sie können grundlegende Informationen zu Ihren RBAC-Rollen abrufen, indem Sie den folgenden Befehl in der Skype for Business Server Verwaltungsshell ausführen:

`Get-CsAdminRole`

Beachten Sie, dass die Identität der RBAC-Rolle (z. B. CsVoiceAdministrator) über eine direkte Zuordnung zu einer Sicherheitsgruppe verfügt, die sich im Container "Benutzer" in Active Directory Domain Services befindet.

Verwenden Sie einen Befehl wie den folgenden, um eine Liste der Cmdlets anzuzeigen, die einer Rolle zugewiesen wurden:

`Get-CsAdminRole -Identity "CsHelpDesk" | Select-Object -ExpandProperty Cmdlets`

## <a name="assigning-an-rbac-role-to-a-user"></a>Zuweisen einer RBAC-Rolle zu einem Benutzer

Um einem Benutzer eine RBAC-Rolle zuzuweisen, müssen Sie diesen Benutzer der entsprechenden Active Directory-Sicherheitsgruppe hinzufügen. Um z. B. die Rolle "CsLocationAdministrator" einem Benutzer zuzuweisen, müssen Sie diesen Benutzer der Gruppe "CsLocationAdministrator" hinzufügen. Dies kann durch Ausführen des folgenden Verfahrens erfolgen:

1. Melden Sie sich mithilfe eines Kontos, das über die Berechtigung zum Ändern der Mitgliedschaft einer Active Directory-Gruppe verfügt, auf einem Computer an, auf dem Active Directory-Benutzer und -Computer installiert wurden.
2. Klicken Sie auf **"Start",** auf **"Alle Programme",** auf **"Verwaltungstools"** und dann auf **"Active Directory-Benutzer und -Computer".**
3. Erweitern Sie in Active Directory-Benutzer und -Computer den Namen Ihrer Domäne, und klicken Sie auf den Container **"Benutzer".**
4. Klicken Sie mit der rechten Maustaste auf die Sicherheitsgruppe **"CsLocationAdministrator",** und klicken Sie dann auf **"Eigenschaften".**
5. Klicken Sie im Dialogfeld **"Eigenschaften"** auf der Registerkarte **"Mitglieder"** auf **"Hinzufügen".**
6. Geben Sie im Dialogfeld **"Benutzer, Computer, Kontakte oder Gruppen auswählen"** den Benutzernamen oder Anzeigenamen des Benutzers ein, der der Gruppe hinzugefügt werden soll (z. B. Ken Myer), geben **Sie die objektnamen** ein, die ausgewählt werden sollen, und klicken Sie dann auf **OK.**
7. Klicken Sie im Dialogfeld **Eigenschaften** auf **OK**.

Um zu überprüfen, ob die RBAC-Rolle zugewiesen wurde, verwenden Sie das cmdlet Get-CsAdminRoleAssignment, und übergeben Sie das Cmdlet den SamAccountName (Active Directory-Anmeldename) des Benutzers. Führen Sie beispielsweise diesen Befehl in der Skype for Business Server-Verwaltungsshell aus:

`Get-CsAdminRoleAssignment  -Identity "kenmyer"`
