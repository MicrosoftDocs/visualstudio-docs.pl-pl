---
description: Podczas ustawiania właściwości length istniejącego obiektu Array określono długość tablicy, która nie jest liczbą dodatnią ani zerem.
title: Długość tablicy musi mieć przypisaną skończoną liczbę dodatnią | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3938f240580564112915ab0ba3036b63dc96cd8f
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2021
ms.locfileid: "103572146"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Długość tablicy musi być mieć przypisaną dodatnią liczbę całkowitą
Podczas ustawiania właściwości **Length** istniejącego obiektu **Array** określono długość tablicy, która nie jest liczbą dodatnią ani zerem. Ten błąd występuje, gdy przypiszesz wartość do właściwości **Length** `Array` obiektu, który jest ujemny lub nie jest liczbą ( `NaN` ). Należy zauważyć, że [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] automatycznie konwertuje liczby ułamkowe na całkowite liczby całkowite.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Przypisz dodatnią liczbę całkowitą do właściwości length. Nie ma górnego limitu rozmiaru tablicy innej niż maksymalna wartość całkowita (około 4 000 000 000). Poniższy przykład ilustruje poprawny sposób ustawiania właściwości **Length** obiektu **Array** .  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie tablic](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)
