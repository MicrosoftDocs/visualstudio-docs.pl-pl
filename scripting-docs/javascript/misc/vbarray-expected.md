---
title: Oczekiwano VBArray | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 467a6ec6ca45f2ea0411e0266163ca23a9e3d594
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572506"
---
# <a name="vbarray-expected"></a>Oczekiwano VBArray
Podano obiekt, który nie był Visual Basic safeArray, gdy jest oczekiwany.  
  
```js
new VBArray(safeArray);  
```  
  
 VBArrays są tylko do odczytu i nie można ich utworzyć bezpośrednio. Argument safeArray jest wartością VBArray i musi uzyskać wartość VBArray przed przekazaniem do konstruktora `VBArray`. Można to zrobić tylko przez pobranie wartości z istniejącego ActiveX lub innego obiektu.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że tylko obiekty **VBArray** są przekazywane do konstruktora **VBArray** .  
  
## <a name="see-also"></a>Zobacz także  
 @No__t_1 [obiektu VBArray](../../javascript/reference/vbarray-object-javascript.md)  
 [Używanie tablic](../../javascript/advanced/using-arrays-javascript.md)