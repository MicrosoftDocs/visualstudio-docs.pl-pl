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
ms.openlocfilehash: 159a5dd0195cc0cbb244664d75e19d1ac6af3dec
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843419"
---
# <a name="vbarray-expected"></a>Oczekiwano VBArray
Należy podać obiekt, który nie był safeArray języka Visual Basic, gdy oczekiwano jednej.  
  
```js
new VBArray(safeArray);  
```  
  
 VBArrays są przeznaczone tylko do odczytu i nie można utworzyć bezpośrednio. SafeArray argument jest wartością VBArray i uzyskać wartość VBArray przed przesłaniem do `VBArray` konstruktora. Tylko można to zrobić poprzez pobranie wartości z istniejących ActiveX lub innego obiektu.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, należy przekazać tylko **VBArray** obiekty do **VBArray** konstruktora.  
  
## <a name="see-also"></a>Zobacz też  
 [VbArray — obiekt](../../javascript/reference/vbarray-object-javascript.md)   
 [Używanie tablic](../../javascript/advanced/using-arrays-javascript.md)