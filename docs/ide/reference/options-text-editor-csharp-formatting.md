---
title: Opcje formatowania edytora C#
ms.date: 08/14/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 57d95cd3f3dcf68e7af143bdde3a16474beda20c
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659280"
---
# <a name="options-dialog-box-text-editor--c--code-style--formatting"></a>Opcje — okno dialogowe: Edytor tekstu \> C# \> \> Formatowanie stylu kodu

Użyj strony opcje **formatowania** i jej podstrony ([**wcięcia**](#indentation-page), **nowe linie**, **odstępy**i **Zawijanie**), aby ustawić opcje formatowania kodu w edytorze kodu.

Aby uzyskać dostęp do tej strony opcji **Tools**, wybierz  >  **Opcje** narzędzia z paska menu. W oknie dialogowym **Opcje** wybierz pozycję **Edytor tekstu**  >  **C#**  >  **Formatowanie stylu kodu**  >  **Formatting**.

> [!TIP]
> **Wcięcia**, **nowe wiersze**, **odstępy**i podstrony **zawijania** każdy wyświetlają okno podglądu u dołu, które pokazuje efekt poszczególnych opcji. Aby użyć okna podglądu, wybierz opcję formatowania. Okno podglądu zawiera przykład wybranej opcji. Po zmianie ustawienia przez wybranie przycisku radiowego lub pola wyboru okno podglądu zostanie zaktualizowane, aby pokazać efekt nowego ustawienia.

## <a name="formatting-general-page"></a>Strona formatowania (ogólna)

### <a name="general-settings"></a>Ustawienia ogólne

Te ustawienia mają wpływ na to, *kiedy* Edytor kodu stosuje opcje formatowania do kodu.

|Etykieta|Opis|
|-----------|-----------------|
|**Automatycznie Formatuj przy wpisywaniu**|Po zaznaczeniu tej opcji, **instrukcja format na;** i **blok formatowania na}** opcje są wyłączone.|
|**Automatyczne formatowanie instrukcji na;**|Po wybraniu formatuje instrukcje po zakończeniu zgodnie z opcjami formatowania wybranymi dla edytora.|
|**Automatycznie Formatuj blok na}**|Po wybraniu format bloki kodu zgodnie z opcjami formatowania wybranych dla edytora zaraz po zakończeniu bloku kodu.|
|**Automatycznie Formatuj przy zwrocie**|Gdy jest zaznaczone, formatuje tekst po naciśnięciu klawisza **Enter** , aby dopasować opcje formatowania wybrane dla edytora.|
|**Automatycznie Formatuj przy wklejaniu**|Gdy ta opcja jest zaznaczona, formatuje tekst wklejony do edytora, aby dopasować opcje formatowania wybrane dla edytora.|

::: moniker range="vs-2019"

Jeśli wcześniej zastosowano ustawienia stylu kodu dla plików języka C# przy użyciu polecenia **Formatuj dokument** w programie Visual Studio 2017, ta funkcja jest teraz dostępna jako [**oczyszczanie kodu**](../code-styles-and-code-cleanup.md#apply-code-styles).

::: moniker-end

::: moniker range="vs-2017"

### <a name="format-document-settings"></a>Formatowanie ustawień dokumentu

Te ustawienia umożliwiają skonfigurowanie polecenia **Formatuj dokument** w celu przeprowadzenia dodatkowego czyszczenia kodu na pliku. Aby uzyskać więcej informacji o tym, jak te ustawienia są stosowane, zobacz [Formatowanie dokumentu — polecenie](../code-styles-and-code-cleanup.md#apply-code-styles).

|Etykieta|Opis|Odpowiednie reguły opcji > i narzędzi EditorConfig|
|-----------|-----------------|-----------------|-----------------|
|**Zastosuj wszystkie reguły formatowania języka C# (wcięcia, zawijanie, odstępy)**|Polecenie **Formatuj dokument** zawsze rozwiązuje problemy związane z formatowaniem. Nie można zmienić tego ustawienia.| [Podstawowe opcje EditorConfig](../../ide/create-portable-custom-editor-options.md)<br/>[Opcje formatowania programu .NET EditorConfig](/dotnet/fundamentals/code-analysis/style-rules/formatting-rules)<br/><br/>**Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  Język **C#**  >  **Formatowanie** > [**wcięcia** lub **nowe wiersze** , **odstępy** lub **Zawijanie**]|
|**Wykonaj Dodawanie czyszczenia kodu podczas formatowania**|Po wybraniu programu stosuje poprawki dla reguł wymienionych poniżej w polecenie **Edit. FormatDocument** .| Brak |
|**Usuń niepotrzebne użycia**|Po wybraniu powoduje usunięcie niepotrzebnych `using` dyrektyw podczas wyzwalania **Edit. FormatDocument** .| Brak |
|**Sortowanie deklaracji using**|Po wybraniu sortuje `using` dyrektywy, gdy zostanie wyzwolone polecenie **Edit. FormatDocument** .| dotnet_sort_system_directives_first<br/><br/>**Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  Język **C#**  >  **Zaawansowane**  >  **Umieść dyrektywy "system" jako pierwsze podczas sortowania przy użyciu** |
|**Dodawanie/usuwanie nawiasów klamrowych dla jednowierszowych instrukcji sterujących**|Po zaznaczeniu, dodaje lub usuwa nawiasy klamrowe z instrukcji kontroli jednowierszowej, gdy jest wyzwalany plik **Edit. FormatDocument** .| csharp_prefer_braces<br/><br/>**Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  Język **C#**  >  **Styl kodu**  >  **Preferencje**  >  bloku kodu **Preferuj nawiasy klamrowe** |
|**Dodaj Modyfikatory dostępności**|Po wybraniu dodaje brakujące Modyfikatory dostępności podczas uruchamiania funkcji **Edit. FormatDocument** .| dotnet_style_require_accessibility_modifiers |
|**Sortuj Modyfikatory dostępności**|Po wybraniu sortuje Modyfikatory dostępności podczas uruchamiania funkcji **Edit. FormatDocument** .| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**Zastosuj preferencje dla treści wyrażenia/bloku**|Gdy ta opcja jest zaznaczona, konwertuje składowe wyrażeń w celu blokowania treści lub na odwrót, gdy zostanie wyzwolone polecenie **Edit. FormatDocument** .| [Opcje EditorConfig składowej w postaci wyrażeń](/dotnet/fundamentals/code-analysis/style-rules/language-rules#expression-bodied-members)<br/><br/>**Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  Język **C#**  >  **Styl kodu**  >  **Preferencje wyrażenia**  >  **Użyj treści wyrażenia dla metod, konstruktorów itp.** |
|**Zastosuj preferencje typu niejawnego/jawnego**|Gdy jest zaznaczone, konwertuje `var` na typ jawny lub na odwrót, gdy zostanie wyzwolone polecenie **Edit. FormatDocument** .| [Opcje EditorConfig typu jawnego](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types)<br/><br/>**Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  Język **C#**  >  **Styl kodu**  >  **Preferencje "var"** |
|**Zastosuj preferencje wbudowanych zmiennych "out"**|Gdy ta pozycja jest zaznaczona, zmienne są podkreślane, gdy `out` jest to możliwe, gdy zostanie wyzwolone polecenie **Edit. FormatDocument** .| csharp_style_inlined_variable_declaration<br/><br/>**Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  Język **C#**  >  **Styl kodu**  >  **Preferencje zmiennych**  >  **Preferuj wbudowaną deklarację zmiennej** |
|**Zastosuj preferencje typu języka/platformy**|Gdy ta opcja jest zaznaczona, konwertuje typy języków na typy struktur lub na odwrót, gdy zostanie wyzwolone polecenie **Edit. FormatDocument** .| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>**Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  Język **C#**  >  **Styl kodu**  >  **Preferencje wstępnie zdefiniowanego typu** |
|**Zastosuj preferencje inicjowania obiektów/kolekcji**|Po wybraniu program używa inicjatorów obiektów i kolekcji, gdy jest to możliwe, gdy zostanie wyzwolone polecenie **Edit. FormatDocument** .| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>**Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  Język **C#**  >  **Styl kodu**  >  **Preferencje wyrażenia**  >  **Preferuj Inicjator obiektu** lub **Preferuj inicjator kolekcji** |
|**Zastosuj preferencje kwalifikacji "this."**|Po wybraniu programu stosuje się `this.` Preferencje podczas wyzwolenia **Edit. FormatDocument** .| [Ta. Opcje EditorConfig kwalifikacji](/dotnet/fundamentals/code-analysis/style-rules/language-rules#this-and-me)<br/><br/>**Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  Język **C#**  >  **Styl kodu**  >  **Preferencje "this."** |
|**Ustaw prywatne pola jako tylko do odczytu, gdy jest to możliwe**|Gdy jest zaznaczone, program udostępnia pola prywatne, gdy `readonly` jest to możliwe, gdy jest wyzwalana funkcja **Edit. FormatDocument** .| dotnet_style_readonly_field<br/><br/>**Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  Język **C#**  >  **Styl kodu**  >  **Preferencje pola**  >  **Preferuj tylko do odczytu** |
|**Usuń niepotrzebne rzuty**|Gdy jest zaznaczone, program usuwa zbędne rzuty, gdy jest to możliwe, gdy zostanie wyzwolone polecenie **Edit. FormatDocument** .| Brak |
|**Usuń nieużywane zmienne**|Po zaznaczeniu usuwa zmienne, które nie są używane podczas uruchamiania **Edit. FormatDocument** .| Brak |

![Ustawienia czyszczenia kodu dla języka C# w programie Visual Studio](media/format-document-settings.png)

::: moniker-end

## <a name="indentation-page"></a>Strona wcięcia

Opcje wcięć na tej stronie są stosowane, gdy kod jest formatowany automatycznie. Przykładem, gdy kod jest automatycznie formatowany jest podczas wklejania kodu do pliku, podczas gdy jest zaznaczone **Automatyczne formatowanie podczas wklejania** . (Opcja **automatycznego formatowania przy wklejaniu** jest w obszarze **Formatowanie**  >  **Ogólne**).

![Opcje wcięć edytora tekstu w języku C# w programie Visual Studio](media/csharp-indentation-options.png)

> [!TIP]
> Dostępne są również opcje wcięć na **Text Editor**  >  **C#**  >  stronie opcje**kart** edytora tekstu C#. Te opcje określają tylko miejsce, w którym Edytor kodu umieszcza kursor po naciśnięciu klawisza **Enter** na końcu wiersza.
>
> ![Opcje kart edytora tekstu w języku C# w programie Visual Studio](media/csharp-tabs-options.png)

## <a name="see-also"></a>Zobacz też

- [Ogólne, środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
