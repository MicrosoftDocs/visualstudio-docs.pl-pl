---
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
ms.openlocfilehash: 09ab257e6c473e2747a24559200e7b1f432d5687
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815282"
---
# <a name="vbarray-expected"></a>Oczekiwano VBArray
Podano obiekt, który nie był Visual Basic safeArray, gdy jest oczekiwany.  
  
```js
new VBArray(safeArray);  
```  
  
 VBArrays są tylko do odczytu i nie można ich utworzyć bezpośrednio. Argument safeArray jest wartością VBArray i musi uzyskać wartość VBArray przed przekazaniem do `VBArray` konstruktora. Można to zrobić tylko przez pobranie wartości z istniejącego ActiveX lub innego obiektu.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że tylko obiekty **VBArray** są przekazywane do konstruktora **VBArray** .  
  
## <a name="see-also"></a>Zobacz także  
 [Obiekt VBArray](../../javascript/reference/vbarray-object-javascript.md)   
 [Używanie tablic](../../javascript/advanced/using-arrays-javascript.md)