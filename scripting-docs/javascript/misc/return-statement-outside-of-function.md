---
description: Użyto instrukcji return w globalnym zakresie kodu.
title: Instrukcja "return" poza funkcją | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: c275db9b2b13f6730ef62a757502b1d51a59ee43
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571665"
---
# <a name="return-statement-outside-of-function"></a>Instrukcja „return" poza funkcją
Użyto `return` instrukcji w globalnym zakresie kodu. `return`Instrukcja powinna znajdować się tylko w treści funkcji.  
  
 Wywoływanie funkcji z `()` operatorem jest wyrażeniem. Wszystkie wyrażenia mają wartości; `return` instrukcja służy do określenia wartości zwracanej przez funkcję. Formularz ogólny:  
  
```js
  
return [ expression ];  
```  
  
 Po `return` wykonaniu instrukcji *wyrażenie* jest oceniane i zwracane jako wartość funkcji. Jeśli nie ma wyrażenia, zwracany jest **niezdefiniowany** .  
  
 Wykonywanie funkcji zostaje zatrzymane po `return` wykonaniu instrukcji, nawet jeśli inne instrukcje są nadal pozostawać w treści funkcji. Wyjątkiem od tej reguły jest, czy instrukcja **Return** występuje w bloku **try** , i istnieje odpowiedni blok **finally** , kod w bloku **finally** zostanie wykonany przed zwróceniem funkcji.  
  
 Jeśli funkcja zwraca, ponieważ osiągnie koniec treści funkcji bez wykonywania `return` instrukcji, zwracana wartość jest wartością **niezdefiniowaną** (oznacza to, że wynik funkcji nie może być używany jako część większego wyrażenia).  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Usuń `return` instrukcję z głównej treści kodu (zakres globalny).  
  
## <a name="see-also"></a>Zobacz też  
 [Return — Instrukcja](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/return)   
 [Obiekt Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [caller, właściwość (Function)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/caller)
