---
description: SQLNativeSql
title: SQLNativeSql | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLNativeSql function
ms.assetid: 2d999fec-9e22-4514-ad5f-22a64b82f95b
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ed1b57f1c90659f9f9d09afee52ddef28514fca2
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2020
ms.locfileid: "91810954"
---
# <a name="sqlnativesql"></a>SQLNativeSql
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber erfüllt **SQLNativeSql** -Anforderungen, ohne auf den Server zuzugreifen. Die Funktion testet die Syntax von SQL-Anweisungen effizient. Durch die Syntaxüberprüfung wird nicht bestimmt, ob Bezeichner oder die Ergebnisse von Ausdrücken in den SQL-Anweisungen gültig sind, und systemeigene [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL-Anweisungen, die von **SQLNativeSql** zurückgegeben werden, können möglicherweise nicht ausgeführt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLNativeSql-Funktion](../../odbc/reference/syntax/sqlnativesql-function.md)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
