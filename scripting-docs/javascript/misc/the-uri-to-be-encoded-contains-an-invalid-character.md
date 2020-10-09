---
title: Identyfikator URI, który ma zostać zakodowany, zawiera nieprawidłowy znak | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 310db785041de0beb0ebbba0cdd9b7c356397bc4
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862382"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Identyfikator URI, który ma być zdekodowany, zawiera nieprawidłowy znak.
Próbowano zakodować ciąg jako identyfikator URI (Uniform Resource Identifier), ale zawiera on nieprawidłowe znaki. Chociaż większość znaków jest prawidłowa wewnątrz ciągów do przekonwertowania na identyfikatory URI, niektóre sekwencje znaków Unicode są niedozwolone.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że ciąg, który ma zostać zakodowany, zawiera tylko prawidłowe sekwencje Unicode. Pełny identyfikator URI składa się z sekwencji składników i separatorów. Nazwy w nawiasach kątowych reprezentują składniki, a znaki ":", "/", ";" i "?" są zarezerwowane jako separatory. Formularz ogólny:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [encodeURI, funkcja](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/encodeuri)   
 [encodeURIComponent, funkcja](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/encodeuricomponent)