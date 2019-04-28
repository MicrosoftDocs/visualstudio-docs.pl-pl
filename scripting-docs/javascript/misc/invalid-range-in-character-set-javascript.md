---
title: Nieprawidłowy zakres w znak zestawu (JavaScript) | Dokumentacja firmy Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1cbfa4de401c2a1dc0626f8f00dbb0bd1bf24408
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007051"
---
# <a name="invalid-range-in-character-set-javascript"></a>Nieprawidłowy zakres w zestawie znaków (JavaScript)
Próbowano utworzyć wyrażenia regularnego z ustawionym nieprawidłowy znak. Zestawy znaków musi należeć do zakresu od pojedynczych znaków, np. a-z lub 0-9 nie może zawierać klasy znaków, takich jak \w w zestawie znaków. Pierwszy znak w zakresie również musi występować przed drugim znakiem z zakresu. Na przykład:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Aby utworzyć zestaw znaków z wyrażenia regularnego i upewnij się, że znajdują się w odpowiedniej kolejności, należy użyć tylko pojedyncze znaki.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt będący wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](https://msdn.microsoft.com/library/1400241x)