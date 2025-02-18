---
title: Überprüfen der Replikation der Schemapartition
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
- ms.lync.dep.DeployMainVerifySchemaPrep
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.assetid: 0357f230-6d0c-41f1-942c-e14f76e55d31
description: 'Gehen Sie folgendermaßen vor, um zu überprüfen, ob die Schemaerweiterung erfolgreich in ihrer Active Directory Domain Services-Gesamtstruktur repliziert wurde:'
ms.openlocfilehash: 6809c95be9ec0fd0de9d686e4b38b6a16ea92573
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58623977"
---
# <a name="verify-replication-of-schema-partition"></a>Überprüfen der Replikation der Schemapartition
 
Gehen Sie folgendermaßen vor, um zu überprüfen, ob die Schemaerweiterung erfolgreich in ihrer Active Directory Domain Services-Gesamtstruktur repliziert wurde:
  
1. Melden Sie sich bei einem Domänencontroller (mit Ausnahme des Domänencontrollers mit der Schemamasterrolle) in der Active Directory Domain Services-Gesamtstruktur an, auf den die Schemaerweiterungen als Mitglied der Gruppe Enterprise Administratoren angewendet wurden.
    
2. Öffnen Sie den ADSI-Editor: Klicken Sie nacheinander auf **Start**, **Verwaltung** und **ADSI-Editor**.
    
    > [!TIP]
    > Alternativ können Sie den ADSI-Editor starten, indem Sie auf **Start** und **Ausführen** klicken und **adsiedit.msc** eingeben.
  
3. Klicken Sie in der MMC-Konsolenstruktur auf "ADSI-Editor", falls nicht bereits ausgewählt.
    
4. Klicken Sie im Menü **Aktion** auf **Verbinden mit**.
    
5. Wählen Sie im Dialogfeld **Verbindungseinstellungen** unter **Bekannten Namenskontext auswählen** die Option **Schema** aus, und klicken Sie auf **OK**.
    
6. Suchen Sie unter dem Schemacontainer nach "CN=ms-RTC-SIP-SchemaVersion". Wenn dieses Objekt vorhanden und der Wert des Attributs **rangeUpper** 1150 und der Wert des Attributs **rangeLower** 3 ist, wurde das Schema erfolgreich aktualisiert und repliziert. Wenn dieses Objekt nicht vorhanden ist oder die Werte der Attribute **rangeUpper** und **rangeLower** nicht diesen Werten entsprechen, wurde das Schema nicht geändert oder repliziert.
    
> [!NOTE]
> Sollte Ihre Überprüfung der Replikation des Schemas noch keine erfolgreiche Replikation ergeben, warten Sie ca. 15 Minuten, und führen Sie dann die Überprüfung erneut durch. Die Active Directory-Replikation basiert auf einem losen Konsistenzmodell, und es kann eine Replikationslatenz auftreten, basierend auf einer Reihe von Faktoren auf dem Server und in der Infrastruktur. 
  

