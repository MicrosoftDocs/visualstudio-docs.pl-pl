---
title: Throw musi występować wyrażenie w tym samym wierszu źródłowym | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 4c8ed951fb30b84f114f8f44a60e94b88f0f1d0f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069526"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Po instrukcji Throw musi występować wyrażenie w tym samym wierszu źródłowym
Użyte `throw` — słowo kluczowe, ale nie korzystał z go za pomocą wyrażenia w tym samym wierszu źródłowym. A `throw` instrukcji składa się z dwóch części: `throw` — słowo kluczowe, a następnie wyrażenie które ma zostać wygenerowany. Na przykład:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Te dwa składniki nie można podzielić.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że `throw` — słowo kluczowe i wyrażenie które ma zostać wygenerowany pojawia się na tym samym wierszu.  
  
## <a name="see-also"></a>Zobacz też  
 [Error — obiekt](../../javascript/reference/error-object-javascript.md)   
 [Throw — instrukcja](../../javascript/reference/throw-statement-javascript.md)   
 [Try...Catch...Finally, instrukcja](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)