---
title: Allgemeine Einstellungen für externe Anwendungen – Erweiterung
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
- ms.lync.tb.ExternalApplicationGeneralSettingsExpander
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.assetid: aa7268ac-b9e3-4d25-bff4-e59d305120f2
description: Befolgen Sie diese Anweisungen, um die Eigenschaften für einen vertrauenswürdigen Anwendungsserver zu bearbeiten, der bereits definiert wurde.
ms.openlocfilehash: 1bcb822ee6a48383f45a10f5ee3db1f5222c00a5
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58606324"
---
# <a name="external-application-general-settings-expander"></a>Allgemeine Einstellungen für externe Anwendungen – Erweiterung
 
Befolgen Sie diese Anweisungen, um die Eigenschaften für einen vertrauenswürdigen Anwendungsserver zu bearbeiten, der bereits definiert wurde.
  
Zwei Abschnitte können geändert werden:
  
> Allgemeine Einstellungen
> 
> Einstellungen für nächsten Hop
    
## <a name="general-settings"></a>Allgemeine Einstellungen

Sie können den aktuellen FQDN (Fully Qualified Domain Name) für den Pool vertrauenswürdiger Anwendungsserver ändern. Bearbeiten Sie den vollqualifizierten Namen für den Pool. Der DNS-A-Eintrag (Host) muss für den neuen Eintrag vorhanden sein, ehe sich Clients oder Server mit dem Pool mit dem neuen Namen verbinden können.
  
Wählen Sie **Replikation von Konfigurationsdaten in diesen Pool aktivieren** aus, wenn die Replikation von Konfigurationsdaten in diesen Pool erforderlich sein sollte. Deaktivieren Sie dieses Kontrollkästchen, wenn die Konfigurationsdaten nicht repliziert werden sollen.
  
## <a name="next-hop-settings"></a>Einstellungen für nächsten Hop

Sie können den nächsten Hopserver des vertrauenswürdigen Anwendungsserverpools angeben, indem Sie in der Dropdownliste den definierten Enterprise Edition Front-End-Pool oder Standard Edition Front-End-Server auswählen. Ein Director oder Director-Pool kann nicht als nächster Hop für einen vertrauenswürdigen Anwendungsserver ausgewählt werden und wird daher nicht in der Liste aufgeführt.
  


Klicken Sie auf **"OK",** um die Änderungen zu akzeptieren und zu speichern. Klicken Sie auf **Abbrechen**, um Ihre Änderungen zu verwerfen und die Eigenschaftenseite zu schließen.
  

