---
title: Kod refaktoryzacji do konwersji zapytania LINQ do instrukcji foreach
description: Konwertuj wszystkie zapytania LINQ zapisywane w składni zapytania na instrukcję foreach.
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
ms.openlocfilehash: 7abdebf36ab075dfd289069671cf3b6851a72b75
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659371"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refaktoryzacja do konwersji LINQ do instrukcji foreach

Użyj tego refaktoryzacji, aby skonwertować [składnię zapytania LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) do instrukcji [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) .

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

## <a name="how-to-use-it"></a>Sposób użycia

1. Wybierz całe zapytanie LINQ zaczynające się od `from` .

   > [!NOTE]
   > Tego refaktoryzacji można użyć tylko do przekonwertowania zapytań LINQ wyrażonych za pomocą składni zapytania, a nie składni metody.

1. Naciśnij klawisz **Ctrl** + **.** lub kliknij ![ ikonę ikony śrubokrętu śrubokrętu ](../media/screwdriver-icon.png) na marginesie pliku kodu.

   ![Menu konwersji LINQ to foreach — szybkie akcje](media/convert-linq-to-foreach.png)

1. Wybierz pozycję **Konwertuj na element "foreach"**. Lub wybierz pozycję **Podgląd zmian** , aby otworzyć okno dialogowe [Podgląd zmian](../../ide/preview-changes.md) , a następnie wybierz pozycję **Zastosuj**.

> [!NOTE]
> W przypadku języka C# kod generowany przez te refaktoryzacji używa typu jawnego lub [var](/dotnet/csharp/language-reference/keywords/var) dla zmiennej iteracji `foreach` pętli. Typ w wygenerowanym kodzie, jawny lub niejawny, zależy od ustawień stylu kodu, które znajdują się w zakresie. Te ustawienia w stylu kodu są konfigurowane na poziomie komputera w obszarze **Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  **C#**  >  **styl kod w stylu**  >  **ogólny**  >  ** \' var "Preferences"** lub na poziomie rozwiązania w pliku [EditorConfig](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types) . Jeśli zmienisz ustawienie stylu kodu w **opcjach**, ponownie otwórz plik kodu, aby zmiany zaczęły obowiązywać.

## <a name="see-also"></a>Zobacz też

- [LINQ](/dotnet/standard/using-linq)
- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
