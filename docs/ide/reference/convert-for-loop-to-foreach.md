---
title: Refaktoryzator kodu do konwersji for pętli do foreach instrukcji
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
ms.openlocfilehash: af52761f5cb199c7f842d01589c35501898b09aa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094605"
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Refaktoryzowanie do konwersji między for pętli i foreach instrukcji

W tym artykule opisano szybkie akcje refaktoryzacji, które konwertują między dwiema strukturami pętli. Zawiera kilka powodów, dla których warto przełączać się między [for](/dotnet/csharp/language-reference/keywords/for) pętli i [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) instrukcji w kodzie.

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Konwertowanie for pętli na instrukcję foreach

Jeśli masz [for](/dotnet/csharp/language-reference/keywords/for) pętli w kodzie, można użyć tego refaktoryzacji do konwersji go [do foreach](/dotnet/csharp/language-reference/keywords/foreach-in) instrukcji.

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

> [!NOTE]
> **Konwersja do foreach** szybkie działanie refaktoryzacji jest dostępna tylko [dla](/dotnet/csharp/language-reference/keywords/for) pętli, które zawierają wszystkie trzy części: inicjatora, warunek i iteratora.

### <a name="why-convert"></a>Dlaczego warto konwertować

Powody, dla których można przekonwertować [for](/dotnet/csharp/language-reference/keywords/for) pętli [do foreach](/dotnet/csharp/language-reference/keywords/foreach-in) instrukcji obejmują:

- Nie używasz zmiennej pętli lokalnej wewnątrz pętli, z wyjątkiem jako indeks, aby uzyskać dostęp do elementów.

- Chcesz uprościć kod i zmniejszyć prawdopodobieństwo błędów logicznych w sekcjach inicjatora, warunku i iteratora.

### <a name="how-to-use-it"></a>Korzystanie

1. Umieść swoją cieszę `for` w słowie kluczowym.

1. Naciśnij **klawisze Ctrl**+**.** lub kliknij ikonę ![ikony](../media/screwdriver-icon.png) śrubokręta na marginesie pliku kodu.

   ![Konwertuj menu foreach](media/convert-to-foreach.png)

1. Wybierz **opcję Konwertuj na "foreach"**. Możesz też wybrać **opcję Podgląd zmian,** aby otworzyć okno dialogowe [Podgląd zmian,](../../ide/preview-changes.md) a następnie wybierz pozycję **Zastosuj**.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Konwertowanie instrukcji foreach na pętlę for

Jeśli masz [foreach (C#)](/dotnet/csharp/language-reference/keywords/foreach-in) lub [dla każdego... Następna instrukcja (Visual Basic)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) w kodzie, można użyć tego refaktoryzacji do konwersji go [do for](/dotnet/csharp/language-reference/keywords/for) pętli.

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

### <a name="why-convert"></a>Dlaczego warto konwertować

Powody, dla których można przekonwertować [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) instrukcji [foreach do for](/dotnet/csharp/language-reference/keywords/for) pętli obejmują:

- Chcesz użyć zmiennej pętli lokalnej wewnątrz pętli dla więcej niż tylko dostęp do elementu.

- [Iteracja za pośrednictwem tablicy wielowymiarowej](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) i ma większa kontrola nad elementami tablicy.

### <a name="how-to-use-it"></a>Korzystanie

1. Umieść swoją cieszę `foreach` w lub `For Each` słowie kluczowym.

1. Naciśnij **klawisze Ctrl**+**.** lub kliknij ikonę ![ikony](../media/screwdriver-icon.png) śrubokręta na marginesie pliku kodu.

   ![Konwertuj na menu](media/convert-to-for.png)

1. Wybierz **opcję Konwertuj na "dla"**. Możesz też wybrać **opcję Podgląd zmian,** aby otworzyć okno dialogowe [Podgląd zmian,](../../ide/preview-changes.md) a następnie wybierz pozycję **Zastosuj**.

1. Ponieważ refaktoryzacji wprowadza nową zmienną liczby iteracji, **Zmień nazwę** pole pojawia się w prawym górnym rogu edytora. Jeśli chcesz wybrać inną nazwę zmiennej, wpisz ją, a następnie naciśnij klawisz **Enter** lub wybierz pozycję **Zastosuj** w polu **Zmień nazwę.** Jeśli nie chcesz wybierać nowej nazwy, naciśnij klawisz **Esc** lub wybierz pozycję **Zastosuj,** aby odrzucić pole **Zmień nazwę.**

> [!NOTE]
> Dla języka C#kod wygenerowany przez te refaktoryzowania używa typu jawnego lub [var](/dotnet/csharp/language-reference/keywords/var) dla typu elementów w kolekcji. Typ w wygenerowanym kodzie, jawne lub niejawne, zależy od ustawień stylu kodu, które są w zakresie. Te ustawienia w stylu kodu są konfigurowane na poziomie komputera w obszarze**Opcje** >  **narzędzi** > **Edytor** > tekstu**C#** > **Code Style** > **General** > **\'var preferencje**lub na poziomie rozwiązania w pliku [EditorConfig.](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types) Jeśli zmienisz ustawienie stylu kodu w **opcji,** otwórz ponownie plik kodu, aby zmiany zostały wprowadzone.

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
