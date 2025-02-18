---
title: Die Konferenz-ID eines Benutzers sehen, ändern und zurücksetzen
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: 77d36233-2aab-4802-ba9c-e9a8885ea643
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:
- M365-collaboration
audience: Admin
appliesto:
- Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Audio Conferencing
- seo-marvel-apr2020
description: Erfahren Sie, wie Sie einem Benutzer in einer Konferenz eine Konferenz-ID Microsoft Teams und welche Parameter die Konferenz-IDs haben sollten.
ms.openlocfilehash: 62cbb281af4db60db15676b109b2573c03eb7552
ms.sourcegitcommit: 15e90083c47eb5bcb03ca80c2e83feffe67646f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2021
ms.locfileid: "58733254"
---
# <a name="view-and-reset-a-conference-id-assigned-to-a-user-in-microsoft-teams"></a>Anzeigen und Zurücksetzen einer Konferenz-ID, die einem Benutzer in einer Konferenz zugewiesen Microsoft Teams

Wenn ein Microsoft Teams-Benutzer für Audiokonferenzen in Microsoft 365 oder Office 365 eingerichtet wird und Microsoft als Audiokonferenzanbieter verwendet wird, wird ihm automatisch eine Konferenz-ID zugewiesen. Die zugewiesene Konferenz-ID wird in der Besprechungs-Einladung gesendet, wenn die Besprechung geplant ist. Jedem Meeting, das ein Benutzer plant wird eine eindeutige Konferenz-ID zugewiesen. 
  
Konferenzkennungen werden zwar automatisch erstellt und Benutzern zugewiesen, es kann aber auch sein, dass Benutzer diese Nummer nicht verwenden möchten und Sie sie auf eine bestimmte Nummer festlegen möchten oder die Benutzer sich nicht mehr erinnern oder ihre Konferenz-ID vergessen haben. Sie können Microsoft Teams Admin Center oder Windows PowerShell, um ihre Konferenz-ID anzeigen, ändern und zurücksetzen.
  
Eine E-Mail wird mit der Konferenz-ID und den Standard-Audiokonferenz-Telefonnummern an den Benutzer gesendet. Wenn Sie die Konferenz-ID zurücksetzen, wird eine andere E-Mail gesendet, die die Konferenz-ID, jedoch keine PIN enthält. Weitere [Informationen zum Zurücksetzen der PIN eines](reset-a-conference-id-for-a-user-in-teams.md) Konferenzorganisators finden Sie Microsoft Teams Zurücksetzen einer Konferenz-ID für einen Benutzer in einer Besprechung. 

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]
  
## <a name="view-and-reset-conference-ids"></a>Anzeigen und Zurücksetzen der Konferenz-IDs

### <a name="to-view-the-conference-id"></a>So zeigen Sie die Konferenz-ID an

![Ein Symbol mit dem Microsoft Teams Logo.](media/teams-logo-30x30.png) **Verwenden des Microsoft Teams Admin Centers**

1. Klicken Sie im linken Navigationsbereich **auf Benutzer**, und wählen Sie den Benutzer aus der Liste der verfügbaren Benutzer aus.

2. Klicken Sie oben auf der Seite auf **Bearbeiten**.

3. Sehen **Sie unter Audiokonferenz unter** **Konferenz-ID nach.**

    > [!TIP]
    > Sie können dem Benutzer alle Konferenzinformationen per E-Mail senden, die die Konferenz-ID und Audiotelefonnummern enthält, indem Sie auf den Link **Konferenzinformationen per** E-Mail senden klicken.
  
**Verwenden von Windows PowerShell**

Weitere Informationen Microsoft Teams Sie in der [PowerShell-Referenz.](/powershell/module/teams/?view=teams-ps)
    
  
### <a name="to-reset-the-conference-id"></a>So setzen Sie die Konferenz-ID zurück

Sie können eine Konferenz-ID für einen Benutzer zurücksetzen, wenn er diese beispielsweise vergessen hat.
  
![Ein Symbol mit dem Microsoft Teams Logo.](media/teams-logo-30x30.png) **Verwenden des Microsoft Teams Admin Centers**

1. Klicken Sie im linken Navigationsbereich **auf Benutzer**, und wählen Sie den Benutzer aus der Liste der verfügbaren Benutzer aus.

2. Klicken Sie oben auf der Seite auf **Bearbeiten**.

3. Klicken **Sie unter Audiokonferenzen** auf **Konferenz-ID zurücksetzen**.

4. Klicken Sie **im Fenster Konferenz-ID** zurücksetzen auf **Zurücksetzen**. Es wird automatisch eine Konferenz-ID erstellt und eine E-Mail mit der neuen Konferenz-ID an den Benutzer gesendet.
  
**Verwenden von Windows PowerShell**

Weitere Informationen Microsoft Teams Sie in der [PowerShell-Referenz.](/powershell/module/teams/?view=teams-ps)


## <a name="what-else-should-you-know"></a>Was sollten Sie noch wissen?

   > [!IMPORTANT]
   >  Nachdem eine neue Konferenz-ID erstellt oder zurückgesetzt wurde, können Anrufer die alte Konferenz-ID nicht mehr verwenden. Sie sollten Benutzer benachrichtigen, dass sie ihre angesetzten Besprechungseinladungen neu planen, damit die neue Konferenz-ID den Einladungen hinzugefügt wird. 
  
    
- Die Konferenz-ID muss die Länge in Ziffern aufweisen, die auf der Audiokonferenzbrücke festgelegt ist. Konferenz-IDs dürfen keine Buchstaben oder Sonderzeichen enthalten. nur Zahlen verwendet werden können.
   
    
## <a name="want-to-know-more-about-windows-powershell"></a>Möchten Sie mehr über Windows PowerShell erfahren?

Bei Windows PowerShell dreht sich alles um das Verwalten von Benutzern und Funktionen, die Benutzer verwenden oder nicht verwenden können. Mit Windows PowerShell können Sie Microsoft 365 oder Office 365 mithilfe eines einzigen Administrationspunkts verwalten, der Ihre tägliche Arbeit vereinfachen kann, wenn Sie mehrere Aufgaben ausführen müssen. Informieren Sie sich in den folgenden Themen über die Verwendung von Windows PowerShell:
    
  - [Warum Sie Office 365 PowerShell verwenden müssen](/microsoft-365/enterprise/why-you-need-to-use-microsoft-365-powershell)
    
  - [Beste Möglichkeiten zum Verwalten von Microsoft 365 oder Office 365 mit Windows PowerShell](/previous-versions//dn568025(v=technet.10))
    
Weitere Informationen zu Windows PowerShell finden Sie in der [PowerShell-Referenz für Microsoft Teams](/powershell/module/teams/?view=teams-ps).
    
## <a name="related-topics"></a>Verwandte Themen

[Testen oder Kaufen des Audiokonferenz-Add-Ons in Microsoft 365 oder Office 365](/SkypeForBusiness/audio-conferencing-in-office-365/try-or-purchase-audio-conferencing-in-office-365)