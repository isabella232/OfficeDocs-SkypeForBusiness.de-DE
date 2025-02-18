---
title: Konfigurieren von Einstellungen für Live-Ereignisse in Microsoft Teams
author: serdarsoysal
ms.author: serdars
manager: serdars
ms.date: 03/11/2019
ms.topic: article
ms.service: msteams
ms.reviewer: sonua
audience: admin
search.appverid: MET150
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365initiative-meetings
- m365initiative-meetings-enabler
- enabler-strategic
description: Erfahren Sie, wie Sie einstellungen für Teams, die in Ihrer Organisation abgehalten werden, verwalten.
f1.keywords:
- CSH
ms.custom:
- ms.teamsadmincenter.liveevents.settings
appliesto:
- Microsoft Teams
ms.openlocfilehash: d1d1608bda574e504e6985ee55c8f06607f710a4
ms.sourcegitcommit: cfc48dc03550c093c4405fb5984648188f523699
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2021
ms.locfileid: "60046041"
---
# <a name="configure-live-event-settings-in-microsoft-teams"></a>Konfigurieren von Einstellungen für Live-Ereignisse in Microsoft Teams

Verwenden Teams Einstellungen für Liveereignisse, um Einstellungen für Liveereignisse zu konfigurieren, die in Ihrer Organisation abgehalten werden. Sie können eine Support-URL einrichten und einen Drittanbieter für die Videoverteilung konfigurieren. Diese Einstellungen gelten für alle Liveereignisse, die in Ihrer Organisation erstellt werden.

Sie können diese Einstellungen ganz einfach im Microsoft Teams Admin Center verwalten. Wechseln Sie im linken Navigationsbereich **zu** Einstellungen  >  **für Liveereignisse in Besprechungen.**

![Screenshot der Teams für Liveereignisse.](../media/teams-live-events-settings-new.png "Screenshot der Teams von Liveereignissen, die Sie im Admin Center Microsoft Teams können")

## <a name="set-up-event-support-url"></a>Einrichten der URL für die Ereignisunterstützung

Diese URL wird Teilnehmern des Live-Ereignisses angezeigt. Fügen Sie die Support-URL für Ihre Organisation hinzu, damit die Teilnehmer während eines Live-Ereignisses den Support kontaktieren können.

### <a name="an-icon-showing-the-microsoft-teams-logo-using-the-microsoft-teams-admin-center"></a>![Ein Symbol mit dem Microsoft Teams Logo.](../media/teams-logo-30x30.png) Verwenden des Microsoft Teams Admin Centers

1. Navigieren Sie im linken Navigationsbereich zu Einstellungen für  >  **Liveereignis für Besprechungen.**
2. Geben **Sie unter Support-URL** die Support-URL Ihrer Organisation ein.

    ![Einstellung der Support-URL für Liveereignisse im Admin Center.](../media/teams-live-events-settings-supporturl.png "Screenshot der SUPPORT-URL-Einstellung für Teams Von Liveereignissen")

### <a name="using-windows-powershell"></a>Verwenden von Windows PowerShell

Führen Sie Folgendes aus:

```PowerShell
Set-CsTeamsMeetingBroadcastConfiguration -SupportURL “{your URL}”
```
Weitere Informationen finden Sie unter [Set-CsTeamsMeetingBroadcastConfiguration.](/powershell/module/skype/set-csteamsmeetingbroadcastconfiguration?view=skype-ps&preserve-view=true)
## <a name="configure-a-third-party-video-distribution-provider"></a>Konfigurieren eines Drittanbieters für die Videoverteilung 

Wenn Sie eine Software defined Network (SDN)-Lösung oder ECDN-Lösung (Enterprise Content Delivery Network) über einen Microsoft-Partner für die Videobereitstellung erworben und eingerichtet haben, konfigurieren Sie den Anbieter für Liveereignisse in Teams. 

### <a name="an-icon-showing-the-microsoft-teams-logo-using-the-microsoft-teams-admin-center"></a>![Ein Symbol mit dem Microsoft Teams Logo.](../media/teams-logo-30x30.png) Verwenden Microsoft Teams Admin Center

1. Navigieren Sie im linken Navigationsbereich zu Einstellungen für  >  **Liveereignis für Besprechungen.**
2. Führen **Sie unter Videoverteilungsanbieter von Drittanbietern** die folgenden Schritte aus: 

    ![Einstellungen des Drittanbieters für die Videoverteilung im Admin Center.](../media/teams-live-events-settings-distribution-provider-new.png "Screenshot der Einstellungen des Drittanbieters für die Videoverteilung für Liveereignisse")

    - **Verwenden eines Drittanbieters für die Verteilung** Aktivieren Sie diese Option, um den Drittanbieter für die Videoverteilung zu aktivieren.
    - **SDN-Anbietername** Wählen Sie den von Ihnen verwendeten Anbieter aus.
    - **SDN-Konfiguration** Geben Sie Details zur SDN-Konfiguration ein.
        
### <a name="using-windows-powershell"></a>Verwenden von Windows PowerShell
Holen Sie sich die Lizenz-ID oder das API-Token und die API-Vorlage von Ihrem Anbieterkontakt, und führen Sie dann je nach verwendeten Anbieter eine der folgenden Optionen aus:

**Hive** 
```PowerShell
Set-CsTeamsMeetingBroadcastConfiguration -AllowSdnProviderForBroadcastMeeting $True -SdnProviderName hive -SdnLicenseId {license ID GUID provided by Hive} -SdnApiTemplateUrl “{API template URL provided by Hive}”
```
**Kollective** 
```PowerShell
Set-CsTeamsMeetingBroadcastConfiguration -AllowSdnProviderForBroadcastMeeting $True -SdnProviderName kollective -SdnApiTemplateUrl "{API template URL provided by Kollective}" -SdnApiToken {API token GUID provided by Kollective}
```
**Riverbed** 
```PowerShell
Set-CsTeamsMeetingBroadcastConfiguration -AllowSdnProviderForBroadcastMeeting $True -SdnProviderName riverbed -SdnApiTemplateUrl "{API template URL provided by Riverbed}" -SdnApiToken {API token GUID provided by Riverbed}
```
**Ramp** 
```PowerShell
Set-CsTeamsMeetingBroadcastConfiguration -AllowSdnProviderForBroadcastMeeting $True -SdnProviderName ramp -SdnRuntimeConfiguration "{Configuration provided by RAMP}"
```
**Peer5**
```PowerShell
Set-CsTeamsMeetingBroadcastConfiguration -AllowSdnProviderForBroadcastMeeting $True -SdnProviderName peer5 -SdnLicenseId {peer5CustomerId}
```

Weitere Informationen finden Sie unter [Set-CsTeamsMeetingBroadcastConfiguration.](/powershell/module/skype/set-csteamsmeetingbroadcastconfiguration?view=skype-ps&preserve-view=true)

> [!NOTE]
> Wenn Sie planen, Liveereignisse mithilfe einer externen App oder eines externen Geräts zu erstellen, müssen Sie auch Ihren [eCDN-Anbieter](/stream/network-caching)mit Microsoft Stream konfigurieren. 

>[!Note]
> Der Wechsel von Microsoft Stream zu [OneDrive for Business und SharePoint für Besprechungsaufzeichnungen](../tmr-meeting-recording-change.md) erfolgt schrittweise. Beim Start können Sie sich für diese Umgebung entscheiden. Sie müssen sich im November abmelden, wenn Sie Stream weiterhin verwenden möchten. Anfang 2021 müssen alle Kunden OneDrive for Business und SharePoint für neue Besprechungsaufzeichungen verwenden.

>[!Note]
> Die von Ihnen ausgewählte eCDN-Lösung unterliegt den Nutzungsbedingungen und Datenschutzrichtlinien des ausgewählten Drittanbieters, die ihre Verwendung der Lösung des eCDN-Anbieters regeln. Ihre Verwendung der Lösung des eCDN-Anbieters unterliegt nicht den Microsoft-Volumenlizenzbedingungen oder den Bedingungen für Onlinedienste. Wenn Sie den Bedingungen des Drittanbieters nicht zustimmen, aktivieren Sie die eCDN-Lösung in Microsoft Teams.

### <a name="related-topics"></a>Verwandte Themen
- [Was sind Teams-Liveereignisse?](what-are-teams-live-events.md)
- [Planen von Teams-Liveereignissen](plan-for-teams-live-events.md)
- [Einrichten von Teams-Liveereignissen](set-up-for-teams-live-events.md)
