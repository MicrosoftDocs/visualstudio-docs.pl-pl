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
ms.openlocfilehash: e6091968dcbdd98240b1705e0fa7dc855dad3bda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816075"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Identyfikator URI, który ma być zdekodowany, zawiera nieprawidłowy znak.
Próbowano zakodować ciąg jako identyfikator URI (Uniform Resource Identifier), ale zawiera on nieprawidłowe znaki. Chociaż większość znaków jest prawidłowa wewnątrz ciągów do przekonwertowania na identyfikatory URI, niektóre sekwencje znaków Unicode są niedozwolone.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że ciąg, który ma zostać zakodowany, zawiera tylko prawidłowe sekwencje Unicode. Pełny identyfikator URI składa się z sekwencji składników i separatorów. Nazwy w nawiasach kątowych reprezentują składniki, a znaki ":", "/", ";" i "?" są zarezerwowane jako separatory. Formularz ogólny:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [encodeURI, funkcja](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent, funkcja](../../javascript/reference/encodeuricomponent-function-javascript.md)