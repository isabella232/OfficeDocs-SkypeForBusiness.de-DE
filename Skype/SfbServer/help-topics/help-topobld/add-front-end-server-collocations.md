---
title: Hinzufügen von Front-End-Server-Kollokationen
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
- ms.lync.tb.AddFrontEndCollocationsPage
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.assetid: 23e3bda7-a8bf-4da4-88e5-098ae2aa268f
description: Für eine Enterprise Edition-Bereitstellung wird der A/V-Konferenzdienst mit dem Front-End-Pool verbunden. Sie können den Vermittlungsserver auch mit dem Front-End-Pool verbinden, oder Sie können ihn als eigenständigen Server bereitstellen. Der A/V-Konferenzdienst ist bei aktivierter Konferenzfunktion immer verbunden.
ms.openlocfilehash: de07dfcb547031c7edb512e6ffccfa791e5adc86
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58619911"
---
# <a name="add-front-end-server-collocations"></a>Hinzufügen von Front-End-Server-Kollokationen

Für eine Enterprise Edition-Bereitstellung wird der A/V-Konferenzdienst mit dem Front-End-Pool verbunden. Sie können den Vermittlungsserver auch mit dem Front-End-Pool verbinden, oder Sie können ihn als eigenständigen Server bereitstellen. Der A/V-Konferenzdienst ist bei aktivierter Konferenzfunktion immer verbunden.

> [!NOTE]
> Ein A/V-Konferenzdienst ist erforderlich, wenn **Konferenz** auf der Seite **Funktionen auswählen** ausgewählt wurde. Ein Front-End-Pool der Enterprise Edition verwendet einen verbundenen A/V-Konferenzdienst. Wenn die Konferenzfunktion nicht ausgewählt wurde, steht die Funktion zum Verbinden des A/V-Konferenzdiensts nicht zur Verfügung.

Sie können die Vermittlungsserverrolle auf einem Front-End-Server der Standard Edition oder in einem Front-End-Pool der Enterprise Edition ausführen. Bei Bereitstellung von direkten SIP-Verbindungen mit einem qualifizierten PSTN-Gateway (Public Switched Telephone Network), das Medienumgehung und DNS-Lastenausgleich unterstützt, ist kein eigenständiger Vermittlungsserver erforderlich. Der Grund ist, dass qualifizierte Gateways einen DNS-Lastenausgleich (Domain Name System) für einen Pool aus Vermittlungsservern implementieren und Datenverkehr von jedem Vermittlungsserver innerhalb eines Pools empfangen können. Außerdem wird empfohlen, dass Sie den Vermittlungsserver in einem Front-End-Pool verbinden, wenn Sie IP-PBXs bereitgestellt oder eine Verbindung mit dem Session Border Controller (SBC) eines Internettelefonieserveranbieters hergestellt haben, solange eine der folgenden Bedingungen erfüllt ist:

- Die IP-Nebenstellenanlage oder der SBC ist für den Empfang von Datenverkehr von einem beliebigen Vermittlungsserver in dem Pool konfiguriert und kann Datenverkehr einheitlich an alle Vermittlungsserver im Pool weiterleiten.

- Die IP-Nebenstellenanlage oder der SBC ist für den Empfang von Datenverkehr von einem beliebigen Vermittlungsserver in dem Pool konfiguriert und kann Datenverkehr einheitlich an alle Vermittlungsserver im Pool weiterleiten.

Sie können das Microsoft Lync Server 2013-Planungstool verwenden, um zu bewerten, ob der Front-End-Pool, in dem Sie den Vermittlungsserver verbinden möchten, die Last verarbeiten kann. Falls diese Anforderungen in Ihrer Umgebung nicht erfüllt sind, müssen Sie einen eigenständigen Vermittlungsserverpool bereitstellen.

Im Allgemeinen wird die Verbindung des Vermittlungsservers nicht empfohlen, wenn in Ihrer Organisation hohe Anforderungen an Verfügbarkeit und Skalierbarkeit gelten. Ausführliche Informationen zur Verbindung dieser Serverrollen in einem Front-End-Pool einer Enterprise Edition-Bereitstellung finden Sie unter [Define and Configure a Front End Pool](/previous-versions/office/lync-server-2013/lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server) in der Bereitstellungsdokumentation. Ausführliche Informationen zu A/V-Konferenzfunktion und -komponenten finden Sie unter [Planning for Conferencing](/previous-versions/office/lync-server-2013/lync-server-2013-planning-for-conferencing) in der Planungsdokumentation. Ausführliche Informationen zu Enterprise-VoIP Features und Komponenten, einschließlich Vermittlungsserver, finden Sie [unter Plan for Enterprise-VoIP in Skype for Business Server 2015](../../plan-your-deployment/enterprise-voice-solution/enterprise-voice.md) in der Planungsdokumentation.