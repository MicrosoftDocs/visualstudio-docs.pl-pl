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
ms.openlocfilehash: a3c71b90d0711bf317d0ed72d51c0d5d45297c80
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841873"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Identyfikator URI, który ma być zdekodowany, zawiera nieprawidłowy znak.
Próbowano przeprowadzić kodowanie ciągu jako identyfikator URI (Uniform Resource Identifier), ale zawiera nieprawidłowe znaki. Mimo że większość znaki są prawidłowe wewnątrz ciągi są konwertowane na identyfikatory URI, niektóre sekwencje znaków Unicode są niedozwolone.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że ciąg do zakodowania zawiera tylko prawidłowe sekwencje Unicode. Pełny identyfikator URI składa się z sekwencji składników i separatorów. Nazwy w nawiasy ostre oznaczają składniki z i ":", "/", ";" i "?" są używane jako separatory znaków zastrzeżonych. Ogólna postać jest:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [encodeURI — funkcja](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent, funkcja](../../javascript/reference/encodeuricomponent-function-javascript.md)