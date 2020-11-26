---
title: Opcje stylu kodu i czyszczenie kodu
description: Dowiedz się, jak skonfigurować program Visual Studio, aby stosować preferencje stylu kodu za pomocą poleceń czyszczenia kodu (Visual Studio 2019) i formatowania dokumentu (Visual Studio 2017).
ms.custom: SEO-VS-2020
ms.date: 04/25/2019
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 9172fff2dde1528c5ea382aea996d316e0738ea0
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189748"
---
# <a name="code-style-preferences"></a>Preferencje stylu kodu

Można zdefiniować ustawienia stylu kodu dla każdego projektu przy użyciu [pliku EditorConfig](#code-styles-in-editorconfig-files)lub dla całego kodu edytowanego w programie Visual Studio na [stronie **Opcje**](#code-styles-in-the-options-dialog-box)edytora tekstu. W przypadku kodu w języku C# można także skonfigurować program Visual Studio, aby zastosować te preferencje stylu kodu przy użyciu poleceń **czyszczenia kodu** (visual Studio 2019) i **formatowania dokumentu** (Visual Studio 2017).

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [zachowanie edytora w programie Visual Studio dla komputerów Mac](/visualstudio/mac/editor-behavior).

## <a name="code-styles-in-editorconfig-files"></a>Style kodu w plikach EditorConfig

[Ustawienia stylu kodu](/dotnet/fundamentals/code-analysis/code-style-rule-options) dla platformy .NET można określić, dodając plik [EditorConfig](create-portable-custom-editor-options.md) do projektu. Pliki EditorConfig są skojarzone z bazą kodu, a nie kontem personalizacji programu Visual Studio. Ustawienia w pliku EditorConfig mają pierwszeństwo przed stylami kodu, które są określone w oknie dialogowym **Opcje** . Użyj pliku EditorConfig, jeśli chcesz wymusić style kodowania dla wszystkich współautorów w repozytorium lub projekcie.

::: moniker range=">=vs-2019"

Możesz ręcznie wypełnić plik EditorConfig lub można automatycznie wygenerować plik na podstawie ustawień stylu kodu, które zostały wybrane w oknie dialogowym **Opcje** programu Visual Studio. Ta strona opcji jest dostępna w obszarze **Narzędzia**  >  **Opcje**  >  **edytora tekstu** > [**C#** lub **Basic**] > ogólny **styl kodu**  >  **General**. Kliknij pozycję **Generuj plik editorconfig z ustawień** , aby automatycznie wygenerować plik z kodowaniem style *. editorconfig* na podstawie ustawień na stronie **Opcje** .

![Generuj plik editorconfig na podstawie ustawień w programie Visual Studio 2019](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

## <a name="code-styles-in-the-options-dialog-box"></a>Style kodu w oknie dialogowym Opcje

Preferencje stylu kodu można ustawić dla wszystkich projektów C# i Visual Basic, otwierając okno dialogowe **Opcje** z menu **Narzędzia** . W oknie dialogowym **Opcje** wybierz pozycję **Edytor tekstu** > [**C#** lub **Basic**] > ogólny **styl kodu**  >  **General**.

Każdy element na liście zawiera podgląd preferencji, gdy jest zaznaczone:

::: moniker range="vs-2017"

![Opcje stylu kodu](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Opcje stylu kodu](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

Opcje ustawione w tym oknie dotyczą konta personalizacji programu Visual Studio i nie są skojarzone z określonym projektem lub bazą kodu. Ponadto nie są wymuszane w czasie kompilacji, w tym w kompilacjach ciągłej integracji (CI). Jeśli chcesz skojarzyć preferencje stylu kodu z projektem i mieć style wymuszane podczas kompilacji, określ preferencje w [pliku editorconfig](#code-styles-in-editorconfig-files) , który jest skojarzony z projektem.

### <a name="preference-and-severity"></a>Preferencja i ważność

Dla każdego ustawienia stylu kodu na tej stronie można ustawić wartości **preferencji** i **ważności** przy użyciu list rozwijanych w każdym wierszu. Ważność można ustawić tylko do **refaktoryzacji**, **sugestii**, **ostrzeżenia** lub **błędu**. Jeśli chcesz włączyć [szybkie akcje](../ide/quick-actions.md) dla stylu kodu, upewnij się, że ustawienie **ważności** ma wartość inne niż **tylko Refaktoryzacja**. Żarówka **Quick Actions** , żarówka :::image type="icon" source="media/light-bulb-dropdown.png"::: o błędach :::image type="icon" source="media/error-bulb.png"::: lub ikona śrubokrętu :::image type="icon" source="media/screwdriver.png"::: pojawia się, gdy używany jest styl niepreferowany i można wybrać opcję na liście **szybkie akcje** , aby automatycznie ponownie napisać kod do preferowanego stylu.

::: moniker range=">=vs-2019"

## <a name="enforce-code-styles-on-build"></a>Wymuś style kodu podczas kompilacji

Począwszy od programu Visual Studio 2019 w wersji 16,8, który zawiera zestaw SDK dla programu .NET 5,0 RC2, można [wymusić stosowanie konwencji kodowania .NET na potrzeby kompilacji](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis) dla wszystkich projektów .NET. W czasie kompilacji naruszenia stylu kodu platformy .NET będą wyświetlane jako ostrzeżenia lub błędy z prefiksem "IDE". Pozwala to na ścisłe wymuszanie spójnych stylów kodu w bazie kodu.

::: moniker-end

## <a name="apply-code-styles"></a>Zastosuj style kodu

::: moniker range="vs-2017"

Można skonfigurować polecenie **Formatuj dokument** (**Edytuj**  >  **Advanced**  >  **dokument w formacie** zaawansowanym), aby zastosować ustawienia stylu kodu (z EditorConfig pliku lub opcji **stylu kodu** ) wraz z regularnym formatowaniem (na przykład wcięciem). Jeśli plik *. editorconfig* istnieje dla projektu, te ustawienia mają pierwszeństwo.

> [!NOTE]
> Stosowanie stylów kodu przy użyciu polecenia **Formatuj dokument** jest dostępne tylko dla plików kodu C#. Jest to funkcja eksperymentalna.

Skonfiguruj ustawienia, które mają być stosowane do formatowania **dokumentu** na [stronie opcje formatowania](reference/options-text-editor-csharp-formatting.md#format-document-settings).

![Ustawienia stylu kodu dla dokumentu formatu w programie Visual Studio 2017](media/format-document-settings-experiment.png)

> [!TIP]
> Reguły skonfigurowane z ważnością **none** nie uczestniczą w oczyszczaniu kodu, ale mogą być stosowane indywidualnie za pośrednictwem menu **szybkie akcje i operacje refaktoryzacji** .

Przy pierwszym wyzwoleniu polecenia **formatowania dokumentu** żółty pasek informacyjny poprosi o skonfigurowanie ustawień oczyszczania kodu.

::: moniker-end

::: moniker range=">=vs-2019"

W przypadku plików kodu C# Program Visual Studio 2019 ma przycisk **czyszczenia kodu** w dolnej części edytora (klawiatura: **Ctrl** + **K**, **Ctrl** + **E**), aby zastosować style kodu z pliku EditorConfig lub ze strony opcje **stylu kodu** . Jeśli plik *. editorconfig* istnieje dla projektu, są to ustawienia, które mają pierwszeństwo.

![Wykonaj czyszczenie kodu w programie Visual Studio 2019](media/execute-code-cleanup.png)

> [!TIP]
> Reguły skonfigurowane z ważnością **none** nie uczestniczą w oczyszczaniu kodu, ale mogą być stosowane indywidualnie za pośrednictwem menu **szybkie akcje i operacje refaktoryzacji** .

Najpierw skonfiguruj style kodu, które mają być stosowane (w jednym z dwóch profilów) w oknie dialogowym **Konfiguruj oczyszczanie kodu** . Aby otworzyć to okno dialogowe, kliknij strzałkę rozwijania obok ikony Broom oczyszczania kodu, a następnie wybierz pozycję **Konfiguruj oczyszczanie kodu**.

![Konfigurowanie czyszczenia kodu w programie Visual Studio 2019](media/configure-code-cleanup.png)

Po skonfigurowaniu czyszczenia kodu możesz kliknąć ikonę Broom lub nacisnąć klawisze **Ctrl** + **K**, **Ctrl** + **E** , aby uruchomić oczyszczanie kodu. Możesz również uruchomić oczyszczanie kodu w całym projekcie lub rozwiązaniu. Kliknij prawym przyciskiem myszy nazwę projektu lub rozwiązania w **Eksplorator rozwiązań**, wybierz pozycję **Analizuj i wyczyść kod**, a następnie wybierz polecenie **Uruchom oczyszczanie kodu**.

![Uruchom oczyszczanie kodu w całym projekcie lub rozwiązaniu](media/run-code-cleanup-project-solution.png)

Jeśli chcesz, aby ustawienia stylu kodu były stosowane za każdym razem, gdy zapisujesz plik, możesz jak [oczyścić kod przy](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.CodeCleanupOnSave) rozszerzeniu Zapisz.

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Szybkie akcje](../ide/quick-actions.md)
- [Ustawienia konwencji kodowania .NET dla EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options)
- [Zachowanie edytora (Visual Studio dla komputerów Mac)](/visualstudio/mac/editor-behavior)
