---
title: Oczekiwano VBArray | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5d1fabd8da6f825a266614a4a5c7fabd5c307130
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63005995"
---
# <a name="vbarray-expected"></a>Oczekiwano VBArray
Należy podać obiekt, który nie był safeArray języka Visual Basic, gdy oczekiwano jednej.  
  
```js
new VBArray(safeArray);  
```  
  
 VBArrays są przeznaczone tylko do odczytu i nie można utworzyć bezpośrednio. SafeArray argument jest wartością VBArray i uzyskać wartość VBArray przed przesłaniem do `VBArray` konstruktora. Tylko można to zrobić poprzez pobranie wartości z istniejących ActiveX lub innego obiektu.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, należy przekazać tylko **VBArray** obiekty do **VBArray** konstruktora.  
  
## <a name="see-also"></a>Zobacz też  
 [VbArray — obiekt](../../javascript/reference/vbarray-object-javascript.md)   
 [Używanie tablic](../../javascript/advanced/using-arrays-javascript.md)