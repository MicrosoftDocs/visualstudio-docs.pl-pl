---
title: Upraszczanie wyrażenia LINQ
description: Ta refaktoryzacja służy do usuwania niepotrzebnych wywołań do wyliczalnej metody WHERE.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 20a3524d786b1f03fc3e221d1b257892d9439a0b
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466170"
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
