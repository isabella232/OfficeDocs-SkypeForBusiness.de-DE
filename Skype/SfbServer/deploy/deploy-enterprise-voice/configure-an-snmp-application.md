---
title: Konfigurieren einer SNMP-Anwendung in Skype for Business Server
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
ms.assetid: c4b4a736-3b2e-45b9-a965-19d22161ad57
description: Konfigurieren Sie eine SNMP-Anwendung für die Arbeit mit E9-1-1 in Skype for Business Server Enterprise-VoIP.
ms.openlocfilehash: ec93aa572b2acf80afa104bba3b5fd1f9573f985
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58597759"
---
# <a name="configure-an-snmp-application-in-skype-for-business-server"></a>Konfigurieren einer SNMP-Anwendung in Skype for Business Server
 
Konfigurieren Sie eine SNMP-Anwendung für die Arbeit mit E9-1-1 in Skype for Business Server Enterprise-VoIP. 
  
Skype for Business Server enthält eine standardmäßige Webdienstschnittstelle, mit der Sie den Standortinformationsdienst mit SNMP-Anwendungen (Simple Network Management Protocol) verbinden können, die MAC-Adressen mit Port- und Switchinformationen abgleichen. 
  
Wenn eine SNMP-Anwendung installiert ist und der Standortinformationsdienst keine Übereinstimmung in der Standortdatenbank findet, fragt der Standortinformationsdienst die Anwendung automatisch mithilfe der vom Client bereitgestellten MAC-Adresse ab. Der Standortinformationsdienst verwendet dann die port- und switch-Informationen, die von der SNMP-Anwendung zurückgegeben werden, um die Standortdatenbank erneut abfragt.
  
> [!NOTE]
> MAC-Adressen sind auf Computern mit Windows 8 nicht verfügbar. 
  
### <a name="to-configure-the-snmp-application-url"></a>So konfigurieren Sie die URL für die SNMP-Anwendung

1.  Starten Sie die Skype for Business Server Verwaltungsshell: Klicken Sie auf **"Start",** auf **"Alle Programme",** auf **Skype for Business 2015** und dann auf **Skype for Business Server Verwaltungsshell.**
    
2. Führen Sie das folgende Cmdlet aus, um die URL für die SNMP-Anwendung zu konfigurieren. 
    
   ```powershell
   Set-CsWebServiceConfiguration -MACResolverUrl "<SNMP application url>" 
   ```

## <a name="see-also"></a>Siehe auch

[Set-CsWebServiceConfiguration](/powershell/module/skype/set-cswebserviceconfiguration?view=skype-ps)