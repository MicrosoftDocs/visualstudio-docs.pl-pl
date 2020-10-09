---
title: Oczekiwano obiektu wyrażenia regularnego | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 370e5a8028bae0e60c265ba65dca12668e4b8d8c
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862058"
---
# <a name="regular-expression-object-expected"></a>Oczekiwano obiektu będącego wyrażeniem regularnym
Podjęto próbę wywołania metody **RegExp. prototype. ToString** lub **RegExp. prototype. valueOf** na obiekcie typu innego niż `RegExp` . Obiekt tego typu wywołania musi być typu `RegExp` .  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Wywołaj metody **RegExp. prototype. ToString** lub **RegExp. prototype. valueOf** na obiektach typu `RegExp` .  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt wyrażenia regularnego](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Składnia wyrażenia regularnego (JavaScript)](/previous-versions/1400241x(v=vs.100))