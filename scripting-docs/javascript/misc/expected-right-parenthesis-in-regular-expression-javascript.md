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
ms.openlocfilehash: 5de54ac2a698cd2536dadbf042554cf70502d92b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076693"
---
# <a name="expected--in-regular-expression-javascript"></a>Oczekiwano znaku „)" w wyrażeniu regularnym (JavaScript)
Podjęto próbę utworzenia przechwytywania wyrażeń regularnych, potwierdzenie lub grupy, ale nie zawiera nawias zamykający. Nawiasy ma kilka celów w wyrażeniach regularnych. Przede wszystkim, są one używane do przechwytywania wyrażeń podrzędnych, określ potwierdzenia lub pogrupować wzorców, dzięki czemu elementy mogą być traktowane jako pojedyncza jednostka, *, +,?, i tak dalej.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj nawias zamykający po prawej stronie.  
  
    > [!NOTE]
    >  Jeśli chcesz dopasować nawiasy pojedynczy znak ucieczki znakiem kreski ułamkowej odwróconej - \\(— tak, aby nie jest interpretowany jako znak specjalny przez [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt będący wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](https://msdn.microsoft.com/library/1400241x)