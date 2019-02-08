---
title: C# edytora opcje formatowania
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ec1847f30f5c04bd32ddea85ff95a0808daa8aa7
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55934383"
---
# <a name="options-text-editor-c-code-style-formatting"></a>Opcje, Edytor tekstu, C#, styl i formatowanie kodu

Użyj **formatowanie** Strona opcji, aby ustawić opcje formatowania kodu w edytorze kodu. Aby uzyskać dostęp do tej strony Opcje, wybierz opcję **narzędzia** > **opcje**. W **opcje** okna dialogowego wybierz **edytora tekstów** > **C#** > **styl kodu**  >  **Formatowanie**.

## <a name="general-page"></a>Strona Ogólne

### <a name="general-settings"></a>Ustawienia ogólne

Te ustawienia mają wpływ na *podczas* edytora kodu stosuje opcji formatowania do kodu.

|Etykieta|Opis|
|-----------|-----------------|
|**Formatuj automatycznie podczas pisania**|W przeciwnym wypadku **Formatuj instrukcję;** i **sformatuj blok w}** opcje zostaną wyłączone.|
|**Automatycznie Formatuj instrukcję**|Po wybraniu formatuje instrukcji po ukończeniu zgodnie z opcjami formatowania, wybrany dla edytora.|
|**Automatycznie sformatuj blok w}**|Po wybraniu formatów kodu bloki zgodnie z opcjami formatowania, wybrany dla edytora zaraz po wykonaniu bloku kodu.|
|**Automatycznie Formatuj przy powrocie**|Po wybraniu formatowania tekstu po **Enter** jest wciśnięty, aby dopasować opcje formatowania, wybrany dla edytora.|
|**Automatycznie Formatuj przy wklejaniu**|Po wybraniu formatuje tekst, który jest wklejany do edytora, aby dopasować opcje formatowania, wybrany dla edytora.|

### <a name="format-document-settings"></a>Format ustawień dokumentów

Te ustawienia skonfigurować **Formatuj dokument** polecenia do wykonywania oczyszczania dodatkowy kod w pliku. Aby uzyskać więcej informacji na temat sposobu stosowania tych ustawień, zobacz [polecenia dokumentu w formacie](../code-styles-and-quick-actions.md#format-document-command).

|Etykieta|Opis|Odpowiednie polecenie EditorConfig i narzędzia > Opcje zasad|
|-----------|-----------------|-----------------|-----------------|
|**Zastosuj wszystkie C# (wcięcia zawijania, odstępy) reguły formatowania**|**Formatuj dokument** polecenia zawsze poprawek formatowania problemów. Nie można zmienić tego ustawienia.| [Podstawowe opcje polecenia EditorConfig](../../ide/create-portable-custom-editor-options.md)<br/>[Opcje formatowania narzędzia .NET EditorConfig](../../ide/editorconfig-code-style-settings-reference.md#formatting-conventions)<br/><br/>**Narzędzia** > **opcje** > **edytora tekstów**  >  **C#**  >   **Formatowanie** > [**wcięcia** lub **nowe wiersze** lub **odstępy** lub **zawijania**]|
|**Wykonania oczyszczania kodu dodawania podczas formatowania**|Po wybraniu stosuje poprawki dla reguł określonych poniżej na **Edit.FormatDocument** polecenia.| Brak |
|**Usuń niepotrzebne użycia**|Po wybraniu usuwa niepotrzebne `using` dyrektywy podczas **Edit.FormatDocument** zostanie wywołany.| Brak |
|**Sortuj deklaracje Using**|Po wybraniu sortuje `using` dyrektywy podczas **Edit.FormatDocument** zostanie wywołany.| dotnet_sort_system_directives_first<br/><br/>**Narzędzia** > **opcje** > **edytora tekstów** > **C#** > **zaawansowane**   >  **Miejsce "System" dyrektywy pierwsze podczas sortowania deklaracji Using** |
|**Dodaj/Usuń nawiasy klamrowe dla instrukcji sterowania jednowierszowy**|Po wybraniu dodaje lub usuwa nawiasy klamrowe z instrukcji sterowania jednowierszowego podczas **Edit.FormatDocument** zostanie wywołany.| csharp_prefer_braces<br/><br/>**Narzędzia** > **opcje** > **edytora tekstów** > **C#** > **styl kodu**   >  **Preferencje bloku kodu** > **Preferuj klamry** |
|**Dodaj modyfikatory dostępności**|Po wybraniu dodaje brakujące modyfikatory dostępności podczas **Edit.FormatDocument** zostanie wywołany.| dotnet_style_require_accessibility_modifiers |
|**Modyfikatory dostępności sortowania**|Po wybraniu sortuje modyfikatory dostępności podczas **Edit.FormatDocument** zostanie wywołany.| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**Zastosuj preferencje treści wyrażenia lub blokowanie ich**|Po wybraniu konwertuje wyrażeniem elementów członkowskich, aby zablokować treści, lub na odwrót, gdy **Edit.FormatDocument** zostanie wywołany.| [Opcje polecenia EditorConfig wyrażeniem składowej](../../ide/editorconfig-code-style-settings-reference.md#expression_bodied_members)<br/><br/>**Narzędzia** > **opcje** > **edytora tekstów** > **C#** > **styl kodu**   >  **Preferencje wyrażeń** > **Użyj treści wyrażenia dla metod, konstruktory itp.** |
|**Zastosuj niejawnej/jawnej preferencjach**|Po wybraniu konwertuje `var` na typ jawny lub na odwrót, gdy **Edit.FormatDocument** zostanie wywołany.| [Opcje polecenia EditorConfig jawnego typu](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types)<br/><br/>**Narzędzia** > **opcje** > **edytora tekstów** > **C#** > **styl kodu**   >  **preferencje "var"** |
|**Zastosuj wbudowane zmienne preferencji "out"**|Po wybraniu inlines `out` zmienne gdzie to możliwe, gdy **Edit.FormatDocument** zostanie wywołany.| csharp_style_inlined_variable_declaration<br/><br/>**Narzędzia** > **opcje** > **edytora tekstów** > **C#** > **styl kodu**   >  **Preferencje zmiennej** > **Preferuj śródwierszową deklarację zmiennej** |
|**Zastosuj preferencjach języka/platformy**|Po wybraniu konwertuje typy języka na typy framework lub na odwrót, gdy **Edit.FormatDocument** zostanie wywołany.| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>**Narzędzia** > **opcje** > **edytora tekstów** > **C#** > **styl kodu**   >  **wstępnie zdefiniowane preferencjach** |
|**Zastosuj preferencje inicjowania obiektu/kolekcji**|Po wybraniu używa inicjatorów obiektów i kolekcji, jeśli jest to możliwe po **Edit.FormatDocument** zostanie wywołany.| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>**Narzędzia** > **opcje** > **edytora tekstów** > **C#** > **styl kodu**   >  **Preferencje wyrażeń** > **Preferuj Inicjator obiektu** lub **Preferuj inicjator kolekcji** |
|**Zastosuj "this." Preferencje kwalifikacji**|Po wybraniu stosuje `this.` preferencje podczas **Edit.FormatDocument** zostanie wywołany.| [Ta. Opcje polecenia EditorConfig kwalifikacji](../../ide/editorconfig-code-style-settings-reference.md#this_and_me)<br/><br/>**Narzędzia** > **opcje** > **edytora tekstów** > **C#** > **styl kodu**   >  **preferencje "this".** |
|**Wprowadź pola prywatne tylko do odczytu, gdy jest to możliwe**|Po wybraniu sprawia, że pola prywatne `readonly` gdzie to możliwe, gdy **Edit.FormatDocument** zostanie wywołany.| dotnet_style_readonly_field<br/><br/>**Narzędzia** > **opcje** > **edytora tekstów** > **C#** > **styl kodu**   >  **Pola preferencje** > **Preferuj tylko do odczytu** |
|**Usuń niepotrzebne rzutowanie**|Po wybraniu usuwa niepotrzebne rzutowanie, gdzie to możliwe po **Edit.FormatDocument** zostanie wywołany.| Brak |
|**Usuń nieużywane zmienne**|Po wybraniu usuwa zmienne, które nie są używane, kiedy **Edit.FormatDocument** zostanie wywołany.| Brak |

![Ustawienia oczyszczania kodu dla języka C# w programie Visual Studio](media/format-document-settings.png)

## <a name="preview-windows"></a>Windows (wersja zapoznawcza)

**Wcięcia**, **nowe wiersze**, **odstępy**, i **zawijania** podstrony każdego wyświetlić okno podglądu u dołu. Okno podglądu przedstawiono wpływ poszczególnych opcji. Aby użyć okno podglądu, wybierz opcję formatowania. Okno podglądu pokazano przykład odpowiadającego wybranej opcji. Po zmianie ustawienia przez wybranie przycisku radiowego lub okienka do zaznaczenia, aktualizacje okna (wersja zapoznawcza), aby pokazać efekt nowe ustawienie.

## <a name="indentation-remarks"></a>Uwagi wcięć

Wcięcie opcji na **karty** stron dla każdego z języków tylko określić, gdzie edytora kodu umieszcza kursor po naciśnięciu klawisza **Enter** na końcu wiersza. Wcięcie opcji w obszarze **formatowanie** są stosowane, gdy kod jest formatowana automatycznie, na przykład po wklejeniu kodu do pliku podczas **automatycznie Formatuj przy wklejaniu** jest zaznaczone i kiedy bloku formatowana jest wpisany ręcznie.

## <a name="see-also"></a>Zobacz także

- [Okno dialogowe Ogólne, środowisko, opcje](../../ide/reference/general-environment-options-dialog-box.md)