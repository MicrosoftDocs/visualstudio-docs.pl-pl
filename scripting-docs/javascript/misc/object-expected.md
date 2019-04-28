---
title: Oczekiwano obiektu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 501496c4f1bb929308ffbb75c6572de3d3f5b33b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63006369"
---
# <a name="object-expected"></a>Oczekiwany obiekt
Podjęto próbę wywołania metody lub właściwości w obiekcie typu innego niż `Object`, lub przekazany argument typu innego niż `Object` podczas `Object` była wymagana.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Tylko wywołania metody lub właściwości w obiekcie typu `Object`.  
  
- Jeśli wystąpi błąd argumentu-object, należy przekazać obiekt typu `Object`.  
  
- Sprawdź, czy odwołanie do niezdefiniowanej ani mieć wartości null jest wprowadzenie wywoływana zamiast obiektu typu `Object`.  
  
     Na przykład, jeśli ten błąd w myVar w poniższym kodzie:  
  
    ```JavaScript  
    var str = myVar.toString();  
    ```  
  
     Zamiast tego można użyć następującego kodu:  
  
    ```JavaScript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Object — obiekt](../../javascript/reference/object-object-javascript.md)   
 [Obiekty i tablice](../../javascript/objects-and-arrays-javascript.md)