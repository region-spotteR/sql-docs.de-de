---
title: Nicht verteilte Befehle (Replikationsmonitor)
description: Beschreibt die Registerkarte „Nicht verteilte Befehle“ des Replikationsmonitors in SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.subscription.performance.f1
ms.assetid: 5451561e-0ce3-4bb5-844a-88cd15b0b371
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: babf92b1effdad49100f7e7dcbde2aa2a45fc23d
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "87112009"
---
# <a name="subscription-undistributed-commands-transactional-subscription"></a>Abonnement, Nicht verteilte Befehle (Transaktionsabonnement)
[!INCLUDE[sql-asdb](../../includes/applies-to-version/sql-asdb.md)]
  Mithilfe der Registerkarte **Nicht verteilte Befehle** können Sie Informationen zur Anzahl der Befehle in der Verteilungsdatenbank anzeigen, die nicht an den ausgewählten Abonnenten übermittelt wurden, sowie die geschätzte Zeit zur Übermittlung dieser Befehle. Weitere Informationen zum Anzeigen der Befehle in der Verteilungsdatenbank finden Sie unter [sp_replshowcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md).  

[!INCLUDE[azure-sql-db-replication-supportability-note](../../includes/azure-sql-db-replication-supportability-note.md)]
  
## <a name="options"></a>Tastatur  
 **Anzahl von Befehlen in der Verteilungsdatenbank, die darauf warten, auf diesen Abonnenten angewendet zu werden**  
 Die Anzahl von Befehlen in der Verteilungsdatenbank, die nicht an den ausgewählten Abonnenten übermittelt wurden. Ein Befehl besteht aus einer Transact-SQL-DML-Anweisung (Data Manipulation Language, Datenbearbeitungssprache) oder einer DDL-Anweisung (Data Definition Language, Datendefinitionssprache).  
  
 **Geschätzte Zeit, um diese Befehle anzuwenden, basierend auf der früheren Leistung**  
 Die geschätzte Zeitdauer für die Übermittlung von Befehlen an den Abonnenten. Wenn dieser Wert größer ist, als die zum Generieren und Anwenden einer Momentaufnahme auf den Abonnenten erforderliche Zeit, sollten Sie eine erneute Initialisierung des Abonnenten in Betracht ziehen. Weitere Informationen finden Sie unter [Erneutes Initialisieren von Abonnements](../../relational-databases/replication/reinitialize-subscriptions.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten des Replikationsmonitors](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Überwachen der Leistung mit dem Replikationsmonitor](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)   
 [Überwachen der Replikation](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
