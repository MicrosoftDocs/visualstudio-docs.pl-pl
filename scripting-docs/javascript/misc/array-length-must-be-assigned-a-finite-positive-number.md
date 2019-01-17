---
title: Długość tablicy musi mieć przypisaną dodatnią liczbę całkowitą | Dokumentacja firmy Microsoft
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
- VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63a9d714173334192028b9096de41968befa85ef
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348701"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Długość tablicy musi być mieć przypisaną dodatnią liczbę całkowitą
Podczas ustawiania **długość** właściwości istniejącego **tablicy** obiektu, określona długość tablicy, która nie jest liczbą dodatnią lub zerem. Ten błąd występuje podczas przypisywania wartości do **długość** właściwość `Array` obiekt, który jest ujemna lub nie jest liczbą (`NaN`). Należy pamiętać, że [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] automatycznie konwertuje cyfr ułamkowych do całego liczb całkowitych.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Dodatnia liczba całkowita należy przypisać do właściwości długości. Nie ma żadnego górnego limitu rozmiaru tablicy innej niż wartość maksymalna liczba całkowita (około 4 miliardów). Poniższy przykład przedstawia właściwy sposób można ustawić **długość** właściwość **tablicy** obiektu.  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie tablic](../../javascript/advanced/using-arrays-javascript.md)