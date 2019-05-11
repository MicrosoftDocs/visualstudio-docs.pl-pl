---
title: Konwertuj pętlę foreach na LINQ
ms.date: 02/20/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 7893ed676372cce94d883353139de91ef639aeb0
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531845"
---
# <a name="convert-a-foreach-loop-to-linq"></a>Konwertuj pętlę foreach na LINQ

Ta Refaktoryzacja mają zastosowanie do:

- C#

**Co:** Pozwala łatwo przekształcać swoje *foreach* pętli, która korzysta z elementu IEnumerable zapytania LINQ lub formularz rozmowy LINQ (znany także jako metoda LINQ).

**Kiedy:** Pętla foreach, która używa elementu IEnumerable, i chcesz, aby tej pętli do odczytu jako zapytania LINQ.

**Dlaczego:** Wolisz używać składni LINQ, zamiast pętli foreach. [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) wykonuje zapytanie w języku najwyższej jakości konstruowania w C#. LINQ można zmniejszyć ilość kodu w pliku, uczynienie go łatwiejszym do odczytywania i zezwolić na różnych źródeł danych mają podobne wzorców wyrażenia zapytania.

> [!NOTE]
> Składni LINQ to zazwyczaj mniej wydajne niż pętli foreach. Warto wiedzieć, wszelkie kosztem wydajności, który może wystąpić, gdy używasz LINQ, można zwiększyć czytelność kodu.

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>Konwertuj pętlę foreach na refaktoryzacji LINQ

1. Umieść kursor w `foreach` — słowo kluczowe.

    ![Instrukcja foreach przy użyciu interfejsu IEnumerable — przykład](media/convert-foreach-to-LINQ.png)

2. Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.

   ![Konwertuj na przykład menu LINQ](media/convert-foreach-to-LINQ-codefix.png)

3. Wybierz **przekonwertować LINQ** lub **przekonwertować Linq (wywołanie formularz)**.

   ![Przykład wyniku zapytania LINQ](media/convert-foreach-to-LINQ-result.png)

   ![Przykładowy wynik formularza wywołanie LINQ](media/convert-foreach-to-LINQ-callform-result.png)

### <a name="sample-code"></a>Przykładowy kod

```csharp
using System.Collections.Generic;

public class Class1
{
    public void MyMethod()
    {
        var greetings = new List<string>()
            { "hi", "yo", "hello", "howdy" };

        IEnumerable<string> enumerable()
        {
            foreach (var greet in greetings)
            {
                if (greet.Length < 3)
                {
                    yield return greet;
                }
            }

            yield break;
        }
    }
}
```

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd okna zmian](../../ide/preview-changes.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)
