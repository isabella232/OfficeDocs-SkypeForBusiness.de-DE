---
title: Bereitstellen Microsoft Teams-Räume Apps unter Android
ms.author: mitressl
author: flinchbot
manager: serdars
audience: ITPro
ms.reviewer: payurevi
ms.topic: quickstart
ms.service: msteams
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
ms.custom: ''
ms.assetid: 678689e4-d547-499b-be64-7d8f16dd8668
description: In diesem Artikel erfahren Sie, wie Sie Apps Microsoft Teams-Räume Android bereitstellen.
ms.openlocfilehash: 4ac068e008b53882dceba5f4ceef6e730a47b3f3
ms.sourcegitcommit: efd56988b22189dface73c156f6f8738f273fa61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2021
ms.locfileid: "60011709"
---
# <a name="deploy-microsoft-teams-rooms-on-android"></a>Bereitstellen Microsoft Teams-Räume Apps unter Android

Die Bereitstellung Microsoft Teams-Räume Android-Geräten kann in die folgenden Phasen aufgeschlüsselt werden:

- **Websitebereitschaft** Vergewissern Sie sich, dass Ihre Bereitstellungsstandorte (Räume) den Bereitstellungsanforderungen entsprechen.
- **Dienstbereitschaft** Erstellen Sie Ressourcenkonten, und weisen Sie sie den Geräten zu (siehe Erstellen eines [Ressourcenkontos](resource-account-ui.md)mit Microsoft 365 Admin Center ). Es wird zwar empfohlen, eine dedizierte Raumlizenz zu verwenden, aber ein ordnungsgemäß lizenziertes Endbenutzerkonto kann sich auch unter Android Teams-Räume anmelden.
- **Konfiguration und Bereitstellung** Richten Sie Teams-Räume ein, und verbinden Sie die benötigten Peripheriegeräte (Details finden Sie in der Dokumentation des Herstellers).

Zum Verwalten Teams-Räume müssen Sie ein globaler Administrator, Teams Dienstadministrator oder Teams geräteadministrator sein. Weitere Informationen zu Administratorrollen finden Sie unter Verwenden [Microsoft Teams zum Verwalten von Teams.](../using-admin-roles.md)

## <a name="site-readiness"></a>Websitebereitschaft

Während die bestellten Geräte an Ihre Organisation übermittelt werden, arbeiten Sie mit Ihren Netzwerken, Einrichtungen und audio-visuellen Teams zusammen, um sicherzustellen, dass die Bereitstellungsanforderungen erfüllt sind und jede Website und jeder Raum hinsichtlich Leistung, Netzwerk und Anzeige bereit ist.

Unsere Empfehlungen für Websites auf der Zusammenarbeitsleiste sind:

- Räume mit einer Größe von bis zu 5 Personen
- Dedizierte Ressourcenkonten
- Bildschirme mit Touch-Funktion
- Ethernet-Verkabelung
- Im Netzwerk für Medien aktivierte Quality of Service (QoS) Microsoft Teams Medien

Überlegungen zur physischen Installation finden Sie in der Dokumentation des Herstellers. Falls sie vorhanden sind, nutzen Sie die Erfahrung Ihres Audio-Visual-Teams, bevor Sie Bildschirme installieren und einhängen und die Verkabelung ausführen.

> [!TIP]
> Lesen Sie vorbereiten Ihres Netzwerks für die [Teams](../prepare-network.md) für die Bandbreitenplanung und bewerten Sie die Eignung Ihres Netzwerks für Echtzeitdatenverkehr.
>
> Wir raten von der Platzierung von Proxyservern zwischen Teams und dem Internet ab. Weitere Informationen zu Proxyservern und Teams finden Sie unter [Proxyserver für Teams.](../proxy-servers-for-skype-for-business-online.md)

|&nbsp;|&nbsp;|
|-----------|------------|
| ![Ein Symbol, das Entscheidungspunkte darstellt.](../media/audio_conferencing_image7.png) <br/>Entscheidungspunkte|<ul><li>Vergewissern Sie sich, dass Ihre Websites die Anforderungen an die Websitebereitschaft für Zusammenarbeitsleisten für Microsoft Teams.</li><li>Vergewissern Sie sich, dass Sie für jeden Standort ausreichend Bandbreite bereitgestellt haben.</li></ul>|
| ![Ein Symbol, das die nächsten Schritte zeigt.](../media/audio_conferencing_image9.png)<br/>Nächste Schritte|<ul><li>Beginnen Sie mit der Planung der Bereitstellung und Konfiguration der Zusammenarbeitsleiste.</li></ul>|

## <a name="service-readiness"></a>Bereitschaft für den Dienst

Vor der Teams-Räume müssen Sie entscheiden, ob sie Microsoft 365 Ressourcenkonten, Endbenutzerkonten oder eine Mischung aus beiden verwenden. Microsoft 365 Ressourcenkonten sind Postfach- und Teams-Konten, die bestimmten Ressourcen zugeordnet sind, z. B. einem Raum, Projektor und so weiter. Diese Ressourcenkonten können automatisch mithilfe von Regeln, die Sie beim Erstellen definieren, auf Besprechungs-Einladungen antworten. Sofern Teams-Räume nur einer bestimmten Person für private Nutzung zugeordnet ist, empfehlen wir die Einrichtung eines Microsoft 365 Ressourcenkontos für dieses Konto.

### <a name="using-a-resource-account"></a>Verwenden eines Ressourcenkontos

Wenn Sie sich für die Einrichtung eines Microsoft 365 Ressourcenkontos entscheiden, müssen Sie eine Lizenz Besprechungsraum erwerben. Die Besprechungsraum enthält ein Ressourcenpostfach, mit dem Personen in Ihrer Organisation den Besprechungsraum über einen Besprechungsraum Outlook Oder Teams. Die Lizenz ermöglicht außerdem Video- und Audiokonferenzen sowie die Bildschirmfreigabe für Besprechungsteilnehmer.

Wenn Sie Anrufe bei einer externen Telefonnummer erhalten oder von einer externen Telefonnummer aus anrufen müssen, benötigen Sie möglicherweise einen Anrufplan oder [Microsoft 365 Business Voice-Add-On-Lizenz](../teams-add-on-licensing/microsoft-teams-add-on-licensing.md?tabs=small-business). Wenn Sie in Ihrer Organisation Direct-Routing aktiviert haben, benötigen Sie nur die Besprechungsraum SKU.

Wenn Sie ein Ressourcenkonto erstellen, können Sie auswählen, ob das Konto Besprechungsanfragen automatisch annehmen oder ablehnen, besprechungsserienbesprechungen zulassen, angeben soll, wie weit im Voraus Personen die Ressource buchen können, und so weiter.

[!INCLUDE [m365-teams-resource-account-difference](../includes/m365-teams-resource-account-difference.md)]

Weitere Informationen zu Ressourcenkonten Microsoft 365 Sie unter [Erstellen eines Ressourcenkontos mithilfe des -Microsoft 365 Admin Center.](resource-account-ui.md)

|&nbsp;|&nbsp;|
|-----------|------------|
| ![Ein Symbol, das Entscheidungspunkte darstellt.](../media/audio_conferencing_image7.png) <br/>Entscheidungspunkte|<ul><li>Entscheiden Sie, ob Sie externe Telefonanrufe erstellen oder empfangen möchten und welche Lizenzierungsanforderungen für Ihre Ressourcenkonten gelten sollen.</li></ul>|
| ![Ein Symbol, das die nächsten Schritte zeigt.](../media/audio_conferencing_image9.png)<br/>Nächste Schritte|<ul><li>Vorbereiten von Ressourcenkonten</li></ul>|

## <a name="configuration-and-deployment"></a>Konfiguration und Bereitstellung

Die Planung der Konfiguration und Bereitstellung umfasst die folgenden Hauptbereiche:

- Bereitstellung des Ressourcenkontos
- Gerätebereitstellung
- Teams-Räume von Anwendungen und Peripheriegeräten
-  Tests
- Postenverwaltung

### <a name="account-provisioning"></a>Kontobereitstellung

Wenn Sie planen, Microsoft 365-Ressourcenkonten zu verwenden, damit Benutzer Zusammenarbeitsbalken buchen können, folgen Sie den Anweisungen unter Erstellen eines Ressourcenkontos mit dem [Microsoft 365 Admin Center,](resource-account-ui.md) um ein Microsoft 365-Ressourcenkonto für jede Zusammenarbeitsleiste zu erstellen, für die eins benötigt wird. Hier müssen Sie auch dem Ressourcenkonto eine Besprechungsraum-Lizenz hinzufügen und, wenn Sie Anrufe an oder von externen Telefonnummern erhalten oder anrufen möchten, eine Anrufplan- oder Business Voice-Lizenz hinzufügen, wenn Ihre Organisation nicht Direct Routing verwendet.

Wenn Sie einzelnen Teams-Räume Benutzer für private Nutzung zuweisen möchten, müssen Sie keine zusätzlichen Konten einrichten. Benutzer können sich mit ihren persönlichen Konten bei zusammenarbeitsleisten anmelden.

> [!TIP]
> Sorgen Sie dafür, dass die Anzeigenamen für ihre Microsoft 365 beschreibend und leicht verständlich sind. Dies sind die Namen, die Benutzern angezeigt werden, wenn sie Nach Besprechungen suchen und Teams-Räume hinzufügen. Sie könnten eine Veranstaltung wie Websiteraumname ( Max. Raumkapazität) verwenden, also könnte Curie, ein 4-Personen-Besprechungsraum in London, beispielsweise den Anzeigenamen - LON-CURIE(4) haben.

|&nbsp;|&nbsp;|
|-----------|------------|
| ![Ein Symbol, das Entscheidungspunkte darstellt.](../media/audio_conferencing_image7.png) <br/>Entscheidungspunkte|<ul><li>Entscheiden Sie die Benennungskonvention für Ihre dedizierten Ressourcenkonten.</li><li>Entscheiden Sie, ob Sie einzelne Konten erstellen oder Massenbereitstellungsskripts verwenden möchten.</li></ul>|
| ![Ein Symbol, das die nächsten Schritte zeigt.](../media/audio_conferencing_image9.png)<br/>Nächste Schritte|<ul><li>Beginnen Sie mit der Planung der Gerätebereitstellung.</li></ul>|

### <a name="device-deployment"></a>Gerätebereitstellung

Als Nächstes müssen Sie Ihren Plan erstellen, um die Geräte und die ihnen zugewiesenen Peripheriegeräte in Ihren Räumen zu liefern, und dann mit der Installation und Konfiguration fortfahren.

|&nbsp;|&nbsp;|
|-----------|------------|
| ![Ein Symbol, das Entscheidungspunkte darstellt.](../media/audio_conferencing_image7.png) <br/>Entscheidungspunkte|<ul><li>Entscheiden Sie, wer die Bereitstellung von Website zu Website verwalten soll.</li><li> Ermitteln Sie die Ressourcen, die Die Teams-Räume auf der Website installieren sollen, und übernehmen Sie die Konfiguration und Tests.</li></ul>|
| ![Ein Symbol, das die nächsten Schritte zeigt.](../media/audio_conferencing_image9.png)<br/>Nächste Schritte|<ul><li>Starten Sie die Gerätetests.</li></ul>|

### <a name="testing"></a> Tests

Nachdem Sie ihre Teams-Räume haben, sollten Sie sie testen. Melden Sie sich bei Teams-Räume, und überprüfen Sie, ob die erwarteten Funktionen funktionieren. Es wird dringend empfohlen, zu überprüfen,  ob sie  im Abschnitt Zusammenarbeitsleisten auf der Registerkarte Teams Geräte des admin center Microsoft Teams werden. Außerdem ist es wichtig, dass Sie eine Reihe von Testanrufen und -besprechungen führen, um Qualität und Leistung zu überprüfen.

Wir empfehlen, im Rahmen des allgemeinen Microsoft Teams-Rollouts die Konfiguration von Dateien für das Anrufqualitätsdashboard (CQD) zu konfigurieren, Qualitätstrends zu überwachen und sich an der Überprüfung der Qualität der Benutzererfahrung zu beteiligen. Weitere Informationen finden Sie im [Handbuch zur Überprüfung der Benutzererfahrung.](../quality-of-experience-review-guide.md)

### <a name="asset-management"></a>Postenverwaltung

Im Rahmen der Bereitstellung sollten Sie Ihr Ressourcenregister mit dem Raumnamen, dem angemeldeten Ressourcenkonto und den zugewiesenen Peripheriegeräten aktualisieren.

## <a name="related-topics"></a>Verwandte Themen

[Konfigurieren von Konten für Microsoft Teams-Räume mithilfe Microsoft Teams Admin Centers](resource-account-ui.md)

<!-- [Configure accounts for collaboration bars for Microsoft Teams using PowerShell](resource-account-ps.md) -->