---
title: Kopieren von Datenbanken auf andere Server | Microsoft-Dokumentation
description: Erfahren Sie, wie eine SQL Server-Datenbank von einem Computer auf einen anderen kopiert wird, um zu testen, sie für den Betrieb von Zweigstellen verfügbar zu machen oder aus anderen Gründen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- servers [SQL Server], copying databases between
- bulk exporting [SQL Server], between servers
- database copying [SQL Server]
- migrating databases [SQL Server]
- moving databases
- copying databases
- bulk importing [SQL Server], between servers
ms.assetid: 978406d6-a3c8-4902-b1f4-4ced75234be5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 55560b212f692b19513d211a69f38efb80b75883
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92194394"
---
# <a name="copy-databases-to-other-servers"></a>Kopieren von Datenbanken auf andere Server
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Es ist manchmal hilfreich, eine Datenbank von einem Computer zum anderen zu kopieren, z. B. für Tests, das Überprüfen von Konsistenz, das Entwickeln von Software, das Ausführen von Berichten, das Erstellen einer Spiegeldatenbank oder eventuell zum Verfügbarmachen der Datenbank für externe Niederlassungen.  
  
 Es gibt mehrere Möglichkeiten, eine Datenbank zu kopieren:  
  
-   Verwenden des Assistenten zum Kopieren von Datenbanken  
  
     Sie können den Assistenten zum Kopieren von Datenbanken verwenden, um Datenbanken zwischen Servern zu kopieren oder zu verschieben oder um eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank auf eine höhere Version zu aktualisieren. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
-   Wiederherstellen einer Datenbanksicherung  
  
     Mit den [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen BACKUP und RESTORE können Sie eine ganze Datenbank kopieren. Typischerweise wird das Wiederherstellen einer vollständigen Datenbanksicherung aus vielen Gründen zum Kopieren einer Datenbank von einem Computer auf einen anderen verwendet. Weitere Informationen zum Sichern und Wiederherstellen zum Zweck des Kopierens einer Datenbank finden Sie unter [Kopieren von Datenbanken durch Sichern und Wiederherstellen](../../relational-databases/databases/copy-databases-with-backup-and-restore.md).  
  
    > [!NOTE]  
    >  Zum Einrichten einer Spiegeldatenbank für die Datenbankspiegelung müssen Sie die Datenbank mithilfe von RESTORE DATABASE *<Datenbankname>* WITH NORECOVERY auf dem Spiegelserver wiederherstellen. Weitere Informationen finden Sie unter [Vorbereiten einer Spiegeldatenbank auf die Spiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)verwendet.  
  
-   Verwenden des Assistenten zum Generieren von Skripts, um Datenbanken zu veröffentlichen  
  
     Sie können mit dem Assistenten zum Generieren von Skripts eine Datenbank von einem lokalen Computer auf einen Webhostinganbieter übertragen. Weitere Informationen finden Sie unter [Assistent zum Generieren und Veröffentlichen von Skripts](../../ssms/scripting/generate-and-publish-scripts-wizard.md).  
  
