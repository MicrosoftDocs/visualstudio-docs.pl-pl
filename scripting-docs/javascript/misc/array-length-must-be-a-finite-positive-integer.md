---
title: Długość tablicy musi być skończoną dodatnią liczbą całkowitą. | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6589bd2e9bb4acbec5f169087a49e64417dfae7
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348597"
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