---
title: Oczekiwano znaku "]" w wyrażeniu regularnym (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9af38a5fa754a811416f1a998b90946345f3e4a2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576482"
---
# <a name="expected--in-regular-expression-javascript"></a>Oczekiwano znaku „]" w wyrażeniu regularnym (JavaScript)
Podjęto próbę utworzenia klasy znaków dla dopasowania wyrażenia regularnego, ale nie zawiera ona prawego nawiasu. Poszczególne kombinacje znaków literału mogą być składane do klas znaków, umieszczając je w nawiasach kwadratowych. Klasa znaku dopasowuje dowolny znak, który zawiera. Na przykład/[abc]/dopasowuje jedną z liter "a", "b" lub "c".  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj prawy nawias do wyrażenia regularnego.  
  
    > [!NOTE]
    > Jeśli chcesz dopasować do pojedynczego nawiasu, należy to zrobić przy użyciu ukośnika odwrotnego-\\ [-so nie jest interpretowana jako znak specjalny przez [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Zobacz także  
 @No__t_1 [obiektu wyrażenia regularnego](../../javascript/reference/regular-expression-object-javascript.md)  
 [Składnia wyrażenia regularnego (JavaScript)](https://msdn.microsoft.com/library/1400241x)