---
title: Oczekiwano znaku ")" w wyrażeniu regularnym (JavaScript) | Microsoft Docs
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
ms.openlocfilehash: 7c10449df9ef3331949695b7423da3eb08b65433
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577536"
---
# <a name="expected--in-regular-expression-javascript"></a>Oczekiwano znaku „)" w wyrażeniu regularnym (JavaScript)
Podjęto próbę utworzenia przechwycenia wyrażenia regularnego, potwierdzenia lub grupy, ale nie zawiera nawiasu zamykającego. Nawiasy mają kilka celów w wyrażeniach regularnych. Przede wszystkim są one używane do przechwytywania wyrażeń podrzędnych, określania zatwierdzeń lub grupowania wzorców ze sobą, aby elementy mogły być traktowane jako pojedyncze jednostki przez *, +,? itd.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj prawy nawias zamykający.  
  
    > [!NOTE]
    > Jeśli chcesz dopasować pojedyncze nawiasy, należy wyjść z ukośnikiem odwrotnym \\ (-tak, aby nie był interpretowany jako znak specjalny przez [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Zobacz także  
 @No__t_1 [obiektu wyrażenia regularnego](../../javascript/reference/regular-expression-object-javascript.md)  
 [Składnia wyrażenia regularnego (JavaScript)](https://msdn.microsoft.com/library/1400241x)