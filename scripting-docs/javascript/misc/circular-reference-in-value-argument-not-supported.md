---
title: Odwołanie cykliczne w argumencie wartości nie jest obsługiwane | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 633ed9c37e8ccde0844205910a8fa2dc12d91414
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817622"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Odwołanie cykliczne w argumencie wartości nie jest obsługiwane
Podjęto próbę wywołania `JSON.stringify` z nieprawidłową wartością. `value`Argument, tablica lub obiekt, zawiera odwołanie cykliczne.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Usuń odwołanie cykliczne z argumentu.  
  
## <a name="example"></a>Przykład  
 Kod w tym przykładzie powoduje błąd w czasie wykonywania, ponieważ `john` ma odwołanie do `mary` i `mary` ma odwołanie do `john` . Aby usunąć odwołanie cykliczne, Usuń lub Wyłącz właściwość `brother` z `mary` obiektu lub `sister` właściwości z `john` obiektu.  
  
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
 [JSON. Parse — funkcja](../../javascript/reference/json-parse-function-javascript.md)   
 [Błędy czasu wykonania JavaScript](../../javascript/reference/javascript-run-time-errors.md)