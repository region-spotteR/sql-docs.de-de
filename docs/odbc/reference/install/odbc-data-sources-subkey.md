---
description: Unterschlüssel für ODBC-Datenquellen
title: Unterschlüssel für ODBC-Datenquellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/23/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9897c68d110f59d03ac8e1b3e403ed21844082fb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448932"
---
# <a name="odbc-data-sources-subkey"></a>Unterschlüssel für ODBC-Datenquellen

Die Werte unter dem `ODBC Data Sources` Unterschlüssel Listen die Datenquellen auf. Das Format dieser Werte wird in der folgenden Tabelle dargestellt.

| Name | Datentyp | Daten |
| :--- | :-------- | :--- |
| *Datenquellen Name* | REG_SZ | *Treiber Beschreibung* |
| &nbsp; | &nbsp; | &nbsp; |

Der Wert für *Datenquellen Name* wird vom Verwaltungs Programm definiert (das normalerweise den Benutzer dazu auffordert), und die *Treiber Beschreibung* wird vom Treiber Entwickler definiert (in der Regel ist dies der Name des DBMS, das dem Treiber zugeordnet ist).

Angenommen, drei Datenquellen wurden definiert: Inventory, der SQL Server verwendet. Gehaltsliste, die dBASE verwendet; und Mitarbeiter, die formatierte Textdateien verwenden. Die Werte unter dem `ODBC Data Sources` Unterschlüssel können wie folgt lauten:

```console
Inventory : REG_SZ : SQL Server
Payroll : REG_SZ : dBASE
Personnel : REG_SZ : Text
```
