---
title: Oczekiwano obiektu modułu wyliczającego | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff61894ce808cd33876e876c596e791a3347ab72
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817596"
---
# <a name="enumerator-object-expected"></a>Oczekiwano obiektu wyliczenia
Podjęto próbę wywołania metody **Enumerator. prototype. atEnd, Enumerator. prototype. Item, Enumerator. prototype. MoveFirst** lub **Enumerator. prototype. MoveNext** na obiekcie typu innego niż `Enumerator` . Obiekt tego typu wywołania musi być typu `Enumerator` . Oto przykład kodu, który dzieli tę regułę:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Wywołaj metody **Enumerator. prototype. atEnd**, **Enumerator. prototype. Item**, **Enumerator. prototype. MoveFirst**lub **Enumerator. prototype. MoveNext** dla obiektów typu `Enumerator` . Aby dowiedzieć się, czy obiekt jest `Enumerator` obiektem, użyj:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Zobacz także  
 [Enumerator, obiekt](../../javascript/reference/enumerator-object-javascript.md)