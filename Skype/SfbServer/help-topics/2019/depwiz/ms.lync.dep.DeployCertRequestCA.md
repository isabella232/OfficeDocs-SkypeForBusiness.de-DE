---
title: Zertifikatanforderung (Zertifizierungsstelle)
ms.reviewer: ''
ms.author: v-cichur
author: cichur
manager: serdars
audience: ITPro
ms.topic: article
ms.custom:
- ms.lync.dep.DeployCertRequestCA
ms.prod: skype-for-business-itpro
f1.keywords:
- CSH
ms.localizationpriority: medium
ms.assetid: a609f1b0-ae13-44ca-a467-b7fb14ff18a1
ROBOTS: NOINDEX, NOFOLLOW
description: 'Wenn Sie eine Zertifikatanforderung an eine Onlinezertifizierungsstelle (z. B. Server, die sich in Ihrem internen Netzwerk befinden) auf der Seite "Zertifizierungsstelle auswählen" stellen, stehen Ihnen zwei Optionen zur Verfügung:'
ms.openlocfilehash: 96f601a26f64802e93d776438dfc92b50f3ae76a
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58591829"
---
# <a name="certificate-request-certificate-authority"></a>Zertifikatanforderung (Zertifizierungsstelle)
 
Beim Erstellen einer Zertifikatsanforderung an eine Onlinezertifizierungsstelle (im Allgemeinen ein Server im internen Netzwerk) auf der Seite **Zertifizierungsstelle auswählen** werden zwei Optionen angezeigt:
  
1. Wählen Sie eine Zertifizierungsstelle aus der Liste mit den in Ihrer Umgebung erkannten Stellen aus.
    
2. Wählen Sie eine andere Zertifizierungsstelle aus.
    
Wenn Sie die erste Option auswählen, wird eine Dropdownliste mit allen Windows serverbasierten Zertifizierungsstellen angezeigt, die in Ihrer Umgebung erkannt werden. Wählen Sie die Zertifizierungsstelle aus, die für Ihr Zertifikat geeignet ist. Möglicherweise müssen Sie sich an Ihren Zertifizierungsstellenadministrator wenden, um zu wissen, welche Zertifizierungsstelle Sie auswählen müssen.
  
Bei Wahl der zweiten Option geben Sie den vollqualifizierten Domänennamen und die Zertifizierungsstelleninstanz der Zertifizierungsstelle ein, die Sie für das Zertifikat verwenden möchten. Diese Option kommt in Frage, wenn die gewünschte Zertifizierungsstelle keine Windows Server-basierte Zertifizierungsstelle ist, jedoch für Windows Server-basierte Zertifizierungsstellen funktioniert.
  
> [!IMPORTANT]
> Für eine erfolgreiche Zertifikatsanforderung müssen Sie Mitglied der entsprechenden Gruppen sein. Zertifizierungsstellen haben in der Regel eine andere Berechtigungsanforderung als die Anforderungen für die Installation von Skype for Business Server auf Servern. Informieren Sie sich über die Voraussetzungen für das Anfordern des Zertifikats bei Ihrem Zertifizierungsstellenadministrator. 
  

