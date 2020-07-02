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
ms.openlocfilehash: b7bc7ff09152cd0ce7b95c6de73ea98446529c44
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815529"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Po instrukcji Throw musi występować wyrażenie w tym samym wierszu źródłowym
Użyto `throw` słowa kluczowego, ale nie było ono zgodne z wyrażeniem w tej samej linii źródłowej. `throw`Instrukcja składa się z dwóch części: `throw` słowa kluczowego, po którym następuje wyrażenie, które ma zostać zgłoszone. Przykład:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Nie można podzielić tych dwóch składników w górę.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że `throw` słowo kluczowe i wyrażenie do wyrzucania pojawiają się w tym samym wierszu.  
  
## <a name="see-also"></a>Zobacz także  
 [Obiekt Error](../../javascript/reference/error-object-javascript.md)   
 [throw — instrukcja](../../javascript/reference/throw-statement-javascript.md)   
 [Spróbuj... catch... finally — instrukcja](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)