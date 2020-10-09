---
title: Nieprawidłowy zakres w zestawie znaków (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 12624d1a0256360ef1e4538a14100923c7de8af8
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862573"
---
# <a name="invalid-range-in-character-set-javascript"></a>Nieprawidłowy zakres w zestawie znaków (JavaScript)
Podjęto próbę utworzenia wyrażenia regularnego z nieprawidłowym zakresem zestawu znaków. Zestawy znaków muszą mieć zakres tylko z pojedynczych znaków, takich jak a-z lub 0-9; nie można dołączać klas znaków, takich jak \w, w zestawie znaków. Pierwszy znak w zakresie musi również występować przed drugim znakiem z zakresu. Na przykład:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Używaj tylko pojedynczych znaków do redagowania zestawu znaków wyrażenia regularnego i upewnij się, że znajdują się one w odpowiedniej kolejności.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt wyrażenia regularnego](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Składnia wyrażenia regularnego (JavaScript)](/previous-versions/1400241x(v=vs.100))