---
title: Szybkie akcje, żarówki i śrubokręty
ms.date: 03/28/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 71ec5cf14f4cd336b8f92c15b4f0859c7a613354
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71186811"
---
# <a name="quick-actions"></a>Szybkie akcje

Szybkie akcje pozwalają na łatwe Refaktoryzacja, generowanie lub inny sposób modyfikować kodu za pomocą jednej akcji. Szybkie akcje są dostępne dla C#plików [C++](/cpp/ide/writing-and-refactoring-code-cpp)kodu, i Visual Basic. Niektóre akcje są specyficzne dla języka, a inne dotyczą wszystkich języków.

Szybkie akcje mogą służyć do:

- Zastosuj poprawkę kodu dla naruszenia reguły [analizatora kodu](../code-quality/roslyn-analyzers-overview.md)

::: moniker range=">=vs-2019"

- [Pomijanie](../code-quality/use-roslyn-analyzers.md#suppress-violations) naruszenia reguł analizatora kodu lub [Konfigurowanie](../code-quality/use-roslyn-analyzers.md#automatically-configure-rule-severity) jego ważności

::: moniker-end

::: moniker range="vs-2017"

- [Pomijanie](../code-quality/use-roslyn-analyzers.md#suppress-violations) naruszenia reguły analizatora kodu

::: moniker-end

- Zastosuj refaktoryzację (na przykład w [wbudowanej zmiennej tymczasowej](../ide/reference/inline-temporary-variable.md))

- Generuj kod (na przykład [wprowadź zmienną lokalną](../ide/reference/introduce-local-variable.md))

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Refaktoryzacja (Visual Studio dla komputerów Mac)](/visualstudio/mac/refactoring).

Szybkie akcje można stosować przy użyciu ![+](media/light-bulb-icon.png) ikon żarówki żarówki lub ![śrubokrętów](media/screwdriver-icon.png) , lub naciskając klawisz **Ctrl** **.** gdy kursor znajduje się w wierszu kodu, dla którego akcja jest dostępna. Zobaczysz ikonę](media/error-light-bulb-icon.png) żarówki błędu żarówki, jeśli istnieje czerwona zygzakowata wskazująca na błąd, a program Visual Studio ma poprawkę dla tego błędu. ![

W przypadku dowolnego języka osoby trzecie mogą zapewnić niestandardową diagnostykę i sugestie, na przykład w ramach zestawu SDK, a na podstawie tych reguł są wyświetlane żarówki programu Visual Studio.

## <a name="icons"></a>Ikony

Ikona wyświetlana, gdy szybka akcja jest dostępna, zawiera wskazanie typu poprawki lub refaktoryzacji, która jest dostępna. Ikona *ikony* ![śrubokrętuśrubokrętawskazuje,żedostępnesąakcjeumożliwiającezmianękodu,alenienależyichużywać.](media/screwdriver-icon.png) Ikona](media/light-bulb-icon.png) *żółtej* ![żarówki żarówki wskazującej, że istnieją dostępne akcje, które *należy* wykonać, aby poprawić kod. Ikona żarówki błędu żarówki błędów wskazuje, że jest dostępna akcja, która naprawia błąd w kodzie. ![](media/error-light-bulb-icon.png)

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Aby zobaczyć żarówkę lub śrubokręt

Jeśli poprawka jest dostępna, wyświetlane są żarówki:

- Po umieszczeniu wskaźnika myszy w lokalizacji błędu

   ![Żarówka z przesuwaniem myszy](../ide/media/vs2015_lightbulb_hover.png)

- Na lewym marginesie edytora, gdy przesuwany jest karetka (kursor) do odpowiedniego wiersza kodu

Możesz również nacisnąć klawisz **Ctrl**+ **.** w dowolnym miejscu w wierszu, aby wyświetlić listę dostępnych szybkich działań i refaktoryzacji.

Aby wyświetlić potencjalne poprawki, wybierz strzałkę w dół obok żarówki lub link **Pokaż potencjalne poprawki** . Zostanie wyświetlona lista dostępnych szybkich akcji.

![Rozwinięta żarówka](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu w programie Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Typowe szybkie akcje](../ide/common-quick-actions.md)
- [Style kodu i szybkie akcje](../ide/code-styles-and-code-cleanup.md)
- [Kod zapisu i refaktoryzacji (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Refaktoryzacja (Visual Studio dla komputerów Mac)](/visualstudio/mac/refactoring)