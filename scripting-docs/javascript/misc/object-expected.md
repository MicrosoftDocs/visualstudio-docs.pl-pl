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
ms.openlocfilehash: 28eec125914f0207fbdf79a39ea2140dd74d6d0d
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816231"
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
  
## <a name="see-also"></a>Zobacz także  
 [Object — obiekt](../../javascript/reference/object-object-javascript.md)   
 [Obiekty i tablice](../../javascript/objects-and-arrays-javascript.md)