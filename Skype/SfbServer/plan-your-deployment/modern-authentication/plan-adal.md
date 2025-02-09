---
title: Planen der modernen Authentifizierung (Modern Authentication, ADAL) mit Skype for Business
ms.reviewer: ''
ms.author: v-cichur
author: cichur
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: IT_Skype16
description: In diesem Artikel wird erläutert, was moderne Authentifizierung (basierend auf der Active Directory-Authentifizierungsbibliothek (ADAL) und OAuth 2.0) ist.
ms.openlocfilehash: 29bbe33754b2363e84f449115bd51396ad9af932
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58614015"
---
# <a name="how-to-use-modern-authentication-adal-with-skype-for-business"></a>Verwenden der modernen Authentifizierung (Modern Authentication, ADAL) mit Skype for Business
 
In diesem Artikel wird die moderne Authentifizierung (basierend auf der Active Directory-Authentifizierungsbibliothek (ADAL) und OAuth 2.0) eingeführt, die im kumulativen März 2016-Update für Skype for Business für Skype for Business Server 2015 oder ab der ersten Version für Skype for Business Server 2019 zu finden ist.
  
## <a name="what-is-adal"></a>Was ist ADAL?

ADAL ist das Akronym für die "Active Directory-Authentifizierungsbibliothek" und stellt zusammen mit OAuth 2.0 eine Grundlage für die moderne Authentifizierung dar. Diese Codebibliothek wurde entwickelt, um gesicherte Ressourcen in Ihrem Verzeichnis über Sicherheitstoken für Clientanwendungen (z. B. Skype for Business) verfügbar zu machen. ADAL arbeitet mit OAuth 2.0 zusammen, um mehr Authentifizierungs- und Autorisierungsszenarien wie mehrstufige Authentifizierung (Multi-Factor Authentication, MFA) und mehr Formen der SAML-Authentifizierung zu ermöglichen.
  
Eine Vielzahl von Apps, die als Clients fungieren, können die moderne Authentifizierung nutzen, um Hilfe beim Zugriff auf gesicherte Ressourcen zu erhalten. In Skype for Business Server wird diese Technologie zwischen lokalen Clients und lokalen Servern verwendet, um Benutzern eine ordnungsgemäße Autorisierungsstufe für Ressourcen zu ermöglichen.
  
Moderne Authentifizierungsunterhaltungen (die auf ADAL und OAuth 2.0 basieren) haben einige Elemente gemeinsam.
  
- Es gibt einen Client, der eine Anforderung für eine Ressource stellt, in diesem Fall ist der Client Skype for Business.
    
- Es gibt eine Ressource, für die der Client eine bestimmte Zugriffsebene benötigt, und diese Ressource wird durch einen Verzeichnisdienst gesichert, in diesem Fall ist die Ressource Skype for Business Server.
    
- Es gibt eine OAuth-Verbindung, d. h. eine Verbindung, die der  *Autorisierung*  eines Benutzers für den Zugriff auf eine Ressource dient. (OAuth ist auch unter dem aussagekräftigeren Namen "Server-zu-Server"-Authentifizierung bekannt und wird häufig als S2S abgekürzt.)
    
In Skype for Business Server Unterhaltungen zur modernen Authentifizierung (Modern Authentication, ADAL) kommuniziert Skype for Business Server über ADFS (ADFS 3.0 in Windows Server 2012 R2). Die Authentifizierung kann mit einem anderen Identitätsanbieter (IdP) erfolgen, aber Skype for Business Server muss für die direkte Kommunikation mit ADFS konfiguriert werden. Wenn Sie ADFS nicht für die Arbeit mit Skype for Business Server konfiguriert haben, schließen Sie die [ADFS-Installation](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd727938(v=ws.10))ab.
  
ADAL ist im kumulativen März 2016-Update für Skype for Business Server 2015 enthalten, und das kumulative Update vom März 2016 für Skype for Business **muss** installiert werden und ist für eine erfolgreiche Konfiguration erforderlich. For Skype for Business Server 2019, it is available from initial release of the product.
  
> [!NOTE]
> Während der ersten Version wird die moderne Authentifizierung in einer lokalen Umgebung nur unterstützt, wenn keine gemischte Skype Topologie beteiligt ist. Beispielsweise, wenn die Umgebung rein Skype for Business Server ist. Diese Anweisung kann geändert werden. 
  
Ein PowerShell-Paket mit .ps1 Dateien mit den von ADAL verwendeten Befehlen muss für eine erfolgreiche Konfiguration heruntergeladen werden.

Informationen zum Implementieren der modernen Authentifizierung in Skype for Business finden Sie unter: Verwenden der [modernen Authentifizierung (Modern Authentication, ADAL) mit Skype for Business](/microsoft-365/enterprise/hybrid-modern-auth-overview)