---
description: Podano obiekt, który nie był Visual Basic safeArray, gdy jest oczekiwany.
title: Oczekiwano VBArray | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e344e24b3fbef7b7f119a36513c222e085328072
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2021
ms.locfileid: "103572081"
---
# <a name="vbarray-expected"></a>Oczekiwano VBArray
Podano obiekt, który nie był Visual Basic safeArray, gdy jest oczekiwany.  
  
```js
new VBArray(safeArray);  
```  
  
 VBArrays są tylko do odczytu i nie można ich utworzyć bezpośrednio. Argument safeArray jest wartością VBArray i musi uzyskać wartość VBArray przed przekazaniem do `VBArray` konstruktora. Można to zrobić tylko przez pobranie wartości z istniejącego ActiveX lub innego obiektu.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że tylko obiekty **VBArray** są przekazywane do konstruktora **VBArray** .  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt VBArray](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/VBArray)   
 [Używanie tablic](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)
