---
title: Planen der Hybridkonnektivität | Skype for Business Server und Teams
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: bjwhalen
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: article
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.collection:
- Hybrid
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
description: Planen Sie die Implementierung der Hybridkonnektivität zwischen Skype for Business Server und Teams, indem Sie Skype for Business Hybridmodus konfigurieren.
ms.custom: seo-marvel-jun2020
ms.openlocfilehash: 40d89076973e4667c41676684841e8c35c356396
ms.sourcegitcommit: b2566e64e02cb51d18836630d3aa9b6f27b924da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2021
ms.locfileid: "59491715"
---
# <a name="plan-hybrid-connectivity-between-skype-for-business-server-and-teams"></a>Planen der Hybridkonnektivität zwischen Skype for Business Server und Teams

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

In diesem Thema erfahren Sie, wie Sie die Hybridkonnektivität zwischen Skype for Business Server und Teams planen. Das Einrichten von Hybridverbindungen ist der erste Schritt beim Migrieren Ihrer lokalen Umgebung zur Cloud.

Wenn Sie über lokale Skype for Business-Benutzer verfügen, die (parallel) auch Microsoft Teams verwenden, können diese Benutzer von ihrem Teams-Client aus nicht mit Skype for Business-Benutzern interagieren oder mit Benutzern in Verbundorganisationen kommunizieren. Um diese Funktionalität in Teams freizuschalten, müssen diese Benutzer von der lokalen Skype for Business-Umgebung in die Cloud verschoben werden, und dies erfordert die Konfiguration des Skype for Business-Hybridmodus. Darüber hinaus sollten sich diese Benutzer im modus "nur" Teams befinden, um sicherzustellen, dass alle eingehenden Anrufe und Chats von jedem Benutzer im Teams Client des Benutzers landen.

Außerdem müssen Sie die Hybridkonnektivität einrichten und alle Benutzer in die Cloud verschieben, bevor Sie Ihre lokale Skype for Business-Bereitstellung außer Betrieb nehmen.  Sobald die Hybridkonnektivität eingerichtet ist, können Sie Ihre Benutzer entsprechend Ihres Zeitplans und Ihrer geschäftlichen Anforderungen in die Cloud verschieben. Bei der direkten Weiterleitung können Sie Ihre lokale Sprachinfrastruktur nutzen, sowohl während Sie in die Cloud verschieben als auch nach Abschluss der Migration.

In diesem Thema werden die Infrastruktur- und Systemanforderungen beschrieben, die Sie benötigen, um die Hybridkonnektivität zwischen Ihren vorhandenen lokalen Skype for Business Server Bereitstellung und Teams zu konfigurieren.

Nachdem Sie dieses Thema gelesen haben und bereit zum Konfigurieren der Hybridkonnektivität sind, finden Sie weitere Informationen unter Konfigurieren der [Hybridkonnektivität zwischen Skype for Business Server und Teams.](configure-hybrid-connectivity.md) Die Konfigurationsthemen enthalten schrittweise Anleitungen zum Einrichten der Hybridkonnektivität zwischen Ihrer lokalen Bereitstellung und Teams.

> [!Important]
> Skype for Business Online wurde am 31. Juli 2021 eingestellt und ist nicht mehr verfügbar. Darüber hinaus wird die PSTN-Konnektivität zwischen Ihrer lokalen Umgebung über Skype for Business Server oder Cloud Connector Edition und Skype for Business Online nicht mehr unterstützt.  Erfahren Sie, wie Sie Ihr lokales Telefonienetzwerk mit Teams über [Direct Routing](/MicrosoftTeams/direct-routing-landing-page)verbinden.

## <a name="implications-of-the-retirement-of-skype-for-business-online"></a>Auswirkungen der Einstellung von Skype for Business Online
Es ist wichtig zu beachten, dass sowohl vor als auch nach der Deaktivierung von Skype for Business Online Benutzer, die in Skype for Business Server lokal verwaltet werden, Teams verwenden können, aber sie können nicht TeamsOnly sein. (Standardmäßig befinden sich Benutzer im Inselmodus). Benutzer können nur dann die vorteile Teams, insbesondere partnerverbundene und PSTN-Unterstützung, nutzen, sobald sie sich im TeamsOnly-Modus befinden. 

Die Einstellung von Skype for Business Online hat keine Auswirkungen auf den vorhandenen Supportlebenszyklus von Skype for Business Server oder Lync Server 2013.  Die Einstellung von Skype for Business Online wirkte sich jedoch auf bestimmte Aspekte des Übergangs von Kunden mit lokalen Skype for Business Server oder Lync Server 2013, einschließlich bestehender Hybridorganisationen, zur Cloud aus. Was sich seit der Einstellung nicht geändert hat, ist, dass die Verwendung von Hybrid als Mittel für den Übergang von der lokalen Bereitstellung in die Cloud unverändert bleibt.

Vor der Einstellung von Skype for Business Online könnten Hybridorganisationen aus drei grundlegenden Benutzertypen bestehen: 
- Lokale Benutzer (die Teams verwenden dürfen, aber nicht im Modus "Nur Teams") 
- Onlinebenutzer mit einem anderen Koexistenzmodus als TeamsOnly
- TeamsOnly-Benutzer.

Nach der Einstellung von Skype for Business Online können Hybridorganisationen jedoch nur aus zwei grundlegenden Benutzertypen bestehen: 
- Lokale Benutzer (Wer dürfen Teams verwenden, aber nicht im TeamsOnly-Modus)
- Teams Nur Benutzer. 

Damit Organisationen von Skype for Business Server oder Lync Server 2013 zu Teams wechseln können, müssen sie weiterhin Hybridbereitstellungen mit demselben Toolset einrichten und konfigurieren, *genau wie vor der Einstellung.* Was sich geändert hat, ist, wenn ein Benutzer aus der lokalen Umgebung zu Teams verschoben wird, es ist nicht mehr erforderlich, den `-MoveToTeams` Wechsel `Move-CsUser` anzugeben, um Benutzer direkt aus der lokalen Umgebung zu TeamsOnly zu verschieben. Wenn dieser Switch nicht angegeben wurde, wurden Benutzer zuvor von Skype for Business Server lokal zu Skype for Business Online migriert, und ihr Modus bleibt unverändert. Als Ergebnis der Einstellung, wenn ein Benutzer aus der lokalen Umgebung in die Cloud verschoben wird, wird benutzern jetzt automatisch der `Move-CsUser` TeamsOnly-Modus zugewiesen, und ihre Besprechungen aus der lokalen Umgebung werden automatisch in Teams Besprechungen konvertiert, so als ob der `-MoveToTeams` Switch angegeben worden wäre, unabhängig davon, ob der Switch tatsächlich angegeben ist. (Dies umfasst Migrationen von Lync Server 2013, die nie den `MoveToTeams` Switch hatten.) 

Wenn ein neuer Benutzer direkt in Microsoft 365 und nicht lokal erstellt wird, verfügt dieser Benutzer unabhängig vom Mandantenmodus automatisch über Teams Modus "Nur". Bedenken Sie, dass in einer Hybridorganisation neue Benutzer im lokalen Active Directory erstellt (und dann in Microsoft 365 synchronisiert) werden sollten, anstatt einen Benutzer direkt in Microsoft 365 zu erstellen, um sicherzustellen, dass lokale Benutzer an den neuen Benutzer weitergeleitet werden können.

Koexistenzmodi sind nach der Einstellung von Skype for Business Online weiterhin vorhanden. Wie zuvor können Benutzer mit Konten, die in Skype for Business Server lokal verwaltet werden, jedem Koexistenzmodus mit Ausnahme von TeamsOnly zugewiesen werden. Nach dem Ausmustern können online verwaltete Benutzer jedoch nur TeamsOnly sein (im Gegensatz zur aktuellen, in der Skype for Business Online-Benutzer einen beliebigen Modus haben können).  

> [!Important]
> - Bestehende Hybridorganisationen mit Benutzern, die in Skype for Business Online verwaltet werden und NICHT TeamsOnly sind, sollten sich darauf konzentrieren, diese Benutzer so bald wie möglich auf Teams Modus "Nur" zu aktualisieren. Wenn in Ihrer Organisation weiterhin Benutzer in Skype for Business Online verwaltet werden, die nicht TeamsOnly sind, ist möglicherweise ein von Microsoft unterstütztes Upgrade geplant, um diese Benutzer auf TeamsOnly zu übertragen. Dies wirkt sich nicht auf Benutzer aus, die in Skype for Business Server lokal verwaltet werden. Planungsbenachrichtigungen werden im Voraus an Hybridkunden mit Benutzern gesendet, die in Skype for Business Online verwaltet werden, bevor diese Onlinebenutzer, die kein TeamsOnly-Benutzer sind, auf Teams aktualisiert werden.
> - Es ist nicht mehr möglich, einem Benutzer, der online verwaltet wird, einen anderen Modus als TeamsOnly zuzuweisen.

## <a name="about-shared-sip-address-space-functionality"></a>Informationen zur Funktionalität des freigegebenen SIP-Adressraums

<a name="BKMK_Overview"> </a>

 Wenn die Hybridkonnektivität zwischen einer lokalen Bereitstellung von Skype for Business Server und Teams eingerichtet ist, können Einige Benutzer lokal verwaltet werden und einige Benutzer online verwaltet werden.

Diese Art von Konfiguration basiert auf der Funktionalität des freigegebenen SIP-Adressraums und wird manchmal als "geteilte Domäne" bezeichnet, d. h. Benutzer einer Domäne, z. B. contoso.com, werden zwischen Skype for Business Server lokalen und Teams aufgeteilt, wie im folgenden Diagramm dargestellt:

![Skype for Business Hybrid Konnektivität – geteilte Domäne.](../../sfbserver2019/media/plan-hybrid-connectivity-2019-1.png)

Wenn der freigegebene SIP-Adressraum konfiguriert ist:

- Azure Active Directory Verbinden wird verwendet, um Ihr lokales Verzeichnis mit Microsoft 365 zu synchronisieren.
- Lokal verwaltete Benutzer interagieren mit lokalen Skype for Business Servern.
- Benutzer, die online verwaltet werden, können mit Teams interagieren und bis zum 31. Juli 2021 basierend auf ihrem Koexistenzmodus online Skype for Business.
- Benutzer aus beiden Umgebungen können miteinander kommunizieren.
- Das lokale Active Directory ist autoritativ. Alle Benutzer sollten zuerst im lokalen Active Directory erstellt und dann mit Azure AD synchronisiert werden. Auch wenn Sie beabsichtigen, dass der Benutzer online verwaltet wird, müssen Sie den Benutzer zuerst in der lokalen Umgebung erstellen und den Benutzer dann in die Onlineumgebung verschieben, um sicherzustellen, dass der Benutzer für lokale Benutzer auffindbar ist.

Bevor ein Benutzer online verschoben werden kann, muss ihm eine Teams Lizenz sowie Skype for Business Online (Plan 2) zugewiesen werden. **Die Zuweisung der Skype for Business Onlinelizenz ist auch nach der Einstellung von Skype for Business Online erforderlich.** Wenn Ihre Benutzer zusätzliche Onlinefunktionen wie Audiokonferenzen oder Telefonsystem nutzen möchten, müssen Sie ihnen die entsprechende Lizenz in Microsoft 365 zuweisen.

## <a name="hybrid-connectivity-infrastructure-requirements"></a>Infrastrukturanforderungen für Hybridkonnektivität

<a name="BKMK_Infrastructure"> </a>

Um eine Hybridkonnektivität zwischen Ihrer lokalen Umgebung und Microsoft 365 Kommunikationsdiensten zu implementieren, müssen Sie die folgenden Infrastrukturanforderungen erfüllen:

- Eine einzelne lokale Bereitstellung von Skype for Business Server oder Lync Server, die in einer unterstützten Topologie bereitgestellt wird. Weitere Informationen finden Sie unter ["Topologieanforderungen"](plan-hybrid-connectivity.md#BKMK_Topology) in diesem Thema.

- Eine Microsoft 365 Organisation mit Teams.
    > [!NOTE]
    > Sie können nur einen einzelnen Mandanten für eine Hybridkonfiguration mit Ihrer lokalen Bereitstellung verwenden.
    
- Azure Active Directory Verbinden, um Ihr lokales Verzeichnis mit Microsoft 365 zu synchronisieren. Weitere Informationen finden Sie unter [Azure AD Verbinden: Konten und Berechtigungen.](/azure/active-directory/connect/active-directory-aadconnect-accounts-permissions)

- Skype for Business Server Verwaltungstools. Diese sind erforderlich, um Benutzer aus der lokalen Umgebung in die Cloud zu verschieben. Diese Tools müssen auf einem Server mit Zugriff auf die lokale Bereitstellung und das Internet installiert werden.
- Onlineverwaltungstools. Sie können entweder das Teams Admin Center oder Windows PowerShell verwenden, um Teams zu verwalten. Um PowerShell zum Verwalten Teams zu verwenden, laden Sie das Teams PowerShell-Modul herunter und installieren es. (Der Skype for Business Online-Connector wurde eingestellt).)
- Der freigegebene SIP-Adressraum muss aktiviert sein, und Ihre lokale Bereitstellung muss so konfiguriert sein, dass Microsoft 365 als Hostinganbieter verwendet wird. Weitere Informationen zu den erforderlichen Schritten zum Konfigurieren der Hybridkonnektivität finden Sie unter Konfigurieren der [Hybridkonnektivität.](configure-hybrid-connectivity.md)

Nachdem Sie die Hybridkonnektivität konfiguriert haben, können Sie Benutzer zu Teams verschieben. Weitere Informationen finden Sie unter [Verschieben von Benutzern aus der lokalen Umgebung in Teams](move-users-from-on-premises-to-teams.md).

## <a name="server-version-requirements"></a>Serverversionsanforderungen

<a name="BKMK_Topology"> </a>

Um Ihre Bereitstellung für die Hybridbereitstellung mit **Teams** zu konfigurieren, benötigen Sie eine der folgenden unterstützten Topologien:

- Eine Skype for Business Server 2019-Bereitstellung mit allen Servern, auf denen Skype for Business Server 2019 ausgeführt wird.
- Eine Skype for Business Server 2015-Bereitstellung mit allen Servern, auf denen Skype for Business Server 2015 ausgeführt wird.
- Eine Lync Server 2013-Bereitstellung mit allen Servern, auf denen Lync Server 2013 ausgeführt wird.  Wenn jedoch eine Hybrid-VoIP-Konnektivität erforderlich ist, müssen Sie eine gemischte Versionstopologie verwenden, wie unten beschrieben.
- Eine Bereitstellung mit maximal 2 verschiedenen Serverversionen wie unten aufgeführt:
  - Skype for Business Server 2015 und Skype for Business Server 2019
  - Lync Server 2013 und Skype for Business Server 2019
  - Lync Server 2013 und Skype for Business Server 2015

*Wenn Hybrid voice in einer Topologie gewünscht wird,* müssen sowohl der Edgeserver, der als Partnerverbund-Edge festgelegt ist, als auch der dem SIP-Partnerverbund zugeordnete Pool Skype for Business 2015 oder höher ausgeführt werden. Benutzer können in einem Lync 2013-Pool verbleiben, sofern vorhanden. Weitere Informationen finden Sie unter [Planen Ihrer VoIP-Lösung.](/MicrosoftTeams/cloud-voice-landing-page)

> [!NOTE]
> Lync Server 2010 wird bei Teams nicht unterstützt.

## <a name="multi-forest-support"></a>Unterstützung mehrerer Gesamtstrukturen

<a name="BKMK_MultiForest"> </a>

Microsoft unterstützt die folgenden Arten von Hybridszenarien mit mehreren Gesamtstrukturen:

- **Topologie der Ressourcengesamtstruktur.** In dieser Art von Topologie gibt es eine Gesamtstruktur, die Skype for Business Server (die Ressourcengesamtstruktur) hostet, und es gibt eine oder mehrere zusätzliche Gesamtstrukturen, die Kontoidentitäten hosten, die auf die Skype for Business Server in der Ressourcengesamtstruktur zugreifen. Im Allgemeinen können Benutzer auf Skype for Business Funktionalität in einer anderen Gesamtstruktur zugreifen, wenn die folgenden Anforderungen erfüllt sind:
  - Benutzer werden ordnungsgemäß mit der Gesamtstruktur synchronisiert, die Skype for Business hostet. In Hybridkonfigurationen bedeutet dies, dass Benutzer als deaktivierte Benutzerobjekte synchronisiert werden müssen.
  - Die Gesamtstruktur, die Skype for Business hostet, muss der Gesamtstruktur vertrauen, die die Benutzer enthält.
    Ausführliche Informationen zu Hybridszenarien der Ressourcengesamtstruktur finden Sie unter [Bereitstellen einer Ressourcengesamtstrukturtopologie für hybride Skype for Business.](configure-a-multi-forest-environment-for-hybrid.md)

- **Mehrere Bereitstellungen von Skype for Business Server in mehreren Gesamtstrukturen.** Diese Konfiguration kann aufgrund von Fusions- und Übernahmeszenarien sowie in komplexeren Unternehmen auftreten. Die Konsolidierung aller Benutzer aus der lokalen Umgebung in die Cloud in einer einzigen Microsoft 365 Organisation kann für jede Organisation mit mehreren Skype for Business Bereitstellungen erreicht werden, vorausgesetzt, die folgenden wichtigen Anforderungen sind erfüllt:
  - Es muss mindestens eine Microsoft 365 Organisation beteiligt sein. Die Konsolidierung in Szenarien mit mehr als einer Organisation wird nicht unterstützt.
  - Zu einem bestimmten Zeitpunkt kann sich nur eine lokale Skype for Business Gesamtstruktur im Hybridmodus befinden (freigegebener SIP-Adressraum). Alle anderen lokalen Skype for Business Gesamtstrukturen müssen vollständig lokal bleiben (und vermutlich miteinander verbunden sein). Beachten Sie, dass diese anderen lokalen Organisationen bei Bedarf mit AAD synchronisiert werden können, um die ab Dezember 2018 verfügbaren [Online-SIP-Domänen zu deaktivieren.](/powershell/module/skype/disable-csonlinesipdomain)

    Kunden mit Bereitstellungen von Skype for Business in mehreren Gesamtstrukturen müssen jede Skype for Business Gesamtstruktur mithilfe von Funktionen für geteilte Domänen (Freigegebener SIP-Adressraum) vollständig in die Microsoft 365 Organisation migrieren. Nachdem die Gesamtstrukturmigration abgeschlossen ist, müssen Kunden die Hybridbereitstellung mit der lokalen Bereitstellung deaktivieren, bevor sie mit der Migration der nächsten lokalen Skype for Business Bereitstellung fortfahren. Darüber hinaus verbleiben lokale Benutzer vor der Migration in die Cloud in einem Verbundstatus mit allen Benutzern, die nicht im lokalen Verzeichnis desselben Benutzers dargestellt sind. Weitere Informationen finden Sie unter [Cloudkonsolidierung für Teams und Skype for Business.](cloud-consolidation.md)

## <a name="federation-requirements"></a>Verbundanforderungen

<a name="BKMK_Federation"> </a>

Beim Konfigurieren Skype for Business Hybridmodus müssen Sie sicherstellen, dass Ihre lokalen und Onlineumgebungen miteinander verbunden werden können.  Die Onlineumgebung verfügt standardmäßig über einen offenen Partnerverbund. Die lokale Umgebung verfügt häufig standardmäßig über einen geschlossenen Partnerverbund.  

Die folgenden Anforderungen müssen erfüllt sein, um eine Hybridbereitstellung erfolgreich konfigurieren zu können:

- Der Domänenabgleich muss für Ihre lokale Bereitstellung und Ihre Microsoft 365 Organisation identisch konfiguriert werden. Wenn die Partnerermittlung in der lokalen Bereitstellung aktiviert ist, muss der offene Partnerverbund für Ihre Onlineorganisation konfiguriert werden. Wenn die Partnerermittlung nicht aktiviert ist, muss der geschlossene Partnerverbund für Ihre Onlineorganisation konfiguriert werden.
- Die Liste blockierter Domänen in der lokalen Bereitstellung muss genau mit der Liste blockierter Domänen für Ihren Onlinemandanten übereinstimmen.
- Die Liste der zulässigen Domänen in der lokalen Bereitstellung muss genau mit der Liste der zulässigen Domänen für Ihren Onlinemandanten übereinstimmen.
- Der Partnerverbund muss für die externe Kommunikation für den Onlinemandanten aktiviert sein.

## <a name="network-considerations"></a>Überlegungen zum Netzwerk

In den folgenden Abschnitten werden Überlegungen zu folgenden Aspekten beschrieben:

- DNS-Einstellungen
- Überlegungen zur Firewall

### <a name="dns-settings-for-hybrid-deployments"></a>DNS-Einstellungen für Hybridbereitstellungen

<a name="BKMK_DNS"> </a>

Beim Erstellen von DNS-Einträgen für Hybridbereitstellungen sollten alle Skype for Business externen DNS-Einträge auf die lokale Infrastruktur verweisen. Ausführliche Informationen zu erforderlichen DNS-Einträgen finden Sie in den [DNS-Anforderungen für Skype for Business Server.](../../sfbserver/plan-your-deployment/network-requirements/dns.md)

Darüber hinaus müssen Sie sicherstellen, dass die in der folgenden Tabelle beschriebene DNS-Auflösung in Ihrer lokalen Bereitstellung funktioniert. (Wenn Sie den Partnerverbund bereits für die lokale Bereitstellung konfiguriert haben, verfügen Sie wahrscheinlich bereits über diese.)

|DNS-Eintrag  <br/> |Auflösbar von  <br/> |DNS-Anforderung  <br/> |
|:-----|:-----|:-----|
|DNS-SRV-Eintrag für _sipfederationtls._tcp.\<sipdomain.com\> für alle unterstützten SIP-Domänen, die auf externe IP(s) des Zugriffs-Edges aufgelöst werden  <br/> |Edgeserver  <br/> |Aktivieren Sie die Verbundkommunikation in einer Hybridkonfiguration. Der Edgeserver muss wissen, wo der Verbunddatenverkehr für die SIP-Domäne weitergeleitet werden soll, die zwischen lokal und online aufgeteilt ist.  <br/> Muss einen strikten DNS-Namensabgleich zwischen der Domäne im Benutzernamen und dem SRV-Eintrag verwenden.  <br/> |
|DNS A-Einträge für edge-Webkonferenzdienst-FQDN, z. B. webcon.contoso.com Auflösen in externe IP-Adressen von Webkonferenz-Edge  <br/> |Computer der mit dem internen Unternehmensnetzwerk verbundenen Benutzer  <br/> |Ermöglichen Sie Onlinebenutzern das Präsentieren oder Anzeigen von Inhalten in lokalen gehosteten Besprechungen. Der Inhalt umfasst PowerPoint Dateien, Whiteboards, Umfragen und freigegebene Notizen.  <br/> |

Je nachdem, wie DNS in Ihrer Organisation konfiguriert ist, müssen Sie diese Einträge möglicherweise der intern gehosteten DNS-Zone für die entsprechenden SIP-Domänen hinzufügen, um eine interne DNS-Auflösung für diese Einträge bereitzustellen.

### <a name="firewall-considerations-for-hybrid-deployments"></a>Überlegungen zur Firewall für Hybridbereitstellungen

<a name="BKMK_Firewall"> </a>

Computer in Ihrem Netzwerk müssen in der Lage sein, standardmäßige Internet-DNS-Lookups durchzuführen. Wenn diese Computer Standard-Internetwebsites erreichen können, erfüllt Ihr Netzwerk diese Anforderung.

Abhängig vom Standort Ihres Microsoft Online Services-Rechenzentrums müssen Sie ihre Netzwerkfirewallgeräte auch so konfigurieren, dass Verbindungen basierend auf Platzhalterdomänennamen akzeptiert werden (z. B. der gesamte Datenverkehr von \* .outlook.com). Wenn die Firewalls Ihrer Organisation Keine Platzhalternamenkonfigurationen unterstützen, müssen Sie die ip-Adressbereiche, die Sie zulassen möchten, und die angegebenen Ports manuell ermitteln.

Weitere Informationen, einschließlich Details zu Ports und Protokollanforderungen, finden Sie unter [Microsoft 365 URLs und IP-Adressbereiche.](/microsoft-365/enterprise/urls-and-ip-address-ranges)
