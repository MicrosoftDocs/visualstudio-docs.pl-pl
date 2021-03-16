---
description: Podjęto próbę wywołania metody lub właściwości obiektu typu innego niż Object lub przekazano argument typu innego niż Object, gdy wymagany jest obiekt.
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
ms.openlocfilehash: a62a68b8dd5289794086dad6858238db6cc4f449
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2021
ms.locfileid: "103572068"
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
