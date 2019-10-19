---
title: Oczekiwano obiektu modułu wyliczającego | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: d90b6b923f631c7785428a1b3879528e97c1bfd6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572867"
---
# <a name="enumerator-object-expected"></a>Oczekiwano obiektu wyliczenia
Podjęto próbę wywołania metody **Enumerator. prototype. atEnd, Enumerator. prototype. Item, Enumerator. prototype. MoveFirst** lub **Enumerator. prototype. MoveNext** na obiekcie typu innego niż `Enumerator`. Obiekt tego typu wywołania musi być typu `Enumerator`. Oto przykład kodu, który dzieli tę regułę:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Wywołaj metody **Enumerator. prototype. atEnd**, **Enumerator. prototype. Item**, **Enumerator. prototype. MoveFirst**lub **Enumerator. prototype. MoveNext** dla obiektów typu `Enumerator`. Aby dowiedzieć się, czy obiekt jest obiektem `Enumerator`, użyj:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Zobacz także  
 [Enumerator, obiekt](../../javascript/reference/enumerator-object-javascript.md)