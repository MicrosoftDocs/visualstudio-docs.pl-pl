---
title: Oczekiwany obiekt Date | Dokumentacja firmy Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2767ffc16b637c6b1e7bdf51cb0815d71f58edac
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050521"
---
# <a name="date-object-expected"></a>Oczekiwany obiekt Date
Podjęto próbę wywołania **Date.prototype.toString** lub **Date.prototype.valueOf** metody na obiekt typu innego niż `Date`. Obiekt tego typu wywołania musi być typu `Date`. Na przykład:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Tylko wywołania **Date.prototype.toString** lub **Date.prototype.valueOf** metod obiektów typu `Date`.  
  
## <a name="see-also"></a>Zobacz też  
 [Date — obiekt](../../javascript/reference/date-object-javascript.md)   
 [GETDATE — metoda (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Obiekty wewnętrzne](../../javascript/intrinsic-objects-javascript.md)