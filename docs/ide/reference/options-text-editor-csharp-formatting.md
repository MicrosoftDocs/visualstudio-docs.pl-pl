---
title: Opcje formatowania edytora języka C#
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
ms.openlocfilehash: 1176232eb3354a9b425e9432eb83037367ee7706
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303079"
---
# <a name="options-dialog-box-text-editor--c--code-style--formatting"></a>Okno dialogowe Opcje: \> Formatowanie \> stylu kodu Edytora \> tekstu C#

Strona Opcje **formatowania** i jej podstrony[**(Wcięcie,**](#indentation-page) **Nowe wiersze,** **Odstępy**i **Zawijanie)** umożliwia ustawienie opcji formatowania kodu w edytorze kodu.

Aby uzyskać dostęp do tej strony opcji, wybierz pozycję**Opcje** **narzędzi** > z paska menu. W oknie dialogowym **Opcje** wybierz pozycję**Formatowanie****stylu kodu** >  **Edytora** > **tekstu C#** > .

> [!TIP]
> **Podstrony wcięcie,** **Nowe wiersze**, **Odstępy**i **Zawijanie** wyświetlają na dole okno podglądu, które pokazuje efekt każdej opcji. Aby użyć okna podglądu, wybierz opcję formatowania. W oknie podglądu pokazano przykład wybranej opcji. Po zmianie ustawienia przez zaznaczenie przycisku opcji lub pola wyboru okno podglądu zostanie zaktualizowane, aby wyświetlić efekt nowego ustawienia.

## <a name="formatting-general-page"></a>Strona formatowania (ogólne)

### <a name="general-settings"></a>Ustawienia ogólne

Te ustawienia mają *wpływ, gdy* edytor kodu stosuje opcje formatowania do kodu.

|Label|Opis|
|-----------|-----------------|
|**Automatyczne formatowanie podczas pisania**|Po usunięciu zaznaczenia **instrukcja formatu na ;** i **format bloku na }** opcje są wyłączone.|
|**Automatyczne formatowanie instrukcji na ;**|Po wybraniu tej opcji formatuje instrukcje po zakończeniu zgodnie z opcjami formatowania wybranymi dla edytora.|
|**Automatyczne formatowanie bloku na }**|Po wybraniu tej opcji formatuje bloki kodu zgodnie z opcjami formatowania wybranymi dla edytora zaraz po zakończeniu bloku kodu.|
|**Automatyczne formatowanie po zwrocie**|Gdy ta opcja jest zaznaczona, formatuje tekst po **naciśnięciu klawisza Enter,** aby dopasować opcje formatowania wybrane dla edytora.|
|**Automatyczne formatowanie przy wklejać**|Gdy ta opcja jest zaznaczona, formatuje tekst wklejany do edytora w celu dopasowania do opcji formatowania wybranych dla edytora.|

::: moniker range="vs-2019"

Jeśli wcześniej zastosowano ustawienia stylu kodu dla plików języka C# za pomocą polecenia **Format dokumentu** w programie Visual Studio 2017, ta funkcja jest teraz dostępna jako [**oczyszczanie kodu**](../code-styles-and-code-cleanup.md#apply-code-styles).

::: moniker-end

::: moniker range="vs-2017"

### <a name="format-document-settings"></a>Formatowanie ustawień dokumentu

Te ustawienia konfigurują polecenie **Format dokumentu** w celu wykonania dodatkowego oczyszczania kodu w pliku. Aby uzyskać więcej informacji o sposobie stosowania tych ustawień, zobacz [Polecenie Formatowanie dokumentu](../code-styles-and-code-cleanup.md#apply-code-styles).

|Label|Opis|Odpowiednie reguły EditorConfig i Narzędzia > Opcje|
|-----------|-----------------|-----------------|-----------------|
|**Zastosuj wszystkie reguły formatowania języka C# (wcięcie, zawijanie, odstępy)**|Polecenie **Formatuj dokument** zawsze rozwiązuje problemy z formatowaniem. Tego ustawienia nie można zmienić.| [Podstawowe opcje EditorConfig](../../ide/create-portable-custom-editor-options.md)<br/>[Opcje formatowania .NET EditorConfig](../../ide/editorconfig-formatting-conventions.md)<br/><br/>**Opcje narzędzi** > **Options****Edytor** > tekstu**C#** > **Formatowanie** > [**Wcięcie** lub **Nowe wiersze** lub **odstępy** lub **zawijanie**] > |
|**Oczyszczanie kodu dodawania podczas formatowania**|Gdy ta opcja jest zaznaczona, stosuje poprawki dla reguł określonych poniżej w poleceniu **Edit.FormatDocument.**| Nie dotyczy |
|**Usuwanie niepotrzebnych zaniechań**|Gdy ta opcja `using` jest zaznaczona, usuwa niepotrzebne dyrektywy po **wyzwoleniu pliku Edit.FormatDocument.**| Nie dotyczy |
|**Sortowanie za pomocą**|Gdy ta `using` opcja jest zaznaczona, sortuje dyrektywy po wyzwoleniu **pliku Edit.FormatDocument.**| dotnet_sort_system_directives_first<br/><br/>**Narzędzia** > **Opcje** > **Edytor** > tekstu**C#** > **Advanced** > **Place "System" dyrektywy najpierw podczas sortowania usings** |
|**Dodawanie/usuwanie nawiasów klamrowych dla instrukcji sterowania jednowierszowego**|Gdy ta opcja jest zaznaczona, dodaje lub usuwa nawiasy klamrowe z instrukcji sterowania jednowierszowego po wyzwoleniu **pliku Edit.FormatDocument.**| csharp_prefer_braces<br/><br/>**Opcje narzędzi** > **Options****Edytor** > tekstu**C#** > **Preferencje bloku kodu** > **styl** > kodu**Preferuj nawiasy klamrowe**  >  |
|**Dodawanie modyfikatorów ułatwień dostępu**|Gdy ta opcja jest zaznaczona, po wyzwoleniu **pliku Edit.FormatDocument** zostanie wyzwolona brakujące modyfikatory ułatwień dostępu.| dotnet_style_require_accessibility_modifiers |
|**Modyfikatory ułatwień dostępu sortowania**|Gdy ta opcja jest zaznaczona, sortuje modyfikatory ułatwień dostępu po wyzwoleniu **pliku Edit.FormatDocument.**| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**Stosowanie preferencji wyrażenia/bloku**|Gdy ta opcja jest zaznaczona, konwertuje elementy członkowskie zabudowane wyrażeniam na obiekty blokowe lub odwrotnie, gdy zostanie wyzwolona **funkcja Edit.FormatDocument.**| [Opcje editorconfig z wyrazami zabudowanych wyrazami](../../ide/editorconfig-language-conventions.md#expression-bodied-members)<br/><br/>**Narzędzia** > **Opcje** > **Edytor** > tekstu**C#** > **Preferencje** > wyrażenia**stylu** > kodu**Użyj treści wyrażenia dla metod, konstruktorów itp.** |
|**Stosowanie preferencji typu niejawnego/jawnego**|Gdy ta opcja `var` jest zaznaczona, jest konwertowana na typ jawny lub odwrotnie po wyzwoleniu **pliku Edit.FormatDocument.**| [Opcje typu editor typu jawnego](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types)<br/><br/>**Opcje narzędzi** > **Options****Edytor** > tekstu**C#** >  > **Preferencje "var"** stylu**kodu** >  |
|**Stosowanie wbudowanych preferencji zmiennych "out"**|Gdy ta opcja `out` jest zaznaczona, zmienne wbudowane są tam, gdzie to możliwe, gdy wyzwalany jest **plik Edit.FormatDocument.**| csharp_style_inlined_variable_declaration<br/><br/>**Opcje narzędzi** > **Options****Edytor** > tekstu**C#** > **Preferencje** > zmiennej**stylu** > kodu**Preferuj deklarację zmiennej wbudowanej**  >  |
|**Stosowanie preferencji typu języka/struktury**|Gdy ta opcja jest zaznaczona, konwertuje typy języków na typy frameworków lub odwrotnie, gdy zostanie wyzwolona **funkcja Edit.FormatDocument.**| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>**Opcje** > **narzędzi** > **Edytor** > tekstu**C#** > **Preferencje typu** **styl** > kodu |
|**Stosowanie preferencji inicjowania obiektu/kolekcji**|Gdy ta opcja jest zaznaczona, używa inicjatorów obiektów i kolekcji, jeśli to możliwe, gdy zostanie wyzwolona **funkcja Edit.FormatDocument.**| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>**Opcje narzędzi** > **Options****Edytor** > tekstu**C#** > **Preferencje** > wyrażenia**stylu** > kodu**Preferuj inicjatora obiektu** lub **Preferuj inicjatora kolekcji**  >  |
|**Zastosuj preferencje kwalifikacji "to".**|Gdy ta opcja `this.` jest zaznaczona, stosuje preferencje po wyzwoleniu **programu Edit.FormatDocument.**| [Tę. opcje editora kwalifikacji](../../ide/editorconfig-language-conventions.md#this-and-me)<br/><br/>**Opcje narzędzi** > **Edytor** > tekstu**C#** > **Styl** > kodu **'this'' preferencje** **Options** >  |
|**W miarę możliwości odczytywanie pól prywatnych**|Gdy ta opcja `readonly` jest zaznaczona, pola prywatne są w miarę możliwości wyzwalane podczas wyzwalania **pliku Edit.FormatDocument.**| dotnet_style_readonly_field<br/><br/>**Opcje narzędzi** > **Options****Edytor** > tekstu**C#** > **Preferencje** > **pola stylu** > kodu**Preferuj tylko do odczytu**  >  |
|**Usuwanie niepotrzebnych odlewów**|Gdy ta opcja jest zaznaczona, usuwa niepotrzebne rzutowania, jeśli to możliwe, gdy zostanie wyzwolona **funkcja Edit.FormatDocument.**| Nie dotyczy |
|**Usuwanie nieużywanych zmiennych**|Gdy ta opcja jest zaznaczona, usuwa zmienne, które nie sąużywane po **wyzwoleniu pliku Edit.FormatDocument.**| Nie dotyczy |

![Ustawienia oczyszczania kodu dla języka C# w programie Visual Studio](media/format-document-settings.png)

::: moniker-end

## <a name="indentation-page"></a>Strona wcięcie

Opcje wcięci na tej stronie mają zastosowanie, gdy kod jest formatowany automatycznie. Jednym z przykładów automatycznego formatowania kodu jest wklejenie kodu do pliku podczas zaznaczenia **formatu automatycznie podczas wklejenia.** (Opcja **Format automatycznie na wklejanie** znajduje się w obszarze **Formatowanie** > **ogólne).**

![Opcje wcięcie edytora tekstu w języku C# w programie Visual Studio](media/csharp-indentation-options.png)

> [!TIP]
> Istnieją również opcje wcięci wycięcie na stronie opcji**kart** **Edytora** > **tekstu C#.** >  Te opcje określają tylko, gdzie edytor kodu umieszcza kursor po naciśnięciu **klawisza Enter** na końcu wiersza.
>
> ![Opcje kart edytora tekstu w języku C# w programie Visual Studio](media/csharp-tabs-options.png)

## <a name="see-also"></a>Zobacz też

- [Ogólne, Środowisko, Opcje, okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
