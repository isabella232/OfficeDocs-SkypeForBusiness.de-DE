---
title: Teamvorlagen für kleine und mittelständische Unternehmen, die mit Microsoft Graph
author: serdarsoysal
ms.author: serdars
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: msteams
search.appverid: MET150
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
f1.keywords:
- NOCSH
appliesto:
- Microsoft Teams
ms.reviewer: lavenkat
description: Verwenden Microsoft Teams vordefinierten Vorlagen, die in Microsoft Graph, um schnell und einfach Teams für kleine und mittelständische Unternehmen zu erstellen.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 324470ffc3366750777c75776e4ae4e783dbb17f
ms.sourcegitcommit: cfc48dc03550c093c4405fb5984648188f523699
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2021
ms.locfileid: "60045681"
---
# <a name="team-templates-built-in-microsoft-graph-for-small-and-medium-businesses"></a>In Microsoft Graph für kleine und mittelständische Unternehmen integrierte Teamvorlagen

Mit Teamvorlagen in Microsoft Teams können Sie schnell und einfach Teams erstellen, indem Sie eine vordefinierte Teamstruktur aus Einstellungen, Kanälen und vorinstallierten Apps bereitstellen.

Für kleine und mittelständische Unternehmen können Vorlagen besonders leistungsfähig sein, da sie Ihnen helfen, Ihre Teams schnell zu implementieren. Vorlagen helfen Benutzern auch dabei, sich mit der effektiven Verwendung von Daten zu Teams. Dieser Artikel ist für Sie da, wenn Sie für die Planung, Bereitstellung und Verwaltung mehrerer Teams in der gesamten Organisation verantwortlich sind.

Wir bieten derzeit drei vordefinierte Vorlagen für kleine und mittelständische Unternehmen, die Sie in verschiedenen Situationen verwenden können. Mit allen Vorlagen werden *private Teams* erstellt. Nachdem Sie die Teams erstellt haben und bereit für das Rollout in Ihrer Organisation sind, können Sie den Datenschutz nach Ihren Anforderungen auf *Organisationsweit* oder öffentlich festlegen.

Weitere allgemeine Informationen zu Teamvorlagen finden Sie unter Erste Schritte [mit Teamvorlagen mit Microsoft Graph.](get-started-with-teams-templates.md)

## <a name="company-wide-template"></a>Company-Wide vorlage

Die Company-Wide-Vorlage ist für die Kommunikation und Zusammenarbeit im gesamten Unternehmen gedacht. Sie können den Kanal Allgemein für unternehmensweite Ankündigungen, Branchennachrichten oder Beiträge von Führungskräften verwenden. Der Kanal "Personalwesen" ist ein hervorragender Ort zum Konsolidieren aller personalbezogenen Aktivitäten wie Stellenangebote, Onboarding neuer Mitarbeiter, Schulungen und Entwicklung. Der Kanal "Lustiges" bietet eine soziale Plattform für alle zufälligen und lustigen Beiträge.

| Vorlagentyp  | TemplateId | Eigenschaften, die mit dieser Vorlage geliefert werden |
| :------------------ | :-------------- | :----------------------------------------------------- | 
| SMB - <br>Unternehmensweit | `https://graph.microsoft.com/beta/`<br>` teamsTemplates('SmallBusinessOrgWide')`| Kanäle <ul><li>Allgemein\*</li><li>Personalwesen\*</li><li>Lustiges\*</li></ul><br> Apps<ul><li>Unternehmensportal (Website, die an den Kanal "Personalwesen" **angeheftet** ist) </li> </UL><br>Teameigenschaften <ul><li>Teamsichtbarkeit auf Privat gesetzt</li></ul> |

*Automatisch als Favoriten gekennzeichnete Kanäle 

Um das Team Company-Wide erstellen, indem Sie die Standardeinstellungen aus der vordefinierten Vorlage verwenden, stellen Sie die JSON-Darstellung des Teamobjekts im Anforderungstext fest. Weitere Informationen zum Bereitstellen von Teamvorlagen finden Sie im Microsoft Graph [zum Erstellen eines Teams.](/graph/api/team-post?view=graph-rest-beta)

#### <a name="request"></a>Anforderung 
```http 
POST https://graph.microsoft.com/beta/teams 
Content-Type: application/json 
{
    "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates('SmallBusinessOrgWide')",
    "displayName": "Org-wide",
    "description": "All posts that are relevant for entire company (e.g. Company-wide announcements, Exec posts, employee poll/feedback).",
    "visibility": "Private"
}
```

## <a name="executive-team-template"></a>Vorlage für das Executive Team

Die Vorlage für das Führungsteam eignet sich ideal für die Erstellung eines Teams für Unternehmensleiter, das Unternehmensinitiativen wie jährliche Prioritäten, Finanzbudgets, strategische Initiativen und die wichtigsten Kunden kommunizieren und zusammenarbeiten soll. Diese Vorlage enthält einen privaten *Kanal* zum Einladen ausgewählter Benutzer zu bestimmten Themen.

| Vorlagentyp  | TemplateId | Eigenschaften, die mit dieser Vorlage geliefert werden |
| :------------------ | :-------------- | :----------------------------------------------------- | 
| SMB - <br>Executives Team | `https://graph.microsoft.com/beta/`<br>` teamsTemplates('SmallBusinessExecutive')` | Kanäle <ul><li>Allgemein\*</li><li>Privat \*</li></ul> Apps<ul><li>OneNote (an den privaten Kanal **angeheftet)**</li> <li>Planner (an den privaten Kanal **angeheftet)** </li></ul><br>Teameigenschaften <ul><li>Teamsichtbarkeit auf Privat gesetzt</li></ul> | 

*Automatisch als Favoriten gekennzeichnete Kanäle<br>

Um das Executives-Team durch Verwenden der Standardeinstellungen aus der vordefinierten Vorlage zu erstellen, stellen Sie die JSON-Darstellung des Teamobjekts im Anforderungstext zur Verfügung. Weitere Informationen zum Bereitstellen von Teamvorlagen finden Sie im Microsoft Graph [zum Erstellen eines Teams.](/graph/api/team-post?view=graph-rest-beta)

#### <a name="request"></a>Anforderung 
```http 
POST https://graph.microsoft.com/beta/teams 
Content-Type: application/json 
{
    "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates('SmallBusinessExecutive')",
    "displayName": "Executive",
    "description": "All posts, announcements and daily collaboration and communication for the company's leadership team.",
    "visibility": "Private"
}
```

## <a name="departmental-team-template"></a>Vorlage für Abteilungsteam

Die Vorlage für ein Abteilungsteam kann zum Erstellen eines Teams für einzelne Abteilungen oder für Projekte verwendet werden. Die Vorlage für das Finanzteam eignet sich ideal für alle Beiträge, Ankündigungen sowie die tägliche Zusammenarbeit und Kommunikation innerhalb der Teammitglieder des Finanzteams und der Geschäftsleitung nach Wunsch. Die Vorlage enthält einen privaten *Kanal,* über den ausgewählte Benutzer zu bestimmten Themen eingeladen werden können.

Darüber hinaus stellen wir das nachstehende Skript für das Finanzteam zur Verfügung, mit dem die Vorlage auf weitere Abteilungen oder bestimmte Projekte erweitert werden kann, indem Sie Ihren Wünschen hinzufügen, löschen oder bearbeiten. Wenn Sie z. B. über eine *Marketingabteilung* verfügen, kann das Skript  angepasst werden, indem das Team von "Finanzen" in *"Marketing"* umbenennt wird, um ein neues Marketingteam zu erstellen.

| Vorlagentyp | TemplateId | Eigenschaften, die mit dieser Vorlage geliefert werden |
|:------------------ | :-------------- | :----------------------------------------------------- | 
| SMB - <br>Finanzen  | `https://graph.microsoft.com/beta/`<br>` teamsTemplates('SmallBusinessFinance')`| Kanäle <ul><li>Allgemein\*</li><li>Privat \*</li></ul><br> Apps<ul><li>OneNote (an den privaten Kanal **angeheftet)**</li> <li>Planner (an den privaten Kanal **angeheftet)** </li> </ul><br>Teameigenschaften <ul><li>Teamsichtbarkeit auf Privat gesetzt</li></ul> | 

*Automatisch als Favoriten gekennzeichnete Kanäle

Um das Finanzteam unter Berücksichtigung der Standardeinstellungen aus der vordefinierten Vorlage zu erstellen, stellen Sie die JSON-Darstellung des Teamobjekts im Anforderungstext fest. Weitere Informationen zum Bereitstellen von Teamvorlagen finden Sie im Microsoft Graph [zum Erstellen eines Teams.](/graph/api/team-post?view=graph-rest-beta)

#### <a name="request"></a>Anforderung 
```http 
POST https://graph.microsoft.com/beta/teams 
Content-Type: application/json 
{
    "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates('SmallBusinessFinance')",
    "displayName": "Finance",
    "description": "All posts, announcements and daily collaboration and communication within the Finance team members (and exec team members as appropriate).",
    "visibility": "Private"
}
```

### <a name="example-finance-team-template-extension-script"></a>Beispiel: Erweiterungsskript für die Vorlage "Finance Team"

```powershell
{
  "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates('standard')",
  "displayName": "Finance",
  "description": "Finance Team",
  "channels": 
   [
        {
            "displayName": "Private",
            "isFavoriteByDefault": true,
            "description": "Invite a more select audience for specific topics.",
             "tabs": 
             [
                {
                    "teamsApp@odata.bind": "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('0d820ecd-def2-4297-adad-78056cde7c78')",
                    "name": "OneNote"
                },
                {
                    "teamsApp@odata.bind": "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.planner')",
                    "name": "Planner"
                }
            ]
        }
    ],
    "memberSettings": 
    {
        "allowCreateUpdateChannels": true,
        "allowDeleteChannels": true,
       "allowAddRemoveApps": true,
        "allowCreateUpdateRemoveTabs": true,
        "allowCreateUpdateRemoveConnectors": true
    },
    "guestSettings": 
    {
        "allowCreateUpdateChannels": false,
        "allowDeleteChannels": false
    },
    "funSettings": 
    {
        "allowGiphy": true,
        "giphyContentRating": "Moderate",
        "allowStickersAndMemes": true,
        "allowCustomMemes": true
    },
    "messagingSettings": 
    {
        "allowUserEditMessages": true,
        "allowUserDeleteMessages": true,
        "allowOwnerDeleteMessages": true,
        "allowTeamMentions": true,
        "allowChannelMentions": true
    },
    "discoverySettings": 
    {
        "showInTeamsSearchAndSuggestions": true
    },
    "installedApps": 
    [
        {
            "teamsApp@odata.bind": "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('0d820ecd-def2-4297-adad-78056cde7c78')"
        },
        {
            "teamsApp@odata.bind": "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.planner')"
        }
    ]
}

```

## <a name="related-topics"></a>Verwandte Themen

- [Erste Schritte mit Teamvorlagen im Microsoft Teams Admin Center](get-started-with-teams-templates-in-the-admin-console.md)
- [Erste Schritte mit Teamvorlagen mittels Microsoft Graph](get-started-with-teams-templates.md)
- [Erstellen eines Teams](/graph/api/team-post?view=graph-rest-beta) (in der Vorschau)
