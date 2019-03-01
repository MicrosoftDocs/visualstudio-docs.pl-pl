---
title: Preferencje stylu kodu
ms.date: 03/10/2017
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 1f5ad2f5860c148d4bb9d0ee026eee9b1e83c74c
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57223133"
---
# <a name="code-style-preferences"></a>Preferencje stylu kodu

Można ustawić preferencji stylu kodu dla projektów C# i Visual Basic, otwierając **opcje** okno dialogowe z **narzędzia** menu. W **opcje** okno dialogowe, wybierz opcję **edytora tekstów** > [**C#** lub **podstawowe**] > **styl kodu**  >  **Ogólne**. Opcje ustawione w tym oknie dotyczą tylko komputer lokalny.

Każdy element na liście pokazuje jego podgląd preferencji, w przypadku wybrania:

![Opcje stylu kodu](media/code-style-quick-actions-dialog.png)

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [zachowanie edytora w programie Visual Studio dla komputerów Mac](/visualstudio/mac/editor-behavior).

## <a name="preference-and-severity"></a>Preferencji i ważność

Dla każdego elementu można ustawić **preferencji** i **ważność** wartości przy użyciu listy rozwijane w każdym wierszu. Można ustawić ważność **Brak**, **sugestii**, **ostrzeżenie**, lub **błąd**. Jeśli chcesz włączyć [szybkie akcje](../ide/quick-actions.md) potrzeby stylu kodu, upewnij się, że **ważność** został ustawiony na coś innego niż **Brak**. **Szybkie akcje** żarówki ![żarówki](media/vs2015_lightbulbsmall.png), błąd żarówki ![błąd żarówki](media/error-bulb.png), lub śrubokręt ![śrubokręt](media/screwdriver.png) ikona pojawia się, gdy Styl innymi niż preferowane jest używany i konieczne jest wybranie opcji na **szybkie akcje** listy, aby automatycznie ponownie pisać kodu do preferowanego stylu.

## <a name="editorconfig-files"></a>Plików EditorConfig

Kod platformy .NET można również zarządzać za pomocą ustawienia stylu [EditorConfig](../ide/editorconfig-code-style-settings-reference.md) pliku. Ustawienia w pliku EditorConfig mają pierwszeństwo przed opcje wybrane w **opcje** okno dialogowe. Plik wtyczki EditorConfig umożliwia wymuszanie i skonfiguruj styl kodowania dla całego repozytorium lub projektu.

## <a name="format-document-command"></a>Format polecenia dokumentu

Można skonfigurować **Formatuj dokument** polecenia (**Edytuj** > **zaawansowane** > **Formatuj dokument**) do Wykonaj czyszczenie dodatkowy kod w pliku, np. Usuń i Sortuj wyrażenia Using lub zastosować preferencji stylu kodu. Można zdefiniować ustawienia, które chcesz **Formatuj dokument** można zastosować [strona Opcje formatowania](reference/options-text-editor-csharp-formatting.md#format-document-settings).

Oczyszczanie kodu stosuje się do ustawień skonfigurowanych w *.editorconfig* pliku lub niedostatecznie tę zasadę lub pliku, określone **narzędzia** > **opcje**  >  **Edytora tekstów**  >  **C#** > [**styl kodu** lub **formatowanie**].

Po raz pierwszy możesz wyzwolić **Formatuj dokument** polecenia w programie Visual Studio, pasek informacji żółty monituje o oczyszczania kodu ustawień.

> [!TIP]
> Zasady skonfigurowane jako **Brak** w *.editorconfig* pliku nie są używane w oczyszczania kodu, ale mogą być stosowane osobno za pośrednictwem **szybkie akcje i Refaktoryzacje** menu.

## <a name="see-also"></a>Zobacz także

- [Szybkie akcje](../ide/quick-actions.md)
- [.NET coding convention ustawienia dla wtyczki EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
- [Zachowanie edytora (Visual Studio dla komputerów Mac)](/visualstudio/mac/editor-behavior)