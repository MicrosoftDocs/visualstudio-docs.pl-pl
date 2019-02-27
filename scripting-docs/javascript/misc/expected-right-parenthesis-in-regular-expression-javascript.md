---
title: Oczekiwano ")" w wyrażeniu regularnym (JavaScript) | Dokumentacja firmy Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72b4cf24b4b738b7ca71e364d7be6486313a4844
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840808"
---
# <a name="expected--in-regular-expression-javascript"></a>Oczekiwano znaku „)" w wyrażeniu regularnym (JavaScript)
Podjęto próbę utworzenia przechwytywania wyrażeń regularnych, potwierdzenie lub grupy, ale nie zawiera nawias zamykający. Nawiasy ma kilka celów w wyrażeniach regularnych. Przede wszystkim, są one używane do przechwytywania wyrażeń podrzędnych, określ potwierdzenia lub pogrupować wzorców, dzięki czemu elementy mogą być traktowane jako pojedyncza jednostka, *, +,?, i tak dalej.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Dodaj nawias zamykający po prawej stronie.  
  
    > [!NOTE]
    >  Jeśli chcesz dopasować nawiasy pojedynczy znak ucieczki znakiem kreski ułamkowej odwróconej - \\(— tak, aby nie jest interpretowany jako znak specjalny przez [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt będący wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](https://msdn.microsoft.com/library/1400241x)