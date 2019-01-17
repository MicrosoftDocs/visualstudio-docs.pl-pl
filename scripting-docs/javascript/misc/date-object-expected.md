---
title: Oczekiwany obiekt Date | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05e27b822f933ade811084552f6f0379257ae82e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349117"
---
# <a name="date-object-expected"></a>Oczekiwany obiekt Date
Podjęto próbę wywołania **Date.prototype.toString** lub **Date.prototype.valueOf** metody na obiekt typu innego niż `Date`. Obiekt tego typu wywołania musi być typu `Date`. Na przykład:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Tylko wywołania **Date.prototype.toString** lub **Date.prototype.valueOf** metod obiektów typu `Date`.  
  
## <a name="see-also"></a>Zobacz też  
 [Date — obiekt](../../javascript/reference/date-object-javascript.md)   
 [GETDATE — metoda (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Obiekty wewnętrzne](../../javascript/intrinsic-objects-javascript.md)