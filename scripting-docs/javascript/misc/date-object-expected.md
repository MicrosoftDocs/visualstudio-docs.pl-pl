---
title: Oczekiwany obiekt date | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 969f2bcb578d74ac02a7bdaa6984de5948e49e27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817609"
---
# <a name="date-object-expected"></a>Oczekiwany obiekt Date
Podjęto próbę wywołania metody **Date. prototype. ToString** lub **Date. prototype. valueOf** na obiekcie typu innego niż `Date` . Obiekt tego typu wywołania musi być typu `Date` . Na przykład:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- W obiektach typu należy wywoływać metody **Date. prototype. ToString** lub **Date. prototype. valueOf** `Date` .  
  
## <a name="see-also"></a>Zobacz też  
 [Date — obiekt](../../javascript/reference/date-object-javascript.md)   
 [getDate, Metoda (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Obiekty wewnętrzne](../../javascript/intrinsic-objects-javascript.md)