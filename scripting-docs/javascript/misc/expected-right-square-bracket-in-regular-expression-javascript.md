---
description: Podjęto próbę utworzenia klasy znaków dla dopasowania wyrażenia regularnego, ale nie zawiera ona prawego nawiasu.
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
ms.openlocfilehash: 6b5e7a25f6fbef3bf87d084b149ee9f356981600
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570950"
---
# <a name="expected--in-regular-expression-javascript"></a>Oczekiwano znaku „]" w wyrażeniu regularnym (JavaScript)
Podjęto próbę utworzenia klasy znaków dla dopasowania wyrażenia regularnego, ale nie zawiera ona prawego nawiasu. Poszczególne kombinacje znaków literału mogą być składane do klas znaków, umieszczając je w nawiasach kwadratowych. Klasa znaku dopasowuje dowolny znak, który zawiera. Na przykład/[abc]/dopasowuje jedną z liter "a", "b" lub "c".  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj prawy nawias do wyrażenia regularnego.  
  
    > [!NOTE]
    > Jeśli chcesz dopasować do pojedynczego nawiasu, należy to zrobić za pomocą ukośnika odwrotnego- \\ [-, tak aby nie był interpretowany jako znak specjalny przez [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt wyrażenia regularnego](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Składnia wyrażenia regularnego (JavaScript)](/previous-versions/1400241x(v=vs.100))
