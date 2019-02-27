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
ms.openlocfilehash: eb942fcdbf475984766af44ada75072df1c2facb
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56844003"
---
# <a name="string-expected"></a>Ciąg oczekiwany
Podjęto próbę wywołania **String.prototype.toString** lub **String.prototype.valueOf** metody na obiekt typu innego niż `String`. Obiekt tego typu wywołania musi być typu `String`.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Tylko wywołania **String.prototype.toString** lub **String.prototype.valueOf** metod obiektów typu `String`.  
  
## <a name="see-also"></a>Zobacz też  
 [String — obiekt](../../javascript/reference/string-object-javascript.md)   
 [toString, metoda (Object)](../../javascript/reference/tostring-method-object-javascript.md)