---
title: Nie można przypisać do wyniku funkcji | Microsoft Docs
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
ms.openlocfilehash: aca09fe3b516fbb8f27def982bf34a22d33d4ada
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572363"
---
# <a name="cannot-assign-to-a-function-result"></a>Nie można przypisać do wyniku funkcji
Podjęto próbę przypisania wartości do wyniku funkcji. Wynik funkcji można przypisać do zmiennej, ale nie może być używany jako zmienna. Jeśli chcesz przypisać nową wartość do samej funkcji, Pomiń nawiasy (operator wywołania funkcji). Poniższy przykład demonstruje sytuację, w której ten błąd jest generowany.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Nie należy używać wartości wyniku wywołania funkcji jako elementu, do którego można *przypisać*. Wynik wywołania funkcji można przypisać *do zmiennej,* chociaż.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
- Alternatywnie można przypisać do zmiennej samą funkcję (a nie jej wartość zwrotną).  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Zobacz także  
   [obiektu funkcji](../../javascript/reference/function-object-javascript.md)  
 [Pisanie kodu JavaScript](../../javascript/writing-javascript-code.md)   
 [Funkcje](../../javascript/functions-javascript.md)