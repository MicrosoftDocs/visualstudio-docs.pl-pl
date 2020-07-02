---
title: Oczekiwano znaku "]" w wyrażeniu regularnym (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 8a2a2b83b818e37c0b62e103fe284c5c4d110c6c
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815635"
---
# <a name="expected--in-regular-expression-javascript"></a>Oczekiwano znaku „]" w wyrażeniu regularnym (JavaScript)
Podjęto próbę utworzenia klasy znaków dla dopasowania wyrażenia regularnego, ale nie zawiera ona prawego nawiasu. Poszczególne kombinacje znaków literału mogą być składane do klas znaków, umieszczając je w nawiasach kwadratowych. Klasa znaku dopasowuje dowolny znak, który zawiera. Na przykład/[abc]/dopasowuje jedną z liter "a", "b" lub "c".  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj prawy nawias do wyrażenia regularnego.  
  
    > [!NOTE]
    > Jeśli chcesz dopasować do pojedynczego nawiasu, należy to zrobić za pomocą ukośnika odwrotnego- \\ [-, tak aby nie był interpretowany jako znak specjalny przez [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Zobacz także  
 [Obiekt wyrażenia regularnego](../../javascript/reference/regular-expression-object-javascript.md)   
 [Składnia wyrażenia regularnego (JavaScript)](https://msdn.microsoft.com/library/1400241x)