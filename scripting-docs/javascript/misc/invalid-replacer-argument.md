---
description: Podjęto próbę wywołania metody JSON. stringify z nieprawidłowym argumentem.
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
ms.openlocfilehash: 95a73d6fcbcf1350eece52e2cd58693646617a28
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570898"
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
 [Obiekt JSON](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON)   
 [JSON. Parse — funkcja](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)   
 [Błędy czasu wykonania JavaScript](/microsoft-edge/devtools-guide/console/error-and-status-codes#javascript-run-time-errors)
