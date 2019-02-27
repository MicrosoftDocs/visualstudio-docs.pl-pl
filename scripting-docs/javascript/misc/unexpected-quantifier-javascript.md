---
title: Nieoczekiwany kwantyfikator (JavaScript) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: f18195f344adca16fce7403d225c42826a2af544
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843406"
---
# <a name="unexpected-quantifier-javascript"></a>Nieoczekiwany kwantyfikator (JavaScript)
Podczas redagowania kryteria wyszukiwania wyrażeń regularnych, utworzono element wzorca z czynnikiem niedozwolony powtórzenia. Na przykład wzorzec  
  
```js
/^+/  
```  
  
 jest niedozwolony ponieważ element ^ (początku danych wejściowych) nie może mieć współczynnik powtórzenia. W poniższej tabeli wymieniono elementy, które nie może być powtórzenie czynników.  
  
|Element|Opis|  
|-------------|-----------------|  
|^|Początku danych wejściowych|  
|$|Koniec danych wejściowych|  
|\b|Granica słowa|  
|\B|Granica wyrazu nie|  
|*|Zero lub więcej powtórzeń|  
|+|Co najmniej powtórzeń|  
|?|Zero lub jeden powtórzeń|  
|{n}|n powtórzeń|  
|{n,}|n lub więcej powtórzeń|  
|{n, m}|Od n do m powtórzeń, (włącznie)|  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że Twoje element wzorzec wyszukiwania zawiera tylko czynniki prawne powtórzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt będący wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](https://msdn.microsoft.com/library/1400241x)