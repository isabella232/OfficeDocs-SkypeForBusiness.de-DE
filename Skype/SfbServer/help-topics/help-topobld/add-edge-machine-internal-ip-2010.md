---
title: Hinzufügen der internen IP-Adresse zum Edgecomputer – 2010
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
- ms.lync.tb.AddEdgeMachineInternalIpPage2010
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.assetid: 31b0ac1d-f320-4677-bd0f-b4b0dc84a6a2
description: Auf dieser Seite können Sie die interne IP-Adresse und den internen vollqualifizierten Domänennamen (FQDN) des Edgeservers angeben.
ms.openlocfilehash: 6e8b055889175a46c7b3846fd45a60819b963a9f
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58587381"
---
# <a name="add-edge-machine-internal-ip-2010"></a>Hinzufügen der internen IP-Adresse zum Edgecomputer – 2010

Auf dieser Seite können Sie die interne IP-Adresse und den internen vollqualifizierten Domänennamen (FQDN) des Edgeservers angeben.

- Geben Sie in der **internen IPv4-Adresse** die IP-Adresse des Edgeservers ein, den Sie dem Pool hinzufügen möchten.

- Geben Sie im **internen FQDN** den vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) des Edgeservers ein, den Sie dem Pool hinzufügen möchten.

Der angegebene FQDN muss mit dem auf dem Server konfigurierten Computernamen übereinstimmen. Der Name eines Computers, der nicht Mitglied einer Domäne ist, ist standardmäßig kein FQDN, sondern ein Kurzname. Der Topologie-Generator verwendet keine Kurznamen, sondern FQDNs. Daher müssen Sie ein DNS-Suffix für den Namen des Computers konfigurieren, der als Edgeserver bereitgestellt werden soll und nicht Mitglied einer Domäne ist. Ausführliche Informationen zum Hinzufügen eines DNS-Suffix zu einem Computernamen finden Sie unter [Configure DNS for Edge Support](/previous-versions/office/lync-server-2013/lync-server-2013-configure-dns-for-edge-support).