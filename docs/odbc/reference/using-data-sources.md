---
description: Verwenden von Datenquellen
title: Verwenden von Datenquellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], about data sources
ms.assetid: d5550619-22b2-4b16-bd08-fbabb6554c40
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 162f1c2bf8d75757ac2c29d60f675ac07ba8b00d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428832"
---
# <a name="using-data-sources"></a>Verwenden von Datenquellen
Datenquellen werden in der Regel vom Endbenutzer oder von einem Techniker mit einem Programm namens *ODBC-Administrator*erstellt. Der ODBC-Administrator fordert den Benutzer zur Verwendung des Treibers auf und ruft dann den Treiber auf. Der Treiber zeigt ein Dialogfeld an, in dem die Informationen angefordert werden, die zum Herstellen einer Verbindung mit der Datenquelle erforderlich sind. Nachdem der Benutzer die Informationen eingegeben hat, speichert der Treiber ihn auf dem System.  
  
 Die Anwendung ruft den Treiber-Manager später auf und übergibt den Namen einer Computer Datenquelle oder den Pfad einer Datei, die eine Datei Datenquelle enthält. Wenn ein Computer Datenquellen Name übermittelt wird, durchsucht der Treiber-Manager das System, um den von der Datenquelle verwendeten Treiber zu finden. Anschließend wird der Treiber geladen und der Datenquellen Name an ihn weitergeleitet. Der Treiber verwendet den Datenquellen Namen, um die Informationen zu finden, die zum Herstellen einer Verbindung mit der Datenquelle benötigt werden. Schließlich wird eine Verbindung mit der Datenquelle hergestellt, und der Benutzer wird in der Regel zur Eingabe einer Benutzer-ID und eines Kennworts aufgefordert.  
  
 Wenn eine Datei Datenquelle übermittelt wird, wird die Datei vom Treiber-Manager geöffnet, und der angegebene Treiber wird geladen. Wenn die Datei auch eine Verbindungs Zeichenfolge enthält, wird diese an den Treiber weitergeleitet. Mithilfe der Informationen in der Verbindungs Zeichenfolge stellt der Treiber eine Verbindung mit der Datenquelle her. Wenn keine Verbindungs Zeichenfolge übermittelt wurde, fordert der Treiber den Benutzer in der Regel zur Eingabe der erforderlichen Informationen auf.
