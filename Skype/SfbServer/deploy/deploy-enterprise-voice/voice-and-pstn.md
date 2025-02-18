---
title: Konfigurieren von VoIP-Richtlinien, PSTN-Verwendungsdatensätzen und VoIP-Routen in Skype for Business
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
ms.assetid: 1e5a15f9-6f42-4dc6-baaa-24daf54afc4d
description: 'Zusammenfassung: Erfahren Sie, wie Sie VoIP-Richtlinien, PSTN-Verwendungsdatensätze und VoIP-Routen in Skype for Business Server konfigurieren.'
ms.openlocfilehash: d38e843645b9c3e45103fb7ea52f4c5f7cd5ceea
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58621837"
---
# <a name="configure-voice-policies-pstn-usage-records-and-voice-routes-in-skype-for-business"></a>Konfigurieren von VoIP-Richtlinien, PSTN-Verwendungsdatensätzen und VoIP-Routen in Skype for Business
 
**Zusammenfassung:** Erfahren Sie, wie Sie VoIP-Richtlinien, PSTN-Verwendungsdatensätze und VoIP-Routen in Skype for Business Server konfigurieren.
  
VoIP-Richtlinien, PSTN-Verwendungsdatensätze und VoIP-Routen stehen in enger Beziehung zueinander. Zur Konfiguration von VoIP-Richtlinien wird eine Reihe von Anruffunktionen ausgewählt. Anschließend wird die Richtlinie einem Satz von PSTN-Verwendungsdatensätzen zugewiesen, in denen die Rechte für die Benutzer oder Gruppen festgelegt sind, denen die VoIP-Richtlinie zugewiesen wird. Auch VoIP-Routen werden PSTN-Verwendungsdatensätze zugewiesen, um Routen und die für ihre Verwendung autorisierten Benutzer einander zuzuordnen. Benutzer können also nur Anrufe über Routen tätigen, für die sie passende PSTN-Verwendungsdatensätze besitzen.
  
Der empfohlene Workflow für eine neue Enterprise-VoIP-Bereitstellung besteht darin, zunächst eine VoIP-Richtlinie mit den geeigneten PSTN-Verwendungsdatensätzen zu konfigurieren und anschließend den einzelnen PSTN-Verwendungsdatensätzen die entsprechenden Routen zuzuordnen. 
  
> [!NOTE]
> Sie können auch VoIP-Richtlinien mit  *Benutzerbereich*  erstellen und sie einzelnen Benutzern oder Gruppen zuweisen.
  
Die einzelnen Schritte zur Durchführung dieser Aufgaben finden Sie in den Verfahren in diesem Abschnitt.
  
## <a name="in-this-section"></a>Inhalt dieses Abschnitts

- [Erstellen oder Ändern einer VoIP-Richtlinie und Konfigurieren von PSTN-Verwendungsdatensätzen in Skype for Business](voice-policy-and-pstn-usage-records.md)
    
- [Konfigurieren von Voicemail escape in Skype for Business](configure-voice-mail-escape.md)
    
- [Anzeigen von PSTN-Verwendungsdatensätzen in Skype for Business](view-pstn-usage-records.md)
    
- [Erstellen oder Ändern einer VoIP-Route in Skype for Business](create-or-modify-a-voice-route.md)
    
- [Exportieren oder Importieren einer VoIP-Routenkonfigurationsdatei in Skype for Business](voice-route-configuration-import-export.md)
    
- [Veröffentlichen ausstehender Änderungen an der VoIP-Routingkonfiguration in Skype for Business](voice-route-config-changes.md)
    

