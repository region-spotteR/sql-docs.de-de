---
description: ODBC-Funktionen und der Visual FoxPro-ODBC-Treiber
title: ODBC-Funktionen und der Visual FoxPro-ODBC-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC level 2 API functions [ODBC]
- ODBC level 1 API functions [ODBC]
- functions [ODBC], API
- ODBC API functions [ODBC]
- level 1 API functions [ODBC]
- API functions [ODBC]
- core level API functions [ODBC]
- level 2 API functions [ODBC]
- ODBC core level API functions [ODBC]
ms.assetid: 512f9cee-ffad-439b-b612-b49c34c32658
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 017e66c137f6c0921f3a382c0832598c9415c9e6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340736"
---
# <a name="odbc-functions-and-the-visual-foxpro-odbc-driver"></a>ODBC-Funktionen und der Visual FoxPro-ODBC-Treiber
Die Themen in diesem Abschnitt bieten eine kurze Zusammenfassung der ODBC-API-Funktionen und aller Visual FoxPro-spezifischen Details.  
  
> [!NOTE]  
>  Allgemeine Informationen zu ODBC-Funktionen finden Sie in der [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md) im "ODBC-Programmier Handbuch".  
  
 Die ODBC-API-Funktionen wurden hier in drei Hauptkategorien unterteilt: API-Funktionen der kernstufe, API-Funktionen auf Ebene 1 und API-Funktionen der Ebene 2.  
  
> [!NOTE]  
>  Einige der Funktionen Verhalten sich unterschiedlich, je nachdem, ob die Datenquelle als Verbindung mit einem Verzeichnis mit [freien Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md) (DBF-Dateien) oder einer Visual FoxPro- [Datenbank](../../odbc/microsoft/visual-foxpro-terminology.md) (DBC-Datei) definiert ist. Bestimmte Vorgänge werden nur für Datenbankverbindungen unterstützt.  
  
## <a name="core-level-api-support"></a>API-Unterstützung auf Kernebene  
 Die API-Funktionen der ODBC-Kernebene sind in der folgenden Tabelle aufgeführt. Alle diese Funktionen werden vom Visual FoxPro-ODBC-Treiber unterstützt.  

:::row:::
    :::column:::
        [SQLAllocConnect](../../odbc/microsoft/sqlallocconnect-visual-foxpro-odbc-driver.md)  
        [SQLAllocEnv](../../odbc/microsoft/sqlallocenv-visual-foxpro-odbc-driver.md)  
        [SQLAllocStmt](../../odbc/microsoft/sqlallocstmt-visual-foxpro-odbc-driver.md)  
        [SQLBindCol](../../odbc/microsoft/sqlbindcol-visual-foxpro-odbc-driver.md)  
        [SQLCancel](../../odbc/microsoft/sqlcancel-visual-foxpro-odbc-driver.md)  
        [SQLColAttributes](../../odbc/microsoft/sqlcolattributes-visual-foxpro-odbc-driver.md)  
        [SQLConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md)  
        [SQLDescribeCol](../../odbc/microsoft/sqldescribecol-visual-foxpro-odbc-driver.md)  
        [SQLDisconnect](../../odbc/microsoft/sqldisconnect-visual-foxpro-odbc-driver.md)  
        [SQLError](../../odbc/microsoft/sqlerror-visual-foxpro-odbc-driver.md)  
        [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)  
    :::column-end:::
    :::column:::
        [SQLExecute](../../odbc/microsoft/sqlexecute-visual-foxpro-odbc-driver.md)  
        [SQLFetch](../../odbc/microsoft/sqlfetch-visual-foxpro-odbc-driver.md)  
        [SQLFreeConnect](../../odbc/microsoft/sqlfreeconnect-visual-foxpro-odbc-driver.md)  
        [SQLFreeEnv](../../odbc/microsoft/sqlfreeenv-visual-foxpro-odbc-driver.md)  
        ['SQLFreeStmt'](../../odbc/microsoft/sqlfreestmt-visual-foxpro-odbc-driver.md)  
        [SQLGetCursorName](../../odbc/microsoft/sqlgetcursorname-visual-foxpro-odbc-driver.md)  
        [SQLNumResultCols](../../odbc/microsoft/sqlnumresultcols-visual-foxpro-odbc-driver.md)  
        [SQLPrepare](../../odbc/microsoft/sqlprepare-visual-foxpro-odbc-driver.md)  
        [SQLRowCount](../../odbc/microsoft/sql-row-count-visual-foxpro-odbc-driver.md)  
        [SQLSetCursorName](../../odbc/microsoft/sqlsetcursorname-visual-foxpro-odbc-driver.md)  
        [SQLtransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md)  
    :::column-end:::
:::row-end:::

## <a name="level-1-api-support"></a>API-Unterstützung der Ebene 1  
 Die ODBC-API-Funktionen der Ebene 1 sind in der folgenden Tabelle aufgeführt. Alle diese Funktionen werden vom Visual FoxPro-ODBC-Treiber vollständig oder teilweise unterstützt.  

:::row:::
    :::column:::
        [SQLBindParameter](../../odbc/microsoft/sqlbindparameter-visual-foxpro-odbc-driver.md)  
        [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)  
        [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)  
        [SQLGetConnectOption](../../odbc/microsoft/sqlgetconnectoption-visual-foxpro-odbc-driver.md)  
        [SQLGetData](../../odbc/microsoft/sqlgetdata-visual-foxpro-odbc-driver.md)  
        [SQLGetFunctions](../../odbc/microsoft/sqlgetfunctions-visual-foxpro-odbc-driver.md)  
        [SQLGetInfo](../../odbc/microsoft/sqlgetinfo-visual-foxpro-odbc-driver.md)  
        [SQLGetStmtOption](../../odbc/microsoft/sqlgetstmtoption-visual-foxpro-odbc-driver.md)  
    :::column-end:::
    :::column:::
        [SQLGetTypeInfo](../../odbc/microsoft/sqlgettypeinfo-visual-foxpro-odbc-driver.md)  
        [SQLParamData](../../odbc/microsoft/sqlparamdata-visual-foxpro-odbc-driver.md)  
        [SQLPutData](../../odbc/microsoft/sqlputdata-visual-foxpro-odbc-driver.md)  
        [SQLSetConnectOption](../../odbc/microsoft/sqlsetconnectoption-visual-foxpro-odbc-driver.md)  
        [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md)  
        ['SQLSpecialColumns'](../../odbc/microsoft/sqlspecialcolumns-visual-foxpro-odbc-driver.md)  
        ['SQLStatistics'](../../odbc/microsoft/sqlstatistics-visual-foxpro-odbc-driver.md)  
        [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)  
    :::column-end:::
:::row-end:::

## <a name="level-2-api-support"></a>API-Unterstützung der Ebene 2  
 Die folgenden ODBC-API-Funktionen der Ebene 2 werden vollständig oder teilweise unterstützt:  
  
-   [SQLDataSources](../../odbc/microsoft/sqldatasources-visual-foxpro-odbc-driver.md)  
  
-   [SQLDrivers](../../odbc/microsoft/sqldrivers-visual-foxpro-odbc-driver.md)  
  
-   [SQLExtendedFetch](../../odbc/microsoft/sqlextendedfetch-visual-foxpro-odbc-driver.md)  
  
-   [SQLMoreResults](../../odbc/microsoft/sqlmoreresults-visual-foxpro-odbc-driver.md)  
  
-   [SQLNumParams](../../odbc/microsoft/sqlnumparams-visual-foxpro-odbc-driver.md)  
  
-   [SQLParamOptions](../../odbc/microsoft/sqlparamoptions-visual-foxpro-odbc-driver.md)  
  
-   [SQLPrimaryKeys](../../odbc/microsoft/sqlprimarykeys-visual-foxpro-odbc-driver.md)  
  
-   [SQLSetPos](../../odbc/microsoft/sqlsetpos-visual-foxpro-odbc-driver.md)  
  
-   [SQLSetScrollOptions](../../odbc/microsoft/sqlsetscrolloptions-visual-foxpro-odbc-driver.md) (partielle Unterstützung)  
  
 Die folgenden API-Funktionen der Ebene 2 werden nicht unterstützt:  
  
-   SQLBrowseConnect  
  
-   SQLColumnPrivileges  
  
-   SQLDescribeParam  
  
-   SQLForeignKeys  
  
-   SQLNativeSql  
  
-   SQLProcedureColumns  
  
-   'SQLProcedures'  
  
-   SQLTablePrivileges
