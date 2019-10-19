---
title: Odwołanie cykliczne w argumencie wartości nie jest obsługiwane | Microsoft Docs
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
ms.openlocfilehash: 542fca58778a7b85b3044ce984b6ea049db12509
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572337"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Odwołanie cykliczne w argumencie wartości nie jest obsługiwane
Podjęto próbę wywołania `JSON.stringify` z nieprawidłową wartością. @No__t_0 argument, tablica lub obiekt, zawiera odwołanie cykliczne.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Usuń odwołanie cykliczne z argumentu.  
  
## <a name="example"></a>Przykład  
 Kod w tym przykładzie powoduje błąd środowiska uruchomieniowego, ponieważ `john` ma odwołanie do `mary` i `mary` ma odwołanie do `john`. Aby usunąć odwołanie cykliczne, Usuń lub Wyłącz Właściwość `brother` z obiektu `mary` lub właściwości `sister` z obiektu `john`.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>Zobacz także  
 @No__t_1 [obiektu JSON](../../javascript/reference/json-object-javascript.md)  
 [Funkcja JSON. parse](../../javascript/reference/json-parse-function-javascript.md)    
 [Błędy czasu wykonania JavaScript](../../javascript/reference/javascript-run-time-errors.md)