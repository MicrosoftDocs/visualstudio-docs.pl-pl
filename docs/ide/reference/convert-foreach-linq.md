---
title: Konwertuj pętlę Foreach na LINQ
description: Konwertuj każdą pętlę Foreach, która używa interfejsu IEnumerable do zapytania LINQ lub formularza wywołania LINQ (znanego również jako metoda LINQ).
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8ff489e11cc5c61c5e840b4b12d05ba5da46ce41
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466293"
---
# <a name="convert-a-foreach-loop-to-linq"></a>Konwertuj pętlę Foreach na LINQ

To Refaktoryzacja dotyczy:

- C#

**Co:** Pozwala łatwo skonwertować pętlę *foreach* , która używa interfejsu IEnumerable do zapytania LINQ lub formularza wywołania LINQ (znanego również jako metoda LINQ).

**Kiedy:** Masz pętlę Foreach, która używa interfejsu IEnumerable, i chcesz, aby ta pętla była odczytywana jako zapytanie LINQ.

**Dlaczego:** Wolisz używać składni LINQ zamiast pętli Foreach. [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) wykonuje zapytanie w konstrukcji języka pierwszej klasy w języku C#. LINQ może zmniejszyć ilość kodu w pliku, ułatwić odczytywanie kodu i zezwalanie innym źródłom danych na podobne wzorce wyrażeń zapytań.

> [!NOTE]
> Składnia LINQ jest zwykle mniej wydajna niż Pętla foreach. Warto wiedzieć, jakie wady wydajności mogą wystąpić podczas korzystania z programu LINQ w celu poprawienia czytelności kodu.

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>Konwertuj pętlę Foreach na refaktoryzację LINQ

1. Umieść kursor w `foreach` słowie kluczowym.

    ![Foreach przy użyciu przykładu interfejsu IEnumerable](media/convert-foreach-to-LINQ.png)

2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

   ![Przykład konwersji do menu LINQ](media/convert-foreach-to-LINQ-codefix.png)

3. Wybierz pozycję **Konwertuj na LINQ** lub **Konwertuj na LINQ (formularz wywołania)**.

   ![Przykładowy wynik zapytania LINQ](media/convert-foreach-to-LINQ-result.png)

   ![Przykład wyniku formularza wywołania LINQ](media/convert-foreach-to-LINQ-callform-result.png)

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
- [Podgląd okna zmian](../../ide/preview-changes.md)
- [Porady dla deweloperów platformy .NET](../csharp-developer-productivity.md)
