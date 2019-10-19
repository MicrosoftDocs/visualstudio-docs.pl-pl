---
title: Długość tablicy musi być skończoną dodatnią liczbą całkowitą | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 69494f1485a97ff4f2c98cf2493e5d0bc5b8aa9f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576077"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>Długość tablicy musi być skończony dodatnią liczbą całkowitą
Wywoływany jest Konstruktor **Array** z argumentem, który nie jest liczbą całkowitą (liczby całkowite składają się z zero powiększonej o zestaw dodatnich liczb całkowitych).  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Używaj dodatnich liczb całkowitych tylko podczas tworzenia nowego obiektu `Array`. Jeśli chcesz utworzyć tablicę z pojedynczym elementem, który nie jest liczbą całkowitą, zrób to w procesie dwuetapowym. Najpierw Utwórz tablicę z jednym elementem, a następnie umieść wartość w pierwszym elemencie (Array [0]). Poniżej przedstawiono przykład, który generuje ten błąd.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     Poniższy przykład ilustruje poprawny sposób określania tablicy z pojedynczym elementem numerycznym.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Nie ma górnego limitu rozmiaru tablicy innej niż maksymalna wartość całkowita (około 4 000 000 000).  
  
## <a name="see-also"></a>Zobacz także  
 [Używanie tablic](../../javascript/advanced/using-arrays-javascript.md)