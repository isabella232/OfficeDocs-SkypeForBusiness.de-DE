---
title: Legacyzusammenführung
ms.reviewer: ''
ms.author: v-cichur
author: cichur
manager: serdars
ms.date: 11/17/2018
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.tb.LegacyMergeAddPicPage
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.assetid: 085fde15-e33a-4d95-8d06-4da1d5d7c770
description: Über den externen FQDN für Webkonferenzen können externe Benutzer an lokalen Besprechungen teilnehmen. Geben Sie den vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) der externen Webkonferenzschnittstelle des Legacyedgeservers an.
ms.openlocfilehash: b0d58d900e0dcd14b947e3a6d0328a7a1edb1ff1
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58591379"
---
# <a name="legacy-merge"></a>Legacyzusammenführung

Über den externen FQDN für Webkonferenzen können externe Benutzer an lokalen Besprechungen teilnehmen. Geben Sie den vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) der externen Webkonferenzschnittstelle des Legacyedgeservers an.

Der Wert **443** des externen Ports für externe Webkonferenzen ist der für Konferenzclients konfigurierte TCP-SIP-Standardport (Transmission Control Protocol) (Session Initiation Protocol). Wenn der Standardwert nicht verwendet wurde, aktualisieren Sie diesen Wert.

Aktivieren Sie das Kontrollkästchen **Dieser Edgepool wird für den Partnerverbund und die Verbindung mit öffentlichen Instant Messaging-Diensten verwendet**, wenn dieser Edgeserver für den Partnerverbund verwendet werden soll. Bei Bereitstellung mehrerer Edgeserver wird nur einer dieser Server für den Partnerverbund aktiviert. Wenn Sie dieses Kontrollkästchen nicht aktivieren und den Partnerverbund zu einem späteren Zeitpunkt aktivieren möchten, müssen Sie den Zusammenführungs-Assistenten des Topologie-Generators erneut ausführen und Ihre Topologie veröffentlichen. Ausführliche Informationen finden Sie unter [Phase 4: Merge Topologies](/previous-versions/office/lync-server-2013/phase-4-merge-topologies).