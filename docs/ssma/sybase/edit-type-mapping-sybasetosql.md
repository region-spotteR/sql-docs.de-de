---
description: Bearbeiten der Typzuordnung (SybaseToSQL)
title: Typzuordnung bearbeiten (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 513f071a-d5e6-4ed5-acca-269bf76323c5
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 3f9f5e0f498dbe6a8fe45a9c80cbf3c512f04bac
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88492279"
---
# <a name="edit-type-mapping-sybasetosql"></a>Bearbeiten der Typzuordnung (SybaseToSQL)
Im Dialogfeld **Typzuordnung bearbeiten** können Sie angeben, wie Typen zwischen den Quell-und Ziel Datenbankobjekten zugeordnet werden sollen.  
  
Sie können auf dieses Dialogfeld an mehreren Stellen zugreifen:  
  
-   Wenn Sie eine Quelldatenbank oder ein Datenbankobjekt auswählen, wird rechts neben dem metadatenexplorer die Registerkarte **Typzuordnung** angezeigt. Klicken Sie zum Hinzufügen einer neuen Typzuordnung auf **Hinzufügen** , oder klicken Sie auf **Bearbeiten** , um eine vorhandene Typzuordnung zu ändern.  
  
-   Wählen Sie **im Menü Extras** die Option **Projekteinstellungen** oder **Standard Projekteinstellungen**aus. Wählen Sie im daraufhin angezeigten Dialogfeld die Option **Typzuordnung**aus. Klicken Sie zum Hinzufügen einer neuen Typzuordnung auf **Hinzufügen** , oder klicken Sie auf **Bearbeiten** , um eine vorhandene Typzuordnung zu ändern.  
  
Tabellen spezifische Typzuordnungen überschreiben Datenbank-und Projekttyp Zuordnungen. Datenbankspezifische Zuordnungen überschreiben Projekt Zuordnungen.  
  
## <a name="options"></a>Tastatur  
**Quellentyp**  
Wählen Sie den Quell Datentyp aus, der einem Datentyp zugeordnet werden soll [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
Wenn der Datentyp eine Variable Länge hat, werden die folgenden Felder unter **Quelltyp**angezeigt:  
  
**From**  
Geben Sie die Mindestlänge für diese Zuordnung an. Beispielsweise können Sie für den **NCHAR** -Datentyp 10 eingeben, um anzugeben, dass diese Zuordnung für einen Bereich gilt, der bei **NCHAR (10)** beginnt.  
  
**An**  
Geben Sie die maximale Länge für diese Zuordnung an. Beispielsweise können Sie für den **NCHAR** -Datentyp 20 eingeben, um anzugeben, dass diese Zuordnung für einen Bereich gilt, der bei **NCHAR (20)** endet.  
  
**Zieltyp**  
Wählen Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp aus, dem der Quell Datentyp zugeordnet ist. Wenn SSMA die Tabelle oder die gespeicherte Prozedur in erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ändert sich der Quell Datentyp in diesen Datentyp.  
  
Wenn der Datentyp eine Variable Länge hat, wird das folgende Feld unter **Zieltyp**angezeigt:  
  
**Replace with**  
Geben Sie die Ziellänge für diese Zuordnung an. Beispielsweise können Sie für den Datentyp **nvarchar** den Wert 20 eingeben, um anzugeben, dass der angegebene Quell Datentyp **nvarchar (20)** zugeordnet werden soll.  
  
