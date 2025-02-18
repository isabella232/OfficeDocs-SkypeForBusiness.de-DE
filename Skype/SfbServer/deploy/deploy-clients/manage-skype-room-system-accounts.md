---
title: Verwalten von Skype Room Systems-Konten
ms.author: v-cichur
author: cichur
manager: serdars
audience: ITPro
ms.reviewer: sohailta
ms.topic: quickstart
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 7b389efc-9685-42e9-9504-be437d20ff57
ms.collection: M365-voice
description: In diesem Thema erfahren Sie, wie Sie Skype Raumsystemkonten verwalten.
ms.openlocfilehash: a92a9058ea884e8be5a0a89eab0dccebc15f05e1
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58601930"
---
# <a name="manage-skype-room-system-accounts"></a>Verwalten von Skype Room Systems-Konten
 
In diesem Thema erfahren Sie, wie Sie Skype Raumsystemkonten verwalten. 

> [!NOTE]
> Microsoft Teams-Räume ist ein anderes Produkt mit unterschiedlichen Abhängigkeiten und Bereitstellungsverfahren. Informationen zu Microsoft Teams-Räume finden Sie in der Übersicht über die [Microsoft Teams-Räume-Verwaltung.](/microsoftteams/rooms/rooms-manage)
  
## <a name="move-the-skype-room-system-account-between-pools"></a>Verschieben des Skype Raumsystemkontos zwischen Pools

Wenn Sie das Skype Raumsystemkonto von einem Skype for Business Server-Pool in einen anderen verschieben müssen (z. B. während Upgrades), verwenden Sie den folgenden Befehl, um den Skype Raumsystem-Kontopool zu verschieben: 
  
```powershell
Move-CsMeetingRoom -Identity LRS01 -Target "LYNCPool15-2.contoso.com"
```

## <a name="disable-the-skype-room-system-account-for-skype-for-business-services"></a>Deaktivieren des Skype Room System-Kontos für Skype for Business-Dienste

Wenn Sie ein vorhandenes Skype Room System-Konto aus Skype for Business Diensten in einem Skype for Business Server Pool deaktivieren müssen, verwenden Sie den folgenden Befehl, um das Konto zu deaktivieren: 
  
```powershell
Disable-CsMeetingRoom LRS01 -domaincontroller DC-ND-001.contoso.com
```

## <a name="optional-create-a-skype-room-system-administrator-group-in-active-directory"></a>Optional: Erstellen einer Skype Raumsystemadministratorgruppe in Active Directory

Jeder Skype Raumsystemclient, der der Domäne beitritt, kann vollständig von einem Domänenbenutzer mit lokalen Administratorrechten auf dem Skype Raumsystemanwendungs-PC verwaltet werden. Daher können Sie eine dedizierte Administratorgruppe in Active Directory erstellen und dieser Gruppe während der Einrichtung des neuen Skype Raumsystemcomputers Administratorrechte erteilen.
