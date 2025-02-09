---
title: Microsoft 365 und Office 365 URLs und IP-Adressbereiche
ms.reviewer: ''
author: SerdarSoysal
ms.author: serdars
manager: serdars
ms.date: 08/21/2018
ms.topic: article
audience: admin
ms.service: msteams
description: Erfahren Sie, wie Sie ordnungsgemäß Microsoft 365 oder Office 365 URLs und IP-Adressbereiche konfigurieren und den Weiterleitungsproxy nach Möglichkeit für Verbindungen mit dem Microsoft Teams umgehen.
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- CSH
ms.custom:
- ms.teamsadmincenter.meetingsettings.network.ports
- seo-marvel-mar2020
ms.collection:
- M365-collaboration
appliesto:
- Microsoft Teams
ms.openlocfilehash: ebbac20f7306aa5014aa5703a57813e3c631a9d3
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58601220"
---
# <a name="microsoft-365-and-office-365-urls-and-ip-address-ranges"></a>Microsoft 365 und Office 365 URLs und IP-Adressbereiche

Wechseln Sie zu Microsoft 365 und [Office 365-URLs](/office365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams) und IP-Adressbereiche, um eine detaillierte und aktuelle Liste der URLs, IP-Adressen, Ports und Protokolle zu erhalten, die ordnungsgemäß für den Computer konfiguriert Teams. Microsoft verbessert die Microsoft 365- und Office 365-Dienste ständig und fügt neue Funktionen hinzu. Daher können sich die erforderlichen Ports, URLs und IP-Adressen im Lauf der Zeit ändern. Es wird empfohlen, über [RSS zu abonnieren,](/office365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams) um Benachrichtigungen zu erhalten, wenn diese Informationen aktualisiert oder geändert werden.

Die Teams Anruf- und Besprechungserfahrung basiert auf der cloudbasierten Infrastruktur der nächsten Generation, die auch von Skype und Skype for Business. Zu diesen Investitionen in die Technologie gehören Azure-basierte Clouddienste für Medienverarbeitung und -signalisierung, H.264-Videocodecs, SILK- und Opus-Audiocodecs, Netzwerkresilienz, Telemetrie und Qualitätsdiagnose. Daher gibt es erforderliche URLs und IPs, die sowohl mit der Skype als Skype for Business.

Für alle Microsoft 365 und Office 365-Workloads besteht die empfohlene Verbindungsmethode für Teams-Dienste in der Umgehung des Weiterleitungsproxys nach Möglichkeit. Wenn sich ein Proxyserver zwischen einem Client und den Office 365-Rechenzentren befindet, sind Medien möglicherweise über TCP anstelle von UDP erzwungen, was sich auf die Medienqualität auswirken würde. Laden Sie Beispielproxy-PAC-Dateien herunter, die zum Konfigurieren der Datenverkehrsumgehung aus Verwalten von Microsoft 365 [und Office 365-Endpunkten verwendet werden können.](/office365/enterprise/managing-office-365-endpoints)

Wenn Ihre Netzwerk- und Sicherheitsrichtlinien einen Fluss von Microsoft 365- oder Office 365-Datenverkehr über einen Proxyserver erfordern, stellen Sie sicher, dass die oben genannten Anforderungen bereits erfüllt sind, bevor Sie Teams in der Produktion bereitstellen. Weitere Informationen finden Sie unter [Proxyserver für Teams oder Skype for Business Online.](proxy-servers-for-skype-for-business-online.md)