---
title: Notfallwiederherstellungstests in Skype for Business Server
ms.reviewer: ''
ms.author: v-cichur
author: cichur
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
description: Durchführen einer Systemwiederherstellung für einen Skype for Business Server Poolserver zum Testen des dokumentierten Notfallwiederherstellungsprozesses
ms.openlocfilehash: a98f2de4d860c4a769526428958ba9b952cfc573
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58609242"
---
# <a name="disaster-recovery-testing-in-skype-for-business-server"></a>Notfallwiederherstellungstests in Skype for Business Server

Führen Sie eine Systemwiederherstellung für einen Skype for Business Server Poolserver aus, um den dokumentierten Notfallwiederherstellungsprozess zu testen. Dieser Test simuliert einen vollständigen Hardwarefehler für einen Server und trägt dazu bei, sicherzustellen, dass die Ressourcen, Pläne und Daten für die Wiederherstellung verfügbar sind. Versuchen Sie, den Fokus des Tests jeden Monat zu drehen, damit Ihre Organisation jedes Mal den Ausfall eines anderen Servers oder eines anderen Geräts testet. 

Beachten Sie, dass der Zeitplan, nach dem Organisationen Notfallwiederherstellungstests durchführen, variieren wird. Es ist sehr wichtig, dass Notfallwiederherstellungstests nicht ignoriert oder nicht beachtet werden. 

Exportieren Sie Ihre Skype for Business Server Topologie, Richtlinien und Konfigurationseinstellungen in eine Datei. Unter anderem kann diese Datei dann verwendet werden, um diese Informationen im zentralen Verwaltungsspeicher wiederherzustellen, nachdem ein Upgrade, ein Hardwarefehler oder ein anderes Problem zu Einem Datenverlust geführt hat.

Importieren Sie Ihre Skype for Business Server Topologie, Richtlinien und Konfigurationseinstellungen in den zentralen Verwaltungsspeicher oder auf den lokalen Computer, wie in den folgenden Befehlen gezeigt: 

`Import-CsConfiguration -ByteInput <Byte[]> [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]`

`Import-CsConfiguration -FileName <String> [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]` 

So sichern Sie Produktionsdaten:

- Sichern Sie die RTC- und LCSLog-Datenbanken mithilfe des Standardmäßigen SQL Server Sicherungsvorgangs, um die Datenbank auf einem Datei- oder Bandabbildgerät zu sichern.
- Verwenden Sie die Sicherungsanwendung von Drittanbietern, um die Daten in einer Datei oder auf einem Band zu sichern.
- Verwenden Sie das Cmdlet Export-CsUserData, um einen XML-Export der gesamten RTC-Datenbank zu erstellen.
- Verwenden Sie die Dateisystemsicherung oder Drittanbietersicherung, um Besprechungsinhalte und Complianceprotokolle zu sichern.
- Verwenden Sie das Befehlszeilentool Export-CsConfiguration, um Skype for Business Server Einstellungen zu sichern.

Der erste Schritt im Failoververfahren umfasst die erzwungene Verschiebung von Benutzern aus dem Produktionspool in den Notfallwiederherstellungspool. Dies ist eine erzwungene Verschiebung, da der Produktionspool nicht verfügbar ist, um die Verschiebung des Benutzers zu akzeptieren.

Der Skype for Business Server Verschieben des Benutzerprozesses ist im Grunde eine Änderung an einem Attribut des Benutzerkontoobjekts zusätzlich zu einer Datensatzaktualisierung in der RTC-SQL-Datenbank. Diese Daten können vom ursprünglichen Sicherungssicherungsgerät aus der Produktions-SQL Server mithilfe des Standardmäßigen SQL Server Wiederherstellungsprozesses oder mithilfe eines Sicherungs-/Wiederherstellungsprogramms eines Drittanbieters wiederhergestellt werden.

Nachdem diese Daten wiederhergestellt wurden, können Benutzer effektiv eine Verbindung mit dem Notfallwiederherstellungspool herstellen und wie gewohnt arbeiten. Damit Benutzer eine Verbindung mit dem Notfallwiederherstellungspool herstellen können, ist eine DNS-Eintragsänderung erforderlich.

Auf den Produktions-Skype for Business-Pool wird von Clients verwiesen, die die Autokonfigurations- und DNS-SRV-Einträge verwenden von:

- SRV: _sip._tls.\<domain> /CNAME: SIP.\<domain>
- CNAME: SIP.\<domain> /cvc-pool-1.\<domain>

Um das Failover zu vereinfachen, muss dieser CNAME-Eintrag aktualisiert werden, um auf den DROCSPool-FQDN zu verweisen:

- CNAME: SIP.<domain> /DROCSPool.\<domain>
- Sip.\<domain>
- AV.\<domain>
- webconf.\<domain>
