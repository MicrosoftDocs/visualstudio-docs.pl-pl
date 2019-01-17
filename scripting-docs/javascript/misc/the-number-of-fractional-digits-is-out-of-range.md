---
title: Liczba cyfr ułamkowych jest poza zakresem | Dokumentacja firmy Microsoft
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
- VS.WebClient.Help.SCRIPT5026
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dbe05d7d-fcf6-4823-9c61-4b814d1ad3c4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17ffec5e6b4cfff85b49f61e7105ca8ce3d75c78
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348467"
---
# <a name="the-number-of-fractional-digits-is-out-of-range"></a>Liczba cyfr ułamkowych jest poza zakresem
Próba przekazania nieprawidłowy argument do funkcji **Number.prototype.toExponential**. Argument do funkcji **toExponential()** musi należeć do zakresu od 0 do 20 (włącznie).  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, argument **toExponential()** nie jest zbyt duży lub za mały.  
  
## <a name="see-also"></a>Zobacz też  
 [toExponential, metoda (Number)](../../javascript/reference/toexponential-method-number-javascript.md)