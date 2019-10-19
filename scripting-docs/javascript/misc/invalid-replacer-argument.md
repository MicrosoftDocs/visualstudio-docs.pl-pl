---
title: Nieprawidłowy argument zastępczy | Microsoft Docs
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
ms.openlocfilehash: 9ba76a2121dfb3853e38bacbdf49c985103c2a35
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573806"
---
# <a name="invalid-replacer-argument"></a>Nieprawidłowy argument zastępczy
Podjęto próbę wywołania `JSON.stringify` z nieprawidłowym argumentem. Argument `replacer` musi być funkcją lub tablicą.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Zmień argument `replacer` na funkcję lub tablicę.  
  
## <a name="example"></a>Przykład  
 Kod w tym przykładzie powoduje błąd w czasie wykonywania, ponieważ `memberfilter` jest obiektem, a nie funkcją lub tablicą.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>Zobacz także  
 @No__t_1 [obiektu JSON](../../javascript/reference/json-object-javascript.md)  
 [Funkcja JSON. parse](../../javascript/reference/json-parse-function-javascript.md)    
 [Błędy czasu wykonania JavaScript](../../javascript/reference/javascript-run-time-errors.md)