---
title: Refaktoryzuj kod konwertujący dla pętli foreach — instrukcja
ms.date: 05/10/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: fc14a07557b3ae46a84f506bc0fa9007efface63
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55921307"
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Refaktoryzacja do konwersji między pętla, a Instrukcja foreach

W tym artykule opisano refaktoryzacji szybkie akcje, które konwersji między dwoma struktury pętli. Obejmuje niektóre przyczyny, dlaczego warto przełączać się między [dla](/dotnet/csharp/language-reference/keywords/for) pętli i [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) instrukcji w kodzie.

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Konwertuj na pętlę foreach — instrukcja

Jeśli masz [dla](/dotnet/csharp/language-reference/keywords/for) pętli w kodzie, służy tej refaktoryzacji można przekonwertować go pod kątem [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) instrukcji.

Ta Refaktoryzacja mają zastosowanie do:

- C#

> [!NOTE]
> **Przekonwertować foreach** refaktoryzacji szybka akcja jest dostępna tylko dla [dla](/dotnet/csharp/language-reference/keywords/for) pętli, które zawierają wszystkie trzy elementy: inicjator, warunek i iteratora.

### <a name="why-convert"></a>Dlaczego konwersji

Przyczyny, należy przekonwertować [dla](/dotnet/csharp/language-reference/keywords/for) pętli do [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) instrukcji obejmują:

- Nie używaj zmiennej lokalnej wewnątrz pętli, z wyjątkiem jako indeks, aby mieć dostęp do elementów.

- Chcesz uprościć kod i zmniejszyć prawdopodobieństwo błędów logicznych w sekcjach iteratora inicjatora, warunek i.

### <a name="how-to-use-it"></a>Jak z niej korzystać

1. Umieść swoje punkt wstawiania w `for` — słowo kluczowe.

1. Naciśnij klawisz **Ctrl**+**.** lub kliknij przycisk śrubokręt ![ikonę śrubokręt](../media/screwdriver-icon.png) ikonę na marginesie pliku kodu.

   ![Konwertuj na foreach menu](media/convert-to-foreach.png)

1. Wybierz **Konwertuj na pętlę "foreach"**. Lub wybierz **podgląd zmian** otworzyć [podgląd zmian](../../ide/preview-changes.md) okna dialogowego, a następnie wybierz **Zastosuj**.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Konwertuj instrukcję foreach do pętli for

Jeśli masz [foreach (C#)](/dotnet/csharp/language-reference/keywords/foreach-in) lub [For Each... Dalej (Visual Basic)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) instrukcji w kodzie, służy tej refaktoryzacji można przekonwertować go pod kątem [dla](/dotnet/csharp/language-reference/keywords/for) pętli.

Ta Refaktoryzacja mają zastosowanie do:

- C#

- Visual Basic

### <a name="why-convert"></a>Dlaczego konwersji

Przyczyny, należy przekonwertować [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) instrukcję, aby [dla](/dotnet/csharp/language-reference/keywords/for) pętli obejmują:

- Chcesz użyć zmiennej lokalnej wewnątrz pętli do więcej niż tylko uzyskiwania dostępu do elementu.

- Jesteś [iteracji tablicy wielowymiarowej](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) i chcesz mieć większą kontrolę nad elementami tablicy.

### <a name="how-to-use-it"></a>Jak z niej korzystać

1. Umieść swoje punkt wstawiania w `foreach` lub `For Each` — słowo kluczowe.

1. Naciśnij klawisz **Ctrl**+**.** lub kliknij przycisk śrubokręt ![ikonę śrubokręt](../media/screwdriver-icon.png) ikonę na marginesie pliku kodu.

   ![Konwertuj na menu](media/convert-to-for.png)

1. Wybierz **Konwertuj na pętlę "for"**. Lub wybierz **podgląd zmian** otworzyć [podgląd zmian](../../ide/preview-changes.md) okna dialogowego, a następnie wybierz **Zastosuj**.

1. Ponieważ refaktoryzacji wprowadza nową zmienną liczbę iteracji **Zmień nazwę** pojawi się okno w prawym górnym rogu edytora. Jeśli chcesz wybrać inną nazwę zmiennej, wpisz go w, a następnie naciśnij klawisz **Enter** lub wybierz **Zastosuj** w **Zmień nazwę** pole. Jeśli nie chcesz wybrać nową nazwę, naciśnij klawisz **Esc** lub wybierz **Zastosuj** odrzucać **Zmień nazwę** pole.

> [!NOTE]
> Aby uzyskać C#, kod wygenerowany przez te operacje refaktoryzacji używa jawnego typu lub [var](/dotnet/csharp/language-reference/keywords/var) dla typu elementów w kolekcji. Typ w wygenerowanym kodzie jawnych lub niejawnych, zależy od ustawienia stylu kodu, które znajdują się w zakresie. Te ustawienia konkretnego stylu kodu są konfigurowane na poziomie komputera, w obszarze **narzędzia** > **opcje** > **edytora tekstów**  >  **C#**  >  **Styl kodu** > **ogólne** > **\'var " Preferencje**, lub na poziomie rozwiązania w [EditorConfig](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types) pliku. Jeśli zmienisz ustawienia stylu kodu w **opcje**, ponownie otwórz plik kodu, aby zmiany zaczęły obowiązywać.

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)