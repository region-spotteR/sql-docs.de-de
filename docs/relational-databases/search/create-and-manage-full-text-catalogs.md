---
title: Erstellen und Verwalten von Volltextkatalogen
description: Erstellen und Verwalten von Volltextkatalogen
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql13.swb.fulltextsearch.ftcatalog.general.f1
- sql13.swb.fulltextsearch.fulltextindexproperties.general.f1
helpviewer_keywords:
- full-text catalogs [SQL Server], creating
- full-text search [SQL Server], using SQL Server Management Studio
ms.assetid: 824b7131-44a6-4815-89e6-62b7bab060e3
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a431635fdca556023a5e598502919bfdc9e40db6
ms.sourcegitcommit: 894c1a23e922dc29b82c1d2c34c7b0ff28b38654
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93067345"
---
# <a name="create-and-manage-full-text-catalogs"></a>Erstellen und Verwalten von Volltextkatalogen

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
Ein Volltextkatalog ist ein logischer Container für eine Gruppe von Volltextindizes. Sie müssen einen Volltextkatalog erstellen, bevor Sie einen Volltextindex erstellen können.

Ein Volltextkatalog ist ein virtuelles Objekt und gehört keiner Dateigruppe an.
  
##  <a name="create-a-full-text-catalog"></a><a name="creating"></a> Erstellen eines Volltextkatalogs  

### <a name="create-a-full-text-catalog-with-transact-sql"></a>Erstellen eines Volltextkatalogs mit Transact-SQL
Verwenden Sie [CREATE FULLTEXT CATALOG](../../t-sql/statements/create-fulltext-catalog-transact-sql.md). Beispiel:

```sql 
USE AdventureWorks;  
GO  
CREATE FULLTEXT CATALOG ftCatalog AS DEFAULT;  
GO  
``` 

### <a name="create-a-full-text-catalog-with-management-studio"></a>Erstellen eines Volltextkatalogs mit Management Studio
1.  Erweitern Sie im Objekt-Explorer den Server, erweitern Sie **Datenbanken** , und erweitern Sie die Datenbank, in der der Volltextkatalog erstellt werden soll.  
  
2.  Erweitern Sie **Speicher** , und klicken Sie dann mit der rechten Maustaste auf **Volltextkataloge**.  
  
3.  Wählen Sie **Neuer Volltextkatalog** aus.  
  
4.  Geben Sie im Dialogfeld **Neuer Volltextkatalog** die Informationen für den erneut zu erstellenden Volltextkatalog an. Weitere Informationen finden Sie unter [Neuer Volltextkatalog &#40;Seite „Allgemein“&#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md).  
  
    > [!NOTE]  
    >  Volltextkatalog-IDs beginnen bei 00005 und werden mit jedem neu erstellten Katalog um eins erhöht.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

##  <a name="get-the-properties-of-a-full-text-catalog"></a><a name="props"></a> Abrufen der Eigenschaften eines Volltextkatalogs  
Verwenden Sie die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Funktion **FULLTEXTCATALOGPROPERTY** , um den Wert verschiedener Eigenschaften des Volltextkatalogs abzurufen. Weitere Informationen finden Sie unter [FULLTEXTCATALOGPROPERTY](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md).

Führen Sie z.B. die folgende Abfrage zum Abrufen der Anzahl der Indizes im Volltextkatalog `Catalog1` aus.

```sql 
USE <database>;  
GO  
SELECT fulltextcatalogproperty('Catalog1', 'ItemCount');  
GO  
```  
  
In der folgenden Tabelle sind die Eigenschaften aufgeführt, die sich auf Volltextkataloge beziehen. Diese Informationen sind für die Verwaltung und Problembehandlung der Volltextsuche möglicherweise hilfreich. 
  
|Eigenschaft|BESCHREIBUNG|  
|--------------|-----------------|  
|**AccentSensitivity**|Einstellung für die Unterscheidung nach Akzent.|
|**ImportStatus**|Gibt an, ob der Volltextkatalog importiert wird.|  
|**IndexSize**|Größe des Volltextkatalogs in Megabytes (MB).| 
|**ItemCount**|Aktuelle Anzahl der volltextindizierten Objekte im Volltextkatalog.|  
|**MergeStatus**|Gibt an, ob eine Masterzusammenführung ausgeführt wird.| 
|**PopulateCompletionAge**|Anzahl von Sekunden, die zwischen dem 01.01.1990, 00:00:00 Uhr, und der Beendigung des letzten Auffüllens des Volltextindex verstrichen sind.| 
|**PopulateStatus**|Gibt den Auffüllungsstatus an.<br /><br /> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|  
|**UniqueKeyCount**|Anzahl der eindeutigen Schlüssel im Volltextkatalog.| 

##  <a name="rebuild-a-full-text-catalog"></a><a name="rebuildone"></a> Erneutes Erstellen eines Volltextkatalogs  

Führen Sie die Transact-SQL-Anweisung [ALTER FULLTEXT CATALOG... REBUILD](
../../t-sql/statements/alter-fulltext-catalog-transact-sql.md) aus, oder führen Sie folgende Schritte in SQL Server Management Studio (SSMS) aus.

1.  Erweitern Sie in SSMS im Objekt-Explorer den Server, erweitern Sie **Datenbanken** , und erweitern Sie die Datenbank, die den erneut zu erstellenden Volltextkatalog enthält.  
  
2.  Erweitern Sie **Speicher** und dann **Volltextkataloge**.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Namen des erneut zu erstellenden Volltextkatalogs, und wählen Sie **Neu erstellen** aus.  
  
4.  Klicken Sie auf die Frage **Möchten Sie den Volltextkatalog löschen und neu erstellen?** auf **OK**.  
  
5.  Klicken Sie im Dialogfeld **Volltextkatalog neu erstellen** auf **Schließen**.  
   
##  <a name="rebuild-all-full-text-catalogs-for-a-database"></a><a name="rebuildall"></a> Erneutes Erstellen aller Volltextkataloge für eine Datenbank  

1.  Erweitern Sie in SSMS im Objekt-Explorer den Server, erweitern Sie **Datenbanken** , und erweitern Sie die Datenbank, die die erneut zu erstellenden Volltextkataloge enthält.  
  
2.  Erweitern Sie **Speicher** , und klicken Sie dann mit der rechten Maustaste auf **Volltextkataloge**.  
  
3.  Wählen Sie **Alle neu erstellen** aus.  
  
4.  Klicken Sie bei der Frage **Möchten Sie alle Volltextkataloge löschen und neu erstellen?** auf die Option **OK**.  
  
5.  Klicken Sie im Dialogfeld **Alle Volltextkataloge neu erstellen** auf **Schließen**.  
  
  
  
##  <a name="remove-a-full-text-catalog-from-a-database"></a><a name="removing"></a> Entfernen eines Volltextkatalogs aus einer Datenbank  

Führen Sie die Transact-SQL-Anweisung [DROP FULLTEXT CATALOG](
../../t-sql/statements/drop-fulltext-catalog-transact-sql.md) aus, oder führen Sie die folgenden Schritte in SQL Server Management Studio (SSMS) aus.

1.  Erweitern Sie in SSMS im Objekt-Explorer den Server, erweitern Sie **Datenbanken** , und erweitern Sie die Datenbank, die den zu entfernenden Volltextkatalog enthält.  
  
2.  Erweitern Sie **Speicher** und dann **Volltextkataloge**.  
  
3.  Klicken Sie mit der rechten Maustaste auf den zu entfernenden Katalog, und wählen Sie dann **Löschen** aus.  
  
4.  Klicken Sie im Dialogfeld **Objekte löschen** auf **OK**.  

## <a name="next-step"></a>Nächster Schritt
[Erstellen und Verwalten von Volltextindizes](../../relational-databases/search/create-and-manage-full-text-indexes.md)