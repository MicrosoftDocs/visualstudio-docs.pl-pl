---
title: Konwertuj pętlę foreach na LINQ
ms.date: 02/20/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: dc0f94d6aa9f13ac038f1af19a1ab1c78158ea14
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57325337"
---
# <a name="convert-foreach-loop-to-linq"></a>Konwertuj pętlę foreach na LINQ

Ta Refaktoryzacja mają zastosowanie do:

- C#

**Co:** Pozwala łatwo przekształcać zapytania LINQ lub formularz rozmowy LINQ (znany także jako metoda LINQ) przy użyciu IEnumerables pętli foreach.

**Kiedy:** Jeśli masz pętli foreach, która korzysta z elementu IEnumerable, który chcesz odczytać zapytania LINQ.

**Dlaczego:** Użytkownicy mogą preferuje przy użyciu składni LINQ zamiast który pętli foreach. [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) sprawia, że zapytanie językiem pierwszej klasy konstruowania w C#. LINQ można zmniejszyć ilość kodu w pliku, ułatwić interpretowanie i zezwolić na różnych źródeł danych mają podobne wzorców wyrażenia zapytania.

> [!NOTE]
> Składni LINQ to zazwyczaj mniej wydajne niż pętli foreach. Dobrze znać handlu wydłużenia off możesz może spowodować w przypadku Poprawa czytelności kodu za pomocą LINQ.

## <a name="convert-foreach-loop-to-linq-refactoring"></a>Konwertuj pętlę foreach na refaktoryzacji LINQ

1. Umieść kursor w `foreach` — słowo kluczowe.

    ![Instrukcja foreach przy użyciu interfejsu IEnumerable](media/convert-foreach-to-LINQ.png)

2. Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.

   ![Konwertuj na LINQ menu](media/convert-foreach-to-LINQ-codefix.png)

3. Wybierz **przekonwertować LINQ** lub **przekonwertować Linq (formularz wywołań)**

   ![Wyniku zapytania LINQ](media/convert-foreach-to-LINQ-result.png)
   
   ![Wynik formularza wywołania LINQ](media/convert-foreach-to-LINQ-callform-result.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
- [Wskazówki dla deweloperów platformy .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)