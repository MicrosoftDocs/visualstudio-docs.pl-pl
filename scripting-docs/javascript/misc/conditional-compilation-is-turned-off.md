---
title: Kompilacja warunkowa jest wyłączona | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: da272529768f3227ce6e0ee3e0ebbf086140dd15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816127"
---
# <a name="conditional-compilation-is-turned-off"></a>Kompilacja warunkowa jest wyłączona
Podjęto próbę użycia zmiennej kompilacji warunkowej bez wcześniejszego włączenia kompilacji warunkowej. Włączenie kompilacji warunkowej instruuje [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kompilator, aby interpretował identyfikatory zaczynające się od @ jako zmienne kompilacji warunkowej. Można to zrobić, zaczynając od kodu warunkowego za pomocą instrukcji:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj następującą instrukcję na początku kodu warunkowego:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilacja warunkowa](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Zmienne kompilacji warunkowej](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on Merge](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if Merge](../../javascript/reference/at-if-statement-javascript.md)   
 [@set Merge](../../javascript/reference/at-set-statement-javascript.md)