---
description: Dialogfeld „Verlegereinstellungen“ für die SQL Server-Replikation
title: Verlegereinstellungen (SSMS)| Microsoft-Dokumentation
descripton: Describes the 'Publisher Settings' dialog box found in Replication Monitor within SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.publishersettings.f1
helpviewer_keywords:
- Publisher Settings dialog box
ms.assetid: 4fb70427-082d-4179-82a1-34b235accc43
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 92a2570f2d591f3eb2fb3c2c460c60809bc0f5fb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88427922"
---
# <a name="sql-server-replication-publisher-settings-dialog-box"></a>Dialogfeld „Verlegereinstellungen“ für die SQL Server-Replikation
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
   Im Dialogfeld **Verlegereinstellungen** können Sie die Einstellungen für Verleger ändern, die dem linken Bereich des Replikationsmonitors hinzugefügt wurden.  
  
## <a name="options"></a>Optionen  
 **Verlegerverbindung**  
 Klicken Sie auf diese Option, um das Dialogfeld **Verbindung mit dem Server herstellen** zu starten. In diesem Dialogfeld können Sie die Verbindungseigenschaften und Anmeldeinformationen anzeigen und ändern, die vom Replikationsmonitor für die Verbindung mit einem Verleger verwendet werden.  
  
 **Verteilerverbindung**  
 Wird nur angezeigt, wenn vom Verleger ein Remoteverteiler verwendet wird. Klicken Sie auf diese Option, um das Dialogfeld **Verbindung mit dem Server herstellen** zu starten. In diesem Dialogfeld können Sie die Verbindungseigenschaften und Anmeldeinformationen anzeigen und ändern, die vom Replikationsmonitor für die Verbindung mit dem Remoteverteiler verwendet werden.  
  
 **Beim Starten des Replikationsmonitors automatisch Verbindung herstellen**  
 Wählen Sie diese Option aus, damit der Replikationsmonitor automatisch eine Verbindung mit dem Verteiler herstellt und Statusinformationen für den Verleger abruft, der im Raster im oberen Bereich des Dialogfelds ausgewählt ist. Wenn dieses Kontrollkästchen deaktiviert ist, müssen Sie nach dem Starten des Replikationsmonitors manuell eine Verbindung herstellen: Klicken Sie dazu mit der rechten Maustaste auf den Verleger im linken Bereich des Replikationsmonitors, und klicken Sie dann auf **Verbinden**.  
  
 **Status dieses Verlegers und seiner Veröffentlichungen automatisch aktualisieren**  
 Wählen Sie diese Option aus, damit der Replikationsmonitor automatisch den Status für den Verleger aktualisiert, der im Raster im oberen Bereich des Dialogfelds ausgewählt ist. Wenn diese Option ausgewählt ist, ruft der Replikationsmonitor die Statusinformationen für den Verleger und seine Veröffentlichungen über den Verteiler ab. Das Abrufintervall wird durch die Option **Aktualisierungsrate** festgelegt. Weitere Informationen zum Aktualisieren im Replikationsmonitor finden Sie unter [Zwischenspeichern, Aktualisieren und Leistung des Replikationsmonitors](../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md).  
  
 **Aktualisierungsrate**  
 Geben Sie einen Wert (in Sekunden) ein, um anzugeben, wie oft der Replikationsmonitor Statusinformationen über den Verteiler abrufen soll. Geringere Werte führen zu einem häufigeren Abruf, was die Leistung des Verteilers beeinträchtigen kann, wenn eine große Anzahl von Verlegern überwacht wird. Es wird empfohlen, das eigene System zu testen, um einen angemessenen Wert zu bestimmen. Die Einstellung **Aktualisierungsrate** wird ebenfalls verwendet, wenn Sie in einem der Detailfenster des Replikationsmonitors die Option **Automatisch aktualisieren** ausgewählt haben.  
  
 **Diese(n) Verleger in der folgenden Gruppe anzeigen**  
 Wählen Sie eine Verlegergruppe aus der Liste aus. Der Verleger wird unter dieser Gruppe im linken Bereich angezeigt. Gruppen stellen eine Möglichkeit zum Organisieren von Verlegern dar und haben keinen Einfluss auf die Funktion der Replikation.  
  
 **Neue Gruppe**  
 Klicken Sie auf diese Option, um eine neue Verlegergruppe zu erstellen. Eine Verlegergruppe stellt eine einfache Möglichkeit dar, um die Verleger innerhalb des Replikationsmonitors zu organisieren. Gruppen haben keinen Einfluss auf die Replikation der Daten oder die Beziehungen zwischen den Servern in der Replikationstopologie.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten des Replikationsmonitors](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Überwachen der Replikation](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
