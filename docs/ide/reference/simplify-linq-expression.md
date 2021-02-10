---
title: Upraszczanie wyrażenia LINQ
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 006fc0fe84b11573ece98019a4446d83de52d62c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957559"
---
# <a name="simplify-linq-expression"></a>Upraszczanie wyrażenia LINQ

To Refaktoryzacja dotyczy:

- C#

**Co:** Przypadki refaktoryzacji `SomeEnumerableType.Where(<LambdaExpression>).Single()` do `SomeEnumerable.Single(<LambdaExpression>)` dla programu `Enumerable.Single()` oraz następujące metody wyliczalne:,,,,, `SingleOrDefault()` `Last()` `LastOrDefault()` `Any()` `Count()` `First()` i `FirstOrDefault()` .

**Kiedy:**  Wszystkie wystąpienia, w których metoda wywołuje `Single()` , `SingleOrDefault()` itd., nie ma żadnych argumentów i jest poprzedzone `Where()` wyrażeniem. `Where()`Nie można utworzyć danych wejściowych wyrażenia jako drzewa wyrażenia.

**Dlaczego:** Usunięcie niepotrzebnego wywołania do wyliczalnej `.Where()` metody zwiększa wydajność i czytelność.

## <a name="how-to"></a>Porady

1. Umieść kursor w ramach `SomeEnumerableType.Where(<LambdaExpression>).Single()` wystąpienia w programie Visual Studio.
2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
3. Wybierz polecenie **Uprość wyrażenie LINQ**

   ![Konwertuj element typeof na element nameof](media/simplify-linq-expression.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
