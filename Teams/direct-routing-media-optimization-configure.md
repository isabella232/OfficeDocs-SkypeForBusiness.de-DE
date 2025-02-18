---
title: Konfigurieren der lokalen Medienoptimierung für direktes Routing
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 04/07/2020
ms.topic: article
ms.service: msteams
audience: admin
ms.collection:
- M365-voice
ms.reviewer: filippse
search.appverid: MET150
f1.keywords:
- NOCSH
description: Konfigurieren der lokalen Medienoptimierung für direktes Routing
appliesto:
- Microsoft Teams
ms.openlocfilehash: 3e383a9d0435dde2c17a38d8a1879b3bf3fb6e4d
ms.sourcegitcommit: 99503baa8b5183972caa8fe61e92a362213599d9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2021
ms.locfileid: "60127402"
---
# <a name="configure-local-media-optimization-for-direct-routing"></a>Konfigurieren der lokalen Medienoptimierung für direktes Routing

Die Konfiguration für die Optimierung lokaler Medien basiert auf Netzwerkeinstellungen, die für andere Cloud-Sprachfeatures wie Location-Based Routing und dynamische Notrufe verwendet werden. Weitere Informationen zu Netzwerkregionen, Netzwerkstandorten, Netzwerksubnetzen und vertrauenswürdigen IP-Adressen finden Sie unter Netzwerkeinstellungen für [Cloud-Sprachfeatures.](cloud-voice-network-settings.md)

Informationen zum Konfigurieren der Optimierung lokaler Medien finden Sie unter [Optimierung lokaler Medien für Direktes Routing.](direct-routing-media-optimization.md)  

Zum Konfigurieren der Lokalen Medienoptimierung sind die folgenden Schritte erforderlich. Sie können das Teams Admin Center oder PowerShell verwenden. Details finden Sie unter [Verwalten der Netzwerktopologie.](manage-your-network-topology.md)

1. Konfigurieren sie den Benutzer und die SBC-Websites (wie in diesem Artikel beschrieben).
2. Konfigurieren Sie die SBCs für die lokale Medienoptimierung (gemäß SBC-Anbieterspezifikation).

Das folgende Diagramm zeigt die in den Beispielen in diesem Artikel verwendete Netzwerkeinrichtung.

> [!div class="mx-imgBorder"]
> ![Diagramm mit Beispielen für die Netzwerkeinrichtung.](media/direct-routing-media-op-9.png "Netzwerkeinrichtung für Beispiele")


## <a name="configure-the-user-and-the-sbc-sites"></a>Konfigurieren des Benutzers und der SBC-Websites

Um den Benutzer und die SBC-Websites zu konfigurieren, müssen Sie:

1. [Verwalten Sie externe vertrauenswürdige IP-Adressen.](#manage-external-trusted-ip-addresses)  

2. [Definieren Sie die Netzwerktopologie,](#define-the-network-topology) indem Sie die Netzwerkbereiche, Netzwerkstandorte und Netzwerk-Subnetze konfigurieren.

3. [Definieren Sie die virtuelle Netzwerktopologie,](#define-the-virtual-network-topology) indem Sie Website(n) mit relevanten Modi und Proxy-SBC-Werten SBC(s) zuweisen.

> [!NOTE]
> Die Logik für die Optimierung lokaler Medien basiert darauf, dass Clientadressen relativ zu Unternehmensnetzwerken, die auf eine interne SBC-Schnittstelle (Session Border Controller) (Direct Routing Certified Session Border Controller) zugreifen können, als externe oder interne Adressen konfiguriert sind. Die Clientposition (intern/extern) wird während der Verarbeitung jedes Anrufs bestimmt, indem die Adresse zur Herstellung der Transport relays ermittelt wird.
> 
> In VPN-Szenarien mit geteilten Tunneln, in denen Relay über den Internetdienstanbieter erreichbar ist, bevorzugt die Logik für die optimale Route des Clients die Standardroute der lokalen Schnittstelle (z. B. öffentliches WLAN). Dies bewirkt, dass Microsoft dem SBC signalisiert, dass der Client extern ist, obwohl er die interne Schnittstelle des Direct-Routing-SBC des Kunden erreichen kann. Bei Kunden mit Direct Routing, die lokale Medienoptimierung verwenden, kann es zu längeren Anrufeinrichtungszeiten und in einigen Fällen zu keinem Audiosignal beim Empfang von Anrufen aus dem PSTN kommen.
> 
> Um dies zu vermeiden, müssen VPN-Administratoren den Zugriff zwischen VPN-Remotebenutzern und der internen SBC-Schnittstelle für Direct-Routing blockieren.



## <a name="configure-sbcs-for-local-media-optimization-according-to-the-sbc-vendor-specification"></a>Konfigurieren Sie SBC(s) für die Optimierung lokaler Medien gemäß der SBC-Anbieterspezifikation

In diesem Artikel wird die Konfiguration für Microsoft-Komponenten beschrieben. Informationen zur SBC-Konfiguration finden Sie in der Dokumentation zu SBC-Lieferanten. Informationen dazu, welche SBC-Hersteller die Optimierung lokaler Medien unterstützen, finden Sie unter [Session Border Controller Certified for Direct Routing](direct-routing-border-controllers.md).

## <a name="manage-external-trusted-ip-addresses"></a>Verwalten von externen vertrauenswürdigen IP-Adressen

Bei externen vertrauenswürdigen IPs handelt es sich um die externen Internet-IPs des Unternehmensnetzwerks. Bei diesen IP-Adressen handelt es sich um die IP-Adressen, die von Microsoft Teams verwendet werden, wenn sie eine Verbindung mit Microsoft 365. Sie müssen diese externen IPs für jede Website hinzufügen, auf der Benutzer die Optimierung lokaler Medien verwenden.

Um die öffentlichen IP-Adressen für jede Website hinzuzufügen, verwenden Sie das cmdlet New-CsTenantTrustedIPAddress Cmdlet . Sie können eine unbegrenzte Anzahl von vertrauenswürdigen IP-Adressen für einen Mandanten definieren. Wenn es sich bei den von Microsoft 365 verwendeten externen IPs um IPv4- und IPv6-Adressen handelt, müssen Sie beide Typen von IP-Adressen hinzufügen. Verwenden Sie für IPv4 mask 32. Verwenden Sie für IPv6 die Maske 128. Sie können sowohl einzelne externe IP-Adressen als auch externe IP-Subnetze hinzufügen, indem Sie im Cmdlet verschiedene MaskBits angeben.

```
New-CsTenantTrustedIPAddress -IPAddress <External IP address> -MaskBits <Subnet bitmask> -Description <description>
```


Beispiel für das Hinzufügen von vertrauenswürdigen IP-Adressen

```
New-CsTenantTrustedIPAddress -IPAddress 172.16.240.110 -MaskBits 32 -Description "Vietnam site trusted IP"
New-CsTenantTrustedIPAddress -IPAddress 172.16.240.120 -MaskBits 32 -Description "Indonesia site trusted IP"
New-CsTenantTrustedIPAddress -IPAddress 172.16.240.130 -MaskBits 32 -Description "Singapore site trusted IP"
```


## <a name="define-the-network-topology"></a>Definieren der Netzwerktopologie

In diesem Abschnitt wird beschrieben, wie Sie die Netzwerkregionen, Netzwerkstandorte und Netzwerksubnetze für Ihre Netzwerktopologie definieren.

Bei allen Parametern muss die Zwischenschreibung beachtet werden, daher müssen Sie sicherstellen, dass Sie die gleiche Schreibung wie beim Setup verwenden.  (Die Werte "GatewaySiteID" "Vietnam" und "vietnam" werden z. B. als unterschiedliche Websites behandelt.)

### <a name="define-network-regions"></a>Definieren von Netzwerkregionen

Verwenden Sie zum Definieren von Netzwerkregionen das cmdlet New-CsTenantNetworkRegion Netzwerk. Der Parameter RegionID ist ein logischer Name, der die Geografie der Region darstellt und keine Abhängigkeiten oder Einschränkungen aufweist. Der Parameter CentralSite `<site ID>` ist optional.

```powershell
New-CsTenantNetworkRegion -NetworkRegionID <region ID>  
```

Das folgende Beispiel erstellt eine Netzwerkregion namens APAC:

```powershell
New-CsTenantNetworkRegion -NetworkRegionID "APAC"  
```

###  <a name="define-network-sites"></a>Definieren von Netzwerkwebsites

Verwenden Sie zum Definieren von Netzwerkwebsites das cmdlet New-CsTenantNetworkSite Netzwerkwebsites. Jede Netzwerkwebsite muss einer Netzwerkregion zugeordnet sein.

```powershell
New-CsTenantNetworkSite -NetworkSiteID <site ID> -NetworkRegionID <region ID>
```

Im folgenden Beispiel werden drei neue Netzwerkwebsites erstellt: Vietnam, Indonesien und Singapur in der Region APAC:

```powershell
New-CsTenantNetworkSite -NetworkSiteID "Vietnam" -NetworkRegionID "APAC"
New-CsTenantNetworkSite -NetworkSiteID "Indonesia" -NetworkRegionID "APAC"
New-CsTenantNetworkSite -NetworkSiteID "Singapore" -NetworkRegionID "APAC"
```

### <a name="define-network-subnets"></a>Definieren von Netzwerk-Subnetzen

Verwenden Sie zum Definieren von Netzwerksubnetzen und zum Zuordnen dieser Subnetze zu Netzwerkstandorten das cmdlet New-CsTenantNetworkSubnet Netzwerkverbindung. Jedes Netzwerksubnetz kann nur einem Standort zugeordnet werden. 

```powershell
New-CsTenantNetworkSubnet -SubnetID <Subnet IP address> -MaskBits <Subnet bitmask> -NetworkSiteID <site ID>
```

Im folgenden Beispiel werden drei Netzwerksubnetze definiert und den drei Netzwerkstandorten zugeordnet: Vietnam, Indonesien und Singapur:

```powershell
New-CsTenantNetworkSubnet -SubnetID 192.168.1.0 -MaskBits 24 -NetworkSiteID “Vietnam”
New-CsTenantNetworkSubnet -SubnetID 192.168.2.0 -MaskBits 24 -NetworkSiteID “Indonesia”
New-CsTenantNetworkSubnet -SubnetID 192.168.3.0 -MaskBits 24 -NetworkSiteID “Singapore”
```

## <a name="define-the-virtual-network-topology"></a>Definieren der virtuellen Netzwerktopologie 

Zuerst erstellt der Mandantenadministrator eine neue SBC-Konfiguration für jeden relevanten SBC mithilfe des cmdlets New-CsOnlinePSTNGateway SBC.
Der Mandantenadministrator definiert die virtuelle Netzwerktopologie durch Angeben der Netzwerkwebsites für die PSTN-Gatewayobjekte mithilfe des Set-CsOnlinePSTNGateway-Cmdlets:

```powershell
PS C:\> Set-CsOnlinePSTNGateway -Identity <Identity> -GatewaySiteID <site ID> -MediaBypass <true/false> -BypassMode <Always/OnlyForLocalUsers> -ProxySBC  <proxy SBC FQDN or $null>
```

Beachten Sie Folgendes: 
   - Wenn der Kunde über einen einzigen SBC verfügt, muss der Parameter "-ProxySBC" entweder obligatorisch $null oder ein SBC-FQDN-Wert sein (Szenario: zentraler SBC mit zentralisierten Trunks).
   - Der -MediaBypass-Parameter muss auf "$true festgelegt werden, um die Optimierung lokaler Medien zu unterstützen.
   - Wenn für SBC der Parameter -BypassMode nicht festgelegt ist, werden X-MS-Header nicht gesendet. 
   - Bei allen Parametern muss die Zwischenschreibung beachtet werden, daher müssen Sie sicherstellen, dass Sie die gleiche Schreibung wie beim Setup verwenden.  (Die Werte "GatewaySiteID" "Vietnam" und "vietnam" werden z. B. als unterschiedliche Websites behandelt.)

Im folgenden Beispiel werden den Netzwerkstandorten Vietnam, Indonesien und Singapur in der Region APAC drei SBCs mit dem Modus Immer umgehen hinzufügt:

```powershell
Set-CSOnlinePSTNGateway -Identity “proxysbc.contoso.com” -GatewaySiteID “Singapore” -MediaBypass $true -BypassMode “Always” -ProxySBC $null

Set-CSOnlinePSTNGateway -Identity “VNsbc.contoso.com” -GatewaySiteID “Vietnam” -MediaBypass $true -BypassMode “Always” -ProxySBC “proxysbc.contoso.com”

Set-CSOnlinePSTNGateway -Identity “IDsbc.contoso.com” -GatewaySiteID “Indonesia” -MediaBypass $true -BypassMode “Always” -ProxySBC “proxysbc.contoso.com”
```

> [!NOTE]
> Um unterbrechungsfreie Vorgänge bei gleichzeitiger Konfiguration der Lokalen Medienoptimierung und des Location-Based-Routings (LBR) sicherzustellen, müssen downstream-SBCs für LBR aktiviert werden, indem der Parameter GatewaySiteLbrEnabled für jeden downstream-SBC auf $true festgelegt wird. (Diese Einstellung ist für den Proxy-SBC nicht obligatorisch.)

Gemäß den vorstehenden Informationen enthält Direct Routing drei proprietäre SIP Headers zu SIP Invites und Re-invites, wie in der folgenden Tabelle dargestellt.

X-MS-Header, die in Direct Routing für Einladungen und Einladungen eingeführt Re-Invites, wenn BypassMode definiert ist:

| Headername | Werte | Kommentare | 
|:------------|:-------|:-------|
| X-MS-UserLocation | intern/extern | Gibt an, ob es sich um einen internen oder externen Benutzer handelt. |
| Request-URI INVITE sip: +84439263000@VNsbc.contoso.com SIP /2.0 | SBC-FQDN | Der für den Aufruf bestimmte FQDN selbst dann, wenn der SBC nicht direkt mit dem Direct-Routing verbunden ist |
| X-MS-MediaPath | Beispiel: proxysbc.contoso.com, VNsbc.contoso.com | Reihenfolge der SBCs, die für den Medienpfad zwischen Dem Benutzer und Ziel-SBC verwendet werden sollten. Der endgültige SBC ist immer |
| X-MS-UserSite | usersiteID | Vom Mandantenadministrator definierte Zeichenfolge |

## <a name="call-flows"></a>Anrufflüsse 

Im Folgenden werden die Anrufflüsse für zwei Modi gezeigt:

- [Immer umgehen](#always-bypass-mode)
- [Nur für lokale Benutzer](#only-for-local-users-mode)

### <a name="always-bypass-mode"></a>Always Bypass mode

Der Immerumgehungsmodus ist die einfachste zu konfigurierende Option. Der Mandantenadministrator kann eine einzelne Website für alle Benutzer und SBCs konfigurieren, wenn alle SBCs von einer beliebigen Website aus erreichbar sind.

Die Beispiele zeigen immer den Umgehungsmodus für die folgenden Szenarien:

- [Ausgehende Anrufe, an dem sich der Benutzer am selben Ort wie der SBC befindet](#outbound-calls-and-the-user-is-in-the-same-location-as-the-sbc-with-always-bypass)
- [Eingehende Anrufe, und der Benutzer befindet sich an demselben Speicherort wie der SBC](#inbound-calls-and-the-user-is-in-the-same-location-as-the-sbc-with-always-bypass)
- [Ausgehende Anrufe, der Benutzer ist extern](#outbound-calls-and-the-user-is-external-with-always-bypass)
- [Eingehende Anrufe und externe Benutzer](#inbound-calls-and-the-user-is-external-with-always-bypass)

Die folgende Tabelle zeigt die in den Beispielen verwendeten FQDN- und IP-Adressen:

| FQDN | Externe SBC-IP-Adresse | Interne SBC-IP-Adresse | Internes Subnetz | Ort | Externes NAT (Trusted IP, vertrauenswürdige IP) |
|:------------|:-------|:-------|:-------|:-------|:-------|
| VNsbc.contoso.com | Keine | 192.168.1.5 | 192.168.1.0/24 | Vietnam | 172.16.240.110 |
| IDsbc.contoso.com | Keine | 192.168.2.5 | 192.168.2.0/24 | Indonesien | 172.16.240.120 |
| proxysbc.contoso.com | 172.16.240.133 | 192.168.3.5 | 192.168.3.0/24 | Singapur | 172.16.240.130 |



#### <a name="outbound-calls-and-the-user-is-in-the-same-location-as-the-sbc-with-always-bypass"></a>Ausgehende Anrufe, an dem sich der Benutzer mit "Always Bypass" am selben Ort wie der SBC befindet

| Modus |    Benutzer |  Ort |  Anrufrichtung |
|:------------|:-------|:-------| :-------|
| AlwaysBypass |    Intern |  Dieselbe Website wie SBC |  Ausgehend |

Die folgende Tabelle zeigt die Konfiguration und Aktion des Endbenutzers:

| Physischer Standort des Benutzers| Benutzer macht oder empfängt einen Anruf an/von der Nummer | Telefonnummer des Benutzers  | Online Voice Routing Policy | Für SBC konfigurierter Modus |
|:------------|:-------|:-------|:-------|:-------|
| Vietnam | +84 4 3926 3000 | +84 4 5555 5555   | Priorität 1: ^ \+ 84(\d {9} )$ -VNsbc.contoso.com <br> Priorität 2: .* - proxysbc.contoso.com   | VNsbc.contoso.com – Immer umgehen <br> proxysbc.contoso.com – Immer umgehen


Das folgende Diagramm zeigt die SIP-Leiter für einen ausgehenden Anruf mit Immer Umgehungsmodus und dem Benutzer am selben Ort wie der SBC.

> [!div class="mx-imgBorder"]
> ![Diagramm, das ausgehende Anrufe zeigt.](media/direct-routing-media-op-10.png "Ausgehende Anrufe")

Die folgende Tabelle zeigt die X-MS-Header, die von Direct Routing gesendet werden:

| Parameter | Erklärung |
|:------------|:-------|
| Einladen +8443926300@VNsbc.contoso.com | Der Ziel-FQDN der SBC gemäß Definition in der Online-Voiceroutingrichtlinie wird im Anforderungs-URI | 
| X-MS-UserLocation: intern | Das Feld wies darauf hin, dass sich der Benutzer im Unternehmensnetzwerk befindet. |
| X-MS-MediaPath: VNsbc.contoso.com |   Gibt an, welche SBC der Client zum Ziel-SBC durchlaufen muss. In diesem Fall, da es "Always Bypass" gibt und der Client intern der Zielname ist, der als einziger Name in der Kopfzeile gesendet wird. | 
|X-MS-UserSite: Vietnam |   Das Feld, das auf der Website angegeben ist, auf der sich der Benutzer befindet. |


#### <a name="inbound-calls-and-the-user-is-in-the-same-location-as-the-sbc-with-always-bypass"></a>Eingehende Anrufe, an die sich der Benutzer mit "Always Bypass" an derselben Position wie der SBC befindet

| Modus |    Benutzer |  Ort |  Anrufrichtung |
|:------------|:-------|:-------|:-------|:-------|
| AlwaysBypass |    Intern | Dieselbe Website wie SBC | Eingehende |


Bei einem eingehenden Anruf ist der Standort des Benutzers unbekannt, und der SBC muss erraten, wo sich der Benutzer befindet. Wenn der Rat nicht richtig ist, ist eine erneute Einladung erforderlich. In diesem Fall wird davon ausgegangen, dass es sich um einen internen Benutzer handelt, dass Medien direkt fließen können und keine weiteren Aktionen erforderlich sind (erneutes Einladen).
Der mit dem Direct Routing-Dienst verbundene SBC meldet den ursprungsenden SBC-Speicherort, indem Record-Route Und Kontaktfelder bereitstellen. Basierend auf diesen Feldern wird der Medienpfad mit Direct Routing berechnet.

Hinweis: Da ein Benutzer mehrere Endpunkte haben kann, ist die Unterstützung von 183 nicht möglich. Für Direct-Routing wird in diesem Fall immer "180 Klingeln" verwendet. 

Das folgende Diagramm zeigt die SIP-Leiter für eingehenden Anruf mit AlwaysBypass-Modus, und der Benutzer befindet sich an derselben Position wie der SBC.

> [!div class="mx-imgBorder"]
> ![Diagramm mit SIP-Leiter.](media/direct-routing-media-op-11.png)


#### <a name="outbound-calls-and-the-user-is-external-with-always-bypass"></a>Ausgehende Anrufe mit "Immer umgehen" für externe Benutzer

| Modus |    Benutzer |  Site |  Anrufrichtung
|:------------|:-------|:-------|:-------|
AlwaysBypass |  Extern |  Nicht zutreffend | Ausgehend |


Das folgende Diagramm zeigt die SIP-Leiter für einen ausgehenden Anruf mit AlwaysBypass-Modus, und der Benutzer ist extern:

> [!div class="mx-imgBorder"]
> ![Diagramm der SIP-Leiter.](media/direct-routing-media-op-12.png)

Die folgende Tabelle zeigt die X-MS-Header, die vom Direct-Routingdienst gesendet werden:

| Parameter |   Erklärung |
|:------------|:-------|
|Einladen +8443926300@VNsbc.contoso.com | Der Ziel-FQDN der SBC, wie in der Online-Voiceroutingrichtlinie definiert, wird in den Anforderungs-URI gesendet.|
| X-MS-UserLocation: extern | Das Feld wies darauf hin, dass sich der Benutzer außerhalb des Unternehmensnetzwerks befindet. |
| X-MS-MediaPath: proxysbc.contoso.com, VNsbc.contoso.com    | Gibt an, welche SBC der Client zum Ziel-SBC durchlaufen muss. In diesem Fall ist der Client extern, da wir "Always Bypass" verwenden. |

#### <a name="inbound-calls-and-the-user-is-external-with-always-bypass"></a>Eingehende Anrufe und externe Benutzer mit "Always Bypass"

| Modus | Benutzer | Site |  Anrufrichtung |
|:------------|:-------|:-------|:-------|
AlwaysBypass |  Extern |  Nicht zutreffend |   Eingehende |

Bei einem eingehenden Anruf muss der mit Direct-Routing verbundene SBC eine erneute Einladung senden (standardmäßig werden immer lokale Medienkandidaten angeboten), wenn sich der Benutzer extern befindet.  Der X-MediaPath-Wert wird auf Grundlage Record-Route angegebenen SBC-Benutzers berechnet.

Das folgende Diagramm zeigt die SIP-Leiter für einen eingehenden Anruf mit AlwaysBypass-Modus, und der Benutzer ist extern.

> [!div class="mx-imgBorder"]
> ![Diagramm wieder mit SIP-Leiter.](media/direct-routing-media-op-13.png)


### <a name="only-for-local-users-mode"></a>Nur für lokalen Benutzermodus

Lokale Medienkandidaten des Ziel-SBC werden nur angeboten, wenn sich ein Benutzer an demselben Speicherort wie der SBC befindet. In allen anderen Fällen werden Medien entweder durch eine interne oder externe IP des Proxy-SBC fließen.

Die folgenden Szenarien werden beschrieben:

- [Ausgehende Anrufe, an dem sich der Benutzer am selben Ort wie der SBC befindet](#outbound-calls-and-the-user-is-in-the-same-location-as-the-sbc-with-only-for-local-users)
- [Eingehende Anrufe, und der Benutzer befindet sich an demselben Speicherort wie der SBC](#inbound-calls-and-the-user-is-in-the-same-location-as-the-sbc-with-only-for-local-users)
- [Der Benutzer befindet sich nicht am selben Speicherort wie der SBC, sondern befindet sich im Unternehmensnetzwerk.](#user-is-not-at-the-same-location-as-the-sbc-but-is-in-the-corporate-network-with-only-for-local-users)
- [Eingehende Anrufe, der Benutzer ist intern, befindet sich aber nicht am selben Speicherort wie der SBC](#inbound-call-and-the-user-is-internal-but-is-not-at-the-same-location-as-the-sbc-with-only-for-local-users)

Die folgende Tabelle zeigt die Konfiguration und Aktion des Endbenutzers:

| Physischer Standort des Benutzers |  Benutzer macht oder empfängt einen Anruf an/von der Nummer |  Telefonnummer des Benutzers | Online Voice Routing Policy |   Für SBC konfigurierter Modus |
|:------------|:-------|:-------|:-------|:-------|
| Vietnam | +84 4 3926 3000 |  +84 4 5555 5555 | Priorität 1: ^ \+ 84(\d {9} )$ -VNsbc.contoso.com <br> Priorität 2: .* - proxysbc.contoso.com | VNsbc.contoso.com – OnlyForLocalUsers Proxysbc.contoso.com – Immer umgehen |

#### <a name="outbound-calls-and-the-user-is-in-the-same-location-as-the-sbc-with-only-for-local-users"></a>Ausgehende Anrufe, und der Benutzer befindet sich an demselben Ort wie der SBC mit Nur für lokale Benutzer.

| Modus | Benutzer | Site | Anrufrichtung |
|:------------|:-------|:-------|:-------|
| OnlyForLocalUsers |   Intern |Identisch mit SBC   | Ausgehend |

Das folgende Diagramm zeigt einen ausgehenden Anruf mit dem OnlyForLocalUsers-Modus, und der Benutzer befindet sich an demselben Ort wie der SBC. Dies ist der gleiche Fluss, der unter Ausgehende Anrufe angezeigt wird, wenn sich der Benutzer am selben Ort [wie der SBC befindet.](#outbound-calls-and-the-user-is-in-the-same-location-as-the-sbc-with-always-bypass)

> [!div class="mx-imgBorder"]
> ![Diagramm zeigt erneut die SIP-Leiter.](media/direct-routing-media-op-14.png)


#### <a name="inbound-calls-and-the-user-is-in-the-same-location-as-the-sbc-with-only-for-local-users"></a>Eingehende Anrufe, und der Benutzer befindet sich an demselben Speicherort wie SBC mit Nur für lokale Benutzer

| Modus | Benutzer | Site | Anrufrichtung |
|:------------|:-------|:-------|:-------|
| OnlyForLocalUsers |   Intern | Identisch mit SBC | Eingehende |

Das folgende Diagramm zeigt einen eingehenden Anruf mit dem OnlyForLocalUsers-Modus, und der Benutzer befindet sich an derselben Position wie der SBC. Dies ist der gleiche Fluss wie in eingehenden Anrufen, wenn sich der Benutzer am selben Ort wie der [SBC befindet.](#inbound-calls-and-the-user-is-in-the-same-location-as-the-sbc-with-always-bypass)

> [!div class="mx-imgBorder"]
> ![Ein weiteres Diagramm zeigt die SIP-Leiter.](media/direct-routing-media-op-15.png)


#### <a name="user-is-not-at-the-same-location-as-the-sbc-but-is-in-the-corporate-network-with-only-for-local-users"></a>Der Benutzer befindet sich nicht am selben Speicherort wie der SBC, sondern befindet sich im Unternehmensnetzwerk mit Nur für lokale Benutzer.

| Modus | Benutzer | Site |Anrufrichtung |
|:------------|:-------|:-------|:-------|
| OnlyForLocalUsers  | Intern |   Anders als SBC | Ausgehend |

Beim direkten Routing wird X-MediaPath basierend auf dem gemeldeten Standort des Benutzers und des Modus berechnet, der auf der SBC konfiguriert ist.


Das folgende Diagramm zeigt einen ausgehenden Anruf mit dem OnlyForLocalUsers-Modus und einem internen Benutzer, der sich nicht am selben Speicherort wie der SBC befindet.

> [!div class="mx-imgBorder"]
> ![Ein weiteres Diagramm zeigt die SIP-Leiter.](media/direct-routing-media-op-16.png)


#### <a name="inbound-call-and-the-user-is-internal-but-is-not-at-the-same-location-as-the-sbc-with-only-for-local-users"></a>Eingehender Anruf, und der Benutzer ist intern, befindet sich aber nicht am selben Speicherort wie SBC mit Nur für lokale Benutzer

| Modus |    Benutzer |  Site |  Anrufrichtung |
|:------------|:-------|:-------|:-------|
| OnlyForLocalUsers | Intern |    Anders als SBC |    Eingehende |

Das folgende Diagramm zeigt einen eingehenden Anruf mit dem OnlyForLocalUsers-Modus und einen internen Benutzer, der sich nicht am selben Speicherort wie der SBC befindet.

> [!div class="mx-imgBorder"]
> ![Ein weiteres Diagramm zeigt die SIP-Leiter.](media/direct-routing-media-op-17.png)

