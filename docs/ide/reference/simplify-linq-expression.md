---
title: Uprość wyrażenie LINQ
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 04485d6ce67c822fd0620bd63f3557851db6dbb9
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2020
ms.locfileid: "88251319"
---
# <a name="simplify-linq-expression"></a>Uprość wyrażenie LINQ

To Refaktoryzacja dotyczy:

- C#

**Co:** Przypadki refaktoryzacji `SomeEnumerableType.Where(<LambdaExpression>).Single()` do `SomeEnumerable.Single(<LambdaExpression>)` dla programu `Enumerable.Single()` oraz następujące metody wyliczalne:,,,,, `SingleOrDefault()` `Last()` `LastOrDefault()` `Any()` `Count()` `First()` i `FirstOrDefault()` .

**Kiedy:**  Wszystkie wystąpienia, w których metoda wywołuje `Single()` , `SingleOrDefault()` itd., nie ma żadnych argumentów i jest poprzedzone `Where()` wyrażeniem. `Where()`Nie można utworzyć danych wejściowych wyrażenia jako drzewa wyrażenia.

**Dlaczego:** Usunięcie niepotrzebnego wywołania do wyliczalnej `.Where()` metody zwiększa wydajność i czytelność.

## <a name="how-to"></a>Porady

1. Umieść kursor w ramach `SomeEnumerableType.Where(<LambdaExpression>).Single()` wystąpienia w programie Visual Studio.
2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
3. Wybierz polecenie **Uprość wyrażenie LINQ**

   ![Konwertuj typeof na nameof](media/simplify-linq-expression.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
