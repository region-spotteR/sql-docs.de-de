---
description: JSON-Pfadausdrücke (SQL Server)
title: JSON-Pfadausdrücke
ms.date: 06/03/2020
ms.prod: sql
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- JSON, path expressions
- path expressions (JSON)
ms.assetid: 25ea679c-84cc-4977-867c-2cbe9d192553
author: jovanpop-msft
ms.author: jovanpop
ms.reviewer: jroth
ms.custom: seo-dt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8be99986e6ca9ded5bb28e53b5c3ae166e8b86b3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490944"
---
# <a name="json-path-expressions-sql-server"></a>JSON-Pfadausdrücke (SQL Server)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

 Verwenden Sie JSON-Pfadausdrücke, um auf die Eigenschaften der JSON-Objekte zu verweisen.  
  
 Sie müssen einen Pfadausdruck angeben, wenn Sie die folgenden Funktionen aufrufen.  
  
-   Wenn Sie **OPENJSON** aufrufen, um eine relationale Sicht der JSON-Daten zu erstellen. Weitere Informationen finden Sie unter [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md).  
  
-   Wenn Sie **JSON_VALUE** aufrufen, um einen Wert aus JSON-Text zu extrahieren. Weitere Informationen finden Sie unter [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md).  
  
-   Wenn Sie **JSON_QUERY** aufrufen, um ein JSON-Objekt oder ein -Array zu extrahieren. Weitere Informationen finden Sie unter [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md).  
  
-   Wenn Sie **JSON_MODIFY** aufrufen, um den Werte einer Eigenschaft in einer JSON-Zeichenfolge zu aktualisieren. Weitere Informationen finden Sie unter [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md).  

## <a name="parts-of-a-path-expression"></a>Teile eines Pfadausdrucks
 Ein Pfadausdruck hat zwei Komponenten.  
  
1.  Der optionale [PATH-Modus](#PATHMODE) mit einem Wert von **lax** oder **strict**.  
  
2.  Der [Pfad](#PATH) selbst.  

##  <a name="path-mode"></a><a name="PATHMODE"></a> Path mode  
 Am Anfang des Pfadausdrucks können Sie optional den „path mode“ deklarieren, indem Sie das Schlüsselwort **lax** oder **strict**angeben. Der Standardwert ist **lax**.  
  
-   Im Modus **lax** gibt die Funktion leere Werte zurück, falls der Pfadausdruck einen Fehler enthält. Falls Sie beispielsweise den Wert **$.name** anfordern und der JSON-Text keinen **name**-Schlüssel enthält, gibt die Funktion NULL zurück, löst jedoch keinen Fehler aus.  
  
-   Im Modus **strict** löst die Funktion einen Fehler aus, wenn der Pfadausdruck einen Fehler enthält.  

Die folgende Abfrage gibt explizit den Modus `lax` im Pfadausdruck an.

```sql  
DECLARE @json NVARCHAR(MAX);
SET @json=N'{ ... }';

SELECT * FROM OPENJSON(@json, N'lax $.info');
```  
  
##  <a name="path"></a><a name="PATH"></a> Path  
 Nach der optionalen Deklaration des „path mode“ geben Sie den Pfad selbst an.  
  
-   Das Dollarzeichen (`$`) stellt das Kontextelement dar.  
  
-   Der Eigenschaftspfad ist ein Satz an Pfadschritten. Pfadschritte können die folgenden Elemente und Operatoren enthalten.  
  
    -   Schlüsselnamen. Beispiel: `$.name` und `$."first name"`. Umschließen Sie den Namen des Schlüssels mit Anführungszeichen, falls er mit einem Dollarzeichen beginnt, oder Sonderzeichen wie z.B. Leerzeichen enthält.   
  
    -   Array-Elemente. Beispiel: `$.product[3]`. Arrays sind nullbasiert.  
  
    -   Der Punktoperator (`.`) zeigt einen Objektmember an. Beispielsweise ist `surname` in `$.people[1].surname` ein untergeordnetes Element von `people`.
  
## <a name="examples"></a>Beispiele  
 Die Beispiele in diesem Abschnitt verweisen auf den folgenden JSON-Text.  
  
```json  
{
    "people": [{
        "name": "John",
        "surname": "Doe"
    }, {
        "name": "Jane",
        "surname": null,
        "active": true
    }]
}
```  
  
 Die folgende Tabelle zeigt einige Beispiele für Pfadausdrücke.  
  
|Pfadausdruck|Wert|  
|---------------------|-----------|  
|$.people[0].name|John|  
|$.people[1]|{ "name": "Jane", "surname": null, "active": true }|  
|$.people[1].surname|NULL|  
|$|{ „people“: [ { „name“: „John“,  „surname“: „Doe“ },<br />   { „name“: „Jane“,  „surname“: null, „active“: true } ] }|  
  
## <a name="how-built-in-functions-handle-duplicate-paths"></a>Wie integrierte Funktionen doppelte Pfade behandeln  
 Falls der JSON-Text doppelte Eigenschaften enthält – beispielsweise zwei Schlüssel mit dem gleichen Namen auf der gleichen Stufe –, geben die Funktionen **JSON_VALUE** und **JSON_QUERY** nur den ersten Wert zurück, der dem Pfad entspricht. Verwenden Sie **OPENJSON**, wie im folgenden Beispiel gezeigt, um ein JSON-Objekt zu analysieren, das doppelte Schlüssel enthält, und um alle Werte zurückzugeben.  
  
```sql  
DECLARE @json NVARCHAR(MAX);
SET @json=N'{"person":{"info":{"name":"John", "name":"Jack"}}}';

SELECT value
  FROM OPENJSON(@json,'$.person.info');
```  

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Weitere Informationen zu JSON in SQL Server und Azure SQL-Datenbank  
  
### <a name="microsoft-videos"></a>Microsoft-Videos

Eine visuelle Einführung in die JSON-Unterstützung, die in SQL Server und Azure SQL-Datenbank integriert ist, finden Sie in den folgenden Videos:

-   [SQL Server 2016 and JSON Support](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support)

-   [Using JSON in SQL Server 2016 and Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database)

-   [JSON as a bridge between NoSQL and relational worlds](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds)
  
## <a name="see-also"></a>Weitere Informationen  
 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)   
 [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)   
 [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)  
  
  
