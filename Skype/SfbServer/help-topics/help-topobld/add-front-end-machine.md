---
title: Hinzufügen von Front-End-Computern
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
- ms.lync.tb.AddFrontEndMachinePage
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.assetid: e7fe2522-1bd2-416a-9dbb-51cacea9c6e0
description: Geben Sie den vollqualifizierten Domänennamen jedes Computers an, der diesem Pool als Front-End-Server hinzugefügt werden soll. Nach dem Hinzufügen eines Computers zur Liste können Sie den vollqualifizierten Domänennamen des Computers zu einem beliebigen Zeitpunkt vor der Veröffentlichung der Topologie aktualisieren oder aus dem Pool entfernen. Wenn Sie den vollqualifizierten Domänennamen nach dem Veröffentlichen der Topologie ändern möchten, müssen Sie den Server im Topologie-Generator löschen und anschließend einen neuen Server mit dem neuen vollqualifizierten Domänennamen zum Pool hinzufügen. Ausführliche Informationen zum Hinzufügen eines Front-End-Pools zur Topologie finden Sie unter Definieren und Konfigurieren eines Front-End-Pools in der Bereitstellungsdokumentation.
ms.openlocfilehash: 29a759443db5a20093c77eab9805f89b865493f4
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58610812"
---
# <a name="add-front-end-machine"></a>Hinzufügen von Front-End-Computern

Geben Sie den vollqualifizierten Domänennamen jedes Computers an, der diesem Pool als Front-End-Server hinzugefügt werden soll. Nach dem Hinzufügen eines Computers zur Liste können Sie den vollqualifizierten Domänennamen des Computers zu einem beliebigen Zeitpunkt vor der Veröffentlichung der Topologie aktualisieren oder aus dem Pool entfernen. Wenn Sie den vollqualifizierten Domänennamen nach dem Veröffentlichen der Topologie ändern möchten, müssen Sie den Server im Topologie-Generator löschen und anschließend einen neuen Server mit dem neuen vollqualifizierten Domänennamen zum Pool hinzufügen. Ausführliche Informationen zum Hinzufügen eines Front-End-Pools zur Topologie finden Sie unter [Definieren und Konfigurieren eines Front-End-Pools](/previous-versions/office/lync-server-2013/lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server) in der Bereitstellungsdokumentation.

> [!IMPORTANT]
> Beachten Sie, dass der Topologie-Generator angibt, dass bis zu 20 Front-End-Server in einem Pool vorhanden sein können. Die maximal unterstützte Anzahl von Servern beträgt 12. In der Fabric können bis zu 20 zustandsbehaftete Server definiert sein, von denen 12 gleichzeitig aktiv und online sein können.