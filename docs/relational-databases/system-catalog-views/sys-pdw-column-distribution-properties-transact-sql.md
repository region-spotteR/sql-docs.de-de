---
description: sys.pdw_column_distribution_properties (Transact-SQL)
title: sys.pdw_column_distribution_properties (Transact-SQL)
ms.custom: seo-dt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 46b74f99-2e22-4dbd-872a-533fce0e239c
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 83bdcf74beb32e7fd5425ca56dcdd79c7c0d3d6c
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92035779"
---
# <a name="syspdw_column_distribution_properties-transact-sql"></a>sys.pdw_column_distribution_properties (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Enthält Verteilungs Informationen für Spalten.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**int**|ID des Objekts, zu dem die Spalte gehört.||  
|**column_id**|**int**|ID der Spalte.||  
|**distribution_ordinal**|**tinyint**|Ordinalzahl (1-basiert) innerhalb des Satzes der Verteilung.|0 = keine Verteilungs Spalte. 1 = [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] verwendet diese Spalte, um die übergeordnete Tabelle zu verteilen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten von Azure Synapse Analytics und Parallel Data Warehouse Catalog](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
