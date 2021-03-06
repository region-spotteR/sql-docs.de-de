---
description: SET ROWCOUNT (Transact-SQL)
title: SET ROWCOUNT (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET_ROWCOUNT_TSQL
- ROWCOUNT_TSQL
- SET ROWCOUNT
- ROWCOUNT
dev_langs:
- TSQL
helpviewer_keywords:
- row return limitations [SQL Server]
- SET ROWCOUNT statement
- number of rows affected by statement
- ROWCOUNT option
- counting rows
- stopping queries
- limiting rows returned
- queries [SQL Server], stopping
ms.assetid: c6966fb7-6421-47ef-98f3-82351f2f6bdc
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e5c692f62e047d27277536241a41e4d9f0d03ea7
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89540539"
---
# <a name="set-rowcount-transact-sql"></a>SET ROWCOUNT (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Bewirkt, dass die Verarbeitung der Abfrage durch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beendet wird, sobald die angegebene Anzahl von Zeilen zurückgegeben wurde.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
SET ROWCOUNT { number | @number_var }   
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *number* | @*number_var*  
 Die Zahl (eine ganze Zahl), die festlegt, wie viele Zeilen verarbeitet werden sollen, bevor die angegebene Abfrage beendet wird.  
  
## <a name="remarks"></a>Bemerkungen  
  
> [!IMPORTANT]  
>  Die Verwendung von SET ROWCOUNT wird in einer zukünftigen Version von SQL Server keine Auswirkungen auf die Anweisungen DELETE, INSERT und UPDATE haben. Vermeiden Sie beim Entwickeln neuer Anwendungen das Verwenden von SET ROWCOUNT zusammen mit DELETE-, INSERT- und UPDATE-Anweisungen, und planen Sie die Änderung von Anwendungen, in denen dies zurzeit verwendet wird. Die Verwendung der TOP-Syntax ergibt ein ähnliches Verhalten. Weitere Informationen finden Sie unter [TOP &#40;Transact-SQL&#41;](../../t-sql/queries/top-transact-sql.md).  
  
 Um diese Option zu deaktivieren (sodass alle Zeilen zurückgegeben werden), geben Sie SET ROWCOUNT 0 an.  
  
 Das Festlegen der Option ROWCOUNT veranlasst, dass die meisten [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen die Verarbeitung beenden, wenn die angegebene Anzahl von Zeilen bearbeitet wurde. Dies gilt auch für Trigger. Die Option ROWCOUNT wirkt sich nicht auf dynamische Cursor aus, begrenzt jedoch das Rowset von Keyset- und INSENSITIVE-Cursorn. Diese Option sollte mit Vorsicht eingesetzt werden.  
  
 SET ROWCOUNT überschreibt das TOP-Schlüsselwort der SELECT-Anweisung, wenn die Zeilenanzahl der kleinere Wert ist.  
  
 Die Einstellung von SET ROWCOUNT wird zur Laufzeit und nicht zur Analysezeit festgelegt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der public-Rolle.  
  
## <a name="examples"></a>Beispiele  
 SET ROWCOUNT beendet die Verarbeitung nach der angegebenen Anzahl von Zeilen. Beachten Sie im folgenden Beispiel, dass über 500 Zeilen mit dem Kriterium `Quantity` kleiner als `300` übereinstimmen. Wenn SET ROWCOUNT angewendet wurde, werden jedoch nicht alle Zeilen zurückgegeben.  
  
```sql
USE AdventureWorks2012;  
GO  
SELECT count(*) AS Count  
FROM Production.ProductInventory  
WHERE Quantity < 300;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Count 
 ----------- 
 537 
 
 (1 row(s) affected)
 ```  
  
 Legen Sie jetzt `ROWCOUNT` auf `4` fest, und geben Sie alle Zeilen zurück, um zu zeigen, dass nur 4 Zeilen zurückgegeben werden.  
  
```sql
SET ROWCOUNT 4;  
SELECT *  
FROM Production.ProductInventory  
WHERE Quantity < 300;  
GO  
  
-- (4 row(s) affected)
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 SET ROWCOUNT beendet die Verarbeitung nach der angegebenen Anzahl von Zeilen. Beachten Sie im folgenden Beispiel, dass mehr als 20 Zeilen mit dem Kriterium `AccountType = 'Assets'` übereinstimmen. Wenn SET ROWCOUNT angewendet wurde, werden jedoch nicht alle Zeilen zurückgegeben.  
  
```sql
-- Uses AdventureWorks  
  
SET ROWCOUNT 5;  
SELECT * FROM [dbo].[DimAccount]  
WHERE AccountType = 'Assets';  
```  
  
 Legen Sie ROWCOUNT auf 0 fest, um alle Zeilen zurückzugeben.  
  
```sql
-- Uses AdventureWorks  
  
SET ROWCOUNT 0;  
SELECT * FROM [dbo].[DimAccount]  
WHERE AccountType = 'Assets';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [SET-Anweisungen &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

