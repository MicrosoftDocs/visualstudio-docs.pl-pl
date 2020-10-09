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
ms.openlocfilehash: aa753a4ba3e0254ed7de026653759bbdcfce0631
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862317"
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
 [Obiekt JSON](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON)   
 [JSON. Parse — funkcja](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)   
 [Błędy czasu wykonania JavaScript](/microsoft-edge/devtools-guide/console/error-and-status-codes#javascript-run-time-errors)