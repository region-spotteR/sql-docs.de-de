---
description: Visual FoxPro-Felddatentypen
title: Visual FoxPro-Feld Datentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- field data types [ODBC]
- Visual FoxPro ODBC driver [ODBC], data types
ms.assetid: 50b733dc-679a-4b10-bc5d-98bb474dead2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 65410f16367af8764e8572c58e53831f3f7b9cda
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449052"
---
# <a name="visual-foxpro-field-data-types"></a>Visual FoxPro-Felddatentypen
In der folgenden Tabelle sind die Werte für das *FieldType* -Argument in ALTER TABLE und CREATE TABLE aufgeführt. Außerdem wird angegeben, ob *nfieldwidth* -und *nprecision* -Argumente erforderlich sind.  
  
|*FieldType*|*Nfieldwidth*|*ngenauigkeit*|Beschreibung|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|C|N|-|Zeichenfeld der Breite *n*|  
|D|-|-|Date|  
|F|N|d|Gleitendes numerisches Feld der Breite *n* mit *d* Dezimalstellen|  
|G|-|-|Allgemein|  
|I|-|-|Integer|  
|L|-|-|Logisch|  
|M|-|-|Memo|  
|N|N|d|Numerisches Feld der Breite *n* mit *d* Dezimalstellen|  
|T|-|-|Datetime|  
|J|-|-|Währung|
