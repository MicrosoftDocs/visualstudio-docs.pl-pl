---
title: Ciąg oczekiwany | Dokumentacja firmy Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5005
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4c214c4b-9cd7-473b-8d90-2344c0375c25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6853d92608859e41fd7d8001ca6e350f5830504
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087004"
---
# <a name="string-expected"></a>Ciąg oczekiwany
Podjęto próbę wywołania **String.prototype.toString** lub **String.prototype.valueOf** metody na obiekt typu innego niż `String`. Obiekt tego typu wywołania musi być typu `String`.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Tylko wywołania **String.prototype.toString** lub **String.prototype.valueOf** metod obiektów typu `String`.  
  
## <a name="see-also"></a>Zobacz też  
 [String — obiekt](../../javascript/reference/string-object-javascript.md)   
 [toString, metoda (Object)](../../javascript/reference/tostring-method-object-javascript.md)