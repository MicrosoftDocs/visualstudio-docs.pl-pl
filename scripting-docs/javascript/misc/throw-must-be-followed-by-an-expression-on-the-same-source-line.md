---
description: Użyto słowa kluczowego throw, ale nie jest ono zgodne z wyrażeniem w tym samym wierszu źródłowym.
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
ms.openlocfilehash: cfa2bace6f82ae972204cc0a405cc7e8682e98af
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570716"
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
