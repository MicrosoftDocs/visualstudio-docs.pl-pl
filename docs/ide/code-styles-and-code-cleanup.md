---
title: Opcje stylu kodu i oczyszczanie kodu
ms.date: 04/25/2019
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 9d540339ca25fc42fc05df4818a6d05204ccae0e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301861"
---
# <a name="code-style-preferences"></a>Preferencje stylu kodu

Ustawienia stylu kodu dla projektu można zdefiniować za pomocą [pliku EditorConfig](#code-styles-in-editorconfig-files)lub całego kodu edytowanego w programie Visual Studio na stronie [ **Opcje** ](#code-styles-in-the-options-dialog-box)edytora tekstu . Dla kodu języka C# można również skonfigurować visual studio, aby zastosować te preferencje stylu kodu za pomocą **oczyszczania kodu** (Visual Studio 2019) i **dokumentu formatu** (Visual Studio 2017) polecenia.

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. W przypadku programu Visual Studio dla komputerów Mac zobacz [Zachowanie edytora w programie Visual Studio dla komputerów Mac](/visualstudio/mac/editor-behavior).

## <a name="code-styles-in-editorconfig-files"></a>Style kodu w plikach EditorConfig

[Ustawienia stylu kodu](../ide/editorconfig-code-style-settings-reference.md) dla platformy .NET można określić, dodając plik [EditorConfig](create-portable-custom-editor-options.md) do projektu. EditorConfig pliki są skojarzone z codebase, a nie konto personalizacji programu Visual Studio. Ustawienia w pliku EditorConfig mają pierwszeństwo przed stylami kodu określonymi w oknie dialogowym **Opcje.** Użyj editorConfig pliku, jeśli chcesz wymusić kodowanie stylów dla wszystkich współautorów repozytorium lub projektu.

::: moniker range=">=vs-2019"

Można ręcznie wypełnić plik EditorConfig lub można automatycznie wygenerować plik na podstawie ustawień stylu kodu, które zostały wybrane w oknie dialogowym **Opcje** programu Visual Studio. Ta strona opcji jest dostępna w > — opcje **narzędzi** > **Options** > —**>** [**C#** lub **Basic**] > **Code Style** > **General**. Kliknij **pozycję Generuj plik .editorconfig z ustawień,** aby automatycznie wygenerować plik *.editorconfig* w stylu kodowania na podstawie ustawień na tej stronie **Opcje.**

![Generowanie pliku editorconfig z ustawień w programie Visual Studio 2019](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

## <a name="code-styles-in-the-options-dialog-box"></a>Style kodu w oknie dialogowym Opcje

Preferencje stylu kodu można ustawić dla wszystkich projektów języka C# i Visual Basic, otwierając okno dialogowe **Opcje** z menu **Narzędzia.** W oknie dialogowym **Opcje** wybierz pozycję **Edytor tekstu** > [**C#** lub **Basic**] >**Ogólne** **stylu** > kodu .

Każdy element na liście pokazuje podgląd preferencji po wybraniu:

::: moniker range="vs-2017"

![Opcje stylu kodu](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Opcje stylu kodu](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

Opcje ustawione w tym oknie mają zastosowanie do konta personalizacji programu Visual Studio i nie są skojarzone z określonym projektem lub bazą kodu. Ponadto nie są one wymuszane w czasie kompilacji, w tym w kompilacji ciągłej integracji (CI). Jeśli chcesz skojarzyć preferencje stylu kodu z projektem i mieć style wymuszane podczas kompilacji, określ preferencje w [pliku .editorconfig](#code-styles-in-editorconfig-files) skojarzonym z projektem.

### <a name="preference-and-severity"></a>Preferencje i ważność

Dla każdego ustawienia stylu kodu na tej stronie można ustawić wartości **preferencji** i **ważności** przy użyciu rozwijanych w każdym wierszu. Ważność można ustawić na **Tylko refaktoryzowanie,** **Sugestia,** **Ostrzeżenie**lub **Błąd**. Jeśli chcesz włączyć [szybkie akcje](../ide/quick-actions.md) dla stylu kodu, upewnij się, że ustawienie **ważności** jest ustawione na coś innego niż **Tylko refaktoryzowanie**. Żarówka ![ **Szybkie akcje,** błąd](media/light-bulb-dropdown.png) ![żarówki](media/error-bulb.png)błąd żarówki ![lub](media/screwdriver.png) śrubokręt pojawia się, gdy używany jest nieuwytomny styl, i można wybrać opcję na liście **Szybkie akcje,** aby automatycznie przepisać kod do preferowanego stylu.

## <a name="apply-code-styles"></a>Stosowanie stylów kodu

::: moniker range="vs-2017"

Można skonfigurować polecenie **Format dokumentu** **(Edytuj** > **dokument formatu****zaawansowanego)** > w celu zastosowania ustawień stylu kodu (z opcji pliku EditorConfig lub **stylu kodu)** wraz ze zwykłym formatowaniem (takim jak wcięcie). Jeśli plik *.editorconfig* istnieje dla projektu, te ustawienia mają pierwszeństwo.

> [!NOTE]
> Stosowanie stylów kodu za pomocą polecenia **Format dokumentu** jest dostępne tylko dla plików kodu języka C#. Jest to funkcja eksperymentalna.

Skonfiguruj ustawienia, które mają być stosowane w **formacie dokumentu** na stronie [Opcje formatowania](reference/options-text-editor-csharp-formatting.md#format-document-settings).

![Ustawienia stylu kodu dokumentu formatu w programie Visual Studio 2017](media/format-document-settings-experiment.png)

> [!TIP]
> Reguły skonfigurowane z ważnością **Brak** nie uczestniczą w oczyszczaniu kodu, ale mogą być stosowane indywidualnie za pomocą menu **Szybkie akcje i Refaktoryzowania.**

Przy pierwszym uruchomieniu polecenia **Format dokumentu** żółty pasek informacji monituje o skonfigurowanie ustawień oczyszczania kodu.

::: moniker-end

::: moniker range=">=vs-2019"

W przypadku plików kodu języka C# program Visual Studio 2019 ma przycisk **oczyszczania kodu** u dołu edytora (klawiatura: **Ctrl**+**K**, **Ctrl**+**E**), aby zastosować style kodu z pliku EditorConfig lub ze strony opcji **stylu kodu.** Jeśli plik *.editorconfig* istnieje dla projektu, są to ustawienia, które mają pierwszeństwo.

![Oczyszczanie kodu w programie Visual Studio 2019](media/execute-code-cleanup.png)

> [!TIP]
> Reguły skonfigurowane z ważnością **Brak** nie uczestniczą w oczyszczaniu kodu, ale mogą być stosowane indywidualnie za pomocą menu **Szybkie akcje i Refaktoryzowania.**

Najpierw skonfiguruj style kodu, które chcesz zastosować (w jednym z dwóch profilów) w oknie dialogowym **Konfigurowanie oczyszczania kodu.** Aby otworzyć to okno dialogowe, kliknij strzałkę rozwiań obok ikony miotły oczyszczania kodu, a następnie wybierz pozycję **Konfiguruj oczyszczanie kodu**.

![Konfigurowanie oczyszczania kodu w programie Visual Studio 2019](media/configure-code-cleanup.png)

Po skonfigurowaniu oczyszczania kodu możesz kliknąć ikonę miotły lub nacisnąć **klawisze Ctrl**+**K**, **Ctrl**+**E,** aby uruchomić oczyszczanie kodu. Można również uruchomić oczyszczanie kodu w całym projekcie lub rozwiązaniu. Kliknij prawym przyciskiem myszy nazwę projektu lub rozwiązania w **Eksploratorze rozwiązań**, wybierz **pozycję Analizuj i Oczyszczanie kodu**, a następnie wybierz polecenie **Uruchom oczyszczanie kodu**.

![Uruchamianie oczyszczania kodu w całym projekcie lub rozwiązaniu](media/run-code-cleanup-project-solution.png)

Jeśli chcesz, aby ustawienia stylu kodu były stosowane przy każdym zapisywaniu pliku, może się to podobać rozszerzenie [Oczyszczanie kodu w programie Zapisz.](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.CodeCleanupOnSave)

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Szybkie akcje](../ide/quick-actions.md)
- [Ustawienia konwencji kodowania .NET dla EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
- [Zachowanie edytora (Visual Studio dla komputerów Mac)](/visualstudio/mac/editor-behavior)
