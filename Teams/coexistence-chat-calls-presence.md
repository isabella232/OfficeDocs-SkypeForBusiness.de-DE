---
title: Koexistenz mit Skype for Business
author: serdarsoysal
ms.author: serdars
manager: Serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: francoid
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection:
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
ms.custom: seo-marvel-mar2020
description: Koexistenzverhalten zwischen Teams & Skype for Business, einschließlich Routingparametern, Chat- & Anrufrouting, Chats & Anrufen aus bereits vorhandenen Threads, & Anwesenheitsinformationen.
ms.openlocfilehash: 5383ff8c68b8950b449b5159a530a1439156a945
ms.sourcegitcommit: 69a5d4994ef75b9c16efa99554fb7f2ee1ccf52a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2021
ms.locfileid: "58972923"
---
# <a name="coexistence-with-skype-for-business"></a>Koexistenz mit Skype for Business

Koexistenz und Interoperabilität zwischen Skype for Business und Teams-Clients und -Benutzern wird durch TeamsUpgrade-Modi definiert, die unter Migrations- und Interoperabilitätsleitfade für Organisationen, die Teams in Verbindung mit [Skype for Business.](migration-interop-guidance-for-teams-with-skype.md)

Einem bestimmten Benutzer wird immer ein TeamsUpgrade-Modus zugewiesen, entweder standardmäßig oder explizit vom Administrator. Der Standardwert ist *Inseln.* Benutzer, die ein Upgrade auf Teams haben den Modus *"TeamsOnly".* *SfBOnly,* *SfBWithTeamsCollab* und *SfBWithTeamsCollabAndMeetings* sind ebenfalls mögliche Modi.

## <a name="routing-parameters"></a>Routingparameter

Der TeamsUpgrade-Modus des Empfängers ist entscheidend bei der Bestimmung des Verhaltens von Chats, Anrufen und Anwesenheitspräsenzen, sowohl innerhalb eines Mandanten als auch innerhalb von Partner mandantenübergreifend.

Wenn der Absender eine Unterhaltung Teams, wird beim Erstellen eines neuen Unterhaltungsthreads die Routingentscheidung getroffen. Vorhandene Unterhaltungsthreads in Teams routing method always retain the routing method determined when the thread was created: Teams supports persistent threads.

 Threadroutingmethoden sind:

- *systemeigene* für eine Teams, um Teams-Mandant-Unterhaltung zu führen
- *In interop* for a Teams to Skype for business conversation in-tenant
- *Partnering* für eine mandantenübergreifend verbundene Unterhaltung

Die Parameter, die die Threadroutingmethode bestimmen, sind:

- Der TeamsUpgrade-Modus des Empfängers
- Der vom Absender verwendete Client
- Ob die Unterhaltung neu ist oder Teil eines vorhandenen Threads ist
- Ob es sich um eine Mandanten- oder Partner-Unterhaltung handelt
- Ob die Unterhaltung möglich ist
  - *In-Tenant-Interoperabilität* setzt voraus, dass der Mandant entweder online entweder rein oder Skype for Business ist. Rein lokale Mandanten können keine In-Mandant-Interoperabilität haben.
  - *Für einen mandantenübergreifenden Verbund* ist immer eine Skype for Business Verbundkonfiguration sowie eine Teams der beiden Mandanten erforderlich. Skype for Business eine Hybridlösung ist für keinen der Mandanten erforderlich.
  - Wenn das Skype for Business des Er originator lokal besend ist, kann dieser Benutzer den Teams-Client nicht für in-Mandant-Interoperabilität oder für den Verbund verwenden. Dieser Benutzer kann nur den Skype for Business für Interoperabilität und Verbund verwenden.
  - Teams, Teams Kommunikation im Mandanten immer möglich ist.

> [!NOTE]
> Wenn Empfänger und Absender beide im TeamsOnly-Upgrademodus sind, handelt es sich bei der Unterhaltung um eine systemeigene Chaterfahrung mit sämtlichen Funktionen für Nachrichten und Anrufe. Weitere Informationen finden Sie unter [Systemeigene Chaterfahrung für externe Benutzer (Partnerbenutzer) in Teams.](native-chat-for-external-users.md) Wenn sich einer der Unterhaltungsteilnehmer NICHT im TeamsOnly-Upgrademodus befindet, bleibt die Unterhaltung eine Inkonsistenzerfahrung mit Nur-Text-Nachrichten.

## <a name="chat-and-call-routing"></a>Weiterleitung von Chats und Anrufen

### <a name="in-tenant-routing-for-new-chats-or-calls"></a>Mandanten-Routing für neue Chats oder Anrufe

In den Tabellen unten wird das Routing von In-Mandant-Chats und -Anrufen erfasst. Sie gelten für neue Anrufe oder Chats, die nicht aus einem bereits vorhandenen Thread gestartet werden. Er beschreibt, welcher Client einen neuen Anruf oder Chat erhält (sofern er von einem Benutzer auf der linken Seite stammt) an einen Benutzer im Mandanten auf der rechten Seite.

An TeamsOnly-Benutzer gesendete Nachrichten werden immer an andere Teams. Nachrichten, die an SfB-Benutzer gesendet werden, werden immer Skype for Business, wenn die Unterhaltung wie oben \* beschrieben möglich ist. An Inseln gesendete Nachrichten werden immer an den Client geroutet, von dem aus sie gesendet wurden.

In den folgenden Tabellen wird angegeben, welcher Client in einem bestimmten Modus einen Anruf vom Er originator erhält (drei Spalten ganz links), je nach Modus des Erzählers, ausgewählter Client und dem Ort, an dem der Skype for Business-Client privat ist (vor Ort oder online).

In den folgenden Tabellen:

- **SfB \** _ stellt einen der folgenden Modi dar: _SfBOnly*, *SfBWithTeamsCollab,* *SfBWithTeamsCollabAndMeetings*.
- *Der italische Text* hebt eine Inaktivität hervor.
- **Nicht möglich** steht für eine Situation, in der der Chat oder Anruf nicht möglich ist. Der Erzähler muss stattdessen Skype for Business in diesen Fällen verwenden. Dies ist einer der Gründe, warum die präskriptive Anleitung von Microsoft für lokale/hybride Kunden die Verwendung eines anderen Modus als Islands (normalerweise SfBWithTeamsCollab) als Ausgangspunkt ihres Upgradewegs zu Teams.

#### <a name="table-1a-in-tenant-new-chat-or-call-routing-to-an-islands-mode-recipient"></a>Tabelle 1a: Routing neuer Chats oder Anrufe im Mandanten an einen Empfänger im Islands-Modus

<br>

|<br><br>Modus|Originator<br><br>Client|<br><br>SfB &nbsp; homed|<br><br>Route->|Empfänger<br><br>Inselmodus|
|---|---|---|:---:|---|
|Inselmodus|Microsoft Teams <br> Skype for Business <br> Microsoft Teams <br> Skype for Business|Online <br> Online<br> Vorbeh.)<br>Vorbeh.)|&boxv;<br>&boxv;<br>&boxv;<br>&boxv;|Microsoft Teams <br> Skype for Business <br> Microsoft Teams <br> Skype for Business|
|SfB\*|Skype for Business <br>Skype for Business|Online <br> Vorbeh.)|&boxv;<br>&boxv;|Skype for Business <br> Skype for Business|
|TeamsOnly|Teams|Online|&boxv;|Teams|
||||||

#### <a name="table-1b-in-tenant-new-chat-or-call-routing-to-a-recipient-in-an-sfb-mode"></a>Tabelle 1b: Routing neuer Chats oder Anrufe in Mandanten an einen Empfänger im \* SfB-Modus

<br>

|<br><br>Modus|Originator<br><br>Client|<br><br>SfB &nbsp; homed|<br><br>Route->|Empfänger<br><br>SfB\*|
|---|---|---|:---:|---|
|Inselmodus|Microsoft Teams <br> Skype for Business <br> Microsoft Teams <br> Skype for Business|Online <br> Online <br> Vorbeh.) <br> Vorbeh.)|&boxv;<br>&boxv;<br>&boxv;<br>&boxv;|*Skype for Business* <br> Skype for Business <br> **Nicht möglich** <br> Skype for Business|
|SfB\*|Skype for Business <br> Skype for Business|Online <br> Vorbeh.)|&boxv;<br>&boxv;|Skype for Business <br> Skype for Business|
|TeamsOnly|Teams|Online|&boxv;|*Skype for Business*|
||||||

#### <a name="table-1c-in-tenant-new-chat-or-call-routing-to-a-teamsonly-mode-recipient"></a>Tabelle 1c: Routing neuer Chats oder Anrufe in Mandanten an einen TeamsOnly-Modusempfänger

<br>

|<br><br>Modus|Originator<br><br>Client|<br><br>SfB &nbsp; homed|<br><br>Route->|Empfänger<br><br>TeamsOnly|
|---|---|---|:---:|---|
|Inselmodus|Microsoft Teams <br> Skype for Business <br> Microsoft Teams <br> Skype for Business|Online <br> Online <br> Vorbeh.) <br> Vorbeh.)|&boxv;<br>&boxv;<br>&boxv;<br>&boxv;|Teams <br> *Microsoft Teams* <br> Microsoft Teams <br> *Microsoft Teams*|
|SfB\*|Skype for Business <br> Skype for Business|Online <br> Vorbeh.)|&boxv;<br>&boxv;|*Microsoft Teams* <br> *Microsoft Teams*|
|TeamsOnly|Teams|Online|&boxv;|Teams|
||||||

### <a name="federated-routing-for-new-chats-or-calls"></a>Verbundrouting für neue Chats oder Anrufe

In den Tabellen unten wird das Routing von Partneranrufen und Chats erfasst, die für neue Anrufe oder Chats gültig sind. Sie beschreiben, welcher Client einen neuen Anruf oder Chat erhält (falls er von einem Benutzer auf der linken Seite stammt) an einen Partnerzielbenutzer auf der rechten Seite.

Zusammenfassung: Wenn die Unterhaltung wie oben beschrieben möglich ist, werden Nachrichten, die an Teams Gesendete Benutzer gesendet werden, immer Teams; An SfB-Benutzer gesendete Nachrichten landen immer in Skype for Business. Nachrichten, die an Islands-Benutzer gesendet wurden, werden immer in Skype for Business landen, unabhängig vom Client, von dem aus sie \* gesendet wurden. Das Routing für Partnerchats und Anrufe unterscheidet sich von der In-Tenant-Weiterleitung, da Islands-Benutzer in einer Partnerkommunikation immer eine Skype for Business.

Der Grund dafür ist, dass wir nicht davon ausgehen können, dass ein Partner Skype for Business Partner bereits eine Teams verwendet, wenn er sich im Islands-Modus befindet. Inseln ist der Standardmodus, es kann jedoch nicht davon ausgegangen werden, dass alle Benutzer der Inseln Teams. Durch das Routing an Skype for Business stellen wir sicher, dass keine Kommunikation mit einem Islands-Benutzer fehlschlägt. Wenn die Route zu Teams wurde, könnte diese Kommunikation verpasst werden, wenn das Ziel keine Daten Teams. Das Routing an Skype for Business stellt sicher, dass die Nachricht immer empfangen wird.

> [!NOTE]
> Die aktuelle Implementierung des Teams-Verbunds basiert auf einem Skype for Business-Verbund und nutzt daher die Interoperabilitätsinfrastruktur (bei der der Mandant des Erherkunfts entweder als reine Online- oder Skype for Business-Hybridbereitstellung verwendet werden muss) und bietet im Vergleich zu einem systemeigenen Thread einen reduzierten Satz an Funktionen. Wir erwarten, in Zukunft systemeigene Teams für Teams-Verbund bereitstellen zu können. Zu diesem Zeitpunkt ist der Thread systemeigene und bietet vollständige Funktionen.

In den nachfolgenden Tabellen wird beschrieben, welcher Client einen Anruf vom Er originator erhält (drei Spalten ganz links), je nach Modus des Erzählers, ausgewählter Client und wo der Skype for Business-Client privat ist (vor oder online).

#### <a name="table-2a-federated-new-chat-or-call-routing-to-an-islands-recipient"></a>Tabelle 2a: Routing neuer Chats oder Anrufe im Partnering an einen Islands-Empfänger

<br>

|<br><br>Modus|Originator<br><br>Client|<br><br>SfB homed|<br><br>Route->|Empfänger<br><br>Inselmodus|
|---|---|---|:---:|---|
|Inselmodus|Microsoft Teams <br> Skype for Business <br> Microsoft Teams <br> Skype for Business|Online <br> Online <br> Vorbeh.) <br> Vorbeh.)|&boxv;<br>&boxv;<br>&boxv;<br>&boxv;|*Skype for Business* <br> Skype for Business <br> **Nicht möglich** <br> Skype for Business|
|SfB\*|Skype for Business <br> Skype for Business|Online <br> Vorbeh.)|&boxv;<br>&boxv;|Skype for Business <br> Skype for Business|
|TeamsOnly|Teams|Online|&boxv;|*Skype for Business*|
|||||

#### <a name="table-2b-federated-new-chat-or-call-routing-to-a-recipient-in-an-sfb-mode"></a>Tabelle 2b: Routing neuer Chats oder Anrufe im Partnering an einen Empfänger im \* SfB-Modus

<br>

|<br><br>Modus|Originator<br><br>Client|<br><br>SfB homed|<br><br>Route->|Empfänger<br><br> SfB\*|
|---|---|---|:---:|---|
|Inselmodus|Microsoft Teams <br> Skype for Business <br> Microsoft Teams <br> Skype for Business|Online <br> Online <br> Vorbeh.) <br> Vorbeh.)|&boxv;<br>&boxv;<br>&boxv;<br>&boxv;|*Skype for Business* <br> Skype for Business <br> **Nicht möglich** <br> Skype for Business|
|SfB\*|Skype for Business <br> Skype for Business|Online <br> Vorbeh.)|&boxv;<br>&boxv;|Skype for Business <br> Skype for Business|
|TeamsOnly|Teams|Online|&boxv;|*Skype for Business*|
||||||

#### <a name="table-2c-federated-new-chat-or-call-routing-to-a-teamsonly-mode-recipient"></a>Tabelle 2c: Routing neuer Chats oder Anrufe im Partnermodus an einen TeamsOnly-Modusempfänger

<br>

|<br><br>Modus|Originator<br><br>Client|<br><br>SfB homed|<br><br>Route->|Empfänger<br><br>TeamsOnly|
|---|---|---|:---:|---|
|Inselmodus|Microsoft Teams <br> Skype for Business <br> Microsoft Teams <br> Skype for Business|Online <br> Online <br> Vorbeh.) <br> Vorbeh.)|&boxv;<br>&boxv;<br>&boxv;<br>&boxv;|Teams <br> *Microsoft Teams* <br> **Nicht möglich** <br> *Microsoft Teams*|
|SfB\*|Skype for Business <br> Skype for Business|Online <br> Vorbeh.)|&boxv;<br>&boxv;|*Microsoft Teams* <br> *Microsoft Teams*|
|TeamsOnly|Teams|Online|&boxv;|Teams|
||||||

## <a name="chats-and-calls-from-pre-existing-threads"></a>Chats und Anrufe aus bereits vorhandenen Threads

### <a name="from-teams"></a>Von Teams

Anrufe oder Chats, die aus einem bereits vorhandenen beständigen Thread in Teams gestartet werden, werden auf die gleiche Weise wie der Thread geroutet, sofern diese Routingoption noch verfügbar ist.

Wenn es sich bei dem bereits vorhandenen beständigen Thread in Teams um einen systemeigenen Thread (d. h. um eine Route an Teams) ging, werden zusätzliche Chatnachrichten und Aufrufe von diesem Thread an Teams. Wenn es sich um einen In interop-Thread handelte (d. h. an Skype for Business geroutet), werden weitere Chatnachrichten und Anrufe an Skype for Business (unter der Voraussetzung, dass Routingoptionen verfügbar sind) an Skype for Business gesendet.

> [!NOTE]
> Es ist möglich, dass bereits vorhandene Threads in Teams nicht mehr routingfähig sind, z. B. wenn es sich bei dem Thread um einen Inopthread für einen Benutzer handelte, für den jetzt ein Upgrade auf Teams. Da er als Inopthread erstellt wurde, wird der Thread an Skype for Business geroutet, aber dieser Benutzer kann Skype for Business nicht mehr für Chats und Anrufe verwenden. In diesem Fall wird der Thread deaktiviert, und es ist keine weitere Kommunikation möglich.

### <a name="from-skype-for-business"></a>Von Skype for Business

Skype for Business Threads werden nach 10 Minuten nicht beibehalten. Das Timeout für SIP-Sitzungen. Chats und Anrufe aus einem vorhandenen Thread in Skype for Business vor Ablauf der SIP-Sitzung werden auf die gleiche Weise wie der Thread geroutet. Anrufe und Chats aus einem vorhandenen Thread in Skype for Business, der über das SIP-Sitzungstimeout hinaus geht, werden an das Skype for Business der Remoteseite geroutet, unabhängig davon, von welchem Client der ursprüngliche Thread auf der Seite der anderen Partei stammt.

### <a name="availability"></a>Verfügbarkeit

Sowohl das oben beschriebene Verhalten im Mandanten als auch das Partnerverhalten sind mit den folgenden Einschränkungen verfügbar:

- Externe Teilnehmer, deren Mandanten sich in einer anderen GoLocal-Bereitstellung oder -Geographie befinden, können während einer Partner-Besprechung keinen Chat sehen
- Verbund und Inoperation zwischen mehr mandantenübergreifenden Office 365 und Office 365 von 21Vianet betrieben werden, werden in eingeschränkten Szenarien unterstützt.


## <a name="presence"></a>Anwesenheit

Wenn Sie eine Situation haben, in der einige Ihrer Benutzer den Teams-Client und andere immer noch den Skype for Business-Client verwenden, gibt es möglicherweise eine Reihe von Benutzern, die beide Clients verwenden. Sie möchten, dass Anwesenheitszustände für alle Benutzer freigegeben werden, und zwar unabhängig davon, über welchen Client ein einzelner Benutzer verfügt. Wenn dies in der gesamten Organisation geteilt wird, können die Benutzer besser bestimmen, ob es sinnvoll ist, einen Chat zu starten oder einen Anruf zu starten.

Wenn beispielsweise der Chat oder Anruf eines Erzählers auf dem Skype for Business-Client des Ziels landen sollte, sollte die Anwesenheit des Skype for Business-Clients für den Erzähler angezeigt werden. Sollte der Client auf dem Teams des Ziels landen, sollte die Anwesenheit des Teams-Clients angezeigt werden.

Um zu wissen, welches Verhalten Sie erwarten, müssen Sie verstehen, dass Anwesenheitsinformationen basierend auf dem Koexistenzmodus eines Benutzers freigegeben werden:

- Wenn sich ein Benutzer im TeamsOnly-Modus befindet, sieht jeder andere Benutzer (ob in Teams oder Skype for Business), dass die Anwesenheitsinformationen des TeamsOnly-Teams werden
- Wenn sich ein Benutzer in einem der SfB-Modi \* (SfbOnly, SfbWithTeamsCollab, SfbWithTeamsCollabAndMeetings) befindet, kann jeder andere Benutzer (ob in Teams oder Skype for Business) sehen, dass der Anwesenheitsmodus des SfB-Benutzers Skype for Business ist. \*
- Wenn sich ein Benutzer im Modus "Inseln" (oder "Legacy") befindet, sind die Anwesenheit in Teams und die Anwesenheit in Skype for Business unabhängig (die Werte müssen nicht übereinstimmen), und anderen Benutzern wird der eine oder andere Anwesenheitszustand des Islands-Benutzers angezeigt, je nachdem, ob sie sich im selben Mandanten oder in einem Partner-Mandanten befinden und welchen Client sie verwenden.
  - Von Teams können alle anderen Benutzer innerhalb desselben Mandanten die Anwesenheitsinformationen des Islands-Teams sehen. dies an der oben angegebenen Routingtabelle im Mandanten ausgerichtet ist
  - Von Teams können alle anderen Benutzer in einem Partner mandanten die Anwesenheitsinformationen des Islands-Skype for Business sehen. dies an der oben angegebenen Verbundroutingtabelle ausgerichtet ist
  - Von Skype for Business anderen Benutzern werden die Anwesenheitsinformationen des Benutzers auf den Inseln Skype for Business (sowohl in Mandanten als auch Partnerland) angezeigt. dies ist an den oben angegebenen Routingtabellen ausgerichtet.

### <a name="in-tenant-presence"></a>Anwesenheitspräsenz in Mandanten

An TeamsOnly-Benutzer gesendete Nachrichten werden immer Teams. Nachrichten, die an SfB-Benutzer gesendet werden, werden immer Skype for Business, wenn die Unterhaltung \* wie oben beschrieben möglich ist. An Inseln gesendete Nachrichten landen immer in dem Client, aus dem sie stammen.

In der Tabelle Publisher die Anwesenheit der Publisher beschrieben, die von einer Watcher abhängig vom Modus der Publisher und dem Client der Watcher (für einen neuen Thread) angezeigt wird.

#### <a name="table-3-in-tenant-presence-new-thread"></a>Tabelle 3: Anwesenheit in Mandanten (neuer Thread)

<br>

|Zusehen<br><br>Client|<br><br>Route->|<br><br>Inselmodus|Publisher<br><br>SfB\*|<br>Teams Nur|
|---|:---:|---|---|---|
|Skype for Business|&boxv;|Skype for Business|Skype for Business|Microsoft Teams|
|Microsoft Teams|&boxv;|Microsoft Teams|Skype for Business|Teams|
|||||

### <a name="federated-presence"></a>Verbundpräsenz

Die Verbundpräsenz basiert auf der in Tabelle 2 gezeigten Erreichbarkeit im Verbund.

In der folgenden Tabelle Publisher die Anwesenheitsart der Publisher beschrieben, die von einem Watcher abhängig vom Modus der Publisher und dem Client der Watcher (für einen neuen Thread) angezeigt wird. In der Praxis macht der Client von Watcher in dieser Phase keinen Unterschied beim Verbund.

#### <a name="table-4-federated-presence-new-thread"></a>Tabelle 4: Verbundpräsenz (neuer Thread)

<br>

|Zusehen<br><br>Client|<br><br>Route->|<br><br>Inselmodus|Publisher<br><br>SfB\*|<br><br>Teams Nur|
|---|:---:|---|---|---|
|Skype for Business|&boxv;|Skype for Business|Skype for Business|Microsoft Teams|
|Microsoft Teams|&boxv;|Skype for Business|Skype for Business|Teams|
||||||

### <a name="presence-in-pre-existing-threads"></a>Anwesenheit in bereits vorhandenen Threads

Um die Anwesenheit und Erreichbarkeit in bereits vorhandenen Threads auszurichten, muss die Anwesenheit des Ziels, die in diesem Thread verfügbar gemacht wird, an das Routing des Threads angepasst werden, sofern Routing möglich ist.

Insbesondere wenn ein Empfänger, mit dem Sie zuvor einen dauerhaften Inop-Unterhaltungsthread hatten, auf Teams aktualisiert wurde, spiegelt dieser Thread keine präzise Anwesenheit mehr wider und kann nicht mehr routingfähig sein. Sie sollten einen neuen Thread starten.

### <a name="federation-and-interop-with-office-365-operated-by-21vianet"></a>Verbund und Inaktivität mit Office 365 21Vianet

Verbund und Inaktivität zwischen mehr mandantenübergreifenden Office 365 und Office 365, betrieben von 21Vianet, werden unterstützt, wenn sich die Office 365-Benutzer mit mehreren Mandanten im Teams-Modus befinden. In einem solchen Szenario können Skype for Business Online-Benutzer in Office 365, betrieben von 21Vianet, über Chats und Anrufe nur mit Teams Nur Benutzer in mehrstufigen Office 365 kommunizieren. Die folgende Tabelle zeigt die unterstützten Szenarien in dieser Konfiguration:
 
|Szenario|Origin|Empfänger|Unterstützt?|
|---|---|---|---|
|Anwesenheit|Microsoft Teams <br> Skype for Business <br> | Skype for Business <br> Teams|Ja<br>Ja|
|Chat|Teams <br> Skype for Business <br> | Skype for Business <br> Teams|Ja (nur 1:1)<br>Ja(nur 1:1)|
|Audioanrufe|Microsoft Teams <br> Skype for Business <br> | Skype for Business <br> Teams|Ja (nur 1:1)<br>Ja (nur 1:1)|
|Videoanrufe|Microsoft Teams <br> Skype for Business <br> | Skype for Business <br> Teams|Ja (nur 1:1)<br>Ja (nur 1:1)|
|Bildschirmfreigabe|Microsoft Teams <br> Skype for Business <br> | Skype for Business <br> Teams |Ja (durch eine heraufgestufte Teams Besprechung)<br>Ja (durch eine heraufgestufte SfB-Besprechung)|
|||||


## <a name="related-links"></a>Verwandte Links
[Anleitungen zur Migration und Interoperabilität für Organisationen, die Teams zusammen mit Skype for Business verwenden](./migration-interop-guidance-for-teams-with-skype.md)

[Video: Verwalten der Koexistenz und Interoperabilität zwischen SfB und Teams](https://www.youtube.com/watch?v=wEc9u4S3GIA&list=PLaSOUojkSiGnKuE30ckcjnDVkMNqDv0Vl&index=11)
