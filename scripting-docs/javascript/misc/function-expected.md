---
title: Oczekiwana funkcja | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 41d1ecc982dcdc4d494fc167e4784e9121bec15e
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843938"
---
# <a name="function-expected"></a>Oczekiwana funkcja
Albo próbowałeś wywołać za pomocą jednego z **prototypu funkcji** metody na obiekt, który nie był `Function` obiektu lub możesz użyć obiektu w kontekście wywołań funkcji. Na przykład, poniższy kod generuje ten błąd, ponieważ **przykład** nie jest funkcją.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Wywoływać tylko **prototypu funkcji** metod `Function` obiektów.  
  
-   Upewnij się, że używasz operatora wywołania funkcji `()` wywołać tylko funkcje.  
  
## <a name="see-also"></a>Zobacz też  
 [Function — obiekt](../../javascript/reference/function-object-javascript.md)   
 [prototype, właściwość (Object)](../../javascript/reference/prototype-property-object-javascript.md)