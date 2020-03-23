---
title: Refaktoryzator kodu do konwersji kwerendy LINQ do foreach instrukcji
description: Konwertuj wszystkie kwerendy LINQ napisane w składni kwerendy do foreach instrukcji.
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
ms.openlocfilehash: 6e1b24cb8406ff29659eb79d1d9fa856db628b89
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094089"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refaktoryzowanie w celu konwersji LINQ na instrukcję foreach

Ta refaktoryzacja służy do konwertowania [składni kwerendy LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) na instrukcję [foreach.](/dotnet/csharp/language-reference/keywords/foreach-in)

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

## <a name="how-to-use-it"></a>Korzystanie

1. Zaznacz całą kwerendę LINQ, zaczynając od `from`.

   > [!NOTE]
   > Ta refaktoryzacja może służyć tylko do konwertowania zapytań LINQ wyrażonych w składni kwerendy, a nie składni metody.

1. Naciśnij **klawisze Ctrl**+**.** lub kliknij ikonę ![ikony](../media/screwdriver-icon.png) śrubokręta na marginesie pliku kodu.

   ![Konwertuj LINQ na menu szybkich akcji](media/convert-linq-to-foreach.png)

1. Wybierz **opcję Konwertuj na "foreach"**. Możesz też wybrać **opcję Podgląd zmian,** aby otworzyć okno dialogowe [Podgląd zmian,](../../ide/preview-changes.md) a następnie wybierz pozycję **Zastosuj**.

> [!NOTE]
> Dla języka C#kod wygenerowany przez te refaktoryzowania [var](/dotnet/csharp/language-reference/keywords/var) używa typu jawnego lub `foreach` var dla zmiennej iteracji pętli. Typ w wygenerowanym kodzie, jawne lub niejawne, zależy od ustawień stylu kodu, które są w zakresie. Te ustawienia w stylu kodu są konfigurowane na poziomie komputera w obszarze**Opcje** >  **narzędzi** > **Edytor** > tekstu**C#** > **Code Style** > **General** > **\'var preferencje**lub na poziomie rozwiązania w pliku [EditorConfig.](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types) Jeśli zmienisz ustawienie stylu kodu w **opcji,** otwórz ponownie plik kodu, aby zmiany zostały wprowadzone.

## <a name="see-also"></a>Zobacz też

- [Linq](/dotnet/standard/using-linq)
- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
