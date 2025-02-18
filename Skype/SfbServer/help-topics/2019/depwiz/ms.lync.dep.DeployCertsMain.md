---
title: Zertifikat-Assistent
ms.reviewer: ''
ms.author: v-cichur
author: cichur
manager: serdars
audience: ITPro
ms.topic: article
ms.custom:
- ms.lync.dep.DeployCertsMain
ms.prod: skype-for-business-itpro
f1.keywords:
- CSH
ms.localizationpriority: medium
ms.assetid: 6ab661d7-5741-4cad-bbe4-62cf862ded85
ROBOTS: NOINDEX, NOFOLLOW
description: Im Zertifikat-Assistenten können Sie Zertifikate anfordern, zuweisen, entfernen und anzeigen. Sie müssen als Mitglied der Gruppe "RTCUniversalServerAdmins" angemeldet sein. Zum Anfordern eines Zertifikats von einer öffentlichen Zertifizierungsstelle sind keine besonderen Gruppenmitgliedschaften erforderlich. Um ein Zertifikat von der Public Key-Infrastruktur (PKI) Ihrer Organisation anzufordern, müssen Sie bestätigen, welche zusätzlichen Gruppenmitgliedschaften Erforderlich sind. Während der Anforderungsaufgabe können Sie alternative Anmeldeinformationen eingeben, die verwendet werden, um das Zertifikat von der ausstellenden Zertifizierungsstelle Ihrer PKI anzufordern.
ms.openlocfilehash: 9d966786f65311920370890a7091012929af7fa3
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58621687"
---
# <a name="certificate-wizard"></a>Zertifikat-Assistent
 
Im Zertifikat-Assistenten können Sie Zertifikate anfordern, zuweisen, entfernen und anzeigen. Sie müssen als Mitglied der Gruppe "RTCUniversalServerAdmins" angemeldet sein. Zum Anfordern eines Zertifikats von einer öffentlichen Zertifizierungsstelle sind keine besonderen Gruppenmitgliedschaften erforderlich. Um ein Zertifikat von der Public Key-Infrastruktur (PKI) Ihrer Organisation anzufordern, müssen Sie bestätigen, welche zusätzlichen Gruppenmitgliedschaften Erforderlich sind. Während der Anforderungsaufgabe können Sie alternative Anmeldeinformationen eingeben, die verwendet werden, um das Zertifikat von der ausstellenden Zertifizierungsstelle Ihrer PKI anzufordern.
  
Klicken Sie zum Anfordern eines neuen Zertifikats auf **Anfordern**.
  
Klicken Sie zum Zuweisen eines noch nicht zugewiesenen Zertifikats auf **Zuweisen**.
  
Klicken Sie zum Entfernen eines bereits zugewiesenen Zertifikats auf **Entfernen**.
  
> [!NOTE]
> Die Schaltfläche **Entfernen** steht nur zur Verfügung, wenn ein Zertifikat zuvor zugewiesen wurde. Ist die Schaltfläche **Entfernen** nicht verfügbar (abgeblendet), wurde kein Zertifikat zugewiesen.
  
Klicken Sie zum Anzeigen eines zugewiesenen Zertifikats auf **Anzeigen**.
  
> [!NOTE]
> Die Schaltfläche **Anzeigen** steht nur zur Verfügung, wenn ein Zertifikat zuvor zugewiesen wurde. Ist die Schaltfläche **Anzeigen** abgeblendet, wurde kein Zertifikat zugewiesen.
  
Klicken Sie zum Aktualisieren des aktuellen Zertifikatzuweisungsbildschirms auf **Aktualisieren**.
  
Klicken Sie zum Importieren eines Zertifikats, das noch nicht im Zertifikatspeicher vorhanden ist, auf **Zertifikat importieren**.
  
> [!NOTE]
> **Das Importzertifikat** wird in der Regel verwendet, um ein Zertifikat zu verarbeiten, das über einen anderen Prozess als eine Anforderung des Zertifikat-Assistenten empfangen wird. Ihr PKI-Administrator erstellt beispielsweise ein Zertifikat und stellt es Ihnen zur Verfügung. Verwenden Sie import **certificate** to import the certificate into the computer's certificate store and make it available to Skype for Business Server to assign.
  
Klicken Sie zum Abschließen der Anforderung eines Zertifikats von einer Zertifizierungsstelle in Ihrer Organisation, für die eine Genehmigung durch den Zertifizierungsstellenadministrator erforderlich ist, auf **Ausstehende Anforderung verarbeiten**. Für die Zertifikatsanforderung wird der Status "Ausstehend" sowie ihre ID-Nummer zurückgegeben. Klicken Sie zum Verarbeiten eines Zertifikats mit ausstehender Genehmigung auf **Aktualisieren**, um die Schaltfläche **Ausstehende Anforderung verarbeiten** zu aktivieren, die danach wieder verfügbar (nicht mehr abgeblendet) ist. Sie können anschließend versuchen, die ausstehende Anforderung abzurufen, doch deren Status bleibt so lange "Ausstehend", bis das Zertifikat vom Zertifizierungsstellenadministrator ausgestellt oder abgelehnt wird. Die Schaltfläche bleibt deaktiviert, wenn es keine gültigen ausstehenden Anforderungen gibt, die mit dem Zertifikat-Assistenten erstellt wurden.
  

