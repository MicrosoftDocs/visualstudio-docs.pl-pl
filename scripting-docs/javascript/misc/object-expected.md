---
title: Oczekiwany obiekt | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 1611596d844d43ef72663154dc48791830dfe29f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573734"
---
# <a name="object-expected"></a>Oczekiwany obiekt
Podjęto próbę wywołania metody lub właściwości obiektu typu innego niż `Object`lub przekazano argument typu innego niż `Object`, gdy `Object` była wymagana.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Należy wywołać metodę lub właściwość obiektów typu `Object`.  
  
- Jeśli wystąpi błąd dla argumentu niebędącego obiektem, należy przekazać obiekt typu `Object`.  
  
- Sprawdź, czy odwołanie do niezdefiniowanego lub wartości null jest wywoływane, zamiast obiektu typu `Object`.  
  
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
 [Obiekt obiektu ](../../javascript/reference/object-object-javascript.md)  
 [Obiekty i tablice](../../javascript/objects-and-arrays-javascript.md)