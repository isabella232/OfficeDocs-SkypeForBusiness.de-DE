---
title: Erstellen von DNS-Einträgen für Skype for Business Server
ms.reviewer: ''
ms.author: v-cichur
author: cichur
manager: serdars
ms.date: 2/15/2018
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
ms.assetid: 798a663c-0b63-4f75-b0a3-9c553cef8c5f
description: 'Zusammenfassung: Erfahren Sie, wie Sie DNS konfigurieren und DNS-Einträge für eine Installation von Skype for Business Server erstellen. Laden Sie eine kostenlose Testversion von Skype for Business Server aus dem Microsoft Evaluation Center herunter: https://www.microsoft.com/evalcenter/evaluate-skype-for-business-server .'
ms.openlocfilehash: 08a652f3ed2dd19d40aa1830ac91459d205b618a
ms.sourcegitcommit: 15e90083c47eb5bcb03ca80c2e83feffe67646f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2021
ms.locfileid: "58726324"
---
# <a name="create-dns-records-for-skype-for-business-server"></a>Erstellen von DNS-Einträgen für Skype for Business Server
 
**Zusammenfassung:** Erfahren Sie, wie Sie DNS konfigurieren und DNS-Einträge für eine Installation von Skype for Business Server erstellen. Laden Sie eine kostenlose Testversion von Skype for Business Server aus dem Microsoft Evaluation Center herunter: [https://www.microsoft.com/evalcenter/evaluate-skype-for-business-server](https://www.microsoft.com/evalcenter/evaluate-skype-for-business-server) .
  
Damit Skype for Business Server ordnungsgemäß funktionieren, müssen eine Reihe von DNS-Einstellungen (Domain Name System) vorhanden sein. Dies ist so, dass Clients wissen, wie sie auf die Dienste zugreifen und dass die Server sich gegenseitig kennen. Diese Einstellungen müssen nur einmal pro Bereitstellung abgeschlossen werden, da sie nach dem Zuweisen eines DNS-Eintrags in der gesamten Domäne verfügbar sind. Sie können die Schritte 1 bis 5 in beliebiger Reihenfolge ausführen. Sie müssen jedoch die Schritte 6, 7 und 8 in der reihenfolge und nach den Schritten 1 bis 5 ausführen, wie im Diagramm beschrieben. Das Erstellen von DNS-Einträgen umfasst Schritt 5 von 8. Weitere Informationen zur Planung von DNS finden Sie unter ["Environmental requirements for Skype for Business Server](../../plan-your-deployment/requirements-for-your-environment/environmental-requirements.md) or [Server requirements for Skype for Business Server 2019".](../../../SfBServer2019/plan/system-requirements.md)
  
> [!IMPORTANT]
> Es ist wichtig zu beachten, dass dies nur ein Beispiel für das Erstellen von DNS-Einträgen in einer Windows Server-DNS-Umgebung ist. Es gibt viele weitere DNS-Einträge, die für Skype for Business Server erforderlich sind, und das Verfahren zum Erstellen von DNS-Einträgen hängt vom System ab, das Sie zum Verwalten von DNS in Ihrer Organisation verwenden. Eine vollständige Liste der Anforderungen für DNS finden Sie unter [DNS-Anforderungen für Skype for Business Server.](../../plan-your-deployment/network-requirements/dns.md) 
  
![Übersichtsdiagramm.](../../media/d2fc733c-6a80-4d17-a02f-93b8c4bfb999.png)
  
## <a name="configure-dns"></a>Konfigurieren von DNS

DNS-Einträge sind erforderlich, damit Skype for Business Server ordnungsgemäß funktionieren und für Benutzer zugänglich sind.
  
In diesem Beispiel wird ein FQDN mit DNS-Lastenausgleich namens "pool.contoso.local" verwendet. Dieser Pool besteht aus drei Servern, auf denen Skype for Business Server Enterprise Edition ausgeführt wird. Ein Standard Edition Front-End-Server kann nur einen einzelnen Server enthalten. Wenn Sie Standard Edition verwenden, verwenden Sie nur den vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) des einzelnen Standard Edition Servers, wenn Sie auf die Front-End-Rolle verweisen, anstatt einen DNS-Pool mit Lastenausgleich von Servern zu erstellen, wie in diesem Beispiel gezeigt. Dieses einfache Beispiel, in dem nur die Front-End-Rolle verwendet wird, enthält die DNS-Einträge in der folgenden Tabelle. Informationen zum Planen Ihrer spezifischen DNS-Anforderungen finden Sie unter [DNS-Anforderungen für Skype for Business Server.](../../plan-your-deployment/network-requirements/dns.md) 
  
 
|**Beschreibung**|**Record type**|**Name**|**Wird aufgelöst zu**|**Lastenausgleichstyp**|
|:-----|:-----|:-----|:-----|:-----|
|Interner Webdienst-FQDN  <br/> |A  <br/> |webint.contoso.local  <br/> |VIP für interne Webdienste  <br/> |Unterstützte Software und Hardware  <br/> |
|Pool-FQDN  <br/> |A  <br/> |pool.contoso.local  <br/> |IP-Adresse des Servers SFB01  <br/> |DNS  <br/> |
|SFB01 FQDN  <br/> |A  <br/> |SFB01.contoso.local  <br/> |IP-Adresse des Servers SFB01  <br/> |DNS  <br/> |
|Pool-FQDN  <br/> |A  <br/> |pool.contoso.local  <br/> |IP-Adresse des Servers SFB02  <br/> |DNS  <br/> |
|SFB02-FQDN  <br/> |A  <br/> |SFB02.contoso.local  <br/> |IP-Adresse des Servers SFB02  <br/> |DNS  <br/> |
|Pool-FQDN  <br/> |A  <br/> |pool.contoso.local  <br/> |IP-Adresse des Servers SFB03  <br/> |DNS  <br/> |
|SFB03 FQDN  <br/> |A  <br/> |SFB03.contoso.local  <br/> |IP-Adresse des Servers SFB03  <br/> |DNS  <br/> |
|Skype for Business Automatische Erkennung  <br/> |A  <br/> |lyncdiscoverinternal.contoso.local  <br/> |VIP für interne Webdienste  <br/> |Unterstützte Software und Hardware  <br/> |
|Einfache URL für Besprechungen  <br/> |A  <br/> |meet.contoso.local  <br/> |VIP für interne Webdienste  <br/> |Unterstützte Software und Hardware  <br/> |
|Einfache URL für Einwahl  <br/> |A  <br/> |dialin.contoso.local  <br/> |VIP für interne Webdienste  <br/> |Unterstützte Software und Hardware  <br/> |
|Einfache URL des Webplaners  <br/> |A  <br/> |scheduler.contoso.local  <br/> |VIP für interne Webdienste  <br/> |Unterstützte Software und Hardware  <br/> |
|Einfache URL für die Verwaltung  <br/> |A  <br/> |admin.contoso.local  <br/> |VIP für interne Webdienste  <br/> |Unterstützte Software und Hardware  <br/> |
|Legacy-Ermittlung  <br/> |SRV  <br/> |_sipinternaltls._tcp.contoso.local  <br/> |Pool-FQDN (Port 5061)  <br/> |Nicht zutreffend  <br/> |
   
### <a name="create-dns-records"></a>Erstellen von DNS-Einträgen

1. Melden Sie sich beim DNS-Server an, und öffnen Sie **den Server-Manager.**
    
2. Klicken Sie auf das Dropdownmenü **"Extras"** und dann auf **"DNS".**
    
3. Erweitern Sie in der Konsolenstruktur für Ihre SIP-Domäne **Forward LookupZonen,** und erweitern Sie dann die SIP-Domäne, in der Skype for Business Server installiert wird.
    
4. Klicken Sie mit der rechten Maustaste auf die SIP-Domäne, und wählen Sie **neuen Host (A oder AAAA)** aus, wie in der Abbildung dargestellt.
    
     ![Auswählen eines neuen A-Datensatzes.](../../media/f89c5c1f-b5b7-428c-a6e3-2bcd12e878c3.png)
  
5. Geben Sie im **Feld "Name"** den Namen des Hostdatensatzes ein (der Domänenname wird automatisch angefügt).
    
6. Geben Sie im **Feld "IP-Adresse"** die IP-Adresse des einzelnen Front-End-Servers ein, und wählen Sie dann **PTR-Eintrag (Associated Pointer)** erstellen oder zulassen, dass **authentifizierte Benutzer DNS-Einträge mit demselben Besitzernamen aktualisieren,** falls zutreffend. Beachten Sie, dass dies davon ausgeht, dass DNS zum Lastenausgleich des gesamten Datenverkehrs mit Ausnahme von Webdiensten verwendet wird. In diesem Beispiel verfügen wir über drei Front-End-Server, wie in der Tabelle dargestellt.
    
   |**Servername**|**Type**|**Data**|
   |:-----|:-----|:-----|
   |SFB01  <br/> |Host (A)  <br/> |10.0.0.5  <br/> |
   |SFB02  <br/> |Host (A)  <br/> |10.0.0.6  <br/> |
   |SFB03  <br/> |Host (A)  <br/> |10.0.0.7  <br/> |
   
7. Erstellen Sie als Nächstes die DNS-Lastenausgleichseinträge für den Pool. Der DNS-Lastenausgleich ermöglicht DNS das Senden von Anforderungen an die einzelnen Server im Pool unter Verwendung desselben DNS-Poolnamens. Weitere Informationen zu DNS und Lastenausgleich finden Sie unter [DNS-Anforderungen für Skype for Business Server.](../../plan-your-deployment/network-requirements/dns.md) 
    
    > [!NOTE]
    > Das Bündeln mehrerer Server ist nur in Enterprise Edition Bereitstellungen verfügbar. Wenn Sie einen einzelnen Enterprise Server oder Standard Edition Server bereitstellen, müssen Sie nur einen A-Eintrag für den einzelnen Server erstellen. 
  
    Wenn Sie beispielsweise über einen Pool mit dem Namen "pool.contoso.local" und drei Front-End-Server verfügen, erstellen Sie die folgenden DNS-Einträge:
    
   |**FQDN**|**Type**|**Data**|
   |:-----|:-----|:-----|
   |pool.contoso.local  <br/> |Host (A)  <br/> |10.0.0.5  <br/> |
   |pool.contoso.local  <br/> |Host (A)  <br/> |10.0.0.6  <br/> |
   |pool.contoso.local  <br/> |Host (A)  <br/> |10.0.0.7  <br/> |
   
8. Fahren Sie mit dem Erstellen von A-Datensätzen für alle Server in der geplanten Bereitstellung fort. 
    
9. Klicken Sie zum Erstellen des SRV-Eintrags (Service Record) für die Legacyermittlung mit der rechten Maustaste auf die SIP-Domäne, und wählen Sie **"Andere neue Datensätze" aus.**
    
10. Klicken Sie in **"Ressourceneintragstyp auswählen"** auf **"Dienstspeicherort (SRV)**" und dann auf **"Datensatz erstellen".**
    
11. Klicken Sie auf **"Dienst",** und geben Sie dann **_sipinternaltls** ein.
    
12. Klicken Sie auf **Protokoll**, und geben Sie **_tcp** ein.
    
13. Klicken Sie auf **Portnummer**, und geben Sie **5061** ein.
    
14. Klicken Sie auf **"Host", der diesen Dienst anbietet,** und geben Sie dann den FQDN des Pools oder Standard Edition Servers ein.
    
     ![Screenshot des Dialogfelds "Neuer Ressourcendatensatz".](../../media/54b1aac5-a2ec-41fe-90c0-02eaeaa9d1b4.png)
  
15. Klicken Sie auf **OK** und dann auf **Fertig**.
    
### <a name="verify-dns-records"></a>Überprüfen von DNS-Einträgen

1. Melden Sie sich bei einem Clientcomputer in der Domäne mit einem Konto an, das Mitglied der Gruppe "Authentifizierte Benutzer" ist oder über entsprechende Berechtigungen verfügt.
    
2. Klicken Sie auf **"Start",** und geben Sie **"cmd" ein,** und drücken Sie die EINGABETASTE.
    
3. Geben Sie **"nslookup" \<FQDN of the Front End pool\>** oder **\<FQDN of the Standard Edition server or single Enterprise Edition server\>** ", und drücken Sie die EINGABETASTE.
    
4. Überprüfen Sie weiterhin die restlichen A-Einträge für Ihre Bereitstellung.
    
5. Wenn Sie Legacyclients unterstützen und den SRV-Eintrag erstellt haben, überprüfen Sie ihn, indem Sie **"set type=srv"** an der **nslookup-Eingabeaufforderung** eingeben und dann die EINGABETASTE drücken.
    
6. Geben Sie **_sipinternaltls._tcp ein. *Domäne*** (z. B. _sipinternaltls._tcp.contoso.local), und drücken Sie dann die EINGABETASTE.
    
7. Die erwartete Ausgabe sollte der in der Abbildung dargestellten entsprechen. Beachten Sie, dass nicht alle DNS-Einträge in der Beispielausgabe angezeigt werden, aber alle Einträge überprüft werden sollten. 
    
     ![Überprüfen Sie die DNS-Einstellungen.](../../media/4fcaa70f-7717-4939-9652-d2048d6293cc.png)
  

