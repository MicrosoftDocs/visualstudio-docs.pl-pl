---
title: Nieprawidłowy argument zastępczy | Dokumentacja firmy Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 640eefb53304de48e4ad2398a02910a1cff1b57d
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841289"
---
# <a name="invalid-replacer-argument"></a>Nieprawidłowy argument zastępczy
Podjęto próbę wywołania `JSON.stringify` z nieprawidłowym argumentem, który jest nieprawidłowy. `replacer` Argument musi być funkcją ani tablicą.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zmiana `replacer` argumentu dla funkcji lub tablicy.  
  
## <a name="example"></a>Przykład  
 Kod, w tym przykładzie powoduje błąd w czasie wykonywania, ponieważ `memberfilter` jest obiektem, zamiast funkcji lub tablicy.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt JSON](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse Function](../../javascript/reference/json-parse-function-javascript.md)   
 [Błędy czasu wykonania JavaScript](../../javascript/reference/javascript-run-time-errors.md)