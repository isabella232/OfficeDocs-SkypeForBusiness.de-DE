---
title: Verschieben von Benutzern zwischen lokalen Bereitstellungen und der Cloud
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
ms.custom: ''
description: 'Zusammenfassung: In einer lokalen Bereitstellung von Skype for Business Server, die für die Hybridbereitstellung aktiviert ist, können Sie Benutzer zwischen der lokalen Umgebung und der Cloud verschieben.'
ms.openlocfilehash: 0c13f29cf2773afb170bb7be20bb2f95c5d13e6c
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58589217"
---
# <a name="move-users-between-on-premises-and-cloud"></a>Verschieben von Benutzern zwischen lokalen Bereitstellungen und der Cloud

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

In einer lokalen Bereitstellung von Skype for Business Server, die für die Hybridbereitstellung aktiviert ist, können Sie Benutzer zwischen der lokalen Umgebung und Teams verschieben. Ob ein Benutzer lokal oder in der Cloud verwaltet wird, gibt das Skype for Business Home des Benutzer an:

- Benutzer, die lokal verwaltet werden, interagieren mit lokalen Skype for Business Servern.
- Benutzer, die online verwaltet werden, können mit dem Teams-Dienst interagieren.

*Microsoft Teams-Benutzer verfügen inhärent über ein Skype for Business Home, ganz gleich, ob sie Skype for Business verwenden oder nicht.* Wenn Sie über lokale Skype for Business Benutzer verfügen, die auch Teams verwenden (nebeneinander), werden diese Benutzer lokal verwaltet. Teams Benutzer mit lokalen Skype for Business können nicht mit Skype for Business Benutzern über ihren Teams-Client zusammenarbeiten, und sie können auch nicht über Teams mit Benutzern in einer Verbundorganisation kommunizieren. Diese Funktionalität ist erst vollständig verfügbar, nachdem der Benutzer von Skype for Business lokal in online verschoben und zu TeamsOnly gemacht wurde. Es wird dringend empfohlen, dass Sie Ihre Benutzer in den TeamsOnly-Modus verschieben, wodurch sichergestellt wird, dass das Routing aller eingehenden Chats und Anrufe in ihrem Teams-Client ankommt. Weitere Informationen finden Sie unter [Teams Koexistenz mit Skype for Business](/microsoftteams/coexistence-chat-calls-presence) und [Migrations- und Interoperabilitätsleitfaden für Organisationen,](/microsoftteams/migration-interop-guidance-for-teams-with-skype)die Teams zusammen mit Skype for Business verwenden.

## <a name="prerequisites"></a>Voraussetzungen

Voraussetzungen zum Verschieben eines Benutzers in den TeamsOnly-Modus:

- Die Organisation muss Azure AD Verbinden ordnungsgemäß konfiguriert haben und alle relevanten Attribute für den Benutzer synchronisieren, wie unter [Konfigurieren von Azure AD Verbinden](configure-azure-ad-connect.md)beschrieben.
- Skype for Business Hybrid muss konfiguriert werden, wie unter [Konfigurieren Skype for Business Hybrid](configure-federation-with-skype-for-business-online.md)beschrieben.
- Dem Benutzer muss eine Lizenz für Teams und Skype for Business Online (Plan 2) zugewiesen werden. Auch nach dem Ausmustern von Skype for Business Online ist die Skype for Business Online-Lizenz weiterhin erforderlich.  Weitere Schritte:
    - Wenn der Benutzer lokal für Einwahlkonferenzen aktiviert ist, muss dem Benutzer standardmäßig auch eine Audiokonferenzlizenz in Teams zugewiesen sein, bevor Sie den Benutzer online verschieben. Nach der Migration zur Cloud wird der Benutzer für Audiokonferenzen in der Cloud bereitgestellt. Wenn Sie aus irgendeinem Grund einen Benutzer in die Cloud verschieben möchten, aber nicht die Audiokonferenzfunktionen verwenden möchten, können Sie diese Überprüfung überschreiben, indem Sie den `BypassAudioConferencingCheck`-Parameter in `Move-CsUser` angeben.
    - Wenn der Benutzer für Enterprise-VoIP lokal aktiviert ist, muss dem Benutzer standardmäßig eine Telefonsystem Lizenz in Teams zugewiesen sein, bevor Sie den Benutzer online verschieben. Nach der Migration zur Cloud wird der Benutzer für das Telefonsystem in der Cloud bereitgestellt. Wenn Sie aus irgendeinem Grund einen Benutzer in die Cloud verschieben möchten, aber nicht Telefonsystem Funktionalität verwenden möchten, können Sie diese Überprüfung überschreiben, indem Sie den `BypassEnterpriseVoiceCheck` Parameter in `Move-CsUser` angeben.


## <a name="moving-users"></a>Verschieben von Benutzern

Wenn ein Benutzer aus der lokalen Umgebung in die Cloud verschoben wird:

- Teams Benutzer werden für die Interoperabilität mit Skype for Business Benutzern aktiviert, und wenn sie TeamsOnly sind, können sie auch mit anderen Organisationen zusammenarbeiten.

- Kontakte aus der lokalen Umgebung werden in Teams verschoben.

- Vorhandene Besprechungen, die sie organisiert haben und die in Zukunft geplant sind, werden online migriert: Wenn Benutzer direkt nach TeamsOnly verschoben werden (siehe unten), werden Besprechungen in Teams Besprechungen konvertiert, andernfalls bleiben Besprechungen Skype for Business, werden jedoch migriert, sodass sie online statt lokal gehostet werden.  Die Migration von Besprechungen geschieht asynchron und beginnt ungefähr 90 Minuten nach dem Verschieben des Benutzers.  Den Status der Besprechungsmigration können Sie mit [Get-csMeetingMigrationStatus](../../SfbOnline/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms.md#managing-mms) ermitteln. Bitte beachten Sie: Alle Inhalte, die im Vorfeld der Besprechung hochgeladen wurden, werden nicht verschoben.

Um Benutzer in Teams zu verschieben, verwenden Sie entweder das Cmdlet Move-CsUser oder die Skype for Business Administrator-Systemsteuerung, die beide lokale Tools sind. Diese Tools unterstützen die folgenden Verschiebungspfade:

- [Von Skype for Business Server (lokal) direkt zu Teams Only](move-users-from-on-premises-to-teams.md) (wodurch sie auch zu Skype for Business Online verschoben werden).  Das Verhalten für den direkten Wechsel von der lokalen Umgebung zu Teams Nur ist jetzt automatisch, unabhängig davon, welche Version von Skype for Business Server oder Lync Server verwendet wird. Es ist nicht mehr erforderlich, den `-MoveToTeams` Switch anzugeben, um dieses Verhalten zu erhalten.  
- [Von online (unabhängig davon, ob Teams Nur oder nicht), zu lokal](move-users-from-the-cloud-to-on-premises.md).

> [!NOTE] 
> Es ist nicht mehr erforderlich, die Option "-MoveToTeams" in Move-CsUser anzugeben, um Benutzer direkt von der lokalen Umgebung zu TeamsOnly zu verschieben. Wenn dieser Switch nicht angegeben wurde, wurden Benutzer zuvor von Skype for Business Server lokal zu Skype for Business Online verwaltet, und ihr Modus bleibt unverändert. Wenn ein Benutzer jetzt mit Move-CsUser von der lokalen Umgebung in die Cloud verschoben wird, wird benutzern automatisch der TeamsOnly-Modus zugewiesen, und ihre Besprechungen aus der lokalen Umgebung werden automatisch in Teams Besprechungen konvertiert, so als ob der `-MoveToTeams` Switch angegeben worden wäre, unabhängig davon, ob der Switch tatsächlich angegeben wurde. 
> 

## <a name="required-administrative-credentials"></a>Erforderliche administrative Anmeldeinformationen

Um Benutzer zwischen der lokalen Umgebung und der Cloud zu verschieben, müssen Sie sowohl in der lokalen Skype for Business Server umgebung als auch in der Teams Organisation ein Konto mit ausreichenden Berechtigungen verwenden. Sie können entweder ein Konto verwenden, das über alle erforderlichen Berechtigungen verfügt, oder Sie können zwei Konten verwenden. In diesem Fall greifen Sie mit lokalen Anmeldeinformationen auf die lokalen Tools zu und geben dann in diesen Tools zusätzliche Anmeldeinformationen für ein Teams Administratorkonto an.  

- In der lokalen Umgebung muss der Benutzer, der die Verschiebung ausführt, über die ROLLE "CSServerAdministrator" in Skype for Business Server verfügen.
- In Teams muss der Benutzer, der die Verschiebung ausführt, eines der folgenden Kriterien erfüllen:
  - Der Benutzer ist Mitglied der Rolle "Globaler Administrator".
  - Der Benutzer ist Mitglied der Rollen Teams Administrator und Benutzeradministrator.
  - Der Benutzer ist Mitglied der Rollen Skype for Business Administrator und Benutzeradministrator.  

    > [!Important]
    > - Wenn Sie die Skype for Business Administrator-Systemsteuerung verwenden, werden Sie aufgefordert, Anmeldeinformationen für ein Microsoft 365 Konto mit den entsprechenden Rollen anzugeben, wie oben erwähnt. Sie müssen ein Konto angeben, das auf .onmicrosoft.com endet. Wenn dies nicht möglich ist, verwenden Sie das Cmdlet Move-CsUser.
    >- Wenn Sie Move-CsUser in PowerShell verwenden, können Sie entweder ein Konto verwenden, das auf .onmicrosoft.com endet, oder Sie können jedes lokale Konto verwenden, das mit Azure AD synchronisiert wird, vorausgesetzt, Sie geben auch den Parameter HostedMigrationOverrideUrl im Cmdlet an. Der Wert der URL für die Außerkraftsetzung der gehosteten Migration ist eine Variante der folgenden URL: https://adminXX.online.lync.com/HostedMigration/hostedmigrationService.svc<br>Ersetzen Sie in der obigen URL den XX durch zwei oder drei Zeichen, die wie folgt bestimmt werden:
    >   - Führen Sie in einer Teams PowerShell-Sitzung das folgende Cmdlet aus:<br>`Get-CsTenant|ft identity`
    >   - Der resultierende Wert weist das folgende Format auf:<br>`OU=<guid>,OU=OCS Tenants,DC=lyncXX001,DC=local`
    >   - Der zwei- oder dreistellige Code ist der XX im Abschnitt DC=lyncXX001. Wenn es sich um einen aus zwei Zeichen bestehenden Code handelt, handelt es sich um eine Ziffer gefolgt von einer Zahl (z. B. 0a). Wenn es sich um einen aus drei Zeichen bestehenden Code handelt, sind dies zwei Buchstaben gefolgt von einer Ziffer (z. B. jp1). In allen Fällen wird 001 unmittelbar nach dem XX-Code angezeigt.


## <a name="voice-configuration-requirements"></a>VoIP-Konfigurationsanforderungen

Wenn Benutzer lokal für Enterprise-VoIP konfiguriert sind, müssen Sie die Aktualisierung ihrer VoIP-Konfiguration koordinieren, wenn Sie sie in die Onlineumgebung verschieben, oder Sie können sie alternativ auch ohne Telefoniefunktionen migrieren. Die verfügbaren Optionen hängen davon ab, ob der Benutzer den Teams oder Skype for Business Client verwendet, sobald er online ist:

- Sie können den Telefonieanbieter eines Benutzers so aktualisieren, dass er einen [Microsoft-Anrufplan verwendet.](/microsoftteams/calling-plans-for-office-365) Dies ist eine Option, ob Benutzer Teams oder Skype for Business Clients verwenden.
- Sie können weiterhin Ihren lokalen PSTN-Anbieter verwenden:
  - VoIP-Benutzer, die Teams verwenden, müssen für [Direct Routing](/microsoftteams/direct-routing-plan)konfiguriert sein. Direct Routing ist nur verfügbar, nachdem der Benutzer von der lokalen Umgebung in die Onlineumgebung verschoben wurde.
  - VoIP-Benutzer, die den Skype for Business-Client verwenden, nachdem sie online verschoben wurden, müssen für Skype for Business Hybrid VoIP-Funktionalität konfiguriert werden.

Weitere Informationen zu Telefonieoptionen in Hybridumgebungen sowie eine Unterstützungsmatrix finden Sie unter [Benutzerkonten in einer Hybridumgebung mit PSTN-Konnektivität.](/microsoftteams/direct-routing-user-accounts-in-a-hybrid-environment)

## <a name="other-considerations"></a>Andere Überlegungen

Die Richtlinien (z. B. die Kontrolle von Nachrichten, Besprechungen und Anrufverhalten) in lokalen und Online-Umgebungen sind unabhängig voneinander. Sie sollten erwägen, alle Richtlinien in der Umgebung zu konfigurieren und dem Benutzer zuzuweisen, bevor Sie diesen Benutzer von der lokalen Umgebung in die Cloud verschieben, damit er die richtige Konfiguration hat, sobald er in die Onlineumgebung migriert wird.

## <a name="see-also"></a>Siehe auch

[Verschieben von Benutzern aus der lokalen Bereitstellung nach Microsoft Teams](move-users-from-on-premises-to-teams.md)

[Einrichten von Meeting Migration Service (MMS)](../../SfbOnline/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms.md)

[Planen von direktem Routing](/microsoftteams/direct-routing-plan)

[Move-CsUser](/powershell/module/skype/move-csuser)
