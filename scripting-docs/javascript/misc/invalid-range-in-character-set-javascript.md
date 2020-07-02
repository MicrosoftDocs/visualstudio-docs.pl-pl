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
ms.openlocfilehash: a81634a96fb85584c9176db8c72bfc5c3468dc2c
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816881"
---
# <a name="invalid-range-in-character-set-javascript"></a>Nieprawidłowy zakres w zestawie znaków (JavaScript)
Podjęto próbę utworzenia wyrażenia regularnego z nieprawidłowym zakresem zestawu znaków. Zestawy znaków muszą mieć zakres tylko z pojedynczych znaków, takich jak a-z lub 0-9; nie można dołączać klas znaków, takich jak \w, w zestawie znaków. Pierwszy znak w zakresie musi również występować przed drugim znakiem z zakresu. Przykład:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Używaj tylko pojedynczych znaków do redagowania zestawu znaków wyrażenia regularnego i upewnij się, że znajdują się one w odpowiedniej kolejności.  
  
## <a name="see-also"></a>Zobacz także  
 [Obiekt wyrażenia regularnego](../../javascript/reference/regular-expression-object-javascript.md)   
 [Składnia wyrażenia regularnego (JavaScript)](https://msdn.microsoft.com/library/1400241x)