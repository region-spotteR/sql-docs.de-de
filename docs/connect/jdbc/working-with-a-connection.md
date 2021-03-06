---
title: Arbeiten mit einer JDBC-Verbindung
description: Hier finden Sie Beispiele für die verschiedenen Möglichkeiten, mit der SQLServerConnection-Klasse des Microsoft JDBC-Treibers für SQL Server eine Verbindung mit einer SQL Server-Datenbank-Instanz herzustellen.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cf8ee392-8a10-40a3-ae32-31c7b1efdd04
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1253c2ec5822fef83d6da71279752202f2d93ebd
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "81631950"
---
# <a name="working-with-a-connection"></a>Arbeiten mit einer Verbindung

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Die folgenden Abschnitte enthalten Beispiele für die verschiedenen Möglichkeiten, um mit der [SQLServerConnection](reference/sqlserverconnection-class.md)-Klasse von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank herzustellen.

> [!NOTE]  
> Wenn beim Herstellen von Verbindungen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit dem JDBC-Treiber Probleme auftreten, finden Sie unter [Behandlung von Verbindungsproblemen](troubleshooting-connectivity.md) Vorschläge zum Beheben der Probleme.

## <a name="creating-a-connection-by-using-the-drivermanager-class"></a>Erstellen einer Verbindung mit der DriverManager-Klasse

Die einfachste Vorgehensweise zum Erstellen einer Verbindung zu einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank besteht darin, den JDBC-Treiber zu laden und wie im Folgenden dargestellt die getConnection-Methode der DriverManager-Klasse aufzurufen:

```java
Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
String connectionUrl = "jdbc:sqlserver://localhost;database=AdventureWorks;integratedSecurity=true;"  
Connection con = DriverManager.getConnection(connectionUrl);  
```

Bei diesem Verfahren wird eine Datenbankverbindung mit dem ersten verfügbaren Treiber in der Liste der Treiber erstellt, der erfolgreich eine Verbindung mit der angegebenen URL herstellen kann.

> [!NOTE]  
> Bei Verwendung der sqljdbc4.jar-Klassenbibliothek müssen Anwendungen den Treiber nicht mit der Class.forName-Methode explizit registrieren oder laden. Wenn die getConnection-Methode der DriverManager-Klasse aufgerufen wird, wird aus der Gruppe der registrierten JDBC-Treiber ein geeigneter Treiber ausgewählt. Weitere Informationen finden Sie unter "Verwenden des JDBC-Treibers".

## <a name="creating-a-connection-by-using-the-sqlserverdriver-class"></a>Erstellen einer Verbindung mit der SQLServerDriver-Klasse

Wenn Sie in der Liste der Treiber für DriverManager einen bestimmten Treiber angeben müssen, können Sie wie im Folgenden dargestellt eine Datenbankverbindung mit der [connect](reference/connect-method-sqlserverdriver.md)-Methode der [SQLServerDriver](reference/sqlserverdriver-class.md)-Klasse erstellen:

```java
Driver d = (Driver) Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver").newInstance();  
String connectionUrl = "jdbc:sqlserver://localhost;database=AdventureWorks;integratedSecurity=true;"  
Connection con = d.connect(connectionUrl, new Properties());  
```

## <a name="creating-a-connection-by-using-the-sqlserverdatasource-class"></a>Erstellen einer Verbindung mit der SQLServerDataSource-Klasse

Wenn Sie eine Verbindung mit der [SQLServerDataSource](reference/sqlserverdatasource-class.md)-Klasse erstellen müssen, können Sie verschiedene Festlegungsmethoden der Klasse verwenden, bevor Sie die [getConnection](reference/getconnection-method.md)-Methode aufrufen, z.B.:

```java
SQLServerDataSource ds = new SQLServerDataSource();  
ds.setUser("MyUserName");  
ds.setPassword("*****");  
ds.setServerName("localhost");  
ds.setPortNumber(1433);
ds.setDatabaseName("AdventureWorks");  
Connection con = ds.getConnection();  
```

## <a name="creating-a-connection-that-targets-a-specific-data-source"></a>Erstellen einer Verbindung mit einer speziellen Datenquelle als Ziel

Wenn Sie eine Datenbankverbindung mit einer speziellen Datenquelle herstellen müssen, können Sie mehrere Verfahren verwenden. Das jeweilige Verfahren hängt von den Eigenschaften ab, die Sie mit der Verbindungs-URL festlegen.

Um eine Verbindung mit der Standardinstanz auf einem Remoteserver herzustellen, verwenden Sie das folgende Beispiel:

```java
String url = "jdbc:sqlserver://MyServer;integratedSecurity=true;"
```

Um eine Verbindung mit einem bestimmten Port eines Servers herzustellen, verwenden Sie das folgende Beispiel:

```java
String url = "jdbc:sqlserver://MyServer:1533;integratedSecurity=true;"
```

Um eine Verbindung mit einer benannten Instanz eines Servers herzustellen, verwenden Sie das folgende Beispiel:

```java
String url = "jdbc:sqlserver://209.196.43.19;instanceName=INSTANCE1;integratedSecurity=true;"
```

Um eine Verbindung mit einer bestimmten Datenbank eines Servers herzustellen, verwenden Sie das folgende Beispiel:

```java
String url = "jdbc:sqlserver://172.31.255.255;database=AdventureWorks;integratedSecurity=true;"
```

Weitere Beispiele für Verbindungs-URL finden Sie unter [Erstellen der Verbindungs-URL](building-the-connection-url.md).

## <a name="creating-a-connection-with-a-custom-login-timeout"></a>Erstellen einer Verbindung mit einem benutzerdefinierten Anmeldetimeout

Wenn Sie Serverlast oder Netzwerkverkehr berücksichtigen müssen, können Sie eine Verbindung mit einem bestimmten Timeoutwert für die Anmeldung in Sekunden erstellen, wie im folgenden Beispiel:

```java
String url = "jdbc:sqlserver://MyServer;loginTimeout=90;integratedSecurity=true;"
```

## <a name="create-a-connection-with-application-level-identity"></a>Erstellen einer Verbindung mit Identität auf Anwendungsebene

Wenn Sie Protokollierung und Profilerstellung verwenden, müssen Sie die Verbindung mit einer bestimmten Anwendung als Ursprung kennzeichnen, wie im folgenden Beispiel:

```java
String url = "jdbc:sqlserver://MyServer;applicationName=MYAPP.EXE;integratedSecurity=true;"
```

## <a name="closing-a-connection"></a>Trennen einer Verbindung

Sie können durch Aufrufen der [close](reference/close-method-sqlserverconnection.md)-Methode der SQLServerConnection-Klasse eine Datenbankverbindung wie im Folgenden dargestellt explizit schließen:

```java
con.close();
```

Dadurch werden die vom SQLServerConnection-Objekt verwendeten Datenbankressourcen freigegeben, bzw. die Verbindung in Poolszenarios werden an den Verbindungspool zurückgegeben.

> [!NOTE]  
> Durch den Aufruf der close-Methode wird auch ein Rollback aller anstehenden Transaktionen ausgeführt.

## <a name="see-also"></a>Weitere Informationen

[Verbinden mit SQL Server mit dem JDBC-Treiber](connecting-to-sql-server-with-the-jdbc-driver.md)
