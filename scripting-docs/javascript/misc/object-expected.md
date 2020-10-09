---
title: Oczekiwany obiekt | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a3b8510c92e15a5b1bf5e15bb774ba031f7181f
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862115"
---
# <a name="object-expected"></a>Oczekiwany obiekt
Podjęto próbę wywołania metody lub właściwości obiektu typu innego niż `Object` lub przekazano argument typu innego niż, `Object` gdy `Object` jest to wymagane.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Wywołaj metodę lub właściwość tylko dla obiektów typu `Object` .  
  
- Jeśli wystąpi błąd dla argumentu niebędącego obiektem, należy przekazać obiekt typu `Object` .  
  
- Sprawdź, czy odwołanie do niezdefiniowanego lub wartości null jest wywoływane, zamiast obiektu typu `Object` .  
  
     Na przykład, jeśli ten błąd wystąpi na MojaZmienna w poniższym kodzie:  
  
    ```JavaScript  
    var str = myVar.toString();  
    ```  
  
     Możesz użyć tego kodu zamiast:  
  
    ```JavaScript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Object — obiekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)   
 [Obiekty i tablice](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)