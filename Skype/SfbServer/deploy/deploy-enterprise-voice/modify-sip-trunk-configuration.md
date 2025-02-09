---
title: 'Skype for Business Server: Ändern der SIP-Trunkkonfigurationseinstellungen'
ms.reviewer: ''
ms.author: v-cichur
author: cichur
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom: ''
ms.assetid: 7d68b09c-9ea0-43bd-997c-df887869d607
description: 'Zusammenfassung: Erfahren Sie, wie Sie die SIP-Trunkkonfigurationseinstellungen mithilfe der Skype for Business Server Systemsteuerung ändern.'
ms.openlocfilehash: 370e6522d07461276c881798d094fa31fb71e9bb
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58620121"
---
# <a name="skype-for-business-server-modify-sip-trunk-configuration-settings"></a>Skype for Business Server: Ändern der SIP-Trunkkonfigurationseinstellungen 
 
**Zusammenfassung:** Erfahren Sie, wie Sie die SIP-Trunkkonfigurationseinstellungen mithilfe der Skype for Business Server Systemsteuerung ändern.
  
Sip trunk configuration settings define the relationship and capabilities between a Mediation Server and the public switched telephone network (PSTN) gateway, an IP-Public Branch eXchange (PBX) or a Session Border Controller (SBC) at the service provider. Mit diesen Einstellungen kann Folgendes angegeben werden:
  
- Ob die Medienumgebung für Trunks aktiviert werden soll.
    
- Die Bedingungen, unter denen RTCP-Pakete (Realtime Transport Control Protocol) gesendet werden.
    
- Gibt an, ob die SRTP-Verschlüsselung (Secure Realtime Transport Protocol) für jeden Trunk erforderlich ist.
    
Wenn Sie Skype for Business Server installieren, wird eine globale Auflistung von SIP-Trunkkonfigurationseinstellungen für Sie erstellt. Außerdem können Administratoren benutzerdefinierte Einstellungssammlungen auf Standortebene oder Dienstebene erstellen (nur für den PSTN-Gatewaydienst). Jede dieser Auflistungen kann später entweder mit Skype for Business Server Systemsteuerung oder Skype for Business Server Verwaltungsshell geändert werden.
  
Beim Ändern der SIP-Trunkkonfigurationseinstellungen mit Skype for Business Server Systemsteuerung stehen Ihnen die folgenden Optionen zur Verfügung.
  
|**UI-Einstellung**|**PowerShell-Parameter**|**Beschreibung**|
|:-----|:-----|:-----|
|Name  <br/> |Identität  <br/> |Eindeutige ID für die Sammlung. Diese Eigenschaft ist schreibgeschützt. Sie können die Identität einer Sammlung an Trunkkonfigurationseinstellungen nicht ändern.  <br/> |
|Beschreibung  <br/> |Beschreibung  <br/> |Bietet Administratoren eine Möglichkeit, zusätzliche Informationen zu den Einstellungen zu speichern (z. B. Zweck der Trunkkonfiguration).  <br/> |
|Maximal unterstützte frühe Dialoge  <br/> |MaxEarlyDialogs  <br/> |Die maximale Anzahl von gegabelten Antworten, die ein PSTN-Gateway, eine IP-Nebenstellenanlage oder ein SBC (Session Border Controller) des Dienstanbieters auf an den Vermittlungsserver gesendete Einladungen empfangen kann.  <br/> |
|Unterstützte Verschlüsselungsstufe  <br/> |SRTPMode  <br/> | Legt den Umfang der Unterstützung zum Schutz von Mediendatenverkehr zwischen dem Vermittlungsserver und dem PSTN-Gateway, der IP-Nebenstellenanlage oder dem SBC (Session Border Controller) des Dienstanbieters fest. Bei der Medienumgehung muss dieser Wert mit der Einstellung "EncryptionLevel" in der Medienkonfiguration kompatibel sein. Die Medienkonfiguration wird mithilfe der Cmdlets ["New-CsMediaConfiguration"](/powershell/module/skype/new-csmediaconfiguration) und ["Set-CsMediaConfiguration"](/powershell/module/skype/set-csmediaconfiguration) festgelegt. <br/>  Gültige Werte sind: <br/>  Required: Die SRTP-Verschlüsselung muss verwendet werden. <br/>  Optional: SRTP wird verwendet, wenn es vom Gateway unterstützt wird. <br/>  Not Supported: Die SRTP-Verschlüsselung wird nicht unterstützt und daher auch nicht verwendet. <br/>  "SRTPMode" wird nur verwendet, wenn das Gateway zur Verwendung von TLS (Transport Layer Security) konfiguriert ist. Wenn das Gateway mit dem Transportprotokoll TCP (Transmission Control Protocol) konfiguriert ist, wird "SRTPMode" intern auf "Not Supported" festgelegt.<br/> |
|Support melden  <br/> |Enable3pccRefer  <br/> EnableReferSupport  <br/> |Mit der Einstellung **Refer-Anforderungen an das Gateway senden** unterstützt der Trunk den Empfang von Refer-Anforderungen vom Vermittlungsserver.  <br/> Mit der Einstellung **Refer-Anforderungen mit 3pcc senden** kann das 3pcc-Protokoll verwendet werden, damit weitergeleitete Anrufe den gehosteten Standort umgehen können. 3pcc ist auch unter dem Namen "Third Party Call Control" bekannt und tritt auf, wenn ein Drittanbieter verwendet wird, um zwei Anrufer miteinander zu verbinden (z. B. wenn ein Anruf von Person A an Person B über eine Telefonzentrale durchgestellt wird).<br/> |
|Medienumgehung aktivieren  <br/> |EnableBypass  <br/> |Gibt an, ob die Medienumgehung für diesen Trunk aktiviert ist. Die Medienumgehung kann nur aktiviert werden, wenn auch **Zentrale Medienverarbeitung** aktiviert ist.<br/> |
|Zentrale Medienverarbeitung  <br/> |1000000000  <br/> |Gibt an, ob ein bekannter Medienendpunkt vorhanden ist. (Ein Beispiel für einen bekannten Medienendpunkt ist ein PSTN-Gateway, bei dem der Medienendpunkt die gleiche IP-Adresse hat wie der Signaldatenverkehr-Endpunkt.)  <br/> |
|RTP-Latching aktivieren  <br/> |EnableRTPLatching  <br/> |Gibt an, ob SIP-Trunks RTP-Latching unterstützen oder nicht. RTP-Latching ist eine Technologie, die RTP-/RTCP-Verbindungen über NAT (Network Address Translator, Netzwerkadressenübersetzung) oder eine Firewall ermöglicht.  <br/> |
|Weiterleiten der Anrufliste aktivieren  <br/> |ForwardCallHistory  <br/> |Gibt an, ob Informationen zum Anruferverlauf durch den Trunk weitergeleitet werden.  <br/> |
|Weiterleiten von P-Asserted-Identity-Daten aktivieren  <br/> |ForwardPAI  <br/> |Gibt an, ob der PAI-Header (P-Asserted-Identity) zusammen mit dem Anruf weitergeleitet wird. Der PAI-Header bietet eine Möglichkeit, die Identität des Anrufers zu überprüfen.  <br/> |
|Timer für Ausgangsroutingfailover aktivieren  <br/> |EnableFastFailoverTimer  <br/> |Gibt an, ob ausgehende Anrufe, die vom Gateway nicht innerhalb von 10 Sekunden beantwortet werden, an den nächsten verfügbaren Trunk weitergeleitet werden. Wenn keine weiteren Trunks verfügbar sind, wird der Anruf automatisch beendet. In einer Organisation mit langsamen Netzwerk- und Gateway-Reaktionen könnte dies dazu führen, dass Anrufe unnötigerweise beendet werden.  <br/> |
|Zugeordnete PSTN-Verwendungen  <br/> |PSTNUsages  <br/> |Eine Sammlung von dem Trunk zugewiesenen PSTN-Verwendungen.  <br/> |
|Übersetzte Nummer zum Testen  <br/> |Nicht zutreffend  <br/> |Eine Telefonnummer, die für Ad-hoc-Tests der Trunkkonfigurationseinstellungen verwendet werden kann.  <br/> |
|Zugehörige Übersetzungsregeln  <br/> |OutboundTranslationRulesList  <br/> |Sammlung an Regeln für die Telefonnummernübersetzung für Anrufe, die per Ausgangsrouting verarbeitet werden (Anrufe, die an Ziele in Nebenstellenanlagen oder im Telefonfestnetz weitergeleitet werden).  <br/> |
|Übersetzungsregeln für angerufene Nummern  <br/> |OutboundCallingNumberTranslationRulesList  <br/> |Sammlung an Regeln für die Nummernübersetzung für ausgehende Anrufe, die dem Trunk zugewiesen sind.  <br/> |
|Testtelefonnummer  <br/> |Nicht zutreffend  <br/> |Eine Telefonnummer, die für Ad-hoc-Tests der Übersetzungsregeln verwendet werden kann.  <br/> |
|Anrufende Nummer  <br/> |Nicht zutreffend  <br/> |Gibt an, dass die zu testende Telefonnummer die Telefonnummer des Anrufers ist.  <br/> |
|Angerufene Nummer  <br/> |Nicht zutreffend  <br/> |Gibt an, dass die zu testende Telefonnummer die Telefonnummer der Person ist, die angerufen wird.  <br/> |
   
> [!NOTE]
> Die Lync Server CsTrunkConfiguration-Cmdlets unterstützen zusätzliche Eigenschaften, die in der Lync Server-Systemsteuerung nicht angezeigt werden. Weitere Informationen finden Sie im Hilfethema zum [Cmdlet "Set-CsTrunkConfiguration".](/powershell/module/skype/set-cstrunkconfiguration)
  
### <a name="to-modify-sip-trunk-configuration-settings-by-using-skype-for-business-server-control-panel"></a>So ändern Sie die SIP-Trunkkonfigurationseinstellungen mithilfe Skype for Business Server Systemsteuerung

1. Klicken Sie in Skype for Business Server Systemsteuerung auf **VoIP-Routing** und dann auf **Trunkkonfiguration.**
    
2. Doppelklicken Sie auf der Registerkarte **Trunkkonfiguration** auf die Trunkkonfigurationseinstellungen, die Sie ändern möchten. Beachten Sie, dass Sie immer nur eine Einstellung bearbeiten können. Wenn Sie die gleichen Änderungen an mehreren Sammlungen vornehmen möchten, verwenden Sie Windows PowerShell.
    
3. Treffen Sie im Dialogfeld **Trunkkonfiguration bearbeiten** die entsprechende Auswahl, und klicken Sie dann auf **OK.**
    
4. Die Eigenschaft **State** für die Auflistung wird in **Commit nicht ausgeführt** aktualisiert. Um für die Änderungen ein Commit auszuführen und die Auflistung zu löschen, klicken Sie auf **Commit ausführen**, und klicken Sie dann auf **Commit für alle Elemente ausführen**.
    
5. Klicken Sie im Dialogfeld **VoIP-Konfigurationseinstellungen, für die kein Commit ausgeführt wurde** auf **OK**.
    
6. Klicken Sie im Dialogfeld **Skype for Business Server Systemsteuerung** auf **OK.**
