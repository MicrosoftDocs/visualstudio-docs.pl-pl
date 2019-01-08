---
title: Nie można przypisać do wyniku funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a29c3f20392dc216c0306137c0dec6b22aaa58a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093864"
---
# <a name="cannot-assign-to-a-function-result"></a>Nie można przypisać do wyniku funkcji
Nastąpiła próba przypisania wartości do wyniku funkcji. Wynik funkcji można przypisać do zmiennej, ale nie można użyć jako zmienną. Jeśli chcesz przypisać nową wartość do samej funkcji, należy pominąć nawiasów (operator wywołania funkcji). W poniższym przykładzie pokazano sytuację, w którym ten błąd jest generowany.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Nie używaj wartość wyniku wywołania funkcji jako coś, co możesz *przypisać*. Wynik wywołania funkcji można przypisać *ze zmienną* chociaż.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
-   Alternatywnie można przypisać funkcja sam (a nie jej wartość zwracana) do zmiennej.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Function — obiekt](../../javascript/reference/function-object-javascript.md)   
 [Pisanie kodu JavaScript](../../javascript/writing-javascript-code.md)   
 [Funkcje](../../javascript/functions-javascript.md)