---
title: Opcje stylu kodu i oczyszczania kodu
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
ms.openlocfilehash: 7b2ebad946d62016199212cfeaae54c32db74d4c
ms.sourcegitcommit: 3fe6bed9ef8fb1478106645f655c7472009ae43a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2019
ms.locfileid: "64558294"
---
# <a name="code-style-preferences"></a>Preferencje stylu kodu

Można zdefiniować kod stylu ustawień projektów za pomocą [pliku EditorConfig](#code-styles-in-editorconfig-files), lub dla całego kodu Edytuj w programie Visual Studio w edytorze tekstów [ **opcje** strony](#code-styles-in-the-options-dialog-box). Dla C# kodu, można również skonfigurować Visual Studio do zastosowania tych preferencji stylu kodu przy użyciu **oczyszczania kodu** (Visual Studio 2019 r) i **Formatuj dokument** polecenia (Visual Studio 2017).

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [zachowanie edytora w programie Visual Studio dla komputerów Mac](/visualstudio/mac/editor-behavior).

## <a name="code-styles-in-editorconfig-files"></a>Style kodu w plikach wtyczki EditorConfig

[Ustawienia stylu kodu](../ide/editorconfig-code-style-settings-reference.md) dla platformy .NET można określić, dodając [EditorConfig](create-portable-custom-editor-options.md) plik do projektu. Plików EditorConfig są skojarzone z bazę kodu, a nie konta personalizacji programu Visual Studio. Ustawienia w pliku EditorConfig mają pierwszeństwo przed style kodu, które są określone w **opcje** okno dialogowe. Jeśli chcesz wymusić kodowania style Wszyscy współautorzy do repozytorium lub projektu, należy użyć pliku EditorConfig.

::: moniker range=">=vs-2019"

Możesz ręcznie wypełnić pliku EditorConfig lub możesz automatycznie wygenerować plik, w oparciu o ustawienia stylu kodu został ustawiony w programie Visual Studio **opcje** okno dialogowe C# lub Edytor tekstu Visual Basic. Ta strona opcji znajduje się w temacie **narzędzia** > **opcje** > **edytora tekstów** > [**C#** lub  **Podstawowe**] > **styl kodu** > **ogólne**.
Kliknij przycisk **Generowanie pliku .editorconfig w ustawieniach** do automatycznego generowania stylem kodowania *.editorconfig* pliku na podstawie ustawień w tym **opcje** strony.

![Generowanie plików editorconfig na podstawie ustawień w Visual Studio 2019 r.](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

## <a name="code-styles-in-the-options-dialog-box"></a>Style kodu w oknie dialogowym Opcje

Można ustawić preferencji stylu kodu dla wszystkich usługi C# i projektach języka Visual Basic, otwierając **opcje** okno dialogowe z **narzędzia** menu. W **opcje** okno dialogowe, wybierz opcję **edytora tekstów** > [**C#** lub **podstawowe**] > **styl kodu**  >  **Ogólne**.

Każdy element na liście pokazuje jego podgląd preferencji, w przypadku wybrania:

::: moniker range="vs-2017"

![Opcje stylu kodu](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Opcje stylu kodu](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

Opcje ustawione w tym oknie mają zastosowanie do konta personalizacji programu Visual Studio i nie są skojarzone z określonym projektem lub bazy kodu. Ponadto nie są wymuszane w czasie kompilacji, w tym w kompilacjach ciągłej integracji (CI). Jeśli chcesz skojarzyć preferencji stylu kodu z projektem i style wymuszane podczas kompilacji, określ preferencje w [pliku .editorconfig](#code-styles-in-editorconfig-files) skojarzony z projektem.

### <a name="preference-and-severity"></a>Preferencji i ważność

Dla każdego ustawienia stylu kodu na tej stronie można ustawić **preferencji** i **ważność** wartości przy użyciu listy rozwijane w każdym wierszu. Można ustawić ważność **Brak**, **sugestii**, **ostrzeżenie**, lub **błąd**. Jeśli chcesz włączyć [szybkie akcje](../ide/quick-actions.md) potrzeby stylu kodu, upewnij się, że **ważność** został ustawiony na coś innego niż **Brak**. **Szybkie akcje** żarówki ![żarówki](media/light-bulb-dropdown.png), błąd żarówki ![błąd żarówki](media/error-bulb.png), lub śrubokręt ![śrubokręt](media/screwdriver.png) ikona pojawia się, gdy Styl innymi niż preferowane jest używany i konieczne jest wybranie opcji na **szybkie akcje** listy, aby automatycznie ponownie pisać kodu do preferowanego stylu.

## <a name="apply-code-styles"></a>Zastosuj styl kodu

::: moniker range="vs-2017"

Można skonfigurować **Formatuj dokument** polecenia (**Edytuj** > **zaawansowane** > **Formatuj dokument**) do Zastosuj ustawienia stylu kodu (z pliku EditorConfig lub **styl kodu** opcje) oraz regularne formatowania, wykonującej (takie jak wcięcia). Jeśli *.editorconfig* plik istnieje w projekcie, te ustawienia mają pierwszeństwo.

> [!NOTE]
> Stosowanie stylów kodu za pomocą **Formatuj dokument** polecenie jest dostępne tylko dla C# plików kodu. Jest to funkcja eksperymentalna.

Skonfiguruj ustawienia, które chcesz **Formatuj dokument** można zastosować [strona Opcje formatowania](reference/options-text-editor-csharp-formatting.md#format-document-settings).

![Ustawienia stylu kodu dla dokumentu w formacie programu Visual Studio 2017](media/format-document-settings-experiment.png)

> [!TIP]
> Zasady skonfigurowane za pomocą ważność **Brak** nie uczestniczyć w oczyszczania kodu, ale mogą być stosowane osobno za pośrednictwem **szybkie akcje i Refaktoryzacje** menu.

Po raz pierwszy możesz wyzwolić **Formatuj dokument** polecenia paska informacyjnego żółty monituje o oczyszczania kodu ustawień.

::: moniker-end

::: moniker range=">=vs-2019"

Dla C# ma plików kodu programu Visual Studio 2019 **oczyszczania kodu** przycisk w dolnej części edytora (klawiatury: **CTRL**+**K**, **Ctrl**+**E**) do zastosowania style kodu z pliku EditorConfig lub **styl kodu**  Strona opcji. Jeśli *.editorconfig* plik istnieje w projekcie, są ustawienia, które mają wyższy priorytet.

![Wykonywanie czyszczenia kodu w Visual Studio 2019 r.](media/execute-code-cleanup.png)

> [!TIP]
> Zasady skonfigurowane za pomocą ważność **Brak** nie uczestniczyć w oczyszczania kodu, ale mogą być stosowane osobno za pośrednictwem **szybkie akcje i Refaktoryzacje** menu.

Najpierw należy skonfigurować style kodu, które chcesz zastosować (w jednym z dwóch profilów) w **skonfigurować oczyszczania kodu** okno dialogowe. Aby otworzyć to okno dialogowe, kliknij strzałkę obok ikony miotła oczyszczania kodu, a następnie wybierz **skonfigurować oczyszczania kodu**. Lub naciśnij **Ctrl**+**K**, **Ctrl**+**Q**.

![Konfigurowanie oczyszczania kodu w Visual Studio 2019 r.](media/configure-code-cleanup.png)

Jeśli chcesz, aby Twoje ustawienia stylu kodu mają być stosowane w każdym razem, gdy plik jest zapisywany, może Cię zainteresować [oczyszczania kodu przy zapisywaniu](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.CodeCleanupOnSave) rozszerzenia.

::: moniker-end

## <a name="see-also"></a>Zobacz także

- [Szybkie akcje](../ide/quick-actions.md)
- [.NET coding convention ustawienia dla wtyczki EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
- [Zachowanie edytora (Visual Studio dla komputerów Mac)](/visualstudio/mac/editor-behavior)