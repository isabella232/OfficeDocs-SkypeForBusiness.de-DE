---
title: Anpassen der Mac-Clientumgebung in Skype for Business
ms.author: v-cichur
author: cichur
manager: serdars
ms.reviewer: PhillipGarding
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: d1d9cfec-e923-4d02-a306-ee40a9114cb8
description: In diesem Artikel werden die Clienteinstellungen und -standardwerte beschrieben, die für die Skype for Business auf dem Mac-Client verfügbar sind, und wie sie von außerhalb der App bearbeitet werden.
ms.openlocfilehash: 9ece447b7d3bce37784e0f1d0b3f8fe3746fce86
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58578129"
---
# <a name="customize-the-mac-client-experience-in-skype-for-business"></a>Anpassen der Mac-Clientumgebung in Skype for Business
 
In diesem Artikel werden die Clienteinstellungen und -standardwerte beschrieben, die für die Skype for Business auf dem Mac-Client verfügbar sind, und wie sie von außerhalb der App bearbeitet werden.
  
## <a name="skype-for-business-on-mac-client-preference-settings"></a>einstellungen für Skype for Business für Mac-Clients

Bestimmte Features und Verhaltensweisen, die für Skype for Business auf Mac-Clients verfügbar sind, werden durch die Einstellungseinstellungen auf dem Client bestimmt. Die einstellungen für Skype for Business für Mac finden Sie in einer Datei auf Macs, die den Skype for Business-Client unter dem folgenden Pfad installiert haben: 
  
 **~/Library/Containers/com.microsoft.SkypeForBusiness/Data/Library/Preferences/com.microsoft.SkypeForBusiness.plist**
  
Um diese Einstellungen festzulegen, rufen Sie eine Terminalaufforderung auf dem Mac des Clients auf, und geben Sie bei Bedarf die Standardwerte ein, um com.microsoft.SkypeForBusiness-Schlüsselbefehle mithilfe der in der folgenden Tabelle beschriebenen Einstellungsschlüssel zu schreiben.
  
**Clienteinstellungsschlüssel**


| Key | Typ | Wert | Beschreibung |
|:-----|:-----|:-----|:-----|
|autoDetectAutoDicoveryURLs    |Boolescher Wert    |0 = manuelle Serverkonfiguration  <br/> 1 = automatische Servererkennung (Standard)    |Geben Sie an, wie Skype for Business den Transport und server identifiziert, der während der Anmeldung verwendet werden soll. Wenn Sie diese Richtlinieneinstellung aktivieren, müssen Sie **internalAutoDiscoveryURL** und **externalAutoDiscoveryURL** angeben.   |
|internalAutoDiscoveryURL    |String    |Vollständige AutoErmittlungs-URL    |Interne AutoErmittlungs-URL    |
|externalAutoDiscoveryURL    |String    |Vollständige AutoErmittlungs-URL    |Externe AutoErmittlungs-URL    |
|httpProxyDomain    |String    ||HTTP-Proxydomäne    |
|httpProxyUserName    |String    ||HTTP-Proxybenutzername    |
|httpProxyPassword    |String    ||HTTP-Proxykennwort    |
|trustedDomainList    |Array    ||Liste der vertrauenswürdigen Domänen für HTTP-Umleitungen.    |
|autoAcceptTimeout    |Nummer    |300 (Standard)    |Timeout für automatisches Annehmen für Benutzer ohne serverseitigen Unterhaltungsverlauf.    |
|warnWhenUnknownLocationForE911    |Boolescher Wert    |0 = Deaktiviert  <br/> 1 = Aktiviert    |Warnt den Benutzer, wenn er eine Notrufnummer von einem unbekannten Ort aus wählt.    |
|sipAddress    |String    ||Die SIP-Adresse (E-Mail), die für die Anmeldung bei Skype for Business verwendet wird.    |
|userName    |String    ||Der UPN (UserName), der zum Anmelden bei Skype for Business verwendet wird.    |
|userNameInAdvancedOnly    |Boolescher Wert    |0 = Anzeigen des Benutzernamenfelds auf dem Hauptanmeldungsbildschirm und im Dialogfeld "Erweiterte Eigenschaften"  <br/> 1 = Nur im Dialogfeld "Erweiterte Eigenschaften" das Feld "Benutzername" anzeigen (Standard)    |Geben Sie an, wo das Benutzernamenfeld während der Anmeldung angezeigt wird.    |
   
### <a name="usage-examples"></a>Verwendungsbeispiele

Wenn Sie der Liste der vertrauenswürdigen Domänen eine einzelne Domäne (Contoso.com) hinzufügen möchten, verwenden Sie den Schlüssel "trustedDomainList" wie dargestellt:
  
Defaults write com.microsoft.SkypeForBusiness trustedDomainList -array-add "Contoso.com"
  
Um der Liste der vertrauenswürdigen Domänen mehrere Domänen hinzuzufügen, verwenden Sie den Schlüssel "trustedDomainList" wie dargestellt:
  
defaults write com.microsoft.SkypeForBusiness trustedDomainList -array-add "sfb.com" "abc.com" "test.org"
  
### <a name="sample-unedited-settings"></a>Beispiel für unbearbeitete Einstellungen

Als Referenz finden Sie hier eine Beispieleinstellungsdatei, die nur die Standardeinstellungen verwendet: 
  
```console
{
    BITApplicationDidEnterBackgroundTime = "1496164840.505589";
    BITApplicationWasLaunched = 1;
    CallHistorySelectedFilterIndex = 0;
    HockeySDKAutomaticallySendCrashReports = 0;
    HockeySDKCrashReportActivated = 1;
    "LastSignOut_me" = "2017-05-30 17:22:17 +0000";
    "NSSplitView Subview Frames CallHistoryListDetailSplit" =     (
        "0.000000, 0.000000, 291.500000, 473.000000, NO, NO",
        "292.500000, 0.000000, 408.500000, 473.000000, NO, NO"
    );
    "NSSplitView Subview Frames calendarListSplitView" =     (
        "0.000000, 0.000000, 320.000000, 473.000000, NO, NO",
        "321.000000, 0.000000, 380.000000, 473.000000, NO, NO"
    );
   "NSSplitView Subview Frames conversationListSplitView" =     (
        "0.000000, 0.000000, 320.000000, 473.000000, NO, NO",
        "321.000000, 0.000000, 380.000000, 473.000000, NO, NO"
    );
    "NSWindow Frame HomeWindow" = "511 134 769 473 0 0 1280 778 ";
    "NSWindow Frame SignInWindow" = "388 208 512 518 0 0 1280 778 ";
    RawCameraSupportVersion = 7030;
    appRunning = 1;
    buildTime = "May 22 2017 12:37:28";
    "user@contoso.com_userPreferences" =     {
        ContactsListState =         {
            expandedGroupState =             {
                "/me/pendingContacts" = 0;
                "/ucwa/v1/applications/414177012058/people/groups/HR6ZQDk_JUI9WUR0Gq0TEAUYfYDk8OwzsPAuDxZfjxg=" = 0;
                "/ucwa/v1/applications/414177012058/people/groups/N-kLDW4VAs4O3PDv36MNyaYxhuqkRGD1eWpzDGdaHnw=" = 0;
                "/ucwa/v1/applications/414177012058/people/groups/RJk1X9SsFDq-MbvPe2eUyKTdPizt7-eMxij-ef1SGWQ=" = 0;
                "/ucwa/v1/applications/414177012058/people/groups/UulRAGZQL3JnSpYCDqy4KsZCboNF2pqmp-ru3sqiDPQ=" = 0;
                "/ucwa/v1/applications/414177012058/people/groups/Wsbhk9lfd8OUv_0aCtHmYPfm0Wal0mzoM5WFbkxaNjM=" = 0;
                "/ucwa/v1/applications/414177012058/people/groups/afYHfnLUqTmnwac55OaqHUNqLLCqFTZuDezsBeSLOko=" = 0;
                "/ucwa/v1/applications/414177012058/people/groups/aok8RuCx35GbuVLMp-_Zi4gnBK_c5qO7mANf4Drf8Ak=" = 0;
                "/ucwa/v1/applications/414177012058/people/groups/hSrWaq6LWhzvT6sRxpyQimwfXzMgLyEc3O4FgSokesc=" = 0;
                "/ucwa/v1/applications/414177012058/people/groups/mDdgSHulTTkweoDbjXVp7Y308xM70eFDDZn2j7sAytM=" = 0;
                "/ucwa/v1/applications/414177012058/people/groups/nj3ApLemRK23ChI-K3x_RRGjlEeqTh6_9w6kYwKWldQ=" = 1;
                "/ucwa/v1/applications/414177012058/people/groups/oRX0pDJ2zEP-DQOfynLdvnTEFFNnsv95uvCmVfHjSik=" = 0;
            };
        };
    };
    defaultAudioPlaybackDevice = <62706c69 73743030 d4010203 04050618 19582476 65727369 6f6e5824 6f626a65 63747359 24617263 68697665 72542474 6f701200 0186a0a5 07080f10 1155246e 756c6cd3 090a0b0c 0d0e5b64 6973706c 61794e61 6d655624 636c6173 735a6964 656e7469 66696572 80038004 80025f10 5a417070 6c655553 42417564 696f456e 67696e65 3a432d4d 65646961 20456c65 6374726f 6e696373 20496e63 2e202020 2020203a 4d696372 6f736f66 74204c69 66654368 6174204c 582d3330 30303a31 34313030 3030303a 322c315f 101a4d69 63726f73 6f667420 4c696665 43686174 204c582d 33303030 d2121314 155a2463 6c617373 6e616d65 5824636c 61737365 735f1016 4d6f6465 6c2e4175 64696f56 6964656f 44657669 6365a216 175f1016 4d6f6465 6c2e4175 64696f56 6964656f 44657669 6365584e 534f626a 6563745f 100f4e53 4b657965 64417263 68697665 72d11a1b 54726f6f 74800100 08001100 1a002300 2d003200 37003d00 43004a00 56005d00 68006a00 6c006e00 cb00e800 ed00f801 01011a01 1d013601 3f015101 54015900 00000000 00020100 00000000 00001c00 00000000 00000000 00000000 00015b>;
    defaultAudioRecordingDevice = <62706c69 73743030 d4010203 04050618 19582476 65727369 6f6e5824 6f626a65 63747359 24617263 68697665 72542474 6f701200 0186a0a5 07080f10 1155246e 756c6cd3 090a0b0c 0d0e5b64 6973706c 61794e61 6d655624 636c6173 735a6964 656e7469 66696572 80038004 80025f10 5a417070 6c655553 42417564 696f456e 67696e65 3a432d4d 65646961 20456c65 6374726f 6e696373 20496e63 2e202020 2020203a 4d696372 6f736f66 74204c69 66654368 6174204c 582d3330 30303a31 34313030 3030303a 322c315f 101a4d69 63726f73 6f667420 4c696665 43686174 204c582d 33303030 d2121314 155a2463 6c617373 6e616d65 5824636c 61737365 735f1016 4d6f6465 6c2e4175 64696f56 6964656f 44657669 6365a216 175f1016 4d6f6465 6c2e4175 64696f56 6964656f 44657669 6365584e 534f626a 6563745f 100f4e53 4b657965 64417263 68697665 72d11a1b 54726f6f 74800100 08001100 1a002300 2d003200 37003d00 43004a00 56005d00 68006a00 6c006e00 cb00e800 ed00f801 01011a01 1d013601 3f015101 54015900 00000000 00020100 00000000 00001c00 00000000 00000000 00000000 00015b>;
    firstRun = 0;
    showEndCallDialog = 1;
}
```
