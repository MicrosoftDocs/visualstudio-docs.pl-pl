---
title: Po elemencie throw musi następować wyrażenie w tym samym wierszu źródłowym | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1ce004eb523497b912e8d7ec29c3b03044f0220
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861998"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Po instrukcji Throw musi występować wyrażenie w tym samym wierszu źródłowym
Użyto `throw` słowa kluczowego, ale nie było ono zgodne z wyrażeniem w tej samej linii źródłowej. `throw`Instrukcja składa się z dwóch części: `throw` słowa kluczowego, po którym następuje wyrażenie, które ma zostać zgłoszone. Na przykład:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Nie można podzielić tych dwóch składników w górę.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że `throw` słowo kluczowe i wyrażenie do wyrzucania pojawiają się w tym samym wierszu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt Error](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [throw — instrukcja](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [Spróbuj... catch... finally — instrukcja](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)