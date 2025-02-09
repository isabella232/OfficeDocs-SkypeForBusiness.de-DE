---
title: Ermöglichen, dass Benutzer des Telefonsystems eine lokale Festnetzanbindung in Skype for Business Server herstellen
ms.reviewer: ''
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 1/27/2018
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection:
- Ent_O365_Hybrid
- IT_Skype16
- IT_Skype4B_Hybrid
- Strat_SB_Hybrid
ms.custom: ''
ms.assetid: 3cc3db88-0210-4804-b54e-ba4af1234884
description: 'In diesem Thema wird beschrieben, wie Benutzer für Telefonsystem mit lokaler PSTN-Konnektivität aktiviert werden. Bevor Sie die Schritte in diesem Thema ausführen, sollten Sie Folgendes lesen: .'
ms.openlocfilehash: 22e0db6b9cd99c7909bcc6477db28546feef21d3
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58625037"
---
# <a name="enable-users-for-phone-system-with-on-premises-pstn-connectivity-in-skype-for-business-server"></a>Ermöglichen, dass Benutzer des Telefonsystems eine lokale Festnetzanbindung in Skype for Business Server herstellen

In diesem Thema wird beschrieben, wie Benutzer für Telefonsystem mit lokaler PSTN-Konnektivität aktiviert werden. Bevor Sie die Schritte in diesem Thema ausführen, sollten Sie Folgendes lesen: .
  
- Informationen zum Einrichten der Hybridkonnektivität finden Sie unter Planen der [Hybridkonnektivität zwischen Skype for Business Server und Skype for Business Online](../../../SfbHybrid/hybrid/plan-hybrid-connectivity.md?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json) und Bereitstellen der [Hybridkonnektivität zwischen Skype for Business Server und Skype for Business Online.](../../../SfbHybrid/hybrid/configure-hybrid-connectivity.md?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json)
    
- Informationen zur Planung Ihrer Bereitstellung finden Sie unter [Plan Telefonsystem with on-premises PSTN connectivity in Skype for Business Server.](plan-phone-system-with-on-premises-pstn-connectivity.md)
    
- Weitere Informationen zu Telefonsystem, einschließlich Lizenzierung und Plänen, finden Sie unter [PSTN-Anrufpläne für Skype for Business.](https://support.office.com/article/PSTN-Calling-plans-for-Skype-for-Business-f47c6a97-bc8b-42e6-b5d4-ce6b41ed1918)
    
> [!Important]
> Skype for Business Online wird am 31. Juli 2021 eingestellt, danach ist der Dienst nicht mehr verfügbar.  Darüber hinaus wird die PSTN-Konnektivität zwischen Ihrer lokalen Umgebung über Skype for Business Server oder Cloud Connector Edition und Skype for Business Online nicht mehr unterstützt.  Erfahren Sie, wie Sie Ihr lokales Telefonienetzwerk über [Direct Routing](/MicrosoftTeams/direct-routing-landing-page)mit Teams verbinden.

## <a name="moving-users-to-phone-system-with-on-premises-pstn-connectivity"></a>Verschieben von Benutzern zu Telefonsystem mit lokaler PSTN-Anbindung

Bevor Sie Ihre Benutzer zu Skype for Business Online verschieben, sollten Sie Ihre Benutzer lokal in Skype for Business Server oder Lync Server 2013 aktivieren und sie dann online verschieben. Weitere Informationen finden Sie unter [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](../../../SfbHybrid/hybrid/plan-hybrid-connectivity.md?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json) and the special considerations section of Enable the users for Enterprise-VoIP on [premises](enable-the-users-for-enterprise-voice-on-premises.md) (performed while the users are homed on-premises). 
  
Alle Benutzer müssen lokal in Active Directory erstellt und mit Microsoft 365 oder Office 365 mithilfe der unterstützten Version von Azure AD Connector synchronisiert werden. Sie können keine Benutzer für Telefonsystem in Office 365 aktivieren, die direkt in Azure AD erstellt wurden. Wenn Sie Telefonsystem mit lokaler PSTN-Konnektivität für einen Benutzer aktivieren möchten, der in Azure AD erstellt wurde, müssen Sie ein neues Konto für diesen Benutzer in Ihrem lokalen AD erstellen, das konto lokal konfigurieren und das Konto dann mithilfe einer unterstützten Version des Azure AD Connector-Tools synchronisieren. 
  
Die Aktivierung eines Benutzers für Telefonsystem mit lokaler PSTN-Konnektivität und das anschließende Verschieben zu Skype for Business Online erfordert die folgenden Schritte:
  
- [Aktivieren Sie die Benutzer für Enterprise-VoIP lokalen](enable-the-users-for-enterprise-voice-on-premises.md) (durchgeführt, während die Benutzer lokal verwaltet werden).
    
- [Weisen Sie eine VoIP-Routingrichtlinie](assign-a-voice-routing-policy.md) zu (während die Benutzer lokal verwaltet werden).
    
- [Synchronisieren Sie Benutzer mit der Cloud, und weisen Sie Lizenzen zu](../../../SfbHybrid/hybrid/configure-hybrid-connectivity.md?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json) (mit Office 365).
    
- [Verschieben sie lokale Benutzer in Skype for Business Online](../../../SfbHybrid/hybrid/move-users-from-on-premises-to-skype-for-business-online.md) (durchgeführt mit Windows PowerShell lokalen, aber mit Ihren Office 365 Administratoranmeldeinformationen).
    
- [Aktivieren Sie Benutzer für Enterprise-VoIP Online- und Telefonsystem Voicemail](enable-users-for-enterprise-voice-online-and-phone-system-voicemail.md) (ausgeführt mit Remote-PowerShell.
