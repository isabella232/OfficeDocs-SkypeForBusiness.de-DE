---
title: Zuweisen von Richtlinien zu Ihren Benutzern in Microsoft Teams
author: cichur
ms.author: v-cichur
manager: serdars
ms.reviewer: tomkau, saragava, ritikag, jastark
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection:
- M365-collaboration
appliesto:
- Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Lernen Sie die verschiedenen Methoden zum Zuweisen von Richtlinien zu Ihren Benutzern in Microsoft Teams.
f1keywords:
- ms.teamsadmincenter.bulkoperations.users.edit
- ms.teamsadmincenter.bulkoperations.edit
ms.openlocfilehash: ed0ed4b03d6472a646cd19897b33a22b2fc4df06
ms.sourcegitcommit: cf2f96dbd485ac4cc822c5a591ccce6b47f12cc7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2021
ms.locfileid: "59456365"
---
# <a name="assign-policies-to-your-users-in-microsoft-teams"></a>Zuweisen von Richtlinien zu Ihren Benutzern in Microsoft Teams

Als Administrator steuern Sie mithilfe von Richtlinien die Teams Features, die Benutzern in Ihrer Organisation zur Verfügung stehen. Beispielsweise gibt es Anrufrichtlinien, Besprechungsrichtlinien und Messagingrichtlinien, um nur einige zu nennen.

Organisationen haben verschiedene Arten von Benutzern mit eindeutigen Anforderungen. Benutzerdefinierte Richtlinien, die Sie erstellen und zuweisen, ermöglichen Ihnen das Anpassen von Richtlinieneinstellungen an verschiedene Benutzergruppen basierend auf diesen Anforderungen.

Zum einfachen Verwalten von Richtlinien in Ihrer Organisation bietet Teams verschiedene Möglichkeiten zum Zuweisen von Richtlinien zu Benutzern. Weisen Sie eine Richtlinie direkt den Benutzern zu, entweder einzeln oder mit einem Maßstab über eine Batchzuweisung, oder einer Gruppe, deren Mitglieder die Benutzer sind. Sie können auch Richtlinienpakete verwenden, um Benutzern in Ihrer Organisation, die ähnliche Rollen haben, eine vordefinierte Sammlung von Richtlinien zuzuordnen. Welche Option Sie auswählen, hängt von der Anzahl der Richtlinien ab, die Sie verwalten, und von der Anzahl der Benutzer, der Sie Richtlinien zuweisen. Globale Richtlinien (Organisationsweite Standardrichtlinien) gelten für die größte Anzahl von Benutzern in Ihrer Organisation. Sie müssen nur den Benutzern Richtlinien zuweisen, die spezielle Richtlinien erfordern.

In diesem Artikel werden die verschiedenen Möglichkeiten beschrieben, wie Sie Benutzern Richtlinien zuweisen können, sowie die empfohlenen Szenarien für die Verwendung von was.

## <a name="which-policy-takes-precedence"></a>Welche Richtlinie hat Vorrang?

Ein Benutzer verfügt über eine effektive Richtlinie für jeden Richtlinientyp. Es ist möglich oder sogar wahrscheinlich, dass einem Benutzer eine Richtlinie direkt zugewiesen wird und außerdem Mitglied einer oder mehreren Gruppen ist, denen eine Richtlinie desselben Typs zugewiesen ist. Welche Richtlinie hat in solchen Szenarien Vorrang? Die effektive Richtlinie eines Benutzers wird anhand der Rangfolgeregeln wie folgt bestimmt.

Wenn einem Benutzer eine Richtlinie direkt zugewiesen wird (entweder einzeln oder über eine Batchzuweisung), hat diese Richtlinie Vorrang. Im folgenden visuellen Beispiel ist die effektive Richtlinie des Benutzers die Besprechungsrichtlinie "Square Square", die dem Benutzer direkt zugewiesen wird.

![Diagramm, das zeigt, wie eine direkt zugewiesene Richtlinie Vorrang hat.](media/assign-policies-example-directly-assigned.png)

Wenn einem Benutzer eine Richtlinie eines bestimmten Typs nicht direkt zugewiesen wurde, hat die einer Gruppe zugewiesene Richtlinie, deren Mitglied er ist, Vorrang. Wenn ein Benutzer ein Mitglied mehrerer Gruppen ist, [](#group-assignment-ranking) hat die Richtlinie, die für den angegebenen Richtlinientyp die höchste Gruppenzuordnungsrangfolge besitzt, Vorrang.

In diesem visuellen Beispiel ist die effektive Richtlinie des Benutzers die Exec Teams- und HD-Richtlinie, die im Vergleich zu anderen Gruppen, denen der Benutzer gehört, die höchste Zuweisungsrangfolge hat und denen auch eine Richtlinie desselben Richtlinientyps zugewiesen ist.  

![Diagramm, das zeigt, wie eine von einer Gruppe geerbte Richtlinie Vorrang hat.](media/assign-policies-example-group.png)

Wenn einem Benutzer eine Richtlinie nicht direkt zugewiesen wurde oder kein Mitglied von Gruppen ist, denen eine Richtlinie zugewiesen wurde, erhält der Benutzer die globale (organisationsweite Standard)-Richtlinie für diesen Richtlinientyp. Hier sehen Sie ein visuelles Beispiel.

![Diagramm, das zeigt, wie eine globale Richtlinie vorrangig ist.](media/assign-policies-example-global.png)

Weitere Informationen finden Sie unter [Rangfolgeregeln.](#precedence-rules)

## <a name="ways-to-assign-policies"></a>Möglichkeiten zum Zuweisen von Richtlinien

Im Folgenden finden Sie eine Übersicht über die Möglichkeiten zum Zuweisen von Richtlinien zu Benutzern und die empfohlenen Szenarien für die einzelnen Szenarien. Wählen Sie die Links aus, um mehr zu erfahren.

Bevor Sie Richtlinien einzelnen Benutzern oder Gruppen zuweisen, beginnen Sie, indem Sie die globalen [(organisationsweiten)](#set-the-global-policies) Standardrichtlinien so festlegen, dass sie für die größte Anzahl von Benutzern in Ihrer Organisation gelten.  Nachdem Sie die globalen Richtlinien festgelegt haben, müssen Sie nur den Benutzern Richtlinien zuweisen, die spezielle Richtlinien erfordern.

|So geht's  |Wenn...  | Verwendung von ...
|---------|---------|----|
|[Zuweisen einer Richtlinie zu einzelnen Benutzern](#assign-a-policy-to-individual-users)    | Sie sind neu bei Teams und beginnen gerade, oder Sie müssen nur einer kleinen Anzahl von Benutzern eine oder mehrere Richtlinien zuweisen. |Die Microsoft Teams Admin Center oder PowerShell-Cmdlets im PowerShell Teams Modul
|[Zuweisen einer Richtlinie zu einer Gruppe](#assign-a-policy-to-a-group) |Weisen Sie Richtlinien basierend auf der Gruppenmitgliedschaft eines Benutzers zu. Weisen Sie beispielsweise allen Benutzern in einer Sicherheitsgruppe oder Verteilerliste eine Richtlinie zu.| Die Microsoft Teams Admin Center oder PowerShell-Cmdlets im PowerShell Teams Modul|
|[Zuweisen einer Richtlinie zu einer Gruppe von Benutzern](#assign-a-policy-to-a-batch-of-users)   | Weisen Sie Richtlinien großen Gruppen von Benutzern zu. Weisen Sie beispielsweise Hunderten oder Tausenden von Benutzern in Ihrer Organisation gleichzeitig eine Richtlinie zu. |Die Microsoft Teams Admin Center oder PowerShell-Cmdlets im PowerShell Teams Modul|
| [Zuweisen eines Richtlinienpakets zu Benutzern](#assign-a-policy-package-to-users)  |Weisen Sie bestimmten Gruppen von Benutzern in Ihrer Organisation, die über die gleichen oder ähnliche Rollen verfügen, mehrere Richtlinien zu. Weisen Sie beispielsweise Lehrkräften in Ihrer Bildungseinrichtungen das Richtlinienpaket für Bildungseinrichtungen zu, um ihnen Vollzugriff auf Chats, Anrufe und Besprechungen zu geben. Weisen Sie das Richtlinienpaket für Bildungseinrichtungen (Schüler/Studenten sekundärer Bildungseinrichtungen) sekundären Schülern/Studenten zu, um bestimmte Funktionen wie private Anrufe zu beschränken.  |Die Microsoft Teams Admin Center oder PowerShell-Cmdlets im PowerShell Teams Modul|
| [Zuweisen eines Richtlinienpakets zu einer Gruppe](#assign-a-policy-package-to-a-group) (in der privaten Vorschau)   |Weisen Sie einer Gruppe von Benutzern in Ihrer Organisation, die über die gleichen oder ähnliche Rollen verfügen, mehrere Richtlinien zu. Weisen Sie beispielsweise allen Benutzern in einer Sicherheitsgruppe oder Verteilerliste ein Richtlinienpaket zu. |Das Microsoft Teams Admin Center (in Kürze verfügbar) oder PowerShell-Cmdlets im Teams PowerShell-Modul|
| [Zuweisen eines Richtlinienpakets zu einer Gruppe von Benutzern](#assign-a-policy-package-to-a-batch-of-users)|Weisen Sie einer Gruppe von Benutzern in Ihrer Organisation, die über die gleichen oder ähnliche Rollen verfügen, mehrere Richtlinien zu. Weisen Sie beispielsweise allen Lehrkräften in Ihrer Schule das Richtlinienpaket für "Education (Lehrer)" mithilfe einer Batchzuweisung zu, um ihnen Vollzugriff auf Chats, Anrufe und Besprechungen zu geben. Weisen Sie das Richtlinienpaket für Bildungseinrichtungen (Sekundäre Bildungseinrichtungen) einer Gruppe von sekundären Schülern/Studenten zu, um bestimmte Funktionen wie private Anrufe zu beschränken.|PowerShell-Cmdlets im Teams PowerShell-Modul|

## <a name="set-the-global-policies"></a>Festlegen der globalen Richtlinien

Führen Sie die folgenden Schritte aus, um die globalen (organisationsweiten Standard)-Richtlinien für jeden Richtlinientyp festlegen.

### <a name="using-the-microsoft-teams-admin-center"></a>Verwenden des Microsoft Teams Admin Centers

1. Wechseln Sie im linken Navigationsbereich Microsoft Teams Admin Center zur Richtlinienseite für den Richtlinientyp, den Sie aktualisieren möchten. Beispielsweise können sie **Teams**  >  **Teams** Besprechungsrichtlinien   >  , **Messaging-Richtlinien** oder **Voice**  >  **Calling-Richtlinien verwenden.**
2. Wählen Sie **die Richtlinie Global (Organisationsweit Standard)** aus, um die aktuellen Einstellungen anzeigen.
3. Aktualisieren Sie die Richtlinie nach Bedarf, und wählen Sie dann **Anwenden aus.**

### <a name="using-powershell"></a>Verwendung von PowerShell

Zum Festlegen der globalen Richtlinien mithilfe von PowerShell verwenden Sie den globalen Bezeichner.  Überprüfen Sie zunächst die aktuelle globale Richtlinie, um zu bestimmen, welche Einstellung Sie ändern möchten.

```powershell
Get-CsTeamsMessagingPolicy -Identity Global
 
Identity                      : Global
Description                   :
AllowUrlPreviews              : True
AllowOwnerDeleteMessage       : False
AllowUserEditMessage          : True
AllowUserDeleteMessage        : True
AllowUserChat                 : True
AllowRemoveUser               : True
AllowGiphy                    : True
GiphyRatingType               : Moderate
AllowMemes                    : True
AllowImmersiveReader          : True
AllowStickers                 : True
AllowUserTranslation          : False
ReadReceiptsEnabledType       : UserPreference
AllowPriorityMessages         : True
ChannelsInChatListEnabledType : DisabledUserOverride
AudioMessageEnabledType       : ChatsAndChannels
Expand (20 lines) Collapse 
```

Aktualisieren Sie als Nächstes die Globale Richtlinie nach Bedarf.  Sie müssen nur Werte für die Einstellungen angeben, die Sie ändern möchten.

```powershell
Set-CsTeamsMessagingPolicy -Identity Global -AllowUserEditMessage $false
```

## <a name="assign-a-policy-to-individual-users"></a>Zuweisen einer Richtlinie zu einzelnen Benutzern

Führen Sie die folgenden Schritte aus, um eine Richtlinie einem einzelnen Benutzer oder einer kleinen Anzahl von Benutzern gleichzeitig zuzuordnen.

### <a name="use-the-microsoft-teams-admin-center"></a>Verwenden des Microsoft Teams Admin Centers

So weisen Sie einem Benutzer eine Richtlinie zu:

1. Wechseln Sie in der linken Navigationsleiste Microsoft Teams Admin Center zu Benutzer **,** und wählen Sie dann den Benutzer aus.
2. Wählen Sie den Benutzer aus, indem Sie links des Benutzernamens klicken und dann **Einstellungen bearbeiten auswählen.**
3. Wählen Sie die Richtlinie aus, die Sie zuweisen möchten, und wählen Sie dann **Anwenden aus.**

Sie können auch die folgenden Schritte ausführen:

1. Wechseln Sie in der linken Navigationsleiste Microsoft Teams Admin Center zur Richtlinienseite.
2. Wählen Sie die Richtlinie aus, die Sie zuweisen möchten, indem Sie links des Richtliniennamens klicken.
3. Wählen Sie **Benutzer verwalten** aus.
4. Suchen Sie im Bereich **Benutzer verwalten** anhand des Anzeigenamens oder des Benutzernamens nach dem Benutzer, wählen Sie den Namen aus, und klicken Sie auf **Hinzufügen**. Wiederholen Sie diesen Schritt für jeden Benutzer, den Sie hinzufügen wollen.
5. Wenn Sie mit dem Hinzufügen von Benutzern fertig sind, wählen Sie **Übernehmen aus.**

### <a name="use-powershell"></a>Verwenden von PowerShell

Jeder Richtlinientyp verfügt über einen eigenen Satz von Cmdlets für die Verwaltung. Verwenden Sie `Grant-` das Cmdlet für einen bestimmten Richtlinientyp, um die Richtlinie zuzuordnen. Verwenden Sie beispielsweise das `Grant-CsTeamsMeetingPolicy` Cmdlet, um Benutzern Teams Besprechungsrichtlinie zuzuordnen. Diese Cmdlets sind im PowerShell Teams Modul enthalten und werden in der Referenz [Skype for Business-Cmdlet dokumentiert.](/powershell/skype/intro?view=skype-ps&preserve-view=true)

Laden Sie die Teams [PowerShell Public Release](https://www.powershellgallery.com/packages/MicrosoftTeams/) herunter, installieren Sie sie (sofern noch nicht vorhanden), und führen Sie dann die folgenden Schritte aus, um eine Verbindung herzustellen.

> [!NOTE]
> Der Skype for Business Online-Connector ist derzeit Bestandteil des aktuellen PowerShell-Moduls von Teams.
>
> Wenn Sie die neueste Version Teams [PowerShell verwenden,](https://www.powershellgallery.com/packages/MicrosoftTeams/)müssen Sie den Skype for Business Online Connector nicht installieren.

```powershell
# When using Teams PowerShell Module

Import-Module MicrosoftTeams
$credential = Get-Credential
Connect-MicrosoftTeams -Credential $credential
```

In diesem Beispiel weisen wir einem Teams namens "Student Meeting Policy" eine Besprechungsrichtlinie namens Reda zu.

```powershell
Grant-CsTeamsMeetingPolicy -Identity reda@contoso.com -PolicyName "Student Meeting Policy"
```

Weitere Informationen finden Sie unter [Verwalten von Richtlinien über PowerShell.](teams-powershell-managing-teams.md#manage-policies-via-powershell)

## <a name="assign-a-policy-to-a-group"></a>Zuweisen einer Richtlinie zu einer Gruppe

Mit der Richtlinienzuweisung zu Gruppen können Sie einer Benutzergruppe, z. B. einer Sicherheitsgruppe oder Verteilerliste, eine Richtlinie zuweisen. Die Richtlinienzuweisung wird anhand von Prioritätsregeln an die Mitglieder der Gruppe weitergegeben. Wenn Mitglieder einer Gruppe hinzugefügt oder daraus entfernt werden, werden ihre geerbten Richtlinienzuweisungen entsprechend aktualisiert.

Die Richtlinienzuweisung zu Gruppen wird für Gruppen mit bis zu 50.000 Benutzern empfohlen, funktioniert aber auch mit größeren Gruppen.

Wenn Sie die Richtlinie zuweisen, wird sie der Gruppe sofort zugewiesen. Die Weitergabe der Richtlinienzuweisung an Mitglieder der Gruppe erfolgt jedoch als Hintergrundvorgang und kann je nach Größe der Gruppe einige Zeit dauern. Dasselbe gilt, wenn eine Richtlinie nicht einer Gruppe zugewiesen wird oder Mitglieder einer Gruppe hinzugefügt oder aus ihr entfernt werden.

Gruppenrichtlinienzuweisungen werden nur an Benutzer weiterveriert, die direkte Mitglieder der Gruppe sind. Die Zuweisungen werden nicht an Mitglieder geschachtelter Gruppen weiterverteilen.

### <a name="what-you-need-to-know-about-policy-assignment-to-groups"></a>Wichtige Informationen zur Richtlinienzuweisung an Gruppen

Bevor Sie beginnen, ist es wichtig, Rangfolgeregeln und Rangfolge von Gruppenzuweisungen zu verstehen.

#### <a name="precedence-rules"></a>Rangfolgeregeln

Für einen bestimmten Richtlinientyp wird die effektive Richtlinie eines Benutzers wie folgt bestimmt:

- Eine Richtlinie, die einem Benutzer direkt zugewiesen ist, hat Vorrang vor allen anderen Richtlinien desselben Typs, der einer Gruppe zugewiesen ist. Mit anderen Worten: Wenn einem Benutzer eine Richtlinie eines bestimmten Typs direkt zugewiesen wird, erbt dieser Benutzer keine Richtlinie desselben Typs von einer Gruppe. Dies bedeutet auch: Wenn ein Benutzer über eine Richtlinie eines bestimmten Typs verfügt, die ihm direkt zugewiesen wurde, müssen Sie diese Richtlinie vom Benutzer entfernen, bevor er eine Richtlinie desselben Typs von einer Gruppe erben kann.

- Wenn einem Benutzer keine Richtlinie direkt zugewiesen ist und Mitglied von zwei oder mehr Gruppen ist und jeder Gruppe eine Richtlinie desselben Typs zugewiesen ist, erbt der Benutzer die Richtlinie der Gruppenzuordnung, die die höchste Rangfolge besitzt.

- Wenn ein Benutzer kein Mitglied von Gruppen ist, denen eine Richtlinie zugewiesen ist, gilt die globale (organisationsweite Standard)-Richtlinie für diesen Richtlinientyp für den Benutzer.

Die effektive Richtlinie eines Benutzers wird gemäß den folgenden Regeln aktualisiert:

- wenn ein Benutzer einer Gruppe hinzugefügt oder aus dieser entfernt wird, der eine Richtlinie zugewiesen ist.
- eine Richtlinie wird einer Gruppe nicht zugewiesen.
- eine Richtlinie, die dem Benutzer direkt zugewiesen ist, wird entfernt.

#### <a name="group-assignment-ranking"></a>Rangfolge von Gruppenzuweisungen

Wenn Sie einer Gruppe eine Richtlinie zuweisen, geben Sie eine Rangfolge für die Gruppenzuweisung an. Damit wird ermittelt, welche Richtlinie ein Benutzer als effektive Richtlinie erben soll, wenn der Benutzer Mitglied von zwei oder mehr Gruppen ist und jeder Gruppe eine Richtlinie desselben Typs zugewiesen wird.

Die Gruppenzuordnungsrangfolge ist relativ zu anderen Gruppenzuweisungen desselben Typs. Wenn Sie z. B. eine Anrufrichtlinie zwei Gruppen zuweisen, legen Sie die Rangfolge einer Aufgabe auf 1 und die andere auf 2, und 1 ist die höchste Einstufung. Die Rangfolge der Gruppenzuweisungen gibt an, welche Gruppenmitgliedschaft im Hinblick auf die Vererbung wichtiger oder relevanter als andere Gruppenmitgliedschaften ist.

Sie haben beispielsweise zwei Gruppen: Mitarbeiter Store Mitarbeiter Store Vorgesetzte. Beiden Gruppen wird eine Anrufrichtlinie Teams Richtlinie für Anrufer Store Mitarbeiter" bzw. Store Manager-Anrufrichtlinie zugewiesen. Für einen Store-Manager, der in beiden Gruppen ist, ist ihre Rolle als Manager relevanter als ihre Rolle als Mitarbeiter. Daher sollte die Anrufrichtlinie, die der Store-Manager-Gruppe zugewiesen ist, eine höhere Rangfolge haben.

|Gruppe |Teams von Anrufen der Richtlinie  |Rang|
|---------|---------|---|
|Store Manager   |Store Anrufrichtlinie für Manager         |1|
|Store Mitarbeiter    |Store Anrufrichtlinie für Mitarbeiter      |2|

Wenn Sie keine Rangfolge angeben, wird der Richtlinienzuweisung die niedrigste Einstufung gegeben.

### <a name="in-the-teams-admin-center"></a>Im Teams Admin Center

> [!NOTE]
> Derzeit ist die Richtlinienzuweisung an Gruppen über das Microsoft Teams Admin Center nur für Teams-Anrufrichtlinien, Teams-Richtlinien zum Parken von Anrufen, Teams-Richtlinie, Teams-Richtlinie für Liveereignisse, Teams-Besprechungsrichtlinie und Teams-Messaging-Richtlinie verfügbar. Verwenden Sie PowerShell für andere Richtlinientypen.

1. Wechseln Sie in der linken Navigationsleiste Microsoft Teams Admin Center zur Seite "Richtlinientyp". Wechseln Sie z. B. **zu**  >  **Besprechungsbesprechungsrichtlinien**.

2. Wählen Sie die **Registerkarte Gruppenrichtlinienzuordnung** aus.

3. Wählen **Sie Gruppe hinzufügen** aus, und gehen Sie dann im Bereich Richtlinie **zu** Gruppe zuweisen wie folgt vor:
    1. Suchen Sie nach der Gruppe, der Sie die Richtlinie zuweisen möchten, und fügen Sie sie hinzu.
    2. Legen Sie die Rangfolge für die Gruppenzuweisung an.
    3. Wählen Sie die Richtlinie aus, die Sie zuweisen möchten.
    4. Wählen Sie **Übernehmen aus.**

Um eine Gruppenrichtlinienzuweisung zu  entfernen, wählen Sie auf der Richtlinienseite auf der Registerkarte Gruppenrichtlinienzuweisung die Gruppenzuweisung und dann Entfernen **aus.**

Um die Bewertung einer Gruppenzuordnung zu ändern, müssen Sie zuerst die Gruppenrichtlinienzuweisung entfernen. Führen Sie dann die vorstehenden Schritte aus, um die Richtlinie einer Gruppe zuzuordnen.

### <a name="use-the-powershell-option"></a>Verwenden der PowerShell-Option

> [!NOTE]
> Derzeit ist die Richtlinienzuweisung an Gruppen mithilfe von PowerShell nicht für alle Teams verfügbar. Eine Liste der unterstützten Richtlinientypen finden Sie unter [New-CsGroupPolicyAssignment.](/powershell/module/teams/new-csgrouppolicyassignment)

#### <a name="install-and-connect-to-the-microsoft-teams-powershell-module"></a>Installieren und Herstellen einer Verbindung mit dem Microsoft Teams PowerShell-Modul

Eine schrittweise Anleitung finden Sie unter Installieren [Teams PowerShell.](teams-powershell-install.md)

#### <a name="assign-a-policy-to-a-group-of-users"></a>Zuweisen einer Richtlinie zu einer Benutzergruppe

Verwenden Sie [das Cmdlet New-CsGroupPolicyAssignment,](/powershell/module/teams/new-csgrouppolicyassignment) um einer Gruppe eine Richtlinie zuzuweisen. Sie können eine Gruppe mit der Objekt-ID, der SIP-Adresse oder der E-Mail-Adresse angeben.

In diesem Beispiel weisen wir einer Teams mit dem Namen "Einzelhandelsmanager-Besprechungsrichtlinie" eine Gruppe mit der Zuordnungsrangfolge 1 zu.

```powershell
New-CsGroupPolicyAssignment -GroupId d8ebfa45-0f28-4d2d-9bcc-b158a49e2d17 -PolicyType TeamsMeetingPolicy -PolicyName "Retail Managers Meeting Policy" -Rank 1
```

#### <a name="get-policy-assignments-for-a-group"></a>Erhalten von Richtlinienzuweisungen für eine Gruppe

Verwenden Sie [das Cmdlet Get-CsGroupPolicyAssignment,](/powershell/module/teams/get-csgrouppolicyassignment) um alle Richtlinien einer Gruppe zuzuweisen. Beachten Sie, dass Gruppen immer nach ihrer Gruppen-ID aufgelistet werden, auch wenn deren SIP-Adresse oder E-Mail-Adresse zum Zuweisen der Richtlinie verwendet wurde.

In diesem Beispiel rufen wir alle Richtlinien ab, die einer bestimmten Gruppe zugewiesen sind.

```powershell
Get-CsGroupPolicyAssignment -GroupId e050ce51-54bc-45b7-b3e6-c00343d31274
```

In diesem Beispiel geben wir alle Gruppen zurück, denen eine Richtlinie Teams ist.

```powershell
Get-CsGroupPolicyAssignment -PolicyType TeamsMeetingPolicy
```

#### <a name="remove-a-policy-from-a-group"></a>Entfernen einer Richtlinie aus einer Gruppe

Verwenden Sie [das Cmdlet Remove-CsGroupPolicyAssignment,](/powershell/module/teams/remove-csgrouppolicyassignment) um eine Richtlinie aus einer Gruppe zu entfernen. Wenn Sie eine Richtlinie aus einer Gruppe entfernen, werden die Prioritäten anderer Richtlinien desselben Typs, die dieser Gruppe zugewiesen sind und eine niedrigere Rangfolge haben, aktualisiert. Wenn Sie z. B. eine Richtlinie entfernen, die eine Rangfolge von 2 hat, werden Richtlinien mit einer Rangfolge von 3 und 4 aktualisiert, um ihre neue Rangfolge wider zuspiegeln. In den beiden folgenden Tabellen ist dieses Beispiel dargestellt.

Hier ist eine Liste der Richtlinienzuweisungen und Prioritäten für eine Teams Besprechungsrichtlinie.

|Gruppenname  |Richtlinienname  |Rang|
|---------|---------|---------|
|Vertrieb    |Vertriebsrichtlinie       | 1        |
|West Region     |Richtlinie "Region Westen"         |2         |
|Division    |Abteilungsrichtlinie         |3         |
|Niederlassung   |Richtlinien für Niederlassungen        |4         |

Wenn die Richtlinie "Region Westen" aus der Gruppe Region "Westen" entfernt wird, werden die Richtlinienzuweisungen und -prioritäten wie folgt aktualisiert.

|Gruppenname  |Richtlinienname  |Rang|
|---------|---------|---------|
|Vertrieb    |Vertriebsrichtlinie       | 1        |
|Division    |Abteilungsrichtlinie         |2         |
|Niederlassung   |Richtlinien für Niederlassungen        |3        |

In diesem Beispiel entfernen wir die Teams Besprechungsrichtlinie aus einer Gruppe.

```powershell
Remove-CsGroupPolicyAssignment -PolicyType TeamsMeetingPolicy -GroupId f985e013-0826-40bb-8c94-e5f367076044
```

#### <a name="change-a-policy-assignment-for-a-group"></a>Ändern einer Richtlinienzuweisung für eine Gruppe

> [!NOTE]
> Das [Cmdlet Set-CsGroupPolicyAssignment](/powershell/module/teams/set-csgrouppolicyassignment) wird in Kürze zur Verfügung stehen. In der Zwischenzeit können Sie zum Ändern einer Gruppenrichtlinienzuweisung die aktuelle Richtlinienzuweisung aus der Gruppe entfernen und dann eine neue Richtlinienzuweisung hinzufügen.

Nachdem Sie einer Gruppe eine Richtlinie zugewiesen haben, können Sie das [Cmdlet Set-CsGroupPolicyAssignment](/powershell/module/teams/set-csgrouppolicyassignment) verwenden, um die Richtlinienzuweisung dieser Gruppe wie folgt zu ändern:

- Ändern der Rangfolge
- Ändern der Richtlinie eines bestimmten Richtlinientyps
- Ändern der Richtlinie eines bestimmten Richtlinientyps und der Rangfolge

In diesem Beispiel ändern wir die Anruf parkrichtlinien einer Gruppe in Teams Richtlinie mit dem Namen SupportCallPark und die Zuweisungsrangfolge in 3.

```powershell
Set-CsGroupPolicyAssignment -GroupId 566b8d39-5c5c-4aaa-bc07-4f36278a1b38 -PolicyType TeamsMeetingPolicy -PolicyName SupportCallPark -Rank 3
```

#### <a name="change-the-effective-policy-for-a-user"></a>Ändern der effektiven Richtlinie für einen Benutzer

Hier ist ein Beispiel für das Ändern der effektiven Richtlinie für einen Benutzer, dem eine Richtlinie direkt zugewiesen wurde.

Zuerst verwenden wir das [Cmdlet Get-CsUserPolicyAssignment](/powershell/module/teams/get-csuserpolicyassignment) zusammen mit dem -Parameter, um Details zu den Teams-Richtlinien für Live meeting broadcast zu erhalten, die dem Benutzer ```PolicySource``` zugeordnet sind.

```powershell
Get-CsUserPolicyAssignment -Identity daniel@contoso.com -PolicyType TeamsMeetingBroadcastPolicy | select -ExpandProperty PolicySource
```

Die Ausgabe zeigt, dass dem Benutzer direkt eine Teams-Live übertragen-Richtlinie namens "Mitarbeiterereignisse" zugewiesen wurde, die Vorrang vor der Richtlinie namens "Anbieter-Liveereignisse" hat, die einer Gruppe zugewiesen ist, der der Benutzer angehört.

```console
AssignmentType PolicyName         Reference
-------------- ----------         ---------
Direct         Employee Events
Group          Vendor Live Events 566b8d39-5c5c-4aaa-bc07-4f36278a1b38
```

Jetzt entfernen wir die Richtlinie für Mitarbeiterereignisse vom Benutzer. Dies bedeutet, dass dem Benutzer keine Richtlinie für Teams-Liveübertragung mehr direkt zugewiesen ist, und die Richtlinie "Anbieter-Liveereignisse" erbt, die der Gruppe zugewiesen ist, der der Benutzer angehört.

Verwenden Sie dazu das folgende Cmdlet Skype for Business PowerShell-Modul.

```powershell
Grant-CsTeamsMeetingBroadcastPolicy -Identity daniel@contoso.com -PolicyName $null
```

Verwenden Sie das folgende Cmdlet im Teams PowerShell-Modul, um dies im Maßstab einer Batchrichtlinienzuweisung zu erreichen, wobei $users eine Liste von Benutzern ist, die Sie angeben.

```powershell
New-CsBatchPolicyAssignmentOperation -OperationName "Assigning null at bulk" -PolicyType TeamsMeetingBroadcastPolicy -PolicyName $null -Identity $users  
```

## <a name="assign-a-policy-to-a-batch-of-users"></a>Zuweisen einer Richtlinie zu einer Gruppe von Benutzern

### <a name="use-the-admin-center"></a>Verwenden des Admin Centers

So weisen Sie Benutzern eine Richtlinie in Massen zu:

1. Wählen Sie im linken Navigationsbereich Microsoft Teams Admin Center Benutzer **aus.**

2. Suchen Sie nach den Benutzern, die die Richtlinie zuweisen möchten, oder filtern Sie die Ansicht so, dass die von Ihnen gesuchten Benutzer angezeigt werden.

3. Wählen Sie in der Spalte **&#x2713;** (Häkchen) die Benutzer aus. Um alle Benutzer auszuwählen, klicken Sie am oberen Rand der Tabelle auf &#x2713; (Häkchen).

4. Wählen **Sie Einstellungen bearbeiten** aus, nehmen Sie die änderungen vor, und wählen Sie dann Übernehmen **aus.**

Um den Status Ihrer Richtlinienzuweisung zu sehen, wählen Sie  in dem  Banner, das oben auf der Seite Benutzer angezeigt wird, nachdem Sie Übernehmen ausgewählt haben, um Ihre Richtlinienzuweisung zu übermitteln die Option **Aktivitätsprotokoll aus.** Oder wechseln Sie in der linken Navigationsleiste Microsoft Teams Admin Center zu **Dashboard**, und wählen Sie dann unter Aktivitätsprotokoll **die** Option Details **anzeigen aus.** Im Aktivitätsprotokoll werden Richtlinienzuweisungen für Batches von mehr als 20 Benutzern im Microsoft Teams Admin Center der letzten 30 Tage angezeigt. Weitere Informationen finden Sie unter [Anzeigen Ihrer Richtlinienzuweisungen im Aktivitätsprotokoll](activity-log.md).

### <a name="use-powershell-method"></a>Verwenden der PowerShell-Methode

> [!NOTE]
> Derzeit ist die Batchrichtlinienzuweisung mit PowerShell nicht für alle Teams verfügbar. Eine Liste der unterstützten Richtlinientypen finden Sie unter [New-CsBatchPolicyAssignmentOperation.](/powershell/module/teams/new-csbatchpolicyassignmentoperation)

Mit der Batchrichtlinienzuweisung können Sie großen Gruppen von Benutzern gleichzeitig eine Richtlinie zuweisen, ohne ein Skript verwenden zu müssen. Sie verwenden das [Cmdlet New-CsBatchPolicyAssignmentOperation,](/powershell/module/teams/new-csbatchpolicyassignmentoperation) um eine Gruppe von Benutzern und die Richtlinie zu übermitteln, die Sie zuweisen möchten. Die Zuweisungen werden als Hintergrundvorgänge verarbeitet, und für jeden Batch wird eine Vorgangs-ID generiert. Anschließend können Sie das [Cmdlet Get-CsBatchPolicyAssignmentOperation](/powershell/module/teams/get-csbatchpolicyassignmentoperation) verwenden, um den Fortschritt und Status der Zuordnungen in einem Stapel nachverfolgt.

Geben Sie Benutzer nach ihrer Objekt-ID oder der SIP-Adresse (Session Initiation Protocol) an. Die SIP-Adresse eines Benutzers hat häufig denselben Wert wie der Benutzerprinzipalname (User Principal Name, UPN) oder die gleiche E-Mail-Adresse, aber dies ist nicht erforderlich. Wenn ein Benutzer mit dem UPN oder der E-Mail-Adresse angegeben wird, aber einen anderen Wert als seine SIP-Adresse hat, kann die Richtlinienzuweisung für den Benutzer nicht ausgeführt werden. Wenn ein Batch doppelte Benutzer enthält, werden die Duplikate vor der Verarbeitung aus dem Batch entfernt, und der Status wird nur für die im Batch verbleibenden eindeutigen Benutzer bereitgestellt.

Ein Batch kann bis zu 5.000 Benutzer umfassen. Um optimale Ergebnisse zu erzielen, übermitteln Sie nicht mehr als ein paar Batches gleichzeitig. Lassen Sie die Verarbeitung von Batches abschließen, bevor Sie weitere Batches übermitteln.

#### <a name="install-and-connect-to-the-teams-powershell-module"></a>Installieren und Herstellen einer Verbindung mit dem Teams PowerShell-Modul

Führen Sie das folgende Skript aus, um [Microsoft Teams PowerShell-Modul zu installieren.](https://www.powershellgallery.com/packages/MicrosoftTeams) Vergewissern Sie sich, dass Sie Version 1.0.5 oder höher installieren.

```powershell
Install-Module -Name MicrosoftTeams
```

Führen Sie die folgenden Schritte aus, um Teams Verbindung herzustellen und eine Sitzung zu starten.

```powershell
Connect-MicrosoftTeams
```

Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihren Administratoranmeldeinformationen an.

#### <a name="install-and-connect-to-the-azure-ad-powershell-for-graph-module-optional"></a>Installieren und Herstellen einer Verbindung mit Azure AD PowerShell für Graph Modul (optional)

Möglicherweise möchten Sie auch das [Azure AD PowerShell](/powershell/azure/active-directory/install-adv2) für Graph-Modul herunterladen und installieren (sofern noch nicht vorhanden) und eine Verbindung mit Azure AD herstellen, damit Sie eine Liste der Benutzer in Ihrer Organisation abrufen können.

Führen Sie Folgendes aus, um eine Verbindung mit Azure AD herzustellen.

```powershell
Connect-AzureAD
```

Wenn Sie dazu aufgefordert werden, melden Sie sich mit den gleichen Administratoranmeldeinformationen an, die Sie zum Herstellen einer Verbindung mit Teams.

#### <a name="assign-a-setup-policy-to-a-batch-of-users"></a>Zuweisen einer Setuprichtlinie zu einer Gruppe von Benutzern

In diesem Beispiel verwenden wir das [Cmdlet New-CsBatchPolicyAssignmentOperation,](/powershell/module/teams/new-csbatchpolicyassignmentoperation) um einer Gruppe von Benutzern, die in der Datei "Users_ids.text" aufgeführt sind, eine App-Setuprichtlinie namens "HR-App-Setuprichtlinie" zuzuweisen.

```powershell
$users_ids = Get-Content .\users_ids.txt
New-CsBatchPolicyAssignmentOperation -PolicyType TeamsAppSetupPolicy -PolicyName "HR App Setup Policy" -Identity $users_ids -OperationName "Example 1 batch"
```

In diesem Beispiel stellen wir eine Verbindung mit Azure AD bereit, um eine Sammlung von Benutzern abzurufen, und weisen dann einer Gruppe von Benutzern, die über ihre SIP-Adresse angegeben wurden, eine Messagingrichtlinie mit dem Namen New Hire Messaging Policy zu.

```powershell
Connect-AzureAD
$users = Get-AzureADUser
New-CsBatchPolicyAssignmentOperation -PolicyType TeamsMessagingPolicy -PolicyName "New Hire Messaging Policy" -Identity $users.SipProxyAddress -OperationName "Example 2 batch"
```

#### <a name="get-the-status-of-a-batch-assignment"></a>Anzeigen des Status einer Batchzuweisung

Führen Sie die folgenden Schritte aus, um den Status einer Batchzuordnung zu erhalten. Dabei steht "OperationId" für die Vorgangs-ID, die vom Cmdlet für einen bestimmten `New-CsBatchPolicyAssignmentOperation` Batch zurückgegeben wird.

```powershell
$Get-CsBatchPolicyAssignmentOperation -OperationId f985e013-0826-40bb-8c94-e5f367076044 | fl
```

Wenn die Ausgabe zeigt, dass ein Fehler aufgetreten ist, führen Sie die folgenden Schritte aus, um weitere Informationen zu Fehlern zu erhalten, die sich in der -Eigenschaft `UserState` befinden.

```powershell
Get-CsBatchPolicyAssignmentOperation -OperationId f985e013-0826-40bb-8c94-e5f367076044 | Select -ExpandProperty UserState
```

Weitere Informationen finden Sie unter [Get-CsBatchPolicyAssignmentOperation.](/powershell/module/teams/get-csbatchpolicyassignmentoperation)

## <a name="assign-a-policy-package-to-users"></a>Zuweisen eines Richtlinienpakets zu Benutzern

Ein Richtlinienpaket in Teams ist eine Sammlung vordefinierter Richtlinien und Richtlinieneinstellungen, die Sie Benutzern zuweisen können, die in Ihrer Organisation über die gleichen oder ähnliche Rollen verfügen. Jedes Richtlinienpaket ist auf eine Benutzerrolle ausgelegt und enthält vordefinierte Richtlinien und Richtlinieneinstellungen, die für diese Rolle typische Aktivitäten unterstützen. Einige Beispiele für Richtlinienpakete sind das Paket "Education (Teacher)" und das Paket "Klinischer Mitarbeiter" im Gesundheitswesen. Weitere Informationen finden Sie unter [Verwalten von Richtlinienpaketen in Teams.](manage-policy-packages.md)

### <a name="assign-a-policy-package-to-one-user"></a>Zuweisen eines Richtlinienpakets zu einem Benutzer

1. Wechseln Sie in der linken Navigationsleiste Microsoft Teams Admin Center zu **Benutzer**, und wählen Sie dann den Benutzer aus.

2. Wählen Sie auf der Seite des Benutzers **Richtlinien** und dann neben Richtlinienpaket **die** Option **Bearbeiten aus.**

3. Wählen Sie **im Bereich Richtlinienpaket** zuweisen das Paket aus, das Sie zuweisen möchten, und wählen Sie dann Speichern **aus.**

### <a name="assign-a-policy-package-to-multiple-users"></a>Zuweisen eines Richtlinienpakets zu mehreren Benutzern

1. Navigieren Sie im linken Navigationsbereich des Microsoft Teams Admin Centers zu Richtlinienpakete **,** und wählen Sie dann das Richtlinienpaket aus, das Sie zuweisen möchten, indem Sie links neben dem Paketnamen klicken.

2. Wählen Sie **Benutzer verwalten** aus.

3. Suchen Sie im Bereich **Benutzer verwalten** anhand des Anzeigenamens oder des Benutzernamens nach dem Benutzer, wählen Sie den Namen aus, und klicken Sie auf **Hinzufügen**. Wiederholen Sie diesen Schritt für jeden Benutzer, den Sie hinzufügen wollen.

4. Wenn Sie mit dem Hinzufügen von Benutzern fertig sind, wählen Sie **Speichern aus.**

## <a name="assign-a-policy-package-to-a-group"></a>Ein Richtlinienpaket einer Gruppe zuweisen

Die Gruppenzuweisung von Richtlinienpaketen ermöglicht es Ihnen, mehrere Richtlinien einer Gruppe von Benutzern wie z. B. einer Sicherheitsgruppe oder einer Verteilerliste zuzuweisen. Die Richtlinienzuweisung wird anhand von Prioritätsregeln an die Mitglieder der Gruppe weitergegeben. Wenn Mitglieder einer Gruppe hinzugefügt oder daraus entfernt werden, werden ihre geerbten Richtlinienzuweisungen entsprechend aktualisiert.

Die Zuweisung von Richtlinienpaketen zu Gruppen wird für Gruppen mit bis zu 50.000 Benutzern empfohlen, funktioniert aber auch bei größeren Gruppen.

Wenn Sie das Richtlinienpaket zuweisen, wird es der Gruppe sofort zugewiesen. Die Weitergabe der Richtlinienzuweisung an Mitglieder der Gruppe erfolgt jedoch als Hintergrundvorgang und kann je nach Größe der Gruppe einige Zeit dauern. Dasselbe gilt, wenn eine Richtlinie nicht einer Gruppe zugewiesen wird oder Mitglieder einer Gruppe hinzugefügt oder aus ihr entfernt werden.

> [!IMPORTANT]
> Bevor Sie beginnen, ist es wichtig, Rangfolgeregeln [und](#precedence-rules) Rangfolge von [Gruppenzuweisungen zu verstehen.](#group-assignment-ranking) Lesen und verstehen Sie die Konzepte in [Wichtige](#what-you-need-to-know-about-policy-assignment-to-groups) Informationen zur Richtlinienzuweisung für Gruppen weiter oben in diesem Artikel.

### <a name="assign-a-policy-package-to-a-group-of-users-in-the-admin-center"></a>Zuweisen eines Richtlinienpakets zu einer Benutzergruppe im Admin Center

1. Melden Sie sich beim Microsoft Teams Admin Center an.
2. Wechseln Sie im linken Navigationsbereich zur Seite des Richtlinienpakets.
3. Wählen Sie die Registerkarte Gruppenpaketzuordnung aus.
4. Wählen **Sie Gruppe hinzufügen** aus, und gehen Sie dann im Bereich Richtlinienpaket einer Gruppe zuweisen wie folgt vor:

   - Suchen Sie nach der Gruppe, der Sie das Richtlinienpaket zuweisen möchten, und fügen Sie sie hinzu.

2. Wechseln Sie im linken Navigationsbereich zur Seite des Richtlinienpakets.

3. Wählen Sie die Registerkarte Gruppenrichtlinienzuordnung aus.

4. Wählen **Sie Gruppe hinzufügen** aus, und gehen Sie dann im Bereich Richtlinienpaket einer Gruppe zuweisen wie folgt vor:

    1. Suchen Sie nach der Gruppe, der Sie das Richtlinienpaket zuweisen möchten, und fügen Sie sie hinzu.
    
    1. Wählen Sie ein Richtlinienpaket aus.
    
    1. Legen Sie die Rangfolge für jeden Richtlinientyp an.
    
    1. Wählen Sie **Übernehmen aus.**
    
    ![Zeigt die Gruppenrichtlinienzuordnung an.](media/group-pkg-assignment.png)

5. Um die Rangfolge für einen bestimmten Richtlinientyp zu verwalten, navigieren Sie zur jeweiligen Richtlinienseite.

6. Wenn Sie ein Richtlinienpaket einer Gruppe erneut zuweisen möchten, entfernen Sie zuerst die Gruppenrichtlinienzuweisung. Führen Sie dann die vorstehenden Schritte aus, um das Richtlinienpaket einer Gruppe zuzuordnen.

### <a name="work-with-powershell"></a>Arbeiten mit PowerShell

#### <a name="get-the-teams-powershell-module"></a>Holen Sie sich Teams PowerShell-Modul

Eine schrittweise Anleitung finden Sie unter Installieren [Teams PowerShell.](teams-powershell-install.md)

#### <a name="assign-a-policy-package-to-a-group-of-users"></a>Zuweisen eines Richtlinienpakets zu einer Benutzergruppe

Verwenden Sie das [Cmdlet Grant-CsGroupPolicyPackageAssignment,](/powershell/module/teams/grant-csgrouppolicypackageassignment) um einer Gruppe ein Richtlinienpaket zuzuweisen. Sie können eine Gruppe mit der Objekt-ID, der SIP-Adresse oder der E-Mail-Adresse angeben. Wenn Sie das Richtlinienpaket zuweisen, geben Sie eine [Gruppenzuordnungsrangfolge](#group-assignment-ranking) für jeden Richtlinientyp im Richtlinienpaket an.

In diesem Beispiel weisen wir das Education_Teacher-Richtlinienpaket einer Gruppe mit der Zuordnungsrangfolge 1 für TeamsAppSetupPolicy und TeamsMeetingBroadcastPolicy und der Rangfolge 2 für TeamsMeetingPolicy zu.

```powershell
Grant-CsGroupPolicyPackageAssignment -GroupId "dae90bb4-120f-4a3e-a15d-30f142e79f69" -PackageName "Education_Teacher" -PolicyRankings "TeamsAppSetupPolicy, 1", "TeamsMeetingBroadcastPolicy, 1", "TeamsMeetingPolicy, 2"
```

## <a name="assign-a-policy-package-to-a-batch-of-users"></a>Zuweisen eines Richtlinienpakets zu einer Gruppe von Benutzern

Mit der Batchrichtlinienpaketzuordnung können Sie großen Gruppen von Benutzern gleichzeitig ein Richtlinienpaket zuweisen, ohne ein Skript verwenden zu müssen. Sie verwenden das [Cmdlet New-CsBatchPolicyAssignmentOperation,](/powershell/module/teams/new-csbatchpolicyassignmentoperation) um eine Gruppe von Benutzern und das Richtlinienpaket zu übermitteln, das Sie zuweisen möchten. Die Zuweisungen werden als Hintergrundvorgänge verarbeitet, und für jeden Batch wird eine Vorgangs-ID generiert. Anschließend können Sie das [Cmdlet Get-CsBatchPolicyAssignmentOperation](/powershell/module/teams/get-csbatchpolicyassignmentoperation) verwenden, um den Fortschritt und Status der Zuordnungen in einem Stapel nachverfolgt.

Geben Sie Benutzer nach ihrer Objekt-ID oder der SIP-Adresse (Session Initiation Protocol) an. Die SIP-Adresse eines Benutzers hat häufig den gleichen Wert wie der Benutzerprinzipalname (User Principal Name, UPN) oder die E-Mail-Adresse, aber dies ist nicht erforderlich. Wenn ein Benutzer mit dem UPN oder der E-Mail-Adresse angegeben wird, aber einen anderen Wert als seine SIP-Adresse hat, kann die Richtlinienzuweisung für den Benutzer nicht ausgeführt werden. Wenn ein Batch doppelte Benutzer enthält, werden die Duplikate vor der Verarbeitung aus dem Batch entfernt, und der Status wird nur für die im Batch verbleibenden eindeutigen Benutzer bereitgestellt.

Ein Batch enthält bis zu 5.000 Benutzer. Um optimale Ergebnisse zu erzielen, übermitteln Sie nicht mehr als ein paar Batches gleichzeitig. Lassen Sie die Verarbeitung von Batches abschließen, bevor Sie weitere Batches übermitteln.

### <a name="use-the-teams-powershell-module"></a>Verwenden des Teams PowerShell-Moduls

Führen Sie Folgendes aus, um [das Microsoft Teams PowerShell-Modul](https://www.powershellgallery.com/packages/MicrosoftTeams) zu installieren (sofern noch nicht vorhanden). Vergewissern Sie sich, dass Sie Version 1.0.5 oder höher installieren.

```powershell
Install-Module -Name MicrosoftTeams
```

Führen Sie die folgenden Schritte aus, um Teams Verbindung herzustellen und eine Sitzung zu starten.

```powershell
Connect-MicrosoftTeams
```

Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihren Administratoranmeldeinformationen an.

### <a name="assign-policy-packages-to-a-batch-of-users"></a>Zuweisen von Richtlinienpaketen zu einer Gruppe von Benutzern

In diesem Beispiel verwenden wir das [Cmdlet New-CsBatchPolicyAssignmentOperation,](/powershell/module/teams/new-csbatchpolicyassignmentoperation) um das Education_PrimaryStudent-Richtlinienpaket einer Gruppe von Benutzern zuzuweisen.

```powershell
New-CsBatchPolicyPackageAssignmentOperation -Identity 1bc0b35f-095a-4a37-a24c-c4b6049816ab,user1@econtoso.com,user2@contoso.com -PackageName Education_PrimaryStudent
```

### <a name="see-the-status-of-a-batch-assignment"></a>Anzeigen des Status einer Batchzuordnung

Führen Sie die folgenden Schritte aus, um den Status einer Batchzuordnung zu erhalten. Dabei steht "OperationId" für die Vorgangs-ID, die vom Cmdlet für einen bestimmten `New-CsBatchPolicyAssignmentOperation` Batch zurückgegeben wird.

```powershell
Get-CsBatchPolicyAssignmentOperation -OperationId f985e013-0826-40bb-8c94-e5f367076044 | fl
```

Wenn die Ausgabe zeigt, dass ein Fehler aufgetreten ist, führen Sie die folgenden Schritte aus, um weitere Informationen zu Fehlern zu erhalten, die sich in der -Eigenschaft `UserState` befinden.

```powershell
Get-CsBatchPolicyAssignmentOperation -OperationId f985e013-0826-40bb-8c94-e5f367076044 | Select -ExpandProperty UserState
```

Weitere Informationen finden Sie unter [Get-CsBatchPolicyAssignmentOperation.](/powershell/module/teams/get-csbatchpolicyassignmentoperation)

## <a name="related-topics"></a>Verwandte Themen

[Übersicht über PowerShell für Microsoft Teams](teams-powershell-overview.md)
