---
title: Preferencje stylu kodu
ms.date: 03/12/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 689bdb62d5a4bc9aea21da67e8e5e844660756d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975362"
---
# <a name="code-style-preferences"></a>Preferencje stylu kodu

Można ustawić preferencji stylu kodu dla projektów C# i Visual Basic, otwierając **opcje** okno dialogowe z **narzędzia** menu. W **opcje** okno dialogowe, wybierz opcję **edytora tekstów** > [**C#** lub **podstawowe**] > **styl kodu**  >  **Ogólne**.

Każdy element na liście pokazuje jego podgląd preferencji, w przypadku wybrania:

::: moniker range="vs-2017"

![Opcje stylu kodu](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Opcje stylu kodu](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

Opcje ustawione w tym oknie mają zastosowanie do konta personalizacji programu Visual Studio i nie są skojarzone z określonym projektem lub bazy kodu. Ponadto nie są wymuszane w czasie kompilacji, w tym w kompilacjach ciągłej integracji (CI). Jeśli chcesz skojarzyć preferencji stylu kodu z projektem i style wymuszane podczas kompilacji, określ preferencje w [pliku .editorconfig](#editorconfig-files).

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [zachowanie edytora w programie Visual Studio dla komputerów Mac](/visualstudio/mac/editor-behavior).

## <a name="editorconfig-files"></a>Plików EditorConfig

Ustawienia stylu kodu, dla platformy .NET można również określić, dodając [EditorConfig](../ide/editorconfig-code-style-settings-reference.md) plik do projektu.

::: moniker range=">=vs-2019"

Kliknij przycisk **Generowanie pliku .editorconfig w ustawieniach** do automatycznego generowania pliku .editorconfig stylu kodowania na podstawie opcji został ustawiony w tym **opcje** strony.

![Generowanie pliku editorconfig z ustawień w 2019 programu VS](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

Plików EditorConfig są skojarzone z bazę kodu, a nie konta personalizacji programu Visual Studio. Ustawienia w pliku EditorConfig mają pierwszeństwo przed opcje wybrane w **opcje** okno dialogowe. Jeśli chcesz wymusić kodowania style Wszyscy współautorzy do repozytorium lub projektu, należy użyć pliku EditorConfig.

## <a name="preference-and-severity"></a>Preferencji i ważność

Dla każdego ustawienia stylu kodu na tej stronie można ustawić **preferencji** i **ważność** wartości przy użyciu listy rozwijane w każdym wierszu. Można ustawić ważność **Brak**, **sugestii**, **ostrzeżenie**, lub **błąd**. Jeśli chcesz włączyć [szybkie akcje](../ide/quick-actions.md) potrzeby stylu kodu, upewnij się, że **ważność** został ustawiony na coś innego niż **Brak**. **Szybkie akcje** żarówki ![żarówki](media/light-bulb-dropdown.png), błąd żarówki ![błąd żarówki](media/error-bulb.png), lub śrubokręt ![śrubokręt](media/screwdriver.png) ikona pojawia się, gdy Styl innymi niż preferowane jest używany i konieczne jest wybranie opcji na **szybkie akcje** listy, aby automatycznie ponownie pisać kodu do preferowanego stylu.

## <a name="format-document-command"></a>Format polecenia dokumentu

Można skonfigurować **Formatuj dokument** polecenia (**Edytuj** > **zaawansowane** > **Formatuj dokument**) do Wykonaj czyszczenie dodatkowy kod w pliku, np. Usuń i Sortuj wyrażenia Using lub zastosować preferencji stylu kodu. Można zdefiniować ustawienia, które chcesz **Formatuj dokument** można zastosować [strona Opcje formatowania](reference/options-text-editor-csharp-formatting.md#format-document-settings).

Oczyszczanie kodu stosuje się do ustawień skonfigurowanych w *.editorconfig* pliku lub niedostatecznie tę zasadę lub pliku, określone **narzędzia** > **opcje**  >  **Edytora tekstów**  >  **C#** > [**styl kodu** lub **formatowanie**].

Po raz pierwszy możesz wyzwolić **Formatuj dokument** polecenia w programie Visual Studio, pasek informacji żółty monituje o oczyszczania kodu ustawień.

> [!TIP]
> Zasady skonfigurowane za pomocą ważność **Brak** nie są używane w oczyszczania kodu, ale mogą być stosowane osobno za pośrednictwem **szybkie akcje i Refaktoryzacje** menu.

## <a name="see-also"></a>Zobacz także

- [Szybkie akcje](../ide/quick-actions.md)
- [.NET coding convention ustawienia dla wtyczki EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
- [Zachowanie edytora (Visual Studio dla komputerów Mac)](/visualstudio/mac/editor-behavior)