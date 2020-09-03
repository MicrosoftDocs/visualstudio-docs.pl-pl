---
title: Długość tablicy musi być skończoną dodatnią liczbą całkowitą | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: fa8b9a85c0c7457cb06d36fd3cd849ce48484b46
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817089"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>Długość tablicy musi być skończony dodatnią liczbą całkowitą
Wywoływany jest Konstruktor **Array** z argumentem, który nie jest liczbą całkowitą (liczby całkowite składają się z zero powiększonej o zestaw dodatnich liczb całkowitych).  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Używaj dodatnich liczb całkowitych tylko podczas tworzenia nowego `Array` obiektu. Jeśli chcesz utworzyć tablicę z pojedynczym elementem, który nie jest liczbą całkowitą, zrób to w procesie dwuetapowym. Najpierw Utwórz tablicę z jednym elementem, a następnie umieść wartość w pierwszym elemencie (Array [0]). Poniżej przedstawiono przykład, który generuje ten błąd.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     Poniższy przykład ilustruje poprawny sposób określania tablicy z pojedynczym elementem numerycznym.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Nie ma górnego limitu rozmiaru tablicy innej niż maksymalna wartość całkowita (około 4 000 000 000).  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie tablic](../../javascript/advanced/using-arrays-javascript.md)