---
title: Kod refaktoryzacji do konwersji zapytania LINQ do instrukcji foreach
description: Konwertuj wszystkie zapytania LINQ zapisywane w składni zapytania na instrukcję foreach.
ms.date: 05/15/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 446d0f3a4988552e8e1fbbac32ca150491975d94
ms.sourcegitcommit: 0f5f7955076238742f2071d286ad8e896f3a6cad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2019
ms.locfileid: "68483674"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refaktoryzacja do konwersji LINQ do instrukcji foreach

Użyj tego refaktoryzacji, aby skonwertować [składnię zapytania LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) do instrukcji [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) .

Ta Refaktoryzacja mają zastosowanie do:

- C#

## <a name="how-to-use-it"></a>Jak z niej korzystać

1. Wybierz całe zapytanie LINQ zaczynające się `from`od.

   > [!NOTE]
   > Tego refaktoryzacji można użyć tylko do przekonwertowania zapytań LINQ wyrażonych za pomocą składni zapytania, a nie składni metody.

1. Naciśnij klawisz **Ctrl**+ **.** lub kliknij ![ikonę ikony](../media/screwdriver-icon.png) śrubokrętu śrubokrętu na marginesie pliku kodu.

   ![Menu konwersji LINQ to foreach — szybkie akcje](media/convert-linq-to-foreach.png)

1. Wybierz pozycję **Konwertuj na element "foreach"** . Lub wybierz pozycję **Podgląd zmian** , aby otworzyć okno dialogowe [Podgląd zmian](../../ide/preview-changes.md) , a następnie wybierz pozycję **Zastosuj**.

> [!NOTE]
> W C#przypadku, kod generowany przez te refaktoryzacji używa typu jawnego lub [var](/dotnet/csharp/language-reference/keywords/var) dla `foreach` zmiennej iteracji pętli. Typ w wygenerowanym kodzie, jawny lub niejawny, zależy od ustawień stylu kodu, które znajdują się w zakresie. Te ustawienia stylu kodu są konfigurowane na poziomie komputera w obszarze **Narzędzia** > **Opcje** > **styl**  >  **C#**  > **Edytor tekstu** >  **Ogólne** wartość "Preferences" lub na poziomie rozwiązania w pliku [EditorConfig](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types) .  **\'**  >  Jeśli zmienisz ustawienie stylu kodu w opcjach , ponownie otwórz plik kodu, aby zmiany zaczęły obowiązywać.

## <a name="see-also"></a>Zobacz także

- [LINQ](/dotnet/standard/using-linq)
- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)