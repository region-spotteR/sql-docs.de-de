---
description: Auftragseigenschaften – Neuer Auftrag (Seite „Zeitpläne“)
title: Auftragseigenschaften – Neuer Auftrag (Seite „Zeitpläne“)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.schedules.f1
ms.assetid: 0b03585b-a510-484d-8a63-9b32459def9c
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c4476f26f2b17cedcc12e723efc08c116b190488
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92037885"
---
# <a name="job-properties---new-job-schedules-page"></a>Auftragseigenschaften – Neuer Auftrag (Seite „Zeitpläne“)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Mithilfe dieser Seite können Sie Zeitpläne für einen [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Auftrag abrufen und verwalten.  
  
## <a name="options"></a>Optionen  
**Zeitplanliste**  
Führt die Zeitpläne für diesen Auftrag auf.  
  
**Neu**  
Erstellt einen neuen Zeitplan. Nachdem Sie den Zeitplan erstellt haben, wird er dem Auftrag hinzugefügt.  
  
**Auswählen**  
Wählt einen Zeitplan aus den vorhandenen Zeitplänen aus. Da ein Auftrag und ein Zeitplan denselben Besitzer haben müssen, können Sie mit dieser Option nur unter Zeitplänen auswählen, deren Besitzer Sie sind.  
  
**Bearbeiten**  
Bearbeitet den ausgewählten Zeitplan, um die Eigenschaften des Auftragszeitplans zu ändern.  
  
**Remove**  
Entfernt den ausgewählten Zeitplan aus der Liste für den Auftrag. Wenn keine anderen Aufträge diesen Zeitplan verwenden, wird der Zeitplan aus der Datenbank gelöscht.  
  
## <a name="see-also"></a>Weitere Informationen  
[Implementieren von Aufträgen](../../ssms/agent/implement-jobs.md)  
