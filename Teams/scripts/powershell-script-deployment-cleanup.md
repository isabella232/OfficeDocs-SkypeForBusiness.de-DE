---
title: PowerShell-Skriptbeispiel – Teams Bereinigung der Bereitstellung
author: cichur
ms.author: v-cichur
manager: serdars
ms.topic: article
ms.reviewer: amitsri
ms.service: msteams
audience: admin
description: Verwenden Sie dieses PowerShell-Skript, um Teams zu deinstallieren und Teams Ordner für Benutzer zu entfernen.
f1.keywords:
- NOCSH
ms.localizationpriority: medium
search.appverid: MET150
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-collaboration
appliesto:
- Microsoft Teams
ms.openlocfilehash: fe59604f6257d6bab736540d48775ffec36e5b9f
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58577789"
---
# <a name="powershell-script-sample---teams-deployment-clean-up"></a>PowerShell-Skriptbeispiel – Teams bereinigen der Bereitstellung

Verwenden Sie dieses Skript, um Teams. Dieses Skript deinstalliert Teams und entfernt Teams Ordner für einen Benutzer. Führen Sie dieses Skript für jedes Benutzerprofil aus, in Teams auf einem Computer installiert wurde.


## <a name="sample-script"></a>Beispielskript

````powershell
<#
.SYNOPSIS
This script uninstalls the Teams app and removes the Teams directory for a user.
.DESCRIPTION
Use this script to remove and clear the Teams app from a computer. Run this PowerShell script for each user profile in which Teams was installed on the computer. After you run this script for all user profiles, redeploy Teams.
#>

$TeamsPath = [System.IO.Path]::Combine($env:LOCALAPPDATA, 'Microsoft', 'Teams')
$TeamsUpdateExePath = [System.IO.Path]::Combine($TeamsPath, 'Update.exe')

try
{
    if ([System.IO.File]::Exists($TeamsUpdateExePath)) {
        Write-Host "Uninstalling Teams process"

        # Uninstall app
        $proc = Start-Process $TeamsUpdateExePath "-uninstall -s" -PassThru
        $proc.WaitForExit()
    }
    Write-Host "Deleting Teams directory"
    Remove-Item –path $TeamsPath -recurse
}
catch
{
    Write-Output "Uninstall failed with exception $_.exception.message"
    exit /b 1
}

````

## <a name="related-topics"></a>Verwandte Themen

- [Installieren von Microsoft Teams mit Microsoft Endpoint Configuration Manager](../msi-deployment.md)
- [Bereitstellen Teams mit Microsoft 365 Apps](/deployoffice/teams-install)
