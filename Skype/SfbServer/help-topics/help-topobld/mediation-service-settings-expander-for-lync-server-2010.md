---
title: Einstellungen für den Vermittlungsdienst für Lync Server 2010 – Erweiterung
ms.reviewer: ''
ms.author: v-cichur
author: cichur
manager: serdars
ms.date: 3/26/2015
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.tb.MediationServiceSettingsExpander2010
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.assetid: 230e0a08-9e16-4bbd-b550-1f04bad8ddbc
description: 'Sie bearbeiten die Eigenschaften des Vermittlungsdiensts, indem Sie die folgenden Eigenschaften definieren:'
ms.openlocfilehash: 99443558dce6373063e060d9dec5a791ae41cee8
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58616651"
---
# <a name="mediation-service-settings-expander-for-lync-server-2010"></a>Einstellungen für den Vermittlungsdienst für Lync Server 2010 – Erweiterung
 
Sie bearbeiten die Eigenschaften des Vermittlungsdiensts, indem Sie die folgenden Eigenschaften definieren:
  
- **Überwachungsports**: Definieren Sie den **TLS**-Port, der vom Vermittlungsdienst überwacht wird. Standardmäßig lautet der Portwert "TCP 5067" mit Transport Layer Security (TLS).
    
    Optional können Sie einen **TCP**-Portwert definieren. Standardmäßig lautet der Wert "TCP 5068".
    
    > [!NOTE]
    > Sie aktivieren die Einstellung für den TCP-Portwert, indem Sie **TCP-Port aktivieren** auswählen. Die Porteinstellungen, die für die Kommunikation mit dem Vermittlungsdienst erforderlich sind, finden Sie in der Dokumentation zum PSTN-Gateway (Public Switched Telephone Network) oder IP-PBX (Internet Protocol Private Branch Exchange). 
  
- Verwenden Sie die Option **TCP-Port aktivieren**, um den Portwert für die TCP-Kommunikation über das PSTN-Gateway oder IP-PBX zu definieren.
    
- Auflistung des momentan zugeordneten und vorhandenen **Trunks** (Session Initiation Protocol-Trunks (SIP)), **Gateways** (PSTN-Gateway oder IP-PBX) und **Standorts** (für Trunk und Gateway konfigurierter Standort).
    
- Wählen Sie einen Trunk, ein Gateway und einen Standort aus, und klicken Sie auf **Als Standardeinstellung festlegen**, um die Auswahl als Standardeinstellung für diesen Vermittlungsdienst festzulegen. Um die Auswahl als Standardeinstellung aufzuheben, wählen Sie die aktuelle Standardeinstellung aus und klicken auf **Festlegung als Standardeinstellung aufheben**. Wählen Sie anschließend eine neue Standardeinstellung aus, und klicken Sie auf **Als Standardeinstellung festlegen**.
    
  **OK**: Mit dieser Option werden die Änderungen am Dialogfeld akzeptiert und übernommen.
  
  **Abbrechen**: Mit dieser Option werden die Änderungen verworfen, und das Dialogfeld wird geschlossen.
  
  **Hilfe**: Mit dieser Option zeigen Sie diese Hilfeseite an.
  

