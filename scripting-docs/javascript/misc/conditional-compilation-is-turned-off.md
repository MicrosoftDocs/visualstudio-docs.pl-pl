---
title: Kompilacja warunkowa jest wyłączona. | Dokumentacja firmy Microsoft
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
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bcbf844ced2bb74ddfea9bd62d68877b7a3c969c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347349"
---
# <a name="conditional-compilation-is-turned-off"></a>Kompilacja warunkowa jest wyłączona
Podjęto próbę użycia zmienną kompilacji warunkowej bez pierwszej kompilacji warunkowej zwroty na. Włączanie kompilacji warunkowej informuje [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kompilatorze Interpretowanie identyfikatorów, począwszy od jako zmienne kompilacji warunkowej. Można to zrobić, począwszy od warunkowego kodu za pomocą instrukcji:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Na początku warunkowego kodu, dodaj następującą instrukcję:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilacja warunkowa](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Zmienne kompilacji warunkowej](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on Instrukcja](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if Instrukcja](../../javascript/reference/at-if-statement-javascript.md)   
 [@set, instrukcja](../../javascript/reference/at-set-statement-javascript.md)