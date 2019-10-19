---
title: Po elemencie throw musi następować wyrażenie w tym samym wierszu źródłowym | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 8854acb3d1992283899c4ff095f5d754c05f55a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572750"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Po instrukcji Throw musi występować wyrażenie w tym samym wierszu źródłowym
Użyto słowa kluczowego `throw`, ale nie jest ono zgodne z wyrażeniem w tym samym wierszu źródłowym. Instrukcja `throw` składa się z dwóch części: słowa kluczowego `throw`, po którym następuje wyrażenie, które ma zostać zgłoszone. Na przykład:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Nie można podzielić tych dwóch składników w górę.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że słowo kluczowe `throw` i wyrażenie do wyrzucania pojawiają się w tym samym wierszu.  
  
## <a name="see-also"></a>Zobacz także  
 [Błąd   obiektu](../../javascript/reference/error-object-javascript.md)  
 [zgłoś   instrukcji](../../javascript/reference/throw-statement-javascript.md)  
 [Try...Catch...Finally, instrukcja](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)