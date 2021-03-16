---
description: Podczas redagowania wzorca wyszukiwania wyrażeń regularnych został utworzony element wzorca z niedozwolonym czynnikiem powtarzania.
title: Nieoczekiwany kwantyfikator (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9351f9306cea9e3f6346b007d6fe05c1d7bbf319
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571964"
---
# <a name="unexpected-quantifier-javascript"></a>Nieoczekiwany kwantyfikator (JavaScript)
Podczas redagowania wzorca wyszukiwania wyrażeń regularnych został utworzony element wzorca z niedozwolonym czynnikiem powtarzania. Na przykład wzorzec  
  
```js
/^+/  
```  
  
 jest niedozwolony, ponieważ element ^ (początek danych wejściowych) nie może mieć współczynnika powtarzania. Poniższa tabela zawiera listę elementów, których nie można powtórzyć.  
  
|Element|Opis|  
|-------------|-----------------|  
|^|Początek danych wejściowych|  
|$|Koniec danych wejściowych|  
|\b|Granica wyrazu|  
|Stosuje|Granica niebędąca słowem|  
|*|Zero lub więcej powtórzeń|  
|+|Co najmniej jedno powtórzenie|  
|?|Zero lub jedno powtórzenie|  
|Azotan|n powtórzeń|  
|{n,}|n lub więcej powtórzeń|  
|{n, m}|Od n do m powtórzeń, włącznie|  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że element wzorca wyszukiwania zawiera tylko prawne czynniki powtarzania.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt wyrażenia regularnego](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Składnia wyrażenia regularnego (JavaScript)](/previous-versions/1400241x(v=vs.100))
