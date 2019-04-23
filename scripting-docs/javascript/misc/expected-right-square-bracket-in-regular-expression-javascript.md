---
title: Oczekiwano ']' w wyrażeniu regularnym (JavaScript) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5c49ab90dae8f30dae075906bb9c7ecb7881428f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60065080"
---
# <a name="expected--in-regular-expression-javascript"></a>Oczekiwano znaku „]" w wyrażeniu regularnym (JavaScript)
Podjęto próbę utworzenia klasy znaków dopasowania wyrażenia regularnego, ale nie zawiera nawias zamykający. Pojedynczy znak literału kombinacje mogą być włączane do klasy znaków w, umieszczając je w nawiasach. Klasa znaków dopasowuje dowolny znak zawartych w nim. Na przykład / [abc] / pasuje do dowolnej litery "a", "b", lub "c".  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj prawy nawias kwadratowy do wyrażenia regularnego.  
  
    > [!NOTE]
    >  Jeśli chcesz dopasować pojedynczy nawias, zmienić jego znaczenie znakiem kreski ułamkowej odwróconej - \\[— tak nie jest interpretowany jako znak specjalny przez [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt będący wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](https://msdn.microsoft.com/library/1400241x)