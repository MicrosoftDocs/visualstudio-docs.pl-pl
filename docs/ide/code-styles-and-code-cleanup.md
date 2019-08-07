---
title: Opcje stylu kodu i czyszczenie kodu
ms.date: 04/25/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 4c7bb8f3e94a761023a19a5ea3361073b73d9f3b
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2019
ms.locfileid: "68822436"
---
# <a name="code-style-preferences"></a>Preferencje stylu kodu

Można zdefiniować ustawienia stylu kodu dla każdego projektu przy użyciu [pliku EditorConfig](#code-styles-in-editorconfig-files)lub dla całego kodu edytowanego w programie Visual Studio na [stronie **Opcje** ](#code-styles-in-the-options-dialog-box)edytora tekstu. W C# przypadku kodu można także skonfigurować program Visual Studio, aby stosował te preferencje stylu kodu za pomocą poleceń **czyszczenia kodu** (Visual Studio 2019) i **formatowania dokumentu** (Visual Studio 2017).

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [zachowanie edytora w programie Visual Studio dla komputerów Mac](/visualstudio/mac/editor-behavior).

## <a name="code-styles-in-editorconfig-files"></a>Style kodu w plikach EditorConfig

[Ustawienia stylu kodu](../ide/editorconfig-code-style-settings-reference.md) dla platformy .NET można określić, dodając plik [EditorConfig](create-portable-custom-editor-options.md) do projektu. Pliki EditorConfig są skojarzone z bazą kodu, a nie kontem personalizacji programu Visual Studio. Ustawienia w pliku EditorConfig mają pierwszeństwo przed stylami kodu, które są określone w oknie dialogowym **Opcje** . Użyj pliku EditorConfig, jeśli chcesz wymusić style kodowania dla wszystkich współautorów w repozytorium lub projekcie.

::: moniker range=">=vs-2019"

Możesz ręcznie wypełnić plik EditorConfig lub można automatycznie wygenerować plik na podstawie ustawień stylu kodu, które zostały wybrane w oknie dialogowym **Opcje** programu Visual Studio. Ta strona opcji jest dostępna w obszarze **Narzędzia** > **Opcje** > **Edytor tekstu** >**C#** [lub **podstawowa**] > **stylu** > kodu**ogólnego**. Kliknij pozycję **Generuj plik editorconfig z ustawień** , aby automatycznie wygenerować plik z kodowaniem style *. editorconfig* na podstawie ustawień na stronie **Opcje** .

![Generuj plik editorconfig na podstawie ustawień w programie Visual Studio 2019](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

## <a name="code-styles-in-the-options-dialog-box"></a>Style kodu w oknie dialogowym Opcje

Preferencje stylu kodu można ustawić dla wszystkich projektów C# i Visual Basic, otwierając okno dialogowe **Opcje** z menu **Narzędzia** . W **opcje** okno dialogowe, wybierz opcję **edytora tekstów** > [**C#** lub **podstawowe**] > **styl kodu**  >  **Ogólne**.

Każdy element na liście pokazuje jego podgląd preferencji, w przypadku wybrania:

::: moniker range="vs-2017"

![Opcje stylu kodu](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Opcje stylu kodu](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

Opcje ustawione w tym oknie dotyczą konta personalizacji programu Visual Studio i nie są skojarzone z określonym projektem lub bazą kodu. Ponadto nie są wymuszane w czasie kompilacji, w tym w kompilacjach ciągłej integracji (CI). Jeśli chcesz skojarzyć preferencje stylu kodu z projektem i mieć style wymuszane podczas kompilacji, określ preferencje w [pliku editorconfig](#code-styles-in-editorconfig-files) , który jest skojarzony z projektem.

### <a name="preference-and-severity"></a>Preferencji i ważność

Dla każdego ustawienia stylu kodu na tej stronie można ustawić wartości **preferencji** i **ważności** przy użyciu list rozwijanych w każdym wierszu. Ważność można ustawić tylko do **refaktoryzacji**, sugestii, **ostrzeżenia**lub **błędu**. Jeśli chcesz włączyć [szybkie akcje](../ide/quick-actions.md) dla stylu kodu, upewnij się, że ustawienie **ważności** ma wartość inne niż **tylko Refaktoryzacja**. W przypadku używania stylu niepreferowanego](media/light-bulb-dropdown.png)żarówki żarówki ![z lampą](media/error-bulb.png) ![szybkich świateł, ![błąd żarówki lub](media/screwdriver.png) ikona śrubokrętu śrubokrętu. można też wybrać opcję na liście **szybkie akcje** , aby automatycznie ponownie napisać kod do preferowanego stylu.

## <a name="apply-code-styles"></a>Zastosuj style kodu

::: moniker range="vs-2017"

Można skonfigurować polecenie **Formatuj dokument** (**Edytuj** > **dokument w formacie** **zaawansowanym** > ), aby zastosować ustawienia stylu kodu (z EditorConfig pliku lub opcji **stylu kodu** ) wraz z regularne formatowanie, które wykonuje (takie jak wcięcia). Jeśli plik *. editorconfig* istnieje dla projektu, te ustawienia mają pierwszeństwo.

> [!NOTE]
> Stosowanie stylów kodu przy użyciu polecenia **Formatuj dokument** jest dostępne tylko dla C# plików kodu. Jest to funkcja eksperymentalna.

Skonfiguruj ustawienia, które mają być stosowane do formatowania **dokumentu** na [stronie opcje formatowania](reference/options-text-editor-csharp-formatting.md#format-document-settings).

![Ustawienia stylu kodu dla dokumentu formatu w programie Visual Studio 2017](media/format-document-settings-experiment.png)

> [!TIP]
> Reguły skonfigurowane z ważnością **none** nie uczestniczą w oczyszczaniu kodu, ale mogą być stosowane indywidualnie za pośrednictwem menu **szybkie akcje i operacje refaktoryzacji** .

Przy pierwszym wyzwoleniu polecenia **formatowania dokumentu** żółty pasek informacyjny poprosi o skonfigurowanie ustawień oczyszczania kodu.

::: moniker-end

::: moniker range=">=vs-2019"

W C# przypadku plików kodu program Visual Studio 2019 ma przycisk **czyszczenia kodu** u dołu edytora (klawiatura: **Ctrl** **K,** CtrlE+), aby zastosować style kodu z pliku EditorConfig lub ze strony opcje **stylu kodu.** + Jeśli plik *. editorconfig* istnieje dla projektu, są to ustawienia, które mają pierwszeństwo.

![Wykonaj czyszczenie kodu w programie Visual Studio 2019](media/execute-code-cleanup.png)

> [!TIP]
> Reguły skonfigurowane z ważnością **none** nie uczestniczą w oczyszczaniu kodu, ale mogą być stosowane indywidualnie za pośrednictwem menu **szybkie akcje i operacje refaktoryzacji** .

Najpierw skonfiguruj style kodu, które mają być stosowane (w jednym z dwóch profilów) w oknie dialogowym **Konfiguruj oczyszczanie kodu** . Aby otworzyć to okno dialogowe, kliknij strzałkę rozwijania obok ikony Broom oczyszczania kodu, a następnie wybierz pozycję **Konfiguruj oczyszczanie kodu**.

![Konfigurowanie czyszczenia kodu w programie Visual Studio 2019](media/configure-code-cleanup.png)

Po skonfigurowaniu czyszczenia kodu możesz kliknąć ikonę Broom lub nacisnąć klawisze **Ctrl**+**K**, **Ctrl**+**E** , aby uruchomić oczyszczanie kodu. Możesz również uruchomić oczyszczanie kodu w całym projekcie lub rozwiązaniu. Kliknij prawym przyciskiem myszy nazwę projektu lub rozwiązania w **Eksplorator rozwiązań**, wybierz pozycję **Analizuj i wyczyść kod**, a następnie wybierz polecenie **Uruchom oczyszczanie kodu**.

![Uruchom oczyszczanie kodu w całym projekcie lub rozwiązaniu](media/run-code-cleanup-project-solution.png)

Jeśli chcesz, aby ustawienia stylu kodu były stosowane za każdym razem, gdy zapisujesz plik, możesz jak [oczyścić kod przy](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.CodeCleanupOnSave) rozszerzeniu Zapisz.

::: moniker-end

## <a name="see-also"></a>Zobacz także

- [Szybkie akcje](../ide/quick-actions.md)
- [.NET coding convention ustawienia dla wtyczki EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
- [Zachowanie edytora (Visual Studio dla komputerów Mac)](/visualstudio/mac/editor-behavior)
