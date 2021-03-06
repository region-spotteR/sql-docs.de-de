---
description: IHpublisherindexes (Transact-SQL)
title: IHpublisherindexes (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublisherindexes
- IHpublisherindexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublisherindexes system table
ms.assetid: 6008ef89-eeb9-46dc-93a2-f7623298cf0f
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5b7e4d37acf72277f88290372a1a7c29b7343473
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89540937"
---
# <a name="ihpublisherindexes-transact-sql"></a>IHpublisherindexes (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **IHpublisherindexes** -Systemtabelle enthält eine Zeile für jeden Index, der von nicht-SQL Server-Verlegern mithilfe des aktuellen Verteilers repliziert wurde. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**publisherindex_id**|**int**|Identifiziert einen veröffentlichten Index.|  
|**table_id**|**int**|Identifiziert die Tabelle aus [IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md) , zu der der Index gehört.|  
|**publisher_id**|**smallint**|Identifiziert den Nicht-SQL Server-Verleger, aus dem der Index veröffentlicht wird.|  
|**name**|**sysname**|Der Name des veröffentlichten Indexes.|  
|**type**|**nvarchar(255)**|Ein unterstützter [Indextyp aus der IHindextypes](../../relational-databases/system-tables/ihindextypes-transact-sql.md) -Systemtabelle.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Heterogene Datenbankreplikation](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
