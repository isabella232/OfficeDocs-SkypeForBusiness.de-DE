---
title: Hinzufügen des Director-Dateispeichers
ms.reviewer: ''
ms.author: v-cichur
author: cichur
manager: serdars
ms.date: 3/25/2015
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.tb.AddDirectorFileStorePage
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.assetid: a15b69e0-d3d1-4648-af25-1c0f25e5da8e
description: Sie müssen eine Dateifreigabe angeben, die als Dateispeicher für Directors verwendet werden soll. Sie können als Dateispeicher eine vorhandene Dateifreigabe oder eine neue Dateifreigabe auswählen, indem Sie den vollqualifizierten Domänennamen (FQDN) des Dateiservers, auf dem sich die Dateifreigabe befindet, und einen Ordnernamen für die neue Dateifreigabe angeben.
ms.openlocfilehash: 5de21190637cbbac65d5cb7f4dc69f8a7591b962
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58600290"
---
# <a name="add-director-file-store"></a>Hinzufügen des Director-Dateispeichers

Sie müssen eine Dateifreigabe angeben, die als Dateispeicher für Directors verwendet werden soll. Sie können als Dateispeicher eine vorhandene Dateifreigabe oder eine neue Dateifreigabe auswählen, indem Sie den vollqualifizierten Domänennamen (FQDN) des Dateiservers, auf dem sich die Dateifreigabe befindet, und einen Ordnernamen für die neue Dateifreigabe angeben.

> [!IMPORTANT]
> Wenn Sie Ihrer Topologie Directors hinzufügen, ist für die Topologieveröffentlichung ein entsprechender Zugriff zum Einzurichten des Dateispeichers und zum Konfigurieren besitzerverwalteter Zugriffssteuerungslisten (Discretionary Access Control Lists, DACLs) für die Dateifreigabe erforderlich, die als Dateispeicher verwendet werden soll. Deshalb müssen Sie bei Ausführung des Topologie-Generators und zum Veröffentlichen der neuen Topologie mit einem Konto mit Vollzugriffsberechtigungen (Lesen/Schreiben/Ändern) für die Dateifreigabe angemeldet sein.

Ausführliche Informationen zur Speicherunterstützung für Dateifreigaben finden Sie unter ["Datei Storage Support"](/previous-versions/office/lync-server-2013/lync-server-2013-file-storage-support) in der Dokumentation zur Unterstützung und SQL Server Platzierung von [Daten und Protokolldateien](/previous-versions/office/lync-server-2013/lync-server-2013-sql-server-data-and-log-file-placement) in der Bereitstellungsdokumentation. Ausführliche Informationen zur gemeinsamen Verwendung der Dateifreigabe finden Sie unter [Unterstützte gemeinsame Serververwendung](/previous-versions/office/lync-server-2013/lync-server-2013-supported-server-collocation) in der Unterstützungsdokumentation. Ausführliche Informationen zum Entwerfen der Topologie für Directors finden Sie unter ["Definieren eines einzelnen Director im Topologie-Generator" in](/previous-versions/office/lync-server-2013/lync-server-2013-define-optional-director-topologies-in-your-topology) der Bereitstellungsdokumentation.