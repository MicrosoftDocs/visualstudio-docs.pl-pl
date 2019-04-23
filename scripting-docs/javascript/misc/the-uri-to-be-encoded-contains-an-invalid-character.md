---
title: Identyfikator URI, który ma być zdekodowany, zawiera nieprawidłowy znak | Dokumentacja firmy Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: f2f9111acf656bf882a3d506fe95b8361f3693ff
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053405"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Identyfikator URI, który ma być zdekodowany, zawiera nieprawidłowy znak.
Próbowano przeprowadzić kodowanie ciągu jako identyfikator URI (Uniform Resource Identifier), ale zawiera nieprawidłowe znaki. Mimo że większość znaki są prawidłowe wewnątrz ciągi są konwertowane na identyfikatory URI, niektóre sekwencje znaków Unicode są niedozwolone.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że ciąg do zakodowania zawiera tylko prawidłowe sekwencje Unicode. Pełny identyfikator URI składa się z sekwencji składników i separatorów. Nazwy w nawiasy ostre oznaczają składniki z i ":", "/", ";" i "?" są używane jako separatory znaków zastrzeżonych. Ogólna postać jest:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [encodeURI — funkcja](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent, funkcja](../../javascript/reference/encodeuricomponent-function-javascript.md)