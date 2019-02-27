---
title: Odwołanie cykliczne w argumencie wartości nie jest obsługiwane. | Dokumentacja firmy Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5034
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1235c8b1bb7b815b5f26e0ffb744c31a3575ba81
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841094"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Odwołanie cykliczne w argumencie wartości nie jest obsługiwane
Podjęto próbę wywołania `JSON.stringify` z wartością, która jest nieprawidłowa. `value` Argumentów, tablicę lub obiekt, zawiera odwołanie cykliczne.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń odwołanie cykliczne w argumencie.  
  
## <a name="example"></a>Przykład  
 Kod, w tym przykładzie powoduje błąd w czasie wykonywania, ponieważ `john` odwołuje się do `mary` i `mary` odwołuje się do `john`. Aby usunąć odwołanie cykliczne, usunąć lub nie ustawiono właściwości `brother` z `mary` obiektu lub `sister` właściwość `john` obiektu.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt JSON](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse Function](../../javascript/reference/json-parse-function-javascript.md)   
 [Błędy czasu wykonania JavaScript](../../javascript/reference/javascript-run-time-errors.md)