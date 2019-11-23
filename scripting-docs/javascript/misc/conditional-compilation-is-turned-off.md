---
title: Kompilacja warunkowa jest wyłączona | Microsoft Docs
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
ms.openlocfilehash: 56621d6f7fcc195a4ece7654adeafd1096c37e8b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572940"
---
# <a name="conditional-compilation-is-turned-off"></a>Kompilacja warunkowa jest wyłączona
Podjęto próbę użycia zmiennej kompilacji warunkowej bez wcześniejszego włączenia kompilacji warunkowej. Włączenie kompilacji warunkowej instruuje kompilator [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], aby interpretował identyfikatory zaczynające się od @ jako zmienne kompilacji warunkowej. Można to zrobić, zaczynając od kodu warunkowego za pomocą instrukcji:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj następującą instrukcję na początku kodu warunkowego:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Zobacz także  
   [kompilacji warunkowej](../../javascript/advanced/conditional-compilation-javascript.md)  
 [Zmienne kompilacji warunkowej](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
   [instrukcji@cc_on](../../javascript/reference/at-cc-on-statement-javascript.md)  
   [instrukcji@if](../../javascript/reference/at-if-statement-javascript.md)  
 [@set, instrukcja](../../javascript/reference/at-set-statement-javascript.md)