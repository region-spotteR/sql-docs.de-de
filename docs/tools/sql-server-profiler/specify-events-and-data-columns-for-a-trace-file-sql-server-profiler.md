---
title: Angeben der Ereignisse und Datenspalten für eine Ablaufverfolgungsdatei
titleSuffix: SQL Server Profiler
description: Hier erfahren Sie, wie Sie angeben, welche Ereignisklassen und Datenspalten der SQL Server Profiler beim Erfassen von Ereignisdaten bei der Ablaufverfolgung enthält.
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 7da715a3-2f03-4063-b6a4-20fd7b44e675
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 624ee18dfeb1fb73f0b7ba77eab8466ab90f6130
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85734194"
---
# <a name="specify-events-and-data-columns-for-a-trace-file-sql-server-profiler"></a>Angeben von Ereignissen und Datenspalten für eine Ablaufverfolgungsdatei (SQL Server Profiler)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

In diesem Thema wird beschrieben, wie Ereignisklassen und Datenspalten mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]angegeben werden.  
  
### <a name="to-specify-events-and-data-columns-for-a-trace"></a>So geben Sie Ereignisse und Datenspalten für eine Ablaufverfolgung an  
  
1.  Klicken Sie im Dialogfeld **Ablaufverfolgungseigenschaften** oder **Eigenschaften der Ablaufverfolgungsvorlage** auf die Registerkarte **Ereignisauswahl** .  
  
     Die Registerkarte **Ereignisauswahl** enthält ein Rastersteuerelement. Bei dem Rastersteuerelement handelt es sich um eine Tabelle, die alle bei der Ablaufverfolgung zu berücksichtigenden Ereignisklassen enthält. Die Tabelle enthält für jede Ereignisklasse eine Zeile. Die Ereignisklassen können sich leicht voneinander unterscheiden. Dies hängt vom Typ und der Version des Servers ab, zu dem eine Verbindung besteht. Die Ereignisklassen werden in der Spalte **Events**des Rasters identifiziert und nach Ereigniskategorie gruppiert. In den übrigen Spalten sind die Datenspalten aufgeführt, die für jede Ereignisklasse zurückgegeben werden können.  
  
2.  Klicken Sie im Dialogfeld **Ereignisauswahl**das Rastersteuerelement, um Ereignisse und Datenspalten zur Ablaufverfolgungsdatei hinzuzufügen oder aus ihr zu entfernen.  
  
3.  Um Ereignisse aus der Ablaufverfolgung zu entfernen, deaktivieren Sie das Kontrollkästchen in der **Ereignisse** -Spalte für jede Ereignisklasse.  
  
4.  Um Ereignisse in einer Ablaufverfolgung einzuschließen, aktivieren Sie das Kontrollkästchen in der **Ereignisse** -Spalte für jede Ereignisklasse, oder aktivieren Sie eine Datenspalte, die sich auf ein Ereignis bezieht.  
  
> [!IMPORTANT]  
>  Wenn die Ablaufverfolgung mit Systemmonitordaten abhängig wird, müssen die Datenspalten **Startzeit** und **Beendigungszeit** in der Ablaufverfolgung eingeschlossen sein.  
  
 Wenn Sie eine Ereignisklasse einschließen, wird auch jede zugeordnete Datenspalte in die Ablaufverfolgung aufgenommen, wenn Sie das Kontrollkästchen aktiviert haben, das mit einem Ereignis korrespondiert. Wenn Sie das Kontrollkästchen für eine bestimmte Spalte aktiviert haben, wird nur diese Spalte in die Ablaufverfolgung aufgenommen.  
  
1.  Um Datenspalten aus einer Ereignisklasse zu entfernen, deaktivieren Sie die Kontrollkästchen der Datenspalte in der Ereignisklassenzeile, oder klicken Sie mit der rechten Maustaste auf den Spaltenheader, und wählen Sie die Option **Spaltenauswahl aufheben** aus.  
  
2.  Wenden Sie optional Filter auf die Ablaufverfolgung an. Weitere Informationen finden Sie unter [Filtern von Ereignissen in einer Ablaufverfolgung &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
