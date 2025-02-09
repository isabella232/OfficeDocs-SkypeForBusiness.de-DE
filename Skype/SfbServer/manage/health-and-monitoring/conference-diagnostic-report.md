---
title: Diagnosebericht über Konferenzen in Skype for Business Server
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
ms.assetid: e9edc23c-8ce8-4ab8-8786-9d22e1e51e14
description: 'Zusammenfassung: Erfahren Sie mehr über den Diagnosebericht über die Konferenz, der in Skype for Business Server verwendet wird.'
ms.openlocfilehash: 578f4f2a60ca5dd1706d3b366e4decc35effeb7b
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58630639"
---
# <a name="conference-diagnostic-report-in-skype-for-business-server"></a>Diagnosebericht über Konferenzen in Skype for Business Server
 
**Zusammenfassung:** Erfahren Sie mehr über den Diagnosebericht über die Konferenz, der in Skype for Business Server verwendet wird.
  
Der Diagnosebericht über Konferenzen enthält Informationen über Erfolg und Fehler aller Konferenzsitzungen. Beachten Sie, dass Skype for Business Server zwischen verschiedenen Arten von Fehlern unterscheidet:
  
- **Fehler erwartet.** Ein erwarteter Fehler ist in der Regel nur im technischsten Sinne ein Fehler. Angenommen, jemand startet eine Konferenz, hängt aber auf, bevor jemand teilnehmen kann. Technisch gesehen ist dies ein Fehler: Die Konferenz wurde initiiert, aber nicht abgeschlossen. Dies ist jedoch ein Fehler, den Sie erwarten würden: Wenn der Organisator die Konferenz abbricht, bevor jemand teilnehmen kann, erwarten Sie nicht, dass die Konferenz abgeschlossen wird.
    
- **Unerwarteter Fehler**: Ein unerwarteter Fehler ist genau das, was der Name aussagt: Ein Fehler, der gemessen an den Umständen nicht zu erwarten ist. Angenommen, Sie rufen eine Person an, und die Person kann den Anruf annehmen. Angenommen, eine Konferenz konnte nicht gehalten werden, da die Besprechungsrichtlinie des Organisators nicht abgerufen werden konnte. Das ist ein unerwarteter Fehler: Schließlich sollten Sie immer in der Lage sein, die Besprechungsrichtlinie eines Benutzers abzurufen.
    
Beachten Sie, dass die Metriken für "Erfolg", "Erwarteter Fehler" und "Unerwarteter Fehler" nicht zwangsläufig identisch mit der Metrik unter "Sitzungen insgesamt" sind. Beispielsweise können die folgenden Werte im Bericht angezeigt werden:
  
|**Erfolge**|**Erwartete Fehler**|**Unerwartete Fehler**|**Sitzungen insgesamt**|
|:-----|:-----|:-----|:-----|
|2024  <br/> |469  <br/> |16   <br/> |2521  <br/> |
   
If you add 2024 + 469 + 16 you get a total of 2,509 sessions and yet, the Total sessions column shows a total of 2,521 sessions. Die "fehlenden" 12 Sitzungen sind Sitzungen, die das System nicht als erfolgreich oder nicht kategorisieren konnte. Dies ist manchmal der Fall, wenn ein Drittanbieterprodukt einen neuen Diagnosecode einführt, der monitoring Server nicht vertraut ist. Wenn dies geschieht, können Aufrufe, die mit diesem Produkt getätigt werden und diesen Diagnosecode melden, nicht immer als "Erfolgreich", "Erwarteter Fehler" oder "Unerwarteter Fehler" kategorisiert werden.
  
## <a name="accessing-the-conference-diagnostic-report"></a>Zugreifen auf den Diagnosebericht über die Konferenz

Der Zugriff auf den Diagnosebericht über die Konferenz erfolgt über die Startseite für Überwachungsberichte. Sie können auf den [Bericht über Fehlerverteilung in Skype for Business Server](failure-distribution-report.md) zugreifen, indem Sie auf eine der folgenden Metriken klicken:
  
- Anzahl der unerwarteten Fehler
    
- Anzahl der erwarteten Fehler
    
## <a name="making-the-best-use-of-the-conference-diagnostic-report"></a>Optimale Nutzung des Diagnoseberichts für die Konferenz

Der Diagnosebericht über die Konferenz enthält eine Reihe von Diagrammen. Jede der im Diagramm angezeigten Spalten ist eigentlich ein Hyperlink. Wenn Sie auf eine Spalte klicken, führen Sie einen Drilldown zum [Bericht über Fehlerverteilung in Skype for Business Server](failure-distribution-report.md) für diesen Zeitraum und diesen Konferenztyp durch.
  
## <a name="filters"></a>Filter

Mithilfe von Filtern können Sie eine gezieltere Datenauswahl zurückgeben oder die zurückgegebenen Daten auf unterschiedliche Weise anzeigen. Mit dem Diagnosebericht über Konferenzen können Sie z. B. nach dem Typ der Konferenz filtern, die durchgeführt wird (z. B. eine konferenzfokussiert) oder nach dem in der Konferenz verwendeten Edgeserver. Sie können außerdem festlegen, wie Daten gruppiert werden sollen. In diesem Fall werden Konferenzen nach Stunde, Tag, Woche oder Monat zusammengefasst.
  
In der folgenden Tabelle sind die Filter aufgeführt, die Sie im Diagnosebericht über Konferenzen verwenden können.
  
**Diagnoseberichtsfilter für Konferenzen**

|**Name**|**Beschreibung**|
|:-----|:-----|
|**From** <br/> |Anfangsdatum und -uhrzeit für den Zeitraum. Wenn die Daten nach Stunden angezeigt werden sollen, geben Sie Anfangsdatum und -uhrzeit wie folgt ein:  <br/> 7.07.2015 13:00 Uhr  <br/> Wenn Sie keinen Anfangszeitpunkt eingeben, beginnt der Bericht automatisch am angegebenen Tag um 12:00 Uhr. Zum Anzeigen der Daten nach Tag geben Sie nur das Datum ein:  <br/> 7/7/2015  <br/> Sollen die Daten nach Woche oder Monat angezeigt werden, geben Sie irgendein Datum ein, das in die anzuzeigende Woche oder den anzuzeigenden Monat fällt (Sie müssen nicht den ersten Tag der Woche oder des Monats eingeben):  <br/> 7/3/2015  <br/> Eine Woche läuft immer von Sonntag bis einschließlich Samstag.  <br/> |
|**Ziel** <br/> |Enddatum und -uhrzeit für den Zeitraum. Wenn die Daten nach Stunden angezeigt werden sollen, geben Sie Enddatum und -uhrzeit wie folgt ein:  <br/> 7.07.2015 13:00 Uhr  <br/> Wenn Sie keinen Endzeitpunkt eingeben, endet der Bericht automatisch am angegebenen Tag um 12:00 Uhr. Zum Anzeigen der Daten nach Tag geben Sie nur das Datum ein:  <br/> 7/7/2015  <br/> Sollen die Daten nach Woche oder Monat angezeigt werden, geben Sie irgendein Datum ein, das in die anzuzeigende Woche oder den anzuzeigenden Monat fällt (Sie müssen nicht den ersten Tag der Woche oder des Monats eingeben):  <br/> 7/3/2015  <br/> Eine Woche läuft immer von Sonntag bis einschließlich Samstag.  <br/> |
|**Intervall** <br/> | Zeitintervall. Wählen Sie eine der folgenden Optionen aus: <br/>  Stündlich (maximal 25 Stunden können angezeigt werden) <br/>  Täglich (maximal 31 Tage können angezeigt werden) <br/>  Wöchentlich (maximal 12 Wochen können angezeigt werden) <br/>  Monatlich (maximal 12 Monate werden angezeigt) <br/>  Wenn mit dem angegebenen Start- und Endzeitpunkt die maximale Anzahl der zulässigen Werte für das ausgewählte Intervall überschritten wird, wird nur die maximale Anzahl an Werten (beginnend mit dem Startzeitpunkt) angezeigt. Wenn Sie z. B. das Intervall "Täglich" mit dem Startdatum 7.07.2015 und dem Enddatum 28.02.2015 auswählen, werden Daten für die Tage 07.08.2015 12:00 Uhr bis 07.09.2015 12:00 Uhr angezeigt (d. s. Daten insgesamt 31 Tage). <br/> |
|**Pool** <br/> |Vollqualifizierter Domänenname (FQDN) des Registrierungsstellenpools oder Edgeservers. Sie können einen einzelnen Pool auswählen, oder auf **[Alle]** klicken, um die Daten für alle Pools anzuzeigen. Diese Dropdownliste wird basierend auf den Datensätzen in der Datenbank automatisch ausgefüllt.<br/> |
|**Konferenzsitzungen** <br/> | Gibt den Typ der Konferenzsitzung an. Wählen Sie eine der folgenden Optionen aus: <br/>  [Alle] <br/>  Konferenzzustandsobjekt-Sitzungen <br/>  Alle MCU-Sitzungen <br/>  Sofortnachrichtenkonferenzen <br/>  Anwendungsfreigabe <br/>  A/V-Konferenzen <br/> |
   
## <a name="metrics"></a>Metriken

In der folgenden Tabelle sind die Informationen aufgeführt, die im Diagnosebericht über Konferenzen für jeden Konferenzsitzungstyp bereitgestellt werden.
  
**Metriken des Diagnoseberichts für Konferenzen**

|**Name**|**Kann nach dieser Metrik sortiert werden?**|**Beschreibung**|
|:-----|:-----|:-----|
|**Anzahl der erfolgreichen Sitzungen** <br/> |Nein  <br/> |Gesamtzahl der erfolgreichen Konferenzen.  <br/> |
|**Prozentsatz der erfolgreichen Sitzungen** <br/> |Nein  <br/> |Prozentsatz der Konferenzen, die mit erheblichen Problemen abgeschlossen wurden. Errechnet sich durch Dividieren der Anzahl der erfolgreichen Sitzungen durch die Gesamtzahl der Sitzungen.  <br/> |
|**Anzahl der erwarteten Fehler** <br/> |Nein  <br/> |Die Gesamtzahl der Konferenzen, bei denen ein "erwarteter Fehler" aufgetreten ist.  <br/> Ein erwarteter Fehler ist ein Fehler, dessen Auftreten erwartet wird. Wenn beispielsweise ein Benutzer seinen Status auf Nicht stören festgelegt hat, ist zu erwarten, dass jeder Anruf an diesen Benutzer fehlschlägt.  <br/> |
|**Prozentsatz der erwarteten Fehler** <br/> |Nein  <br/> |Prozentsatz der Konferenzen, bei denen ein erwarteter Fehler aufgetreten ist. Errechnet sich durch Dividieren der Anzahl der erwarteten Fehler durch die Gesamtzahl der Sitzungen.  <br/> |
|**Anzahl der unerwarteten Fehler** <br/> |Nein  <br/> |Gesamtzahl der Konferenzen, bei denen ein "unerwarteter Fehler" aufgetreten ist.  <br/> Ein unerwarteter Fehler ist ein Fehler, der in einem System auftritt, das abgesehen davon anscheinend intakt ist. Beispielsweise sollte ein Anruf nicht beendet werden, wenn der Anrufer in der Warteschleife platziert ist. Geschieht dies jedoch, würde dieser Vorgang als unerwarteter Fehler gekennzeichnet werden.  <br/> |
|**Prozentsatz der unerwarteten Fehler** <br/> |Nein  <br/> |Prozentsatz der Konferenzen, bei denen ein unerwarteter Fehler aufgetreten ist. Errechnet sich durch Dividieren der Anzahl der unerwarteten Fehler durch die Gesamtzahl der Sitzungen.  <br/> |
|**Sitzungen insgesamt** <br/> |Nein  <br/> |Die Gesamtzahl der Konferenzen, einschließlich erfolgreicher Konferenzen, fehlgeschlagener Konferenzen (sowohl erwarteter als auch unerwarteter Fehler) und nicht kategorisierter Konferenzen.  <br/> |
   

