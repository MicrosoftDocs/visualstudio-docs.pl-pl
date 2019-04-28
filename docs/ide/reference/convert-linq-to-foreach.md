---
title: Refaktoryzuj kod konwertujący zapytania LINQ do instrukcji foreach
ms.date: 05/15/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 9e58b9af583c6183a12f611bcc527443bc9bd30a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968243"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refaktoryzacja do przekonwertowania LINQ do instrukcji foreach

Użyj tej refaktoryzacji można przekonwertować [składni zapytań LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) do [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) instrukcji.

Ta Refaktoryzacja mają zastosowanie do:

- C#

## <a name="how-to-use-it"></a>Jak z niej korzystać

1. Zaznacz całą LINQ zapytania począwszy od `from`.

   > [!NOTE]
   > Ta Refaktoryzacja należy używać tylko do zapytań LINQ, wyrażone za pomocą składni zapytania i nie metody konwersji.

1. Naciśnij klawisz **Ctrl**+**.** lub kliknij przycisk śrubokręt ![ikonę śrubokręt](../media/screwdriver-icon.png) ikonę na marginesie pliku kodu.

   ![Konwertuj LINQ do menu Szybkie akcje foreach](media/convert-linq-to-foreach.png)

1. Wybierz **Konwertuj na pętlę "foreach"**. Lub wybierz **podgląd zmian** otworzyć [podgląd zmian](../../ide/preview-changes.md) okna dialogowego, a następnie wybierz **Zastosuj**.

> [!NOTE]
> Aby uzyskać C#, kod wygenerowany przez te operacje refaktoryzacji używa jawnego typu lub [var](/dotnet/csharp/language-reference/keywords/var) dla zmiennej iteracji `foreach` pętli. Typ w wygenerowanym kodzie jawnych lub niejawnych, zależy od ustawienia stylu kodu, które znajdują się w zakresie. Te ustawienia konkretnego stylu kodu są konfigurowane na poziomie komputera, w obszarze **narzędzia** > **opcje** > **edytora tekstów**  >  **C#**  >  **Styl kodu** > **ogólne** > **\'var " Preferencje**, lub na poziomie rozwiązania w [EditorConfig](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types) pliku. Jeśli zmienisz ustawienia stylu kodu w **opcje**, ponownie otwórz plik kodu, aby zmiany zaczęły obowiązywać.

## <a name="see-also"></a>Zobacz także

- [LINQ](/dotnet/standard/using-linq)
- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)