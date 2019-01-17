---
title: Ciąg oczekiwany | Dokumentacja firmy Microsoft
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
- VS.WebClient.Help.SCRIPT5005
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4c214c4b-9cd7-473b-8d90-2344c0375c25
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2dabf754b2bfb4b20555b41457df04d54a5c31c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346803"
---
# <a name="string-expected"></a>Ciąg oczekiwany
Podjęto próbę wywołania **String.prototype.toString** lub **String.prototype.valueOf** metody na obiekt typu innego niż `String`. Obiekt tego typu wywołania musi być typu `String`.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Tylko wywołania **String.prototype.toString** lub **String.prototype.valueOf** metod obiektów typu `String`.  
  
## <a name="see-also"></a>Zobacz też  
 [String — obiekt](../../javascript/reference/string-object-javascript.md)   
 [toString, metoda (Object)](../../javascript/reference/tostring-method-object-javascript.md)