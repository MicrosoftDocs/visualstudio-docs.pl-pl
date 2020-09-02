---
title: Nieprawidłowy argument zastępczy | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 452af60c37e4a56996438cc2957e9b69ccee98ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816829"
---
# <a name="invalid-replacer-argument"></a>Nieprawidłowy argument zastępczy
Podjęto próbę wywołania `JSON.stringify` z nieprawidłowym argumentem. `replacer`Argument musi być funkcją lub tablicą.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Zmień `replacer` argument na funkcję lub tablicę.  
  
## <a name="example"></a>Przykład  
 Kod w tym przykładzie powoduje błąd środowiska uruchomieniowego, ponieważ `memberfilter` jest obiektem, a nie funkcją lub tablicą.  
  
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
 [JSON. Parse — funkcja](../../javascript/reference/json-parse-function-javascript.md)   
 [Błędy czasu wykonania JavaScript](../../javascript/reference/javascript-run-time-errors.md)