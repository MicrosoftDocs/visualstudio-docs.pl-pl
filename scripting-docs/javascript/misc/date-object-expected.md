---
description: Podjęto próbę wywołania metody Date. prototype. toString lub Date. prototype. valueOf na obiekcie typu innego niż data.
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
ms.openlocfilehash: 171514ae180c2e9b24e8aee56a23c47a909bd152
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571093"
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
 [Date — obiekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date)   
 [getDate, Metoda (Date)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date/getdate)   
 [Obiekty wewnętrzne](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)
