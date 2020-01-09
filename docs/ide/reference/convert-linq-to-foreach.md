---
title: Kod refaktoryzacji do konwersji zapytania LINQ do instrukcji foreach
description: Konwertuj wszystkie zapytania LINQ zapisywane w składni zapytania na instrukcję foreach.
ms.date: 05/15/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: bb2cdf96d7f7829ff6a6d1394160548da2adae7f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595751"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refaktoryzacja do konwersji LINQ do instrukcji foreach

Użyj tego refaktoryzacji, aby skonwertować [składnię zapytania LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) do instrukcji [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) .

Ta Refaktoryzacja mają zastosowanie do:

- Język C#

## <a name="how-to-use-it"></a>Jak z niej korzystać

1. Wybierz całą kwerendę LINQ rozpoczynającą się od `from`.

   > [!NOTE]
   > Tego refaktoryzacji można użyć tylko do przekonwertowania zapytań LINQ wyrażonych za pomocą składni zapytania, a nie składni metody.

1. Naciśnij klawisz **Ctrl**+ **.** lub kliknij ikonę śrubokrętu ![ikonę śrubokrętu](../media/screwdriver-icon.png) na marginesie pliku kodu.

   ![Menu konwersji LINQ to foreach — szybkie akcje](media/convert-linq-to-foreach.png)

1. Wybierz pozycję **Konwertuj na element "foreach"** . Lub wybierz pozycję **Podgląd zmian** , aby otworzyć okno dialogowe [Podgląd zmian](../../ide/preview-changes.md) , a następnie wybierz pozycję **Zastosuj**.

> [!NOTE]
> W C#przypadku, kod generowany przez te refaktoryzacji używa typu jawnego lub [var](/dotnet/csharp/language-reference/keywords/var) dla zmiennej iteracji pętli `foreach`. Typ w wygenerowanym kodzie, jawny lub niejawny, zależy od ustawień stylu kodu, które znajdują się w zakresie. Te ustawienia stylu kodu są konfigurowane na poziomie komputera w obszarze **narzędzia** > **Opcje** > **edytorze tekstów** > **C#**  > **stylu kodu** > **Ogólne** >  **\'var "Preferences"** lub na poziomie rozwiązania w pliku [EditorConfig](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types) . Jeśli zmienisz ustawienie stylu kodu w **opcjach**, ponownie otwórz plik kodu, aby zmiany zaczęły obowiązywać.

## <a name="see-also"></a>Zobacz także

- [LINQ](/dotnet/standard/using-linq)
- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
