---
title: Oczekiwany obiekt date | Microsoft Docs
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
ms.openlocfilehash: 10af48c4804df3b5513df71578b948abe73ff8c2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572900"
---
# <a name="date-object-expected"></a>Oczekiwany obiekt Date
Podjęto próbę wywołania metody **Date. prototype. ToString** lub **Date. prototype. valueOf** na obiekcie typu innego niż `Date`. Obiekt tego typu wywołania musi być typu `Date`. Na przykład:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Wywołaj metody **Date. prototype. ToString** lub **Date. prototype. valueOf** na obiektach typu `Date`.  
  
## <a name="see-also"></a>Zobacz także  
   [obiektu Date](../../javascript/reference/date-object-javascript.md)  
 [getDate, Metoda (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Obiekty wewnętrzne](../../javascript/intrinsic-objects-javascript.md)