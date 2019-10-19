---
title: Nieoczekiwany kwantyfikator (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 2070ec6ad01eb62c6be9b6b9acfc91cba7bc863d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572534"
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
 @No__t_1 [obiektu wyrażenia regularnego](../../javascript/reference/regular-expression-object-javascript.md)  
 [Składnia wyrażenia regularnego (JavaScript)](https://msdn.microsoft.com/library/1400241x)