---
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
ms.openlocfilehash: da4ff08ae667b868670364c7ad6b9a6b69ae6ad3
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815334"
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
  
## <a name="see-also"></a>Zobacz także  
 [Obiekt wyrażenia regularnego](../../javascript/reference/regular-expression-object-javascript.md)   
 [Składnia wyrażenia regularnego (JavaScript)](https://msdn.microsoft.com/library/1400241x)