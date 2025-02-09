---
title: Verwalten von Notfallwiederherstellung, hoher Verfügbarkeit und Sicherungsdienst
ms.reviewer: ''
author: cichur
ms.author: v-cichur
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
description: Erfahren Sie mehr über die Verfahren für Notfallwiederherstellungsvorgänge sowie für die Wartung des Sicherungsdiensts, der die Daten in gepaarten Front-End-Pools synchronisiert.
ms.openlocfilehash: b8635728710efbd2c820b6ca57333f77b56d04e5
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58612264"
---
# <a name="managing-skype-for-business-server-disaster-recovery-high-availability-and-backup-service"></a>Verwalten von Skype for Business Server Notfallwiederherstellung, hoher Verfügbarkeit und Sicherungsdienst

Dieser Abschnitt enthält Verfahren für Notfallwiederherstellungsvorgänge sowie für die Wartung des Sicherungsdiensts, der die Daten in gepaarten Front-End-Pools synchronisiert.

Notfallwiederherstellungsprozeduren, sowohl Failover als auch Failback, sind manuell. Wenn ein Notfall vorliegt, muss der Administrator die Failoverprozeduren manuell aufrufen. Das gleiche gilt für Failback nach der Reparatur des Pools.

Bei den Verfahren für die Notfallwiederherstellung in diesem Abschnitt wird Folgendes vorausgesetzt:

  - Sie verfügen über eine Bereitstellung mit gepaarten Front-End-Pools, die sich an verschiedenen Standorten befinden, wie unter ["Plan for high availability and disaster recovery"](../../plan-your-deployment/high-availability-and-disaster-recovery/high-availability-and-disaster-recovery.md)beschrieben. Der Sicherungsdienst wurde in diesen gekoppelten Pools ausgeführt, um sie synchronisiert zu halten.

  - Wenn der zentrale Verwaltungsspeicher in einem der Pools gehostet wird, wird er installiert und in beiden poolpaaren ausgeführt, wobei einer dieser Pools den aktiven Master und den anderen Pool hostet, der den Standbymodus hostet.

> [!IMPORTANT]
> In den folgenden Verfahren bezieht sich der *Parameter PoolFQDN* auf den FQDN des Pools, der von einem Notfall betroffen ist, nicht auf den Pool, aus dem die betroffenen Benutzer umgeleitet werden. Für dieselbe Gruppe betroffener Benutzer bezieht sie sich sowohl in Failover- als auch failback-Cmdlets auf denselben Pool (d. b. den Pool, der die Benutzer vor dem Failover zuerst verwaltet hat).<BR><br>Nehmen wir beispielsweise an, dass ein Fall aufgetreten ist, in dem alle Benutzer, die in einem Pool P1 verwaltet werden, auf den Sicherungspool P2 umgestellt wurden. Wenn der Administrator alle Benutzer verschieben möchte, die derzeit von P2 bedient werden, um von P1 bedient zu werden, muss der Administrator die folgenden Schritte ausführen: 
> <OL>
> <LI>
> <P>Failback all the users originally homed on P1 from P2 to P1 using the failback cmdlet. In diesem Fall ist der *PoolFQDN* der FQDN von P1.</P>
> <LI>
> <P>Failover für alle Benutzer, die ursprünglich mit P2 zu P1 verwaltet wurden, mithilfe des Failover-Cmdlets. In diesem Fall ist der PoolFQDN der FQDN von P2.</P>
> <LI>
> <P>Wenn der Administrator diese P2-Benutzer später wieder auf P2 zurücksetzen möchte, ist der PoolFQDN der FQDN von P2.</P></LI></OL><br>Beachten Sie, dass Schritt 1 oben vor Schritt 2 ausgeführt werden muss, um die Poolintegrität zu erhalten. Wenn Sie Schritt 2 vor Schritt 1 testen, schlägt das Cmdlet "Schritt 2" fehl.


## <a name="see-also"></a>Siehe auch

[Planen der hohen Verfügbarkeit und Notfallwiederherstellung](../../plan-your-deployment/high-availability-and-disaster-recovery/high-availability-and-disaster-recovery.md) 
  
