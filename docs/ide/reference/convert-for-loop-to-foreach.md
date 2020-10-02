---
title: Kod refaktoryzacji do konwersji pętli for na instrukcję foreach
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
ms.openlocfilehash: 47aa5a328f158d890908bf1ddcb69a838ad1ed66
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659384"
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Refaktoryzacja do konwersji między pętlą for i instrukcją foreach

W tym artykule opisano refaktoryzacje akcji, które są konwertowane między dwiema strukturami pętli. Zawiera kilka powodów, dla których warto przełączać się między pętlą [for](/dotnet/csharp/language-reference/keywords/for) a instrukcją [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) w kodzie.

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Konwertuj pętlę for na instrukcję foreach

Jeśli masz pętlę [for](/dotnet/csharp/language-reference/keywords/for) w kodzie, możesz użyć tej refaktoryzacji do przekonwertowania jej do instrukcji [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) .

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

> [!NOTE]
> Refaktoryzacja operacji **konwersji do trybu foreach** jest dostępna tylko [dla pętli,](/dotnet/csharp/language-reference/keywords/for) które zawierają wszystkie trzy części: inicjator, warunek i iterator.

### <a name="why-convert"></a>Dlaczego warto skonwertować

Powody, dla których warto skonwertować pętlę [for](/dotnet/csharp/language-reference/keywords/for) na instrukcję [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) , to:

- Nie używasz zmiennej pętli lokalnej wewnątrz pętli, chyba że indeks ma dostęp do elementów.

- Chcesz uprościć swój kod i zmniejszyć prawdopodobieństwo błędów logiki w sekcjach inicjator, warunek i iterator.

### <a name="how-to-use-it"></a>Sposób użycia

1. Umieść karetkę w `for` słowie kluczowym.

1. Naciśnij klawisz **Ctrl** + **.** lub kliknij ![ ikonę ikony śrubokrętu śrubokrętu ](../media/screwdriver-icon.png) na marginesie pliku kodu.

   ![Konwertuj na menu foreach](media/convert-to-foreach.png)

1. Wybierz pozycję **Konwertuj na element "foreach"**. Lub wybierz pozycję **Podgląd zmian** , aby otworzyć okno dialogowe [Podgląd zmian](../../ide/preview-changes.md) , a następnie wybierz pozycję **Zastosuj**.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Konwertuj instrukcję foreach na pętlę for

Jeśli masz element [foreach (C#)](/dotnet/csharp/language-reference/keywords/foreach-in) lub [for each... Next (Visual Basic)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) w kodzie, można użyć tego refaktoryzacji, aby przekonwertować go na pętlę [for](/dotnet/csharp/language-reference/keywords/for) .

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

### <a name="why-convert"></a>Dlaczego warto skonwertować

Powody, dla których warto skonwertować instrukcję [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) na pętlę [for](/dotnet/csharp/language-reference/keywords/for) :

- Chcesz użyć zmiennej pętli lokalnej wewnątrz pętli, aby uzyskać więcej niż tylko dostęp do elementu.

- [Iteracja jest przechodzenia przez wielowymiarową tablicę](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) i chcesz mieć większą kontrolę nad elementami tablicy.

### <a name="how-to-use-it"></a>Sposób użycia

1. Umieść karetkę w `foreach` `For Each` słowie kluczowym or.

1. Naciśnij klawisz **Ctrl** + **.** lub kliknij ![ ikonę ikony śrubokrętu śrubokrętu ](../media/screwdriver-icon.png) na marginesie pliku kodu.

   ![Konwertuj na menu dla](media/convert-to-for.png)

1. Wybierz pozycję **Konwertuj na "for"**. Lub wybierz pozycję **Podgląd zmian** , aby otworzyć okno dialogowe [Podgląd zmian](../../ide/preview-changes.md) , a następnie wybierz pozycję **Zastosuj**.

1. Ponieważ Refaktoryzacja wprowadza nową zmienną liczby iteracji, pole **Zmień nazwę** pojawia się w prawym górnym rogu edytora. Jeśli chcesz wybrać inną nazwę dla zmiennej, wpisz ją w, a następnie naciśnij klawisz **Enter** lub wybierz pozycję **Zastosuj** w polu **Zmień nazwę** . Jeśli nie chcesz wybierać nowej nazwy, naciśnij klawisz **ESC** lub wybierz pozycję **Zastosuj** , aby odrzucić pole **Zmień nazwę** .

> [!NOTE]
> W przypadku języka C# kod generowany przez te refaktoryzacji używa typu jawnego lub [var](/dotnet/csharp/language-reference/keywords/var) dla typu elementów w kolekcji. Typ w wygenerowanym kodzie, jawny lub niejawny, zależy od ustawień stylu kodu, które znajdują się w zakresie. Te ustawienia w stylu kodu są konfigurowane na poziomie komputera w obszarze **Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  **C#**  >  **styl kod w stylu**  >  **ogólny**  >  ** \' var "Preferences"** lub na poziomie rozwiązania w pliku [EditorConfig](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types) . Jeśli zmienisz ustawienie stylu kodu w **opcjach**, ponownie otwórz plik kodu, aby zmiany zaczęły obowiązywać.

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
