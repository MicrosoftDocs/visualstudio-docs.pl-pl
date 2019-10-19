---
title: Oczekiwana funkcja | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 988ca00613d3dec4c55309fd77bc43705a6038ae
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576591"
---
# <a name="function-expected"></a>Oczekiwana funkcja
Podjęto próbę wywołania jednej z metod **prototypu funkcji** na obiekcie, który nie jest obiektem `Function` lub użyto obiektu w kontekście wywołania funkcji. Na przykład poniższy kod generuje ten błąd, ponieważ **przykład** nie jest funkcją.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Metodę **prototypu funkcji** należy wywoływać tylko w obiektach `Function`.  
  
- Upewnij się, że używasz operatora wywołania funkcji `()`, aby wywoływać tylko funkcje.  
  
## <a name="see-also"></a>Zobacz także  
 @No__t_1 [obiektu funkcji](../../javascript/reference/function-object-javascript.md)  
 [prototype, właściwość (Object)](../../javascript/reference/prototype-property-object-javascript.md)