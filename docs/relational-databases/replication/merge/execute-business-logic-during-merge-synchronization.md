---
title: Geschäftslogik für die Mergesynchronisierung
description: Erfahren Sie, wie Sie verwalteten Assemblycode für die Geschäftslogik schreiben, der für die Mergesynchronisierung verwendet wird.
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- custom error resolution [SQL Server replication]
- custom change handling [SQL Server replication]
- errors [SQL Server replication], business logic handlers
- merge replication business logic handlers [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
- business logic handlers [SQL Server replication]
ms.assetid: 9d4da2ef-c17f-4a31-a1f6-5c3b7ca85f71
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d3f3601aca4a8cf5325071a99a6c7605253ff0aa
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85880079"
---
# <a name="execute-business-logic-during-merge-synchronization"></a>Ausführen der Geschäftslogik während der Mergesynchronisierung
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Im Geschäftslogikhandler können Sie eine Assembly in verwaltetem Code schreiben, die während des Mergesynchronisierungsvorgangs aufgerufen wird. Die Assembly enthält Geschäftslogik, die auf viele Bedingungen während der Synchronisierung reagieren kann: Datenänderungen, Konflikte und Fehler. Das Geschäftslogikhandler-Framework stellt ein einfaches Programmiermodell bereit. Dabei weisen die Daten, die der Mergeprozess an Ihre Assembly übergibt, das Format eines ADO.NET-Datasets auf. Auf diese Weise können Sie auf Ihren Kenntnissen von ADO.NET aufbauen und müssen sich mit keiner neuen proprietären Schnittstelle vertraut machen. Weitere Informationen zum Programmieren von Geschäftslogikhandlern finden Sie hier:  
  
-   In der API-Referenz (Application Programming Interface, Schnittstelle für Anwendungsprogrammierung): <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>  
  
-   Anweisungen zum Implementieren eines Geschäftslogikhandlers: [Implementieren eines Geschäftslogikhandlers für einen Mergeartikel](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)  
  
## <a name="uses-for-business-logic-handlers"></a>Verwendungsmöglichkeiten für Geschäftslogikhandler  
 Bei der Mergesynchronisierung können Geschäftslogikhandler für folgende Zwecke aufgerufen werden:  
  
-   Verarbeiten von benutzerdefinierten Änderungen  
  
-   Benutzerdefinierte Konfliktlösung  
  
-   Benutzerdefinierte Fehlerbehebung  
  
> [!NOTE]  
>  Der von Ihnen angegebene Geschäftslogikhandler wird für jede Zeile ausgeführt, die synchronisiert wird. Eine komplexe Logik und Aufrufe anderer Anwendungen oder Netzwerkdienste können sich auf die Leistung auswirken.  
  
### <a name="custom-change-handling"></a>Verarbeiten von benutzerdefinierten Änderungen  
 Der Geschäftslogikhandler kann bei der Verarbeitung von Datenänderungen aufgerufen werden, die keine Konflikte verursachen, und eine von drei Aktionen ausführen:  
  
-   Daten ablehnen  
  
     Das ist bei Anwendungen nützlich, bei denen keine Änderungen von einem oder an einen bestimmten Abonnenten weitergegeben werden sollen. Ein Administrator kann z. B. Einfügungen herausfiltern, die nicht in die Partition des Abonnenten gehören, oder Löschungen ablehnen, die auf einem Abonnenten ausgeführt werden. Ein weiteres Beispiel ist eine Anwendung, die eine Bestellung ablehnt, die auf einem Abonnenten eingegeben wird, weil der Bestand nicht mehr verfügbar ist.  
  
-   Daten annehmen  
  
     Das ist bei Anwendungen nützlich, bei denen Datenänderungen überprüft werden müssen, die auf dem Verleger oder dem Abonnenten vorgenommen wurden, bevor sie weitergegeben werden. Beispielsweise kann eine Anwendung der mittleren Ebene neue Bestellungen überprüfen, die über den Außendienst eingehen, und in einen Beschaffungsworkflowprozess der mittleren Ebene integrieren.  
  
-   Benutzerdefinierte Daten anwenden  
  
     Das ist bei Anwendungen nützlich, die bestimmte Datenwerte oder Vorgänge überschreiben müssen. Eine Anwendung kann z. B. eine Zeilenlöschung in ein spezielles Update transformieren, das eine **status** -Spalte in der Zeile auf einen Wert "gelöscht" festlegt und dann die Identität des Clients ermittelt, der das Löschen ausgeführt hat. Das kann zum Überwachen und für Workflowzwecke nützlich sein.  
  
### <a name="custom-conflict-resolution"></a>Benutzerdefinierte Konfliktlösung  
 Die Mergereplikation stellt eine Konflikterkennung und -lösung bereit, mit deren Hilfe Sie eine Standardstrategie zur Konfliktlösung übernehmen oder eine benutzerdefinierte Lösung von Konflikten auswählen können. Weitere Informationen finden Sie unter [Erweiterte Konflikterkennung und -lösung bei der Mergereplikation](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)angegeben wird. Der Geschäftslogikhandler kann bei der Verarbeitung von Datenänderungen aufgerufen werden, die Konflikte verursachen, und eine von zwei Aktionen ausführen:  
  
-   Standardlösung übernehmen  
  
     Das ist bei Anwendungen nützlich, die einen Konflikt möglicherweise überprüfen, weitere Aktionen ausführen und gegebenenfalls eine benutzerdefinierte Konfliktmeldung protokollieren müssen.  
  
-   Benutzerdefinierte Lösung ausführen  
  
     Das ist bei Anwendungen nützlich, die gegebenenfalls ihrer speziellen Geschäftslogik entsprechende Datenwerte auswählen und dieses benutzerdefinierte Dataset für den Synchronisierungsprozess bereitstellen müssen. Eine Anwendung kann z. B. eine neue Version der gewinnenden Zeile bereitstellen, indem sie Werte aus den Verleger- und Abonnentendatasets kombiniert.  
  
### <a name="custom-error-resolution"></a>Benutzerdefinierte Fehlerbehebung  
 Die benutzerdefinierte Logik kann bei der Weitergabe von Änderungen aufgerufen werden, die zu einem Fehler führen. Die Logik kann eine der folgenden beiden Aktionen ausführen:  
  
-   Standardfehlerbehebung übernehmen  
  
     Das ist bei Anwendungen nützlich, die einen Fehler möglicherweise überprüfen, weitere Aktionen ausführen und gegebenenfalls eine benutzerdefinierte Fehlermeldung protokollieren müssen.  
  
-   Standardfehlerbehebung übernehmen  
  
     Das ist bei Anwendungen nützlich, die gegebenenfalls ihrer speziellen Geschäftslogik entsprechende Datenwerte auswählen und dieses benutzerdefinierte Dataset für den Synchronisierungsprozess bereitstellen müssen. Werden z. B. Verletzungen doppelter Schlüssel beim Replikationsprozess gefunden, kann der Geschäftslogikhandler eine neue Version der Datenänderung bereitstellen, bei der der Schlüssel keinen Konflikt mehr verursacht. Auf dem Verleger oder Abonnenten vorgenommene Änderungen können dann in der Datenbank persistent gespeichert werden, und der Replikationsprozess muss die fehlerhafte Einfügung nicht mehr durch eine Löschung ausgleichen.  
  
## <a name="deployment-scenarios-for-business-logic-handlers"></a>Bereitstellungsszenarien für Geschäftslogikhandler  
 Folgende Stellen können Geschäftslogikhandler bereitstellen:  
  
-   Verteiler Verwenden Sie ein Pushabonnement, damit die Geschäftslogik auf dem Verteiler ausgeführt wird.  
  
-   Der Abonnent. Verwenden Sie ein Pullabonnement, damit die Geschäftslogik auf dem Abonnenten ausgeführt wird.  
  
-   Ein IIS-Server (Internetinformationsdienste), wenn die Websynchronisierung verwendet wird. Verwenden Sie ein mit der Websynchronisierung synchronisiertes Pullabonnement. Der Geschäftslogikhandler wird dann auf dem IIS-Server ausgeführt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mergereplikation](../../../relational-databases/replication/merge/merge-replication.md)   
 [Abonnieren von Veröffentlichungen](../../../relational-databases/replication/subscribe-to-publications.md)   
 [Synchronisieren von Daten](../../../relational-databases/replication/synchronize-data.md)   
 [Websynchronisierung für die Mergereplikation](../../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
