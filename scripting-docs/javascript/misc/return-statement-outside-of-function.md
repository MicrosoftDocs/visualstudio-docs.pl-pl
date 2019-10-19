---
title: Instrukcja "return" poza funkcją | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a90af6de8e2c238e3660111b19d13c1eaf628c9e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573687"
---
# <a name="return-statement-outside-of-function"></a>Instrukcja „return" poza funkcją
Użyto instrukcji `return` w globalnym zakresie kodu. Instrukcja `return` powinna występować tylko w treści funkcji.  
  
 Wywoływanie funkcji z operatorem `()` jest wyrażeniem. Wszystkie wyrażenia mają wartości; Instrukcja `return` służy do określania wartości zwracanej przez funkcję. Formularz ogólny:  
  
```js
  
return [ expression ];  
```  
  
 Po wykonaniu instrukcji `return` *wyrażenie* jest oceniane i zwracane jako wartość funkcji. Jeśli nie ma wyrażenia, zwracany jest **niezdefiniowany** .  
  
 Wykonywanie funkcji zostaje zatrzymane po wykonaniu instrukcji `return`, nawet jeśli inne instrukcje nadal pozostają w treści funkcji. Wyjątkiem od tej reguły jest, czy instrukcja **Return** występuje w bloku **try** , i istnieje odpowiedni blok **finally** , kod w bloku **finally** zostanie wykonany przed zwróceniem funkcji.  
  
 Jeśli funkcja zwraca, ponieważ dociera do końca treści funkcji bez wykonywania instrukcji `return`, zwracana wartość jest wartością **niezdefiniowaną** (oznacza to, że wynik funkcji nie może być używany jako część większego wyrażenia).  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Usuń instrukcję `return` z głównej treści kodu (zakres globalny).  
  
## <a name="see-also"></a>Zobacz także  
 [Return — instrukcja](../../javascript/reference/return-statement-javascript.md)    
 @No__t_1 [obiektu funkcji](../../javascript/reference/function-object-javascript.md)  
 [caller, właściwość (Function)](../../javascript/reference/caller-property-function-javascript.md)