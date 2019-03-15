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
ms.openlocfilehash: 1a08e54025ac0826b88a3d3fcee299beef245d13
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867040"
---
# <a name="quick-actions"></a>Szybkie akcje

Szybkie akcje pozwalają na łatwe Refaktoryzacja, generowanie lub inny sposób modyfikować kodu za pomocą jednej akcji. Szybkie akcje są dostępne dla C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp)i plikach kodu języka Visual Basic. Niektóre akcje są specyficzne dla języka, a inne dotyczą wszystkich wersji językowych.

Szybkie akcje może służyć do:

- Zastosuj poprawkę kodu [analizator kodu](../code-quality/roslyn-analyzers-overview.md) naruszenie reguły

- [Pomiń](../code-quality/use-roslyn-analyzers.md#suppress-violations) naruszenie reguły analizator kodu

- Stosowanie refaktoryzacji (na przykład [wbudowanej zmiennej tymczasowej](../ide/reference/inline-temporary-variable.md))

- Generuj kod (na przykład [wprowadzanie zmiennej lokalnej](../ide/reference/introduce-local-variable.md))

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [Refactoring (Visual Studio dla komputerów Mac)](/visualstudio/mac/refactoring).

Szybkie akcje, które można zastosować za pomocą żarówki ![ikoną żarówki](media/light-bulb-icon.png) lub śrubokręt ![ikonę śrubokręt](media/screwdriver-icon.png) ikony, lub naciskając **Ctrl** + **.** gdy kursor jest ustawiony na wiersz kodu, w którym akcja jest dostępna. Zostanie wyświetlony błąd żarówki z funkcją ![ikona żarówki z funkcją błędu](media/error-light-bulb-icon.png) Jeśli jest czerwona fala wskazująca na wystąpienie błędu, a program Visual Studio zawiera poprawki dla tego błędu.

W dowolnym języku innych firm może zapewnić Diagnostyka niestandardowa i sugestie, na przykład jako część zestawu SDK i żarówki programu Visual Studio są wyświetlane w oparciu o te reguły.

## <a name="icons"></a>Ikony

Ikona, który jest wyświetlany, gdy dostępna jest szybka akcja oznacza wskazanie typu poprawkę lub refaktoryzacji, która jest dostępna. *Śrubokręt* ![ikonę śrubokręt](media/screwdriver-icon.png) ikona wskazuje, wystarczy, że istnieją akcje dostępne zmienić kod, ale niekoniecznie nie należy używać. *Żółta ikona żarówki* ![ikoną żarówki](media/light-bulb-icon.png) ikona wskazuje, akcje są dostępne, *powinien* czy, aby poprawić kod. *Błąd żarówki* ![ikona żarówki z funkcją błędu](media/error-light-bulb-icon.png) ikona wskazuje, jest dostępna akcja, która naprawia błąd w kodzie.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Aby zobaczyć żarówkę lub śrubokręt

Jeśli dostępna jest poprawka żarówki wyświetlane są:

- Gdy umieść kursor myszy w lokalizacji błędu

   ![Ikona żarówki z umieszczeniu wskaźnika myszy](../ide/media/vs2015_lightbulb_hover.png)

- Na lewym marginesie edytor, gdy przeniesiesz karetki (kursor) do odpowiednich wiersza kodu

Można również nacisnąć klawisz **Ctrl**+**.** dowolne miejsce na wiersz, aby wyświetlić listę dostępnych szybkie akcje i refaktoryzacje.

Aby wyświetlić potencjalne rozwiązania, wybierz albo strzałkę w dół obok ikony żarówki lub **Pokaż potencjalne rozwiązania** łącza. Zostanie wyświetlona lista dostępnych szybkich akcji.

![Ikona żarówki rozwinięte](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu w programie Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Typowe szybkie akcje](../ide/common-quick-actions.md)
- [Style kodu i szybkie akcje](../ide/code-styles-and-quick-actions.md)
- [Pisanie i Refaktoryzacja kodu (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Refaktoryzacja (Visual Studio dla komputerów Mac)](/visualstudio/mac/refactoring)