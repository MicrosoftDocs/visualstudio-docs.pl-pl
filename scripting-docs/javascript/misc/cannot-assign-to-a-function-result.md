---
title: Nie można przypisać do wyniku funkcji | Dokumentacja firmy Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38cf04b388eaea8ad85f0399978f914feb937c0a
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56844016"
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