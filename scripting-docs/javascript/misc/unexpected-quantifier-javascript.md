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
ms.openlocfilehash: f67f9a2fc81b0bd950e171e4274eb09eacd88bbc
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861856"
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