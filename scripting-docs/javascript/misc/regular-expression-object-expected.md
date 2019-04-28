---
title: Oczekiwano obiektu będącego wyrażeniem regularnym | Dokumentacja firmy Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a42cf4b76f4de6d4170f7ef85dafc00841964cfc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63006425"
---
# <a name="regular-expression-object-expected"></a>Oczekiwano obiektu będącego wyrażeniem regularnym
Podjęto próbę wywołania **RegExp.prototype.toString** lub **RegExp.prototype.valueOf** metody na obiekt typu innego niż `RegExp`. Obiekt tego typu wywołania musi być typu `RegExp`.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Tylko wywołania **RegExp.prototype.toString** lub **RegExp.prototype.valueOf** metod obiektów typu `RegExp`.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt będący wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](https://msdn.microsoft.com/library/1400241x)