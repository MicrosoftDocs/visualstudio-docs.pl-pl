---
title: Długość tablicy musi mieć przypisaną dodatnią liczbę całkowitą | Dokumentacja firmy Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 39f2720efbcd8defffb9d0c77047a50e57939e95
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62818054"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Długość tablicy musi być mieć przypisaną dodatnią liczbę całkowitą
Podczas ustawiania **długość** właściwości istniejącego **tablicy** obiektu, określona długość tablicy, która nie jest liczbą dodatnią lub zerem. Ten błąd występuje podczas przypisywania wartości do **długość** właściwość `Array` obiekt, który jest ujemna lub nie jest liczbą (`NaN`). Należy pamiętać, że [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] automatycznie konwertuje cyfr ułamkowych do całego liczb całkowitych.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodatnia liczba całkowita należy przypisać do właściwości długości. Nie ma żadnego górnego limitu rozmiaru tablicy innej niż wartość maksymalna liczba całkowita (około 4 miliardów). Poniższy przykład przedstawia właściwy sposób można ustawić **długość** właściwość **tablicy** obiektu.  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie tablic](../../javascript/advanced/using-arrays-javascript.md)