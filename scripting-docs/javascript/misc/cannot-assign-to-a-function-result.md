---
description: Podjęto próbę przypisania wartości do wyniku funkcji.
title: Nie można przypisać do wyniku funkcji | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 125d2dc7d41b1b65027952e4e6cb94ff97083e6e
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571925"
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
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [Pisanie kodu JavaScript](https://developer.mozilla.org/docs/Learn/Getting_started_with_the_web/JavaScript_basics)   
 [Funkcje](https://developer.mozilla.org/docs/Learn/JavaScript/Building_blocks/Functions)
