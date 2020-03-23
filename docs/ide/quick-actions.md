---
title: Szybkie akcje, żarówki i śrubokręty
ms.date: 03/28/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2ce8ce85e027a7ed7f78d0da1f68f328c1ca103d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596960"
---
# <a name="quick-actions"></a>Szybkie akcje

Szybkie akcje umożliwiają łatwe refaktoryzowanie, generowanie lub modyfikowanie kodu za pomocą jednej akcji. Szybkie akcje są dostępne dla plików kodu Języka C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp)i Visual Basic. Niektóre akcje są specyficzne dla języka, a inne dotyczą wszystkich języków.

Szybkie akcje mogą być używane do:

- Stosowanie poprawki kodu w przypadku naruszenia [reguły analizatora kodu](../code-quality/roslyn-analyzers-overview.md)

::: moniker range=">=vs-2019"

- [Pomijanie](../code-quality/use-roslyn-analyzers.md#suppress-violations) naruszenia reguły analizatora kodu lub [konfigurowanie](../code-quality/use-roslyn-analyzers.md#automatically-configure-rule-severity) jej ważności

::: moniker-end

::: moniker range="vs-2017"

- [Pomijanie](../code-quality/use-roslyn-analyzers.md#suppress-violations) naruszenia reguły analizatora kodu

::: moniker-end

- Stosowanie refaktoryzacji (na przykład [zmiennej tymczasowej w linii)](../ide/reference/inline-temporary-variable.md)

- Generowanie kodu (na przykład [wprowadzenie zmiennej lokalnej)](../ide/reference/introduce-local-variable.md)

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. W przypadku programu Visual Studio dla komputerów Mac zobacz [Refaktoryzowanie (Visual Studio dla komputerów Mac).](/visualstudio/mac/refactoring)

Szybkie akcje można stosować za pomocą ![ikony](media/light-bulb-icon.png) żarówki ![lub ikony](media/screwdriver-icon.png) śrubokręta lub naciskając klawisz **Ctrl**+**.** gdy kursor znajduje się w wierszu kodu, dla którego dostępna jest akcja. Zostanie wyświetlony błąd żarówki ![błąd żarówki ikony](media/error-light-bulb-icon.png) żarówki, jeśli istnieje czerwony squiggle wskazujący błąd i Visual Studio ma poprawkę dostępną dla tego błędu.

Dla dowolnego języka strony trzecie mogą zapewnić niestandardowe diagnostyki i sugestie, na przykład jako część SDK i visual studio żarówki są wyświetlane na podstawie tych reguł.

## <a name="icons"></a>Ikony

Ikona, która pojawia się, gdy dostępna jest szybka akcja, wskazuje typ dostępnej poprawki lub refaktoryzacji. Ikona ![śrubokręta wskazuje tylko, że istnieją działania dostępne do zmiany kodu, ale nie należy ich używać. *screwdriver* ](media/screwdriver-icon.png) ](media/light-bulb-icon.png) *Ikona ikony żółtej żarówki* ![wskazuje, że są dostępne działania, które *należy* wykonać, aby poprawić swój kod. Ikona ikony błędu](media/error-light-bulb-icon.png) *żarówki błędu żarówki* ![wskazuje, że jest dostępna akcja, która rozwiązuje błąd w kodzie.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Aby zobaczyć żarówkę lub śrubokręt

Jeśli poprawka jest dostępna, pojawią się żarówki:

- Po najechaniu myszą w miejscu błędu

   ![Żarówka z unoszącą się myszą](../ide/media/vs2015_lightbulb_hover.png)

- Na lewym marginesie edytora po przeniesieniu daszka (kursora) do odpowiedniego wiersza kodu

Można również nacisnąć **klawisz Ctrl**+**.** w dowolnym miejscu w wierszu, aby wyświetlić listę dostępnych szybkich akcji i refaktoryzacji.

Aby wyświetlić potencjalne poprawki, wybierz strzałkę w dół obok żarówki lub **łącze Pokaż potencjalne poprawki.** Zostanie wyświetlona lista dostępnych szybkich akcji.

![Żarówka rozszerzona](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu w programie Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Typowe szybkie akcje](../ide/common-quick-actions.md)
- [Style kodu i szybkie akcje](../ide/code-styles-and-code-cleanup.md)
- [Kod zapisu i refaktoryzacji (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Refaktoryzowanie (Visual Studio dla komputerów Mac)](/visualstudio/mac/refactoring)
