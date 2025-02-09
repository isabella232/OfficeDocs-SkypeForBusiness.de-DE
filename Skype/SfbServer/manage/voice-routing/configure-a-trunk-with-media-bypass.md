---
title: 'Skype for Business Server: Konfigurieren eines Trunks mit Medienumgehung'
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
description: Konfigurieren eines Trunks mit aktivierter Medienumgehung "
ms.openlocfilehash: 44bc66a1407e42f4cf8611f1e7f5aec0d0c0819d
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58635269"
---
# <a name="skype-for-business-server---configure-a-trunk-with-media-bypass"></a>Skype for Business Server: Konfigurieren eines Trunks mit Medienumgehung 

Führen Sie die folgenden Schritte aus, um einen Trunk mit aktivierter Medienumgehung zu konfigurieren. Informationen zum Konfigurieren eines Trunks mit deaktivierter Medienumgehung finden Sie unter [Konfigurieren eines Trunks ohne Medienumgehung in Skype for Business Server.](configure-a-trunk-without-media-bypass.md) Die Medienumgehung ist nützlich, wenn Sie die Anzahl von bereitgestellten Vermittlungsservern reduzieren möchten. Üblicherweise wird ein Vermittlungsserverpool an einem zentralen Standort bereitgestellt und steuert die Gateways an den Zweigstellenstandorten. Durch Aktivierung der Medienumgehung können Mediendaten für PSTN-Anrufe (Telefonfestnetz) von Clients an Zweigstellenstandorten direkt durch die Gateways an diesen Standorten geleitet werden. Skype for Business Server Ausgehende Anrufrouten und Enterprise-VoIP Richtlinien müssen ordnungsgemäß konfiguriert sein, damit PSTN-Anrufe von Clients an einem Zweigstellenstandort an das entsprechende Gateway weitergeleitet werden.

Es wird dringend empfohlen, die Medienumgehung zu aktivieren. Bevor Sie jedoch die Medienumgehung für einen SIP-Trunk aktivieren, vergewissern Sie sich, dass Ihr qualifizierter SIP-Trunkanbieter die Medienumgehung unterstützt und die Anforderungen für die erfolgreiche Aktivierung des Szenarios erfüllen kann. Insbesondere muss der Anbieter über die IP-Adressen der Server im internen Netzwerk Ihrer Organisation verfügen. Wenn der Anbieter dieses Szenario nicht unterstützen kann, ist die Medienumgehung nicht erfolgreich. Ausführliche Informationen finden Sie unter [Plan for media bypass in Skype for Business](../../plan-your-deployment/enterprise-voice-solution/media-bypass.md).

> [!NOTE]
> Die Medienumgehung funktioniert nicht mit jedem PSTN-Gateway, jeder IP-Nebenstellenanlage und jedem Session Border Controller (SBC). Microsoft hat eine Reihe von PSTN-Gateways und SBCs mit zertifizierten Partnern getestet und einige Tests mit Ip-Nebenstellenanlagen von Cisco durchgeführt. Die Medienumgehung wird nur für Produkte und Versionen unterstützt, die auf der Seite ["Telefonieinfrastruktur für Skype for Business Server"](../../../SfbPartnerCertification/certification/infra-gateways.md) aufgeführt sind. 


Eine Trunkkonfiguration, wie unten beschrieben, gruppiert einen Satz von Parametern, die auf Trunks angewendet werden, denen diese Trunkkonfiguration zugewiesen ist. Eine bestimmte Trunkkonfiguration kann auf globale Ebene (für alle Trunks, die keine speziellere Standort- oder Poolkonfiguration haben) oder für einen Standort oder Pool festgelegt werden. Die Trunkkonfiguration auf Poolebene wird verwendet, um eine bestimmte Trunkkonfiguration auf einen einzelnen Trunk anzuwenden.

**So konfigurieren Sie einen Trunk mit Medienumgehung**

1. Öffnen Sie Skype für die Busines Server-Systemsteuerung.
2. Klicken Sie in der linken Navigationsleiste auf **VoIP-Routing** und dann auf **Trunkkonfiguration**.
3. Verwenden Sie auf der Seite **Trunkkonfiguration** eine der folgenden Methoden, um einen Trunk zu konfigurieren:
    - Doppelklicken Sie auf einen vorhandenen Trunk (z. B. den Trunk **Global**), um das Dialogfeld **Trunkkonfiguration bearbeiten** anzuzeigen.
    - Klicken Sie auf **Neu**, und wählen Sie einen Bereich für die neue Trunkkonfiguration aus:
        - **Standorttrunk:** Wählen Sie den Standort für diese Trunkkonfiguration aus **"Standort auswählen"** aus, und klicken Sie dann auf **"OK".** Wenn bereits eine Trunkkonfiguration für einen Standort erstellt wurde, wird der Standort nicht unter **Standort auswählen** angezeigt. Diese Trunkkonfiguration wird auf alle Trunks am Standort angewendet.
        - **Pooltrunk:** Wählen Sie den Namen des Trunks aus, für den diese Trunkkonfiguration gilt. Dieser Trunk kann der Stammtrunk oder alle zusätzlichen Trunks sein, die im Topologie-Generator definiert sind. Klicken Sie unter **"Dienst auswählen"** auf **"OK".** Wenn bereits eine Trunkkonfiguration für einen bestimmten Trunk erstellt wurde, erscheint dieser Trunk nicht unter **Dienst auswählen**.
    
    > [!NOTE]
    > Nachdem Sie den Bereich für die Trunkkonfiguration ausgewählt haben, kann dieser nicht mehr geändert werden. Das Feld **Name** wird mit dem Namen der Trunkkonfiguration vorausgefüllt, der dem Standort oder Dienst zugeordnet ist, und kann nicht geändert werden. 

5. Geben Sie einen Wert in **maximal unterstützten frühen Dialogfeldern** an. Dies ist die maximale Anzahl verzweigter Antworten, die ein PSTN-Gateway, eine IP-Nebenstellenanlage oder ein SBC (Session Border Controller) von ITSP an eine INVITE empfangen kann, die an den Vermittlungsserver gesendet wird. Der Standardwert lautet 20.

    > [!NOTE] 
    > Bevor Sie diesen Wert ändern, setzen Sie sich mit Ihrem Dienstanbieter oder Gerätehersteller in Verbindung, um genaue Informationen zu den Funktionen Ihres Systems zu erhalten. 

6. Wählen Sie unter **Unterstützte Verschlüsselungsstufe** eine der folgenden Optionen aus:
    - **Erforderlich**: Zum Schutz des Datenverkehrs zwischen dem Vermittlungsserver und dem Gateway oder der Nebenstellenanlage (Private Branch Exchange, PBX) muss die SRTP-Verschlüsselung (Secure Real-Time Transport Protocol) verwendet werden.
    - **Optional**: Die SRTP-Verschlüsselung wird verwendet, wenn der Dienstanbieter oder Gerätehersteller dieses Protokoll unterstützt.
    - **Nicht unterstützt**: Die SRTP-Verschlüsselung wird vom Dienstanbieter oder Gerätehersteller nicht unterstützt und daher nicht verwendet.
7. Aktivieren Sie das Kontrollkästchen **Medienumgehung aktivieren**, wenn Sie eine Umgehung des Vermittlungsservers zur Verarbeitung durch den Trunkpeer wünschen.

    > [!IMPORTANT]
    > Damit die Medienumgehung ordnungsgemäß funktioniert, müssen das PSTN-Gateway, die IP-Nebenstellenanlage oder der SBC beim Dienstanbieter bestimmte Funktionen unterstützen. Ausführliche Informationen finden Sie unter [Plan for media bypass in Skype for Business](../../plan-your-deployment/enterprise-voice-solution/media-bypass.md). 

8. Aktivieren Sie das Kontrollkästchen **Zentrale Medienverarbeitung**, wenn ein bekannter Medienendpunkt vorhanden ist (beispielsweise ein PSTN-Gateway, bei dem der Medienendpunkt dieselbe IP-Adresse aufweist wie der signalgebende Endpunkt). Deaktivieren Sie dieses Kontrollkästchen, wenn der Trunk über keinen bekannten Medienendpunkt verfügt.
9. Wenn der Trunkpeer den Empfang von SIP REFER-Anforderungen vom Vermittlungsserver unterstützt, aktivieren Sie das **Kontrollkästchen Senden aktivieren über das Kontrollkästchen Gateway.** 

    > [!NOTE] 
    > Wenn Sie diese Option deaktivieren, während die Option **Medienumgehung aktivieren** ausgewählt ist, sind zusätzliche Einstellungen erforderlich. Wenn der Trunkpeer den Empfang von SIP REFER-Anforderungen vom Vermittlungsserver nicht unterstützt und die Medienumgehung aktiviert ist, müssen Sie außerdem das Cmdlet **Set-CsTrunkConfiguration** ausführen, um RTCP für aktive und gehaltene Anrufe zu deaktivieren, um geeignete Bedingungen für die Medienumgehung zu schaffen. Alternativ können Sie **"Refer aktivieren" mithilfe der Drittanbieteranrufsteuerung** auswählen, wenn übertragene Anrufe medienumgehungen werden sollen und das Gateway keine SIP REFER-Anforderungen unterstützt. 

10. (Optional) Um Routing zwischen Trunks zu ermöglichen, können Sie dieser Trunkkonfiguration PSTN-Verwendungseinträge zuordnen und konfigurieren. Die dieser Trunkkonfiguration zugeordneten PSTN-Verwendungen werden für alle eingehenden Anrufe über den Trunk angewendet, der nicht von einem Skype for Business Server-Endpunkt stammt. Verwenden Sie eine der folgenden Methoden, um die einer Trunkkonfiguration zugeordneten PSTN-Verwendungseinträge zu verwalten:
    - Klicken Sie auf **"Auswählen",** um einen oder mehrere Datensätze aus einer Liste aller PSTN-Verwendungsdatensätze auszuwählen, die in Ihrer Enterprise-VoIP Bereitstellung verfügbar sind. Markieren Sie die Einträge, die Sie dieser Trunkkonfiguration zuordnen möchten, und klicken Sie dann auf **OK**.
    - Markieren Sie einen Eintrag, und klicken Sie auf **Entfernen**, um einen PSTN-Verwendungseintrag aus dieser Trunkkonfiguration zu entfernen.
    - Führen Sie die folgenden Schritte aus, um einen neuen PSTN-Verwendungseintrag zu definieren und dieser Trunkkonfiguration zuzuordnen:
        1. Klicken Sie auf **Neu**.
        2. Geben Sie im Feld **Name** einen eindeutigen beschreibenden Namen für den Eintrag ein.
            > [!NOTE] 
            > Der Name des PSTN-Verwendungsdatensatzes muss innerhalb der Enterprise-VoIP-Bereitstellung eindeutig sein. Nach dem Speichern des Datensatzes kann das Feld **Name** nicht mehr bearbeitet werden. 
        3. Verwenden Sie eine der folgenden Methoden, um Routen für diesen PSTN-Verwendungseintrag zuzuordnen und zu konfigurieren:
            - Klicken Sie auf **"Auswählen",** um eine oder mehrere Routen aus der Liste aller verfügbaren Routen in Ihrer Enterprise-VoIP Bereitstellung auszuwählen. Markieren Sie die Routen, die Sie dieser Trunkkonfiguration zuordnen möchten, und klicken Sie dann auf **OK**. 
            - Zum Entfernen einer Route aus dem PSTN-Verwendungseintrag markieren Sie die Route, und klicken Sie auf **Entfernen**.
            - Klicken Sie auf **Neu**, um eine neue Route zu definieren und sie diesem PSTN-Verwendungseintrag zuzuordnen. 
            - Markieren Sie die Route, und klicken Sie auf **Details anzeigen**, um eine Route zu bearbeiten, die dem PSTN-Verwendungseintrag zugeordnet ist. 
        4. Klicken Sie auf **OK**.
    - Führen Sie die folgenden Schritte aus, um einen PSTN-Verwendungseintrag zu bearbeiten, der bereits dieser Trunkkonfiguration zugeordnet ist:
        1. Markieren Sie den PSTN-Verwendungseintrag, den Sie bearbeiten möchten, und klicken Sie auf **Details anzeigen**.
        2. Verwenden Sie eine der folgenden Methoden, um Routen für diesen PSTN-Verwendungseintrag zuzuordnen und zu konfigurieren:
            - Klicken Sie auf **"Auswählen",** um eine oder mehrere Routen aus der Liste aller verfügbaren Routen in Ihrer Enterprise-VoIP Bereitstellung auszuwählen. Markieren Sie die Routen, die Sie dieser Trunkkonfiguration zuordnen möchten, und klicken Sie dann auf **OK**. 
            - Zum Entfernen einer Route aus dem PSTN-Verwendungseintrag markieren Sie die Route, und klicken Sie auf **Entfernen**.
            - Klicken Sie auf **Neu**, um eine neue Route zu definieren und sie diesem PSTN-Verwendungseintrag zuzuordnen. 
            - Markieren Sie die Route, und klicken Sie auf **Details anzeigen**, um eine Route zu bearbeiten, die dem PSTN-Verwendungseintrag zugeordnet ist. 
        3. Klicken Sie auf **OK**.

    > [!Important]
    > Es ist wichtig, PSTN-Verwendungsdatensätze gemäß dem Vermittlungsserverpeer zuzuordnen, der dem zu konfigurierenden Trunk zugeordnet ist. Wenn der Vermittlungsserverpeer ein PSTN-Gateway oder ein Session Border Controller (SBC) ist, wird dringend empfohlen, die Trunkkonfiguration keinem PSTN-Verwendungsdatensatz zuzuordnen, der an ein PSTN-Ziel oder andere downstreame Systeme, die über Skype for Business Server verbunden sind, leitet. 

11. Ordnen Sie die PSTN-Verwendungseinträge zur Erzielung optimaler Leistung an. Wenn Sie die Position eines Eintrags in der Liste ändern möchten, markieren Sie den PSTN-Verwendungseintrag, und klicken Sie auf den nach oben oder nach unten weisenden Pfeil.

    > [!Important]
    > Die Reihenfolge, in der PSTN-Verwendungseinträge in der Trunkkonfiguration aufgeführt werden, ist relevant. Skype for Business Server durchläuft die Liste von oben nach unten. 

12. **Aktivieren Sie die RTP-Verriegelung,** um Medienumgehung für Clients hinter einer Netzwerkadressübersetzung (NETWORK Address Translation, NAT) oder Firewall und einem SBC zu aktivieren, der die Verriegelung unterstützt.
13. **Enable forward call history** should be selected to enable sending of call history information to the gateway peer of the Mediation Server.
14. **Enable forward P-Asserted-Identity data** should be selected to enable the P-Asserted-Identity (PAI) call originator information to be forwarded between the Mediation Server side and gateway side (and vice versa), when present.
15. **Failovertimer für Ausgangsrouting aktivieren** sollte ausgewählt sein, um ein schnelleres Failover zu ermöglichen. Das diesem Trunk zugeordnete Gateway kann innerhalb von 10 Sekunden eine Benachrichtigung senden, dass ein ausgehender Anruf verarbeitet wird. Eine Umleitung zu einem anderen Trunk erfolgt, wenn diese Benachrichtigung nicht vom Vermittlungsserver empfangen wird. In Netzwerken, in denen Latenz die Reaktionszeit verzögern kann oder das Gateway länger als 10 Sekunden benötigt, um zu antworten, sollte das schnelle Failover deaktiviert werden.
16. (Optional) Zuordnen und Konfigurieren von **Übersetzungsregeln für die wählende Nummer** für den Trunk. Diese Übersetzungsregeln gelten für die Anrufnummer für ausgehende Anrufe.
    - Klicken Sie auf **"Auswählen",** um eine oder mehrere Regeln aus einer Liste aller Übersetzungsregeln auszuwählen, die in Ihrer Enterprise-VoIP Bereitstellung verfügbar sind. Klicken Sie im Abschnitt **Übersetzungsregeln auswählen** auf die Regeln, die Sie dem Trunk zuordnen möchten, und klicken Sie anschließend auf **OK**.
    - Klicken Sie auf **Neu**, um eine neue Übersetzungsregel zu definieren und dem Trunk zuzuordnen. Ausführliche Informationen zum Definieren einer neuen Regel finden Sie unter [Definieren von Übersetzungsregeln in Skype for Business Server](defining-translation-rules.md).
    - Klicken Sie auf den Regelnamen und anschließend auf **Details anzeigen**, um eine Übersetzungsregel zu bearbeiten, die bereits dem Trunk zugeordnet ist. Ausführliche Informationen finden Sie unter [Definieren von Übersetzungsregeln in Skype for Business Server.](defining-translation-rules.md)
    - Um eine vorhandene Übersetzungsregel als Ausgangspunkt für die Definition einer neuen Regel zu verwenden, klicken Sie auf den Regelnamen, klicken Sie auf **Kopieren** und anschließend auf **Einfügen**. Ausführliche Informationen finden Sie unter [Definieren von Übersetzungsregeln in Skype for Business Server.](defining-translation-rules.md)
    - Wenn Sie eine Übersetzungsregel vom Trunk entfernen möchten, markieren Sie den Regelnamen, und klicken Sie auf **Entfernen**.
    > [!Warning]
    > Ordnen Sie einem Trunk keine Übersetzungsregeln zu, wenn Sie Übersetzungsregeln für den zugeordneten Trunkpeer konfiguriert haben, da zwischen den zwei Regeln Konflikte auftreten können. 

17. (Optional) Zuordnen und Konfigurieren von **Übersetzungsregeln für die gewählte Nummer** für den Trunk. Diese Übersetzungsregeln werden bei ausgehenden Anrufen auf die gewählte Nummer angewendet.
    - Klicken Sie auf **"Auswählen",** um eine oder mehrere Regeln aus einer Liste aller Übersetzungsregeln auszuwählen, die in Ihrer Enterprise-VoIP Bereitstellung verfügbar sind. Klicken Sie im Abschnitt **Übersetzungsregeln auswählen** auf die Regeln, die Sie dem Trunk zuordnen möchten, und klicken Sie anschließend auf **OK**.
    - Klicken Sie auf **Neu**, um eine neue Übersetzungsregel zu definieren und dem Trunk zuzuordnen. Ausführliche Informationen zum Definieren einer neuen Regel finden Sie unter [Definieren von Übersetzungsregeln in Skype for Business Server](defining-translation-rules.md).
    - Klicken Sie auf den Regelnamen und anschließend auf **Details anzeigen**, um eine Übersetzungsregel zu bearbeiten, die bereits dem Trunk zugeordnet ist. Ausführliche Informationen finden Sie unter [Definieren von Übersetzungsregeln in Skype for Business Server.](defining-translation-rules.md)
    - Um eine vorhandene Übersetzungsregel als Ausgangspunkt für die Definition einer neuen Regel zu verwenden, klicken Sie auf den Regelnamen, klicken Sie auf **Kopieren** und anschließend auf **Einfügen**. Ausführliche Informationen finden Sie unter [Definieren von Übersetzungsregeln in Skype for Business Server.](defining-translation-rules.md)
    - Wenn Sie eine Übersetzungsregel vom Trunk entfernen möchten, markieren Sie den Regelnamen, und klicken Sie auf **Entfernen**.

    > [!Warning] 
    > Ordnen Sie einem Trunk keine Übersetzungsregeln zu, wenn Sie Übersetzungsregeln für den zugeordneten Trunkpeer konfiguriert haben, da zwischen den zwei Regeln Konflikte auftreten können. 

18. Stellen Sie sicher, dass die Übersetzungsregeln des Trunks in der richtigen Reihenfolge angeordnet sind. Wenn Sie die Position einer Regel in der Liste ändern möchten, markieren Sie den Regelnamen, und klicken Sie auf den nach oben oder nach unten weisenden Pfeil.

    >[!Important] 
    > Skype for Business Server durchläuft die Übersetzungsregelliste von oben nach unten und verwendet die erste Regel, die der gewählten Nummer entspricht. Wenn Sie einen Trunk so konfigurieren, dass eine gewählte Nummer mit mehr als einer Übersetzungsregel übereinstimmen kann, müssen Sie sicherstellen, dass die einschränkenderen Regeln über den weniger einschränkenden Regeln angeordnet sind. Wenn Sie beispielsweise eine Übersetzungsregel verwenden, die mit einer beliebigen elfstelligen Nummer übereinstimmt, und eine andere Übersetzungsregel auf elfstellige Nummern zutrifft, die mit +1425 beginnen, muss die Regel für eine beliebige elfstellige Nummer *unter* der restriktiveren Regel platziert werden. 

19. Nachdem Sie die Trunkkonfiguration abgeschlossen haben, klicken Sie auf **OK**.
20. Klicken Sie auf der Seite **Trunkkonfiguration** auf **Commit**, und klicken Sie anschließend auf **Commit für alle**. 

    > [!Note]
    > Jedes Mal, wenn Sie eine Trunkkonfiguration erstellen oder ändern, müssen Sie den Befehl **Commit für alle** ausführen, um die Konfigurationsänderung zu veröffentlichen. Ausführliche Informationen finden Sie unter [Veröffentlichen ausstehender Änderungen an der VoIP-Routingkonfiguration.](/previous-versions/office/lync-server-2013/lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration) (BENÖTIGEN SIE EINEN NEUEN LINK?)

Nachdem Sie den Trunk konfiguriert haben, fahren Sie mit der Konfiguration der Medienumgehung fort, indem Sie zwischen globalen Medienumgehungsoptionen wählen, wie unter ["Bereitstellen der Medienumgehung in Skype for Business Server"](../../deploy/deploy-enterprise-voice/deploy-media-bypass.md)beschrieben.
