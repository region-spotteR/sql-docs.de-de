---
description: UpdateRule-Eigenschaft (ADOX)
title: UpdateRule-Eigenschaft (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Key::GetUpdateRule
- _Key::get_UpdateRule
- _Key::PutUpdateRule
- _Key::put_UpdateRule
- _Key::UpdateRule
helpviewer_keywords:
- UpdateRule property [ADOX]
ms.assetid: f4e21060-40cb-4790-8611-4086a092dda2
author: rothja
ms.author: jroth
ms.openlocfilehash: d3113bf5c77dbef03378d2c1359673bf32782f73
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88983041"
---
# <a name="updaterule-property-adox"></a>UpdateRule-Eigenschaft (ADOX)
Gibt die Aktion an, die ausgeführt wird, wenn ein primär [Schlüssel](./key-object-adox.md) aktualisiert wird.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Long** -Wert fest, der eine der [ruleenum](./ruleenum.md) -Konstanten sein kann, und gibt diesen zurück. Der Standardwert ist **adrinone**.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Eigenschaft ist bei [Schlüssel](./key-object-adox.md) Objekten, die bereits an die Auflistung angehängt wurden, schreibgeschützt.  
  
## <a name="applies-to"></a>Gilt für  
 [Key-Objekt (ADOX)](./key-object-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Append-Methode für Schlüssel, Key Type-, RelatedColumn-, RelatedTable- und UpdateRule-Eigenschaften – Beispiel (VB)](./keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)