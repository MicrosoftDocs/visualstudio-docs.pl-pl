---
title: Konwertowanie pętli foreach na LINQ
descritpion: Convert any foreach loop that uses an IEnumerable to a LINQ query or a LINQ call form (also known as a LINQ method).
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 12c03830ccd37e0970e3c74bc78cdd9c8a8732b7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094215"
---
# <a name="convert-a-foreach-loop-to-linq"></a>Konwertowanie pętli foreach na LINQ

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia łatwe konwertowanie *foreach* pętli, która używa IEnumerable do zapytania LINQ lub formularz wywołania LINQ (znany również jako metoda LINQ).

**Kiedy:** Masz foreach pętli, która używa IEnumerable i chcesz, aby ta pętla do odczytu jako kwerendy LINQ.

**Dlaczego?** Wolisz używać składni LINQ, a nie foreach pętli. [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) sprawia, że kwerenda do konstrukcji języka pierwszej klasy w języku C#. LINQ można zmniejszyć ilość kodu w pliku, aby kod łatwiejsze do odczytania i zezwolić na różne źródła danych mają podobne wzorce wyrażeń zapytania.

> [!NOTE]
> Składnia LINQ jest zazwyczaj mniej wydajne niż foreach pętli. Dobrze jest być świadomym wszelkich kompromisów wydajności, które mogą wystąpić podczas korzystania z LINQ w celu poprawy czytelności kodu.

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>Konwertowanie pętli foreach na refaktoryzowanie LINQ

1. Umieść kursor w `foreach` słowie kluczowym.

    ![Foreach przy użyciu próbki IEnumerable](media/convert-foreach-to-LINQ.png)

2. Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**

   ![Konwertuj na przykład menu LINQ](media/convert-foreach-to-LINQ-codefix.png)

3. Wybierz **opcję Konwertuj na LINQ** lub **Konwertuj na Linq (formularz wywołania).**

   ![Przykład wyników kwerendy LINQ](media/convert-foreach-to-LINQ-result.png)

   ![Przykład wyników formularza wywołania LINQ](media/convert-foreach-to-LINQ-callform-result.png)

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

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Okno Zmiany podglądu](../../ide/preview-changes.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)
