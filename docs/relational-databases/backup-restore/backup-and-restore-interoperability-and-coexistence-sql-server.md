---
title: 'Sichern und Wiederherstellen: Interoperabilität von Features'
description: In diesem Artikel werden die Sicherungs- und Wiederherstellungsfeatures in SQL Server beschrieben, einschließlich des Datenbankstarts, der Onlinewiederherstellung und deaktivierter Indizes sowie der Datenbankspiegelung.
ms.custom: seo-lt-2019
ms.date: 12/17/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- file restores [SQL Server], related features
- restoring [SQL Server], files
- restoring files [SQL Server], related features
- backups [SQL Server], files or filegroups
- file backups [SQL Server], related features
ms.assetid: 69f212b8-edcd-4c5d-8a8a-679ced33c128
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3dcf1473fc92ba69d68f9aae9d871540e2604b52
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85737824"
---
# <a name="backup-and-restore-interoperability-and-coexistence-sql-server"></a>Sichern und Wiederherstellen: Interoperabilität und Koexistenz (SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  In diesem Thema werden Überlegungen im Zusammenhang mit der Sicherung und Wiederherstellung für mehrere Funktionen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]beschrieben. Diese Funktionen sind: Dateiwiederherstellung und Datenbankstart, Onlinewiederherstellung und deaktivierte Indizes, Datenbankspiegelung sowie schrittweise Wiederherstellung und Volltextindizes.  
  
 **In diesem Thema:**  
  
-   [Dateiwiederherstellung und Starten einer Datenbank](#FileRestoreAndDbStartup)  
  
-   [Onlinewiederherstellung und deaktivierte Indizes](#OnlineRestoreAndDisabledIndexes)  
  
-   [Datenbankspiegelung und Sicherung/Wiederherstellung](#DbMandBnR)  
  
-   [Schrittweise Wiederherstellung und Volltextindizes](#PiecemealAndFTIndexes)  
  
-   [Dateisicherung und -wiederherstellung und die Komprimierung](#FileBnRandCompression)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
##  <a name="file-restore-and-database-startup"></a><a name="FileRestoreAndDbStartup"></a> Dateiwiederherstellung und Starten einer Datenbank  
 Dieser Abschnitt betrifft nur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken mit mehreren Dateigruppen.  
  
> [!NOTE]  
>  Wenn eine Datenbank gestartet wird, werden nur Dateigruppen, deren Dateien online waren, als die Datenbank geschlossen wurde, wiederhergestellt und online geschaltet.  
  
 Falls beim Starten der Datenbank ein Problem auftritt, wird bei der Wiederherstellung ein Fehler gemeldet, und die Datenbank wird als SUSPECT gekennzeichnet. Wenn das Problem auf eine Datei oder mehrere Dateien isoliert werden kann, kann der Datenbankadministrator die Dateien offline schalten und versuchen, die Datenbank erneut zu starten. Sie können die folgende [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) -Anweisung verwenden, um eine Datei offline zu schalten:  
  
 ALTER DATABASE *Datenbankname* MODIFY FILE (NAME **='***Dateiname***'** , OFFLINE)  
  
 Wenn der Start erfolgreich ist, bleibt jede Dateigruppe, die eine Offlinedatei enthält, offline.  
  
##  <a name="online-restore-and-disabled-indexes"></a><a name="OnlineRestoreAndDisabledIndexes"></a> Onlinewiederherstellung und deaktivierte Indizes  
 Dieses Abschnitt betrifft nur Datenbanken mit mehreren Dateigruppen und für das einfache Wiederherstellungsmodell Datenbanken mit mindestens einer schreibgeschützten Dateigruppe.  
  
 Wenn die Datenbank online ist, kann der Index in diesen Fällen nur erstellt, gelöscht, aktiviert oder deaktiviert werden, wenn alle Dateigruppen, die einen beliebigen Teil des Indexes enthalten, online sind.  
  
 Informationen zum Wiederherstellen von Offlinedateigruppen finden Sie unter [Onlinewiederherstellung &#40;SQL Server&#41;](../../relational-databases/backup-restore/online-restore-sql-server.md).  
  
##  <a name="database-mirroring-and-backup-and-restore"></a><a name="DbMandBnR"></a> Datenbankspiegelung und Sicherung/Wiederherstellung  
 Dieser Abschnitt betrifft nur Datenbanken mit mehreren Dateigruppen, für die das vollständige Wiederherstellungsmodell verwendet wird.  
  
> [!NOTE]  
>  Die Datenbankspiegelungsfunktion wird in zukünftigen Versionen von Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]nicht mehr bereitgestellt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].  
  
 Die Datenbankspiegelung ist eine Lösung zum Verbessern der Datenbankverfügbarkeit. Die Datenbankspiegelung wird auf Datenbankbasis implementiert und ist nur für Datenbanken mit dem vollständigen Wiederherstellungsmodell geeignet. Weitere Informationen finden Sie unter [Datenbankspiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
> [!NOTE]  
>  Verwenden Sie zum Verteilen von Kopien einer Teilmenge der Dateigruppen in einer Datenbank die Replikation: Replizieren Sie nur die Objekte in den Dateigruppen, die auf andere Server kopiert werden sollen. Weitere Informationen über Replikation finden Sie unter [SQL Server-Replikation](../../relational-databases/replication/sql-server-replication.md).  
  
### <a name="creating-the-mirror-database"></a>Erstellen der Spiegeldatenbank  
 Die Spiegeldatenbank wird durch Dateiwiederherstellung (ohne Datenbankwiederherstellung) von Sicherungen der Prinzipaldatenbank auf dem Spiegelserver erstellt. Bei der Wiederherstellung muss der Datenbankname beibehalten werden. Weitere Informationen finden Sie unter [Vorbereiten einer Spiegeldatenbank auf die Spiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)verwendet.  
  
 Sie können die Spiegeldatenbank mithilfe einer schrittweisen Wiederherstellungssequenz erstellen, insofern dies unterstützt wird. Sie können die Spiegelung jedoch erst starten, wenn Sie alle Dateigruppen und ggf. Protokollsicherungen wiederhergestellt haben, sodass die gespiegelte Datenbank zeitlich nicht zu weit von der Prinzipaldatenbank entfernt ist. Weitere Informationen finden Sie unter [Schrittweise Wiederherstellungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md).  
  
### <a name="restrictions-on-backup-and-restore-during-mirroring"></a>Einschränkungen bei der Sicherung und Wiederherstellung während der Spiegelung  
 Während eine Datenbank-Spiegelungssitzung aktiv ist, gelten die folgenden Einschränkungen:  
  
-   Das Sichern und Wiederherstellen der Spiegeldatenbank ist nicht zulässig.  
  
-   Das Sichern der Prinzipaldatenbank ist zulässig, BACKUP LOG WITH NORECOVERY ist jedoch nicht zulässig.  
  
-   Das Wiederherstellen der Prinzipaldatenbank ist nicht zulässig.  
  
##  <a name="piecemeal-restore-and-full-text-indexes"></a><a name="PiecemealAndFTIndexes"></a> Schrittweise Wiederherstellung und Volltextindizes  
 Dieser Abschnitt betrifft nur Datenbanken mit mehreren Dateigruppen und bei Datenbanken mit einfachem Modell nur schreibgeschützte Dateigruppen.  
  
 Volltextindizes werden in Datenbankdateigruppen gespeichert und können von einer schrittweisen Wiederherstellung betroffen sein. Wenn sich ein Volltextindex in derselben Dateigruppe befindet wie zugehörige Tabellendaten, wird die schrittweise Wiederherstellung ordnungsgemäß ausgeführt.  
  
> [!NOTE]  
>  Wählen Sie zum Anzeigen der Dateigruppen-ID der Dateigruppe, die einen Volltextindex enthält, die data_space_id-Spalte von [sys.fulltext_indexes](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)aus.  
  
### <a name="full-text-indexes-and-tables-in-separate-filegroups"></a>Volltextindizes und -tabellen in separaten Dateigruppen  
 Wenn sich ein Volltextindex in einer separaten Dateigruppe getrennt von allen zugehörigen Tabellendaten befindet, hängt das Verhalten der schrittweisen Wiederherstellung davon ab, welche Dateigruppe zuerst wiederhergestellt und online geschaltet wird:  
  
-   Wenn die Dateigruppe, in der der Volltextindex enthalten ist, vor den Dateigruppen mit den zugehörigen Tabellendaten wiederhergestellt und online geschaltet wird, wird die Volltextsuche ordnungsgemäß ausgeführt, sobald der Volltextindex online ist.  
  
-   Wenn die Dateigruppe, in der die Tabellendaten enthalten sind, vor der Dateigruppe mit dem Volltextindex wiederhergestellt und online geschaltet wird, kann das Volltextverhalten davon betroffen sein. Das liegt daran, dass [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen, die eine Auffüllung auslösen oder den Katalog neu erstellen oder neu organisieren, so lange fehlschlagen, bis der Index online geschaltet wird. Zu diesen Anweisungen zählen CREATE FULLTEXT INDEX, ALTER FULLTEXT INDEX, DROP FULLTEXT INDEX und ALTER FULLTEXT CATALOG.  
  
     In diesem Fall sind die folgenden Faktoren signifikant:  
  
    -   Wenn für den Volltextindex die Änderungsnachverfolgung aktiviert ist, schlagen die DML-Anweisungen des Benutzers so lange fehl, bis die Indexdateigruppe online geschaltet wird. Auch Löschvorgänge schlagen so lange fehl, bis die Indexdateigruppe online ist.  
  
    -   Unabhängig von der Änderungsnachverfolgung wird bei Volltextabfragen ein Fehler gemeldet, weil der Index nicht verfügbar ist. Wenn versucht wird, eine Volltextabfrage auszuführen, während die Dateigruppe mit dem Volltextindex offline ist, wird ein Fehler zurückgegeben.  
  
    -   Statusfunktionen (z. B. FULLTEXTCATALOGPROPERTY) werden nur dann erfolgreich ausgeführt, wenn sie nicht auf den Volltextindex zugreifen müssen. Beispielsweise ist der Zugriff auf Online-Volltextmetadaten möglich, für **uniquekeycount, itemcount** wird jedoch ein Fehler ausgelöst.  
  
     Nachdem die Volltextindex-Dateigruppe wiederhergestellt und online geschaltet wurde, sind die Index- und Tabellendaten konsistent.  
  
 Sobald sowohl die Tabellendateigruppe als auch die Volltextindex-Dateigruppe online sind, wird eine ggf. angehaltene Volltextauffüllung fortgesetzt.  
  
##  <a name="file-backup-and-restore-and-compression"></a><a name="FileBnRandCompression"></a> Dateisicherung und -wiederherstellung und die Komprimierung  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt die NTFS-Dateisystemkomprimierung schreibgeschützter Dateigruppen und Datenbanken.  
  
 Das Wiederherstellen von Dateien in einer schreibgeschützten Dateigruppe wird für komprimierte NTFS-Dateien unterstützt. Das Sichern und Wiederherstellen dieser Dateigruppen erfolgt im Prinzip wie bei jeder anderen schreibgeschützten Dateigruppe, jedoch mit folgenden Ausnahmen:  
  
-   Beim Wiederherstellen einer Datei mit Lese-/Schreibschutz (einschließlich der primären Dateien oder Protokolldateien einer Datenbank mit Lese-/Schreibschutz) in einem komprimierten Volume wird eine Fehlermeldung angezeigt.  
  
-   Das Wiederherstellen einer schreibgeschützten Datenbank in einem komprimierten Volume ist zulässig.  
  
> [!NOTE]  
>  Protokolldateien von Datenbanken mit Lese-/Schreibzugriff sollten unter keinen Umständen in komprimierten Dateisystemen gespeichert werden.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Vorbereiten einer Spiegeldatenbank auf die Spiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
-   [Sichern und Wiederherstellen von Volltextkatalogen und Indizes](../../relational-databases/search/back-up-and-restore-full-text-catalogs-and-indexes.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern und Wiederherstellen von SQL Server-Datenbanken](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Sichern und Wiederherstellen von replizierten Datenbanken](../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)   
[Aktive sekundäre Replikate: Sicherung auf sekundären Replikaten \(Always On-Verfügbarkeitsgruppen\)](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)  
  
  
