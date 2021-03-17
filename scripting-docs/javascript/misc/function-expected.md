---
description: Podjęto próbę wywołania jednej z metod prototypu funkcji na obiekcie, który nie jest obiektem funkcji, lub użyto obiektu w kontekście wywołania funkcji.
title: Oczekiwana funkcja | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 99e354118844d7e57f708cf3f2d5653ee1c0fc65
ms.sourcegitcommit: 3a855d3513407ea78336386dc3be0b75142614b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2021
ms.locfileid: "103622611"
---
# <a name="function-expected"></a>Oczekiwana funkcja
Podjęto próbę wywołania jednej z metod **prototypu funkcji** na obiekcie, który nie jest `Function` obiektem, lub użyto obiektu w kontekście wywołania funkcji. Na przykład poniższy kod generuje ten błąd, ponieważ **przykład** nie jest funkcją.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Metody **prototypu funkcji** należy wywoływać tylko dla `Function` obiektów.  
  
- Upewnij się, że używasz operatora wywołania funkcji `()` tylko do wywoływania funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [prototype, właściwość (Object)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)
