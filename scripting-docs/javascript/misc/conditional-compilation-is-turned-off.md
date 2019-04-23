---
title: Kompilacja warunkowa jest wyłączona. | Dokumentacja firmy Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8317121b840d82ab12d4a9e1ca50f6680eb1e21d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60051742"
---
# <a name="conditional-compilation-is-turned-off"></a>Kompilacja warunkowa jest wyłączona
Podjęto próbę użycia zmienną kompilacji warunkowej bez pierwszej kompilacji warunkowej zwroty na. Włączanie kompilacji warunkowej informuje [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kompilatorze Interpretowanie identyfikatorów, począwszy od jako zmienne kompilacji warunkowej. Można to zrobić, począwszy od warunkowego kodu za pomocą instrukcji:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Na początku warunkowego kodu, dodaj następującą instrukcję:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilacja warunkowa](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Zmienne kompilacji warunkowej](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on Instrukcja](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if Instrukcja](../../javascript/reference/at-if-statement-javascript.md)   
 [@set, instrukcja](../../javascript/reference/at-set-statement-javascript.md)