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
ms.openlocfilehash: 3d3c225df20113308ee7037742ad74efb6a0cc2e
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840357"
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