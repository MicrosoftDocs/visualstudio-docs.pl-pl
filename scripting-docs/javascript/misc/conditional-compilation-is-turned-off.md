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
ms.openlocfilehash: 91e32971013d2dfcf0ee2dc901d84681522c7e89
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861655"
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
 [Kompilacja warunkowa](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/121hztk3(v=vs.84))   
 [Zmienne kompilacji warunkowej](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/s59bkzce(v=vs.84))   
 [@cc_on Merge](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-cc-on)   
 [@if Merge](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-if)   
 [@set Merge](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-set)