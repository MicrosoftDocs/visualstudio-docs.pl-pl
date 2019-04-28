---
title: Oczekiwano obiektu wyliczenia | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 06005f635e5173e903cfba6a952750d64181d0bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946345"
---
# <a name="enumerator-object-expected"></a>Oczekiwano obiektu wyliczenia
Podjęto próbę wywołania **Enumerator.prototype.atEnd, Enumerator.prototype.item, Enumerator.prototype.moveFirst,** lub **Enumerator.prototype.moveNext** metody na obiekt typu innych niż `Enumerator`. Obiekt tego typu wywołania musi być typu `Enumerator`. Poniżej przedstawiono przykładowy kod, która narusza tę regułę:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Tylko wywołania **Enumerator.prototype.atEnd**, **Enumerator.prototype.item**, **Enumerator.prototype.moveFirst**, lub  **Enumerator.prototype.moveNext** metod obiektów typu `Enumerator`. Aby sprawdzić, czy obiekt jest `Enumerator` obiektu, należy użyć:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Enumerator, obiekt](../../javascript/reference/enumerator-object-javascript.md)