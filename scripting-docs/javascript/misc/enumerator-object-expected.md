---
description: Podjęto próbę wywołania metody Enumerator. prototype. atEnd, Enumerator. prototype. Item, Enumerator. prototype. moveFirst lub Enumerator. prototype. moveNext na obiekcie typu innego niż moduł wyliczający.
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
ms.openlocfilehash: 9fc48ca3e0f17d97af3d538033c2319538afc079
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571054"
---
# <a name="enumerator-object-expected"></a>Oczekiwano obiektu wyliczenia
Podjęto próbę wywołania metody **Enumerator. prototype. atEnd, Enumerator. prototype. Item, Enumerator. prototype. MoveFirst** lub **Enumerator. prototype. MoveNext** na obiekcie typu innego niż `Enumerator` . Obiekt tego typu wywołania musi być typu `Enumerator` . Oto przykład kodu, który dzieli tę regułę:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Wywołaj metody **Enumerator. prototype. atEnd**, **Enumerator. prototype. Item**, **Enumerator. prototype. MoveFirst** lub **Enumerator. prototype. MoveNext** dla obiektów typu `Enumerator` . Aby dowiedzieć się, czy obiekt jest `Enumerator` obiektem, użyj:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Enumerator, obiekt](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/Enumerator)
