---
title: Zuweisen und Ändern von Notfallstandorten für Benutzer
author: cichur
ms.author: v-cichur
manager: serdars
ms.reviewer: jastark, roykuntz
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:
- M365-voice
audience: Admin
appliesto:
- Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: In diesem Artikel erfahren Sie, wie Sie den Ort für einen Notfallstandort für Benutzer in Ihrer Organisation zuweisen oder ändern.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 146c97be9b416b0e338b6b6c49eeb19171b26cee
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58617601"
---
# <a name="assign-or-change-the-place-for-an-emergency-location-for-a-user"></a>Zuweisen oder Ändern des Orts für einen Notfallstandort für einen Benutzer

Jeder aktiven Telefonnummer muss ein Notfallstandort zugeordnet sein, wenn Sie die Telefonnummer einem Benutzer zuweisen. (Sie ordnen die Adresse zu, wenn Sie in einem Office 365 eine Telefonnummer erhalten oder wenn Sie eine Telefonnummer übertragen.) Wenn Sie die Nummer einem Notfallstandort zuordnen, können Sie auch einen Ort hinzufügen, um einen exakteren Standort innerhalb eines physischen Standorts einzuordnen. Ein Ort kann der Stockwerk, Gebäudeflügel oder die Büronummer sein, in der sich der Benutzer befindet. Sie können eine unbegrenzte Anzahl von Orten für einen bestimmten Notfallstandort haben und den Ort ändern, wenn der Benutzer in ein anderes Büro oder Gebäude wechselt. Wenn der Benutzer z. B. von der Etage 34 in die Etage 35 wechselt.
  
Informationen zum Erhalten von Anrufplänen und deren Kosten finden Sie unter [Teams-Add-On-Lizenzierung.](teams-add-on-licensing/microsoft-teams-add-on-licensing.md)
  
Sie können den Ort für einen Notfallstandort für einen Benutzer im Microsoft Teams Admin Center oder mithilfe von PowerShell zuweisen oder ändern.

## <a name="using-the-microsoft-teams-admin-center"></a>Verwenden des Microsoft Teams Admin Centers

1. Klicken Sie in der linken Navigationsleiste Microsoft Teams Admin Center **auf**  >  **Sprachanrufnummern Telefon .**

2. Klicken Sie **Telefon Seite** Zahlen bearbeiten  auf die Registerkarte Zahlen, wählen Sie eine Benutzernummer in der Liste aus, und klicken Sie dann auf **Bearbeiten**.

3. Gehen Sie **im** Bereich Bearbeiten **unter Notfallstandort** wie folgt vor:

    - Um einen Ort zuzuordnen, suchen Sie nach dem Speicherort oder Ort, und wählen Sie dann den Ort in den Suchergebnissen aus.

    - Wenn Sie den Ort ändern möchten, der dem Benutzer bereits zugewiesen ist, klicken Sie auf **X,** um die vorhandene Position zu entfernen, suchen Sie nach dem Ort, den Sie zuweisen möchten, und wählen Sie ihn aus.

4. Je nachdem, ob Sie dem Benutzer eine E-Mail mit seinen Telefonnummerninformationen senden möchten, deaktivieren oder aktivieren Sie **Dem Benutzer eine E-Mail mit den Telefonnummerninformationen senden**. Standardmäßig ist dies aktiviert.

5. Klicken Sie auf **Anwenden**.

## <a name="using-powershell"></a>Verwendung von PowerShell

Weitere [Informationen finden Sie unter Set-CsOnlineLisLocation.](/powershell/module/skype/set-csonlinelislocation)
    
## <a name="related-topics"></a>Verwandte Themen

- [Verwalten von Notrufen](what-are-emergency-locations-addresses-and-call-routing.md)
- [Hinzufügen, Ändern oder Entfernen eines Notfallstandorts für Ihre Organisation](add-change-remove-emergency-location-organization.md)
- [Hinzufügen, Ändern oder Entfernen eines Ortes als Notfallstandort für Ihre Organisation](add-change-remove-emergency-place-organization.md)
- [Zuweisen oder Ändern eines Notfallstandorts für einen Benutzer](assign-change-emergency-location-user.md)
- [Verwalten von Telefonnummern für Ihre Organisation](/microsoftteams/manage-phone-numbers-for-your-organization)
- [Nutzungsbedingungen für Notrufe](./emergency-calling-terms-and-conditions.md)