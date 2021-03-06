---
title: Mixed-Datentyp und Simple-Inhalt | Microsoft-Dokumentation
description: Hier sehen Sie anhand eines Beispiels, dass SQL Server das Erstellen eines XML-Schemas nicht unterstützt, wenn dieses einen gemischten Typ auf einfachen Inhalt beschränkt.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- mixed types [SQL Server]
ms.assetid: 6ea1f11d-e64b-4ebb-ab68-4eb6e4027665
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 990ead43919e80a910860ee15a3758a36e2a1f93
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715126"
---
# <a name="mixed-type-and-simple-content"></a>Mixed-Datentyp und Simple-Inhalt
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt das Beschränken eines mixed-Datentyps auf simple-Inhalt nicht.  
  
## <a name="example"></a>Beispiel  
 In der folgenden XML-Schemaauflistung ist `myComplexTypeA` ein complex-Datentyp, der leer sein kann. Das heißt, bei beiden Elementen wurde `minOccurs` auf 0 festgelegt. Der Versuch, dies wie in der `myComplexTypeB` -Deklaration auf einen einfachen Inhalt zu beschränken, wird nicht unterstützt. Daher schlägt die Erstellung der folgenden XML-Schemaauflistung fehl:  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns" xmlns:ns="http://ns"  
xmlns:ns1="http://ns1">  
  
    <complexType name="myComplexTypeA" mixed="true">  
        <sequence>  
            <element name="a" type="string" minOccurs="0"/>  
            <element name="b" type="string" minOccurs="0" maxOccurs="23"/>  
        </sequence>  
    </complexType>  
  
    <complexType name="myComplexTypeB">  
        <simpleContent>  
            <restriction base="ns:myComplexTypeA">  
                <simpleType>  
                    <restriction base="int">  
                        <minExclusive value="25"/>  
                    </restriction>  
                </simpleType>  
            </restriction>  
        </simpleContent>  
    </complexType>  
</schema>  
'  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anforderungen und Einschränkungen für XML-Schemaauflistungen auf dem Server](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
