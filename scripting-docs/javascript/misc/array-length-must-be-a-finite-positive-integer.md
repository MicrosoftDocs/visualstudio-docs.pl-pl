---
title: Długość tablicy musi być skończoną dodatnią liczbą całkowitą. | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 691f7aff61a8a2bfae6444540afe9a28a200278d
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840435"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>Długość tablicy musi być skończony dodatnią liczbą całkowitą
Wywołujesz **tablicy** Konstruktor z argumentem, który nie jest liczbą całkowitą (liczby całkowite składają się z zera, a także zestaw dodatnie liczby całkowite).  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Użyj dodatnie liczby całkowite, tylko wtedy, gdy jest to utworzenie nowego `Array` obiektu. Jeśli chcesz utworzyć tablicy z pojedynczy element, który nie jest liczbą całkowitą, należy to zrobić w dwóch etapach. Najpierw Utwórz tablicę z jednym elementem, a następnie umieść wartość w pierwszym elemencie (array[0]). Oto przykład, który generuje ten błąd.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     W poniższym przykładzie pokazano prawidłowym sposobem, aby określić tablicę z jednym elementem liczbowych.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Nie ma żadnego górnego limitu rozmiaru tablicy innej niż wartość maksymalna liczba całkowita (około 4 miliardów).  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie tablic](../../javascript/advanced/using-arrays-javascript.md)