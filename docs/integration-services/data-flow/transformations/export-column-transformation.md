---
description: Transformation für das Exportieren von Spalten
title: Transformation für das Exportieren von Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.exportcolumntrans.f1
- sql13.dts.designer.fileextractortransformation.columns.f1
- sql13.dts.designer.fileextractortransformation.errorhandling.f1
helpviewer_keywords:
- exporting data
- append options [Integration Services]
- Export Column transformation [Integration Services]
- columns [Integration Services], exporting
- inserting data
- truncate options [Integration Services]
ms.assetid: 678d2dfc-e40c-4fbb-b2cc-42fffc44478a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1cf2f0799896bfaac652e00a7736a0de3d8be97e
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92194604"
---
# <a name="export-column-transformation"></a>Transformation für das Exportieren von Spalten

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  Die Transformation für das Exportieren von Spalten liest Daten in einem Datenfluss und fügt sie in eine Datei ein. Wenn z. B. der Datenfluss Produktinformationen enthält, wie z. B. ein Image jedes Produkts, könnten Sie mithilfe der Transformation für das Exportieren von Spalten die Bilder in Dateien speichern.  
  
## <a name="append-and-truncate-options"></a>Optionen zum Anfügen und Abschneiden  
 In der folgenden Tabelle wird beschrieben, wie die Einstellungen für die Optionen zum Anfügen und Abschneiden die Ergebnisse beeinflussen.  
  
|Anfügen|Truncate|Die Datei ist vorhanden|Ergebnisse|  
|------------|--------------|-----------------|-------------|  
|False|False|Nein|Die Transformation erstellt eine neue Datei und schreibt die Daten in die Datei.|  
|True|False|Nein|Die Transformation erstellt eine neue Datei und schreibt die Daten in die Datei.|  
|False|True|Nein|Die Transformation erstellt eine neue Datei und schreibt die Daten in die Datei.|  
|True|True|No|Zur Entwurfszeit tritt bei der Überprüfung der Transformation ein Fehler auf. Beide Eigenschaften dürfen nicht auf **true**festgelegt werden.|  
|False|False|Yes|Ein Laufzeitfehler tritt auf. Die Datei ist vorhanden, aber die Transformation kann nicht in diese schreiben.|  
|False|True|Yes|Die Transformation löscht die Datei und erstellt sie neu und schreibt die Daten in diese Datei.|  
|True|False|Yes|Die Transformation öffnet die Datei und fügt die Daten am Dateiende an.|  
|True|True|Yes|Zur Entwurfszeit tritt bei der Überprüfung der Transformation ein Fehler auf. Beide Eigenschaften dürfen nicht auf **true**festgelegt werden.|  
  
## <a name="configuration-of-the-export-column-transformation"></a>Konfiguration der Transformation für das Exportieren von Spalten  
 Es gibt folgende Möglichkeiten, um die Transformation für das Exportieren von Spalten zu konfigurieren:  
  
-   Geben Sie die Datenspalten und die Spalten an, die den Pfad von Dateien enthalten, in die die Daten geschrieben werden sollen.  
  
-   Geben Sie an, ob der Vorgang zum Einfügen von Daten an vorhandene Dateien anfügt oder diese abschneidet.  
  
-   Geben Sie an, ob eine Bytereihenfolgemarke (BOM, Byte-Order Mark) in die Datei geschrieben wird.  
  
    > [!NOTE]  
    >  Eine BOM wird nur geschrieben, wenn die Daten nicht an eine vorhandene Datei angefügt werden und die Daten vom DT_NTEXT-Datentyp sind.  
  
 Die Transformation verwendet Eingabespaltenpaare: Eine Spalte enthält einen Dateinamen, die andere Spalte enthält Daten. In jeder Zeile des Datasets kann eine andere Datei angegeben sein. Beim Verarbeiten einer Zeile durch die Transformation werden die Daten in die angegebene Datei eingefügt. Zur Laufzeit erstellt die Transformation die Dateien, falls sie noch nicht vorhanden sind. Anschließend schreibt die Transformation die Daten in die Dateien. Die zu schreibenden Daten müssen den Datentyp DT_TEXT, DT_NTEXT oder DT_IMAGE aufweisen. Weitere Informationen finden Sie unter [Integration Services Datentypen](../../../integration-services/data-flow/integration-services-data-types.md).  
  
 Diese Transformation weist eine Eingabe, eine Ausgabe und eine Fehlerausgabe auf.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Common Properties](../set-the-properties-of-a-data-flow-component.md)  
  
-   [Benutzerdefinierte Eigenschaften von Transformationen](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Weitere Informationen zum Festlegen der Eigenschaften finden Sie unter [Festlegen der Eigenschaften einer Datenflusskomponente](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="export-column-transformation-editor-columns-page"></a>Transformations-Editor für das Exportieren von Spalten (Seite Spalten)
  Auf der Seite **Spalten** des Dialogfelds **Transformations-Editor für das Exportieren von Spalten** können Sie die Spalten im Datenfluss angeben, die in Dateien extrahiert werden sollen. Sie können angeben, ob die Daten durch die Transformation für das Exportieren von Spalten an eine Datei angefügt werden, oder ob eine vorhandene Datei mit den Daten überschrieben wird.  
  
### <a name="options"></a>Optionen  
 **Spalte extrahieren**  
 Wählen Sie Spalten aus der Liste der Eingabespalten aus, die Text- oder Bilddaten enthalten. Alle Zeilen sollten Definitionen für **Spalte extrahieren** und **Dateipfadspalte**aufweisen.  
  
 **Dateipfadspalte**  
 Wählen Sie Spalten aus der Liste der Eingabespalten aus, die Dateipfade und Dateinamen enthalten. Alle Zeilen sollten Definitionen für **Spalte extrahieren** und **Dateipfadspalte**aufweisen.  
  
 **Anfügen zulassen**  
 Geben Sie an, ob Daten durch die Transformation an vorhandene Dateien angefügt werden sollen. Die Standardeinstellung ist **false**.  
  
 **Abschneiden erzwingen**  
 Geben Sie an, ob die Inhalte vorhandener Dateien vor dem Schreiben der Daten durch die Transformation gelöscht werden sollen. Die Standardeinstellung ist **false**.  
  
 **Bytereihenfolge-Marke schreiben**  
 Geben Sie an, ob eine Bytereihenfolge-Marke in die Datei geschrieben werden soll. Eine Bytereihenfolge-Marke wird nur geschrieben, wenn die Daten den Datentyp **DT_NTEXT** oder DT_WSTR aufweisen und nicht an eine vorhandene Datendatei angefügt werden.  
  
## <a name="export-column-transformation-editor-error-output-page"></a>Transformations-Editor für das Exportieren von Spalten (Seite Fehlerausgabe)
  Auf der Seite **Fehlerausgabe** des Dialogfelds **Transformations-Editor für das Exportieren von Spalten** geben Sie Optionen für die Fehlerbehandlung an.  
  
### <a name="options"></a>Tastatur  
 **Eingabe/Ausgabe**  
 Zeigen Sie den Namen der Ausgabe an. Klicken Sie auf den Namen, um die Sicht zu erweitern und Spalten einzuschließen.  
  
 **Spalte**  
 Zeigen Sie die Ausgabespalten an, die Sie auf der Seite **Spalten** des Dialogfelds **Transformations-Editor für das Exportieren von Spalten** ausgewählt haben.  
  
 **Fehler**  
 Geben Sie an, was bei Auftreten eines Fehlers geschehen soll: den Fehler ignorieren, die Zeile umleiten oder die Komponente mit einem Fehler abbrechen.  
  
 **Abschneiden**  
 Geben Sie an, was bei Auftreten eines Abschneidevorgangs geschehen soll: den Fehler ignorieren, die Zeile umleiten oder die Komponente mit einem Fehler abbrechen.  
  
 **Beschreibung**  
 Zeigt die Beschreibung des Vorgangs an.  
  
 **Diesen Wert für ausgewählte Zellen festlegen**  
 Gibt an, was im Falle eines Fehlers oder einer Kürzung mit den ausgewählten Zellen geschehen soll: den Fehler ignorieren, die Zeile umleiten oder die Komponente mit einem Fehler abbrechen.  
  
 **Anwenden**  
 Wendet die Fehlerbehandlungsoption auf die ausgewählten Zellen an.  
  
