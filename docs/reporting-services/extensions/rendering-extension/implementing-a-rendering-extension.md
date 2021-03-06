---
title: Bereitstellen von Renderingerweiterungen | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie durch Implementieren von Renderingerweiterungen Reporting Services-Berichtsdaten und -Layoutinformationen in gerätespezifische Formate umwandeln.
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- rendering extensions [Reporting Services]
- custom rendering extensions [Reporting Services]
- transformations [Reporting Services]
- extensions [Reporting Services], rendering
- rendering extensions [Reporting Services], implementing
ms.assetid: 4a5c64f5-2391-4597-ba3f-81d265b23703
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d61af9bd987256a2ad293f7f9566fd1a2bcd041e
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84529086"
---
# <a name="implementing-a-rendering-extension"></a>Implementieren von Renderingerweiterungen
  Eine Renderingerweiterung stellt eine Komponente oder ein Modul eines Berichtsservers dar, mit dem Daten- und Layoutinformationen in ein gerätespezifisches Format umgewandelt werden. Die SQL Server Reporting Services enthalten sechs Renderingerweiterungen: HTML, Excel, Word, CSV oder Text, XML, Image und PDF. Sie können zusätzliche Renderingerweiterungen erstellen, um Berichte in anderen Formaten zu generieren.  
  
> [!NOTE]  
>  Welche Renderingerweiterungen zur Verfügung stehen, sehen Sie auf der Liste der installierten Erweiterungen in der Datei RSReportServer.config.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Rendering Extensions Overview (Übersicht über Renderingerweiterungen)](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)  
 Erläutert, wie eine benutzerdefinierte Renderingerweiterung für [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] geschrieben wird.  
  
 [Implementing the IRenderingExtension Interface (Implementieren der IRenderingExtension-Schnittstelle)](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)  
 Beschreibt die Attribute einer Renderingerweiterung.  
  
 [Bereitstellen von Renderingerweiterungen](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
 Beschreibt, wie Sie eine Renderingerweiterung auf einem Berichtsserver bereitstellen  
  
 [Removing a Rendering Extension (Entfernen von Renderingerweiterungen)](../../../reporting-services/extensions/rendering-extension/removing-a-rendering-extension.md)  
 Beschreibt, wie Sie eine Renderingerweiterung von einem Berichtsserver entfernen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterungen für Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
