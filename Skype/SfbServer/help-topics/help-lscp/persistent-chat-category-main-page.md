---
title: Kategorie für beständigen Chat – Hauptseite
ms.reviewer: ''
ms.author: v-cichur
author: cichur
manager: serdars
ms.date: 3/27/2015
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.lscp.PersistentChatCategoryMain
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.assetid: b71c6e6f-681c-4230-954d-3e95ab64ca00
description: Sie können den Abschnitt Kategorie der Seite für beständigen Chat verwenden, um Kategorien zu konfigurieren. Eine Kategorie für beständigen Chatroom ist eine logische Struktur zum Organisieren von Chatrooms. In einer Kategorie ist eine Standardgruppe von Zugriffssteuerungslisten (Access Control Lists, ACLs) zum Steuern der Benutzer und Benutzergruppen definiert, die zum Erstellen oder zum Beitreten zu Chatrooms berechtigt sind. Sie können Kategorien verwenden, um "Chinesische Mauern" zwischen verschiedenen Unterabteilungen der Organisationen einzurichten.
ms.openlocfilehash: 6125672648d107b2c7e666dcf9637cac1e2fb3c7
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58630959"
---
# <a name="persistent-chat-category-main-page"></a>Kategorie für beständigen Chat – Hauptseite
 
Sie können den Abschnitt **Kategorie** der Seite für **beständigen Chat** verwenden, um Kategorien zu konfigurieren. Eine Kategorie für beständigen Chatroom ist eine logische Struktur zum Organisieren von Chatrooms. In einer Kategorie ist eine Standardgruppe von Zugriffssteuerungslisten (Access Control Lists, ACLs) zum Steuern der Benutzer und Benutzergruppen definiert, die zum Erstellen oder zum Beitreten zu Chatrooms berechtigt sind. Sie können Kategorien verwenden, um "Chinesische Mauern" zwischen verschiedenen Unterabteilungen der Organisationen einzurichten.
  
Chatroomkategorien können Chatrooms enthalten, jedoch keine anderen Kategorien. Jede Kategorie beschreibt ihre Inhalte mit Metadaten, z. B. _Name_ und _Beschreibung._ Darüber hinaus verfügt die Kategorie über Eigenschaften, die festgelegt werden können, um das Verhalten der zu ihr gehörenden Chatrooms zu steuern, z. B. ob die  _Chatrooms Einladungen_ oder _Dateiuploads_ zulassen oder  _den Chatverlauf_ enthalten.
  
Informationen zum Erstellen einer neuen Kategorie finden Sie unter [Verwalten von Kategorien im Server für beständigen Chat in Skype for Business Server 2015.](../../manage/persistent-chat/categories.md) Als Administrator für beständigen Chat können Sie Kategorien mithilfe der Systemsteuerung oder Windows PowerShell Cmdlets erstellen.
  
## <a name="tasks-that-you-can-perform"></a>Mögliche Aufgaben

Auf der Seite **Kategorie** können Sie die folgenden Aufgaben ausführen:
  
- Erstellen oder Bearbeiten einer neuen Kategorie
    
- Verschieben eines Chatrooms von einer Kategorie in eine andere
    
- Löschen eines Chatrooms oder einer Kategorie
    
## <a name="to-configure-categories-for-persistent-chat-rooms"></a>So konfigurieren Sie Kategorien für Chatrooms für beständigen Chat

1. Melden Sie sich mit einem Benutzerkonto, dem die Rolle "CsPersistentChatAdministrator" oder "CsAdministrator" zugewiesen ist, auf einem beliebigen Computer in Ihrer internen Bereitstellung an.
    
2. Wählen Sie im **Startmenü** die Skype for Business Server Systemsteuerung aus, oder öffnen Sie ein Browserfenster, und geben Sie dann die Admin-URL ein. .
    
3. Klicken Sie in der linken Navigationsleiste auf **Beständiger Chat** und dann auf **Kategorie**.
    
    Wählen Sie für mehrere Bereitstellungen des Servers für beständigen Chat in der Dropdownliste den entsprechenden Pool aus.
    
4. Klicken Sie auf der Seite **Kategorie** auf **Neu** oder **Bearbeiten**.
    
5. Wählen Sie in **"Dienst auswählen"** den Dienst aus, der dem Serverpool für beständigen Chat entspricht, in dem die Kategorie erstellt werden muss. Der Dienst ist der Serverpool für beständigen Chat, den der Beständige Chat (Client) verwendet, um zu identifizieren, zu welchem Pool die Kategorie gehört. Eine Kategorie kann nur zu einem Serverpool für beständigen Chat gehören und kann nicht in einen anderen Pool verschoben oder für einen anderen Pool freigegeben werden.
    
6. Führen Sie unter **Neue Kategorie** die folgenden Schritte aus:
    
7. Geben Sie unter **Name** einen Namen für die neue Chatroomkategorie an.
    
8. Geben Sie unter **Beschreibung** eine ausführliche Beschreibung der Chatroomkategorie an (z. B. eine Chatroomkategorie für Contoso).
    
9. Um zu steuern, ob Einladungen für Chatrooms aktiviert werden können, die zu dieser Kategorie gehören, aktivieren oder deaktivieren Sie das Kontrollkästchen **Einladungen aktivieren.** Wenn diese Option ausgewählt ist, können Für Räume in dieser Kategorie Einladungen aktiviert oder deaktiviert werden. wenn dies deaktiviert ist, dürfen die Räume in dieser Kategorie keine Einladungen haben. Wenn ein Raum Einladungen eingeht und ein neues Mitglied zu einem Raum hinzugefügt wird, erhält er eine Benachrichtigung über den neuen Chatroom in ihrem Client für beständigen Chat.
    
10. Um Dateiuploads in Chatrooms dieser Kategorie zu steuern, aktivieren bzw. deaktivieren Sie das Kontrollkästchen **Dateiupload aktivieren**. Ist diese Option aktiviert, können für die Chatrooms dieser Kategorie Dateiuploads aktiviert und deaktiviert werden. Ist die Option deaktiviert, sind Dateiuploads für die Chatrooms dieser Kategorie nicht zulässig.
    
11. Aktivieren oder deaktivieren Sie das Kontrollkästchen **Chatverlauf aktivieren** oder deaktivieren, um den Chatverlauf zu steuern. Wenn diese Option ausgewählt ist, werden Chatrooms beständig. andernfalls werden Chatnachrichten nicht beibehalten. Wenn die Kompatibilität aktiviert ist, werden Chatrooms in Der Compliance gespeichert, aber die Benutzer können nicht auf ältere Nachrichten zugreifen. Diese Option kann für Chatrooms verwendet werden, die für Ad-hoc-Zusammenarbeiten in Echtzeit vorgesehen sind, für die kein Chatverlauf beibehalten werden muss.
    
12. Führen Sie unter **Kategorie bearbeiten** die folgenden Schritte aus:
    
    - Fügen Sie in **"Mitgliedschaft"** im Abschnitt **"Zugelassene Mitglieder"** Benutzer und andere Active Directory Domain Services-Prinzipale (Benutzer, Verteilergruppen, Organisationseinheiten usw.) hinzu, die als Mitglieder von Chatrooms der Kategorie hinzugefügt werden dürfen. Prinzipale, die in einer Kategorie zugelassen sind, können nach den Räumen in der Kategorie suchen (es sei denn, der Raum ist ausgeblendet, in diesem Fall können nur Mitglieder des Raums im Verzeichnis danach suchen).
    
    - Fügen Sie in **"Mitgliedschaft"** im Abschnitt **"Abgelehnte Mitglieder"** Benutzer und andere Active Directory-Prinzipale hinzu, die Mitgliedern zugeordnet sind, denen aus dem Raum verweigert wird, oder entfernen Sie sie.
    
    - Fügen Sie in **"Mitgliedschaft"** im Abschnitt **"Ersteller"** Benutzer und andere Active Directory-Prinzipale hinzu, die den Erstellern für die Kategorie zugeordnet sind, oder entfernen Sie sie. Ein Ersteller ist ein Benutzer, der Berechtigungen zum Erstellen von Chatrooms und zum Zuweisen von Chatroom-Managern und -mitgliedern besitzt.
    
13. Klicken Sie auf **Commit ausführen**.
    
## <a name="see-also"></a>Siehe auch

Ausführliche Informationen zu den Features und Funktionen des Servers für beständigen Chat finden Sie unter [Plan for Persistent Chat Server in Skype for Business Server 2015,](../../plan-your-deployment/persistent-chat-server/persistent-chat-server.md)Deploy Persistent Chat Server in Skype for Business Server [2015,](../../deploy/deploy-persistent-chat-server/deploy-persistent-chat-server.md)and [Manage Persistent Chat Server in Skype for Business Server 2015.](../../manage/persistent-chat/persistent-chat.md)
  

