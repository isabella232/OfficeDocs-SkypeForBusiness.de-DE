---
title: Aufzeichnungsrichtlinien für Liveereignisse
author: cichur
ms.author: v-cichur
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: christi.balaki
audience: admin
search.appverid: MET150
f1.keywords:
- CSH
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
description: Hier finden Sie Informationen zu Richtlinien für die Aufzeichnung von Liveereignisen.
appliesto:
- Microsoft Teams
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: bd9f800ed85d994f797c5e49d64ae0e84f90885c
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58613454"
---
# <a name="live-event-recording-policies-in-microsoft-teams"></a>Richtlinien für die Aufzeichnung von Liveereignisen in Microsoft Teams

Es gibt mehrere Optionen zum Aufzeichnen eines Microsoft Teams Live-Ereignisses. Die Aufzeichnungsoptionen werden mithilfe von Aufzeichnungsrichtlinien festgelegt. In diesem Artikel werden die verschiedenen Einstellungen beschrieben.

Die Aufzeichnungsoptionen werden mit dem [PowerShell-Befehl Set-CsTeamsMeetingBroadcastPolicy festgelegt.](/powershell/module/skype/set-csteamsmeetingbroadcastpolicy)

## <a name="scheduling-and-option-behaviors"></a>Terminplanung und Optionsverhalten

Beim Planen einer Liveereignisaufzeichnung gibt es zwei Organisatoroptionen:

- Aufzeichnung für Produzenten und Moderatoren verfügbar

  - Aufzeichnungsdatei: Stellt eine Aufzeichnungsdatei bereit, die Produzenten und Moderatoren herunterladen können, nachdem das Ereignis vorbei ist.

- Aufzeichnung für Teilnehmer verfügbar

  - DVR: Ein digitaler Videorekorder (DVR) ermöglicht Teilnehmern das Zurückspulen und Anhalten während des Ereignisses.

  - VOD: Ein Video auf Abruf (VoD) ermöglicht Teilnehmern, das Ereignis nach dem Ende des Ereignisses zu verfolgen.

## <a name="broadcast-recording-policy-setting"></a>Richtlinieneinstellung für Aufzeichnung übertragen

Im Rahmen der Übertragungsrichtlinie gibt es eine Einstellung, mit der Sie die Aufzeichnung für ein Liveereignis aktivieren oder deaktivieren können.

| &nbsp;| Aufzeichnung für Produzenten und Moderatoren verfügbar | Aufzeichnung für Teilnehmer verfügbar |
| ------------------------------- | ---------------------------------------------------- | ------------------------------------- |
| Immer aufzeichnen               | Deaktiviert und ausgewählt                                | Aktiviert und ausgewählt         |
| Organisator kann Aufzeichnen oder nicht | Standardmäßig aktiviert und ausgewählt                  | Standardmäßig aktiviert und ausgewählt   |
| Nie aufzeichnen               | Deaktiviert und nicht ausgewählt                            | Deaktiviert und nicht ausgewählt      |

## <a name="storage-and-persistence-behavior"></a>Storage und Persistenzverhalten

| Option                                       | Status   | DVR                                                   | VOD                                                     | Aufzeichnung läuft                |
| ------------------------------------------------ | ------------ | --------------------------------------------------------- | ----------------------------------------------------------- | ---------------------------- |
| Aufzeichnung für Teilnehmer verfügbar | Ausgewählt     | DVR ist verfügbar, und Azure Media Services (AMS)-Ressource wird 180 Tage lang gespeichert. | Teilnehmer können auf das Ereignis zugreifen und es anschauen                     |                              |
|                                                  | Nicht ausgewählt | DVR ist verfügbar, und die AMS-Ressource wird 180 Tage lang gespeichert. | Teilnehmer erhalten keinen Zugriff auf das Ereignis, nachdem es vorbei ist |                              |
||Deaktiviert (Nicht ausgewählt)|DVR ist verfügbar, und die AMS-Ressource wird nach dem -Ereignis gelöscht.|Teilnehmer erhalten keinen Zugriff auf das Ereignis, nachdem es vorbei ist||
| Aufzeichnung für Produzenten und Moderatoren verfügbar | Ausgewählt     |                                                           |                                                             | Eine MP4-Datei wird erstellt und gespeichert. |
|                                                  | Nicht ausgewählt |                                                           |                                                             | Es wird keine Datei erstellt           |

### <a name="related-topics"></a>Verwandte Themen

- [Was sind Teams-Liveereignisse?](what-are-teams-live-events.md)
- [Planen von Teams-Liveereignissen](plan-for-teams-live-events.md)
- [Konfigurieren der Einstellungen für Liveereignisse in Teams](configure-teams-live-events.md)
- [Teams Besprechungsaufzeichnung mit Wolken](../cloud-recording.md)
