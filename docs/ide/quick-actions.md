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
ms.openlocfilehash: bfafcca1cddcaa216b8a9e12dd7d961949afa2bb
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036525"
---
# <a name="quick-actions"></a>Szybkie akcje

Szybkie akcje umożliwiają łatwe refaktoryzację, generowanie lub modyfikowanie kodu przy użyciu jednej akcji. Szybkie akcje są dostępne dla plików kodu w języku C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp)i Visual Basic. Niektóre akcje są specyficzne dla języka, a inne dotyczą wszystkich języków.

Szybkie akcje mogą służyć do:

- Zastosuj poprawkę kodu dla naruszenia reguły [analizatora kodu](../code-quality/roslyn-analyzers-overview.md)

::: moniker range=">=vs-2019"

- [Pomijanie](../code-quality/use-roslyn-analyzers.md#suppress-violations) naruszenia reguł analizatora kodu lub [Konfigurowanie](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu) jego ważności

::: moniker-end

::: moniker range="vs-2017"

- [Pomijanie](../code-quality/use-roslyn-analyzers.md#suppress-violations) naruszenia reguły analizatora kodu

::: moniker-end

- Zastosuj refaktoryzację (na przykład w [wbudowanej zmiennej tymczasowej](../ide/reference/inline-temporary-variable.md))

- Generuj kod (na przykład [wprowadź zmienną lokalną](../ide/reference/introduce-local-variable.md))

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Refaktoryzacja (Visual Studio dla komputerów Mac)](/visualstudio/mac/refactoring).

Szybkie akcje można stosować przy użyciu ikon żarówki żarówki ![ ](media/light-bulb-icon.png) lub ![ śrubokrętów ](media/screwdriver-icon.png) , lub naciskając klawisz **Ctrl** + **.** gdy kursor znajduje się w wierszu kodu, dla którego akcja jest dostępna. Zobaczysz ikonę żarówki błędu żarówki, ![ ](media/error-light-bulb-icon.png) Jeśli istnieje czerwona zygzakowata wskazująca na błąd, a program Visual Studio ma poprawkę dla tego błędu.

W przypadku dowolnego języka osoby trzecie mogą zapewnić niestandardową diagnostykę i sugestie, na przykład w ramach zestawu SDK, a na podstawie tych reguł są wyświetlane żarówki programu Visual Studio.

## <a name="icons"></a>Ikony

Ikona wyświetlana, gdy szybka akcja jest dostępna, zawiera wskazanie typu poprawki lub refaktoryzacji, która jest dostępna. *screwdriver* ![ Ikona ikony śrubokrętu śrubokręta ](media/screwdriver-icon.png) wskazuje, że dostępne są akcje umożliwiające zmianę kodu, ale nie należy ich używać. Ikona *żółtej* żarówki żarówki ![ ](media/light-bulb-icon.png) wskazującej, że istnieją dostępne akcje, które *należy* wykonać, aby poprawić kod. Ikona *żarówki błędu* żarówki błędów ![ wskazuje, ](media/error-light-bulb-icon.png) że jest dostępna akcja, która naprawia błąd w kodzie.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Aby zobaczyć żarówkę lub śrubokręt

Jeśli poprawka jest dostępna, wyświetlane są żarówki:

- Po umieszczeniu wskaźnika myszy w lokalizacji błędu

   ![Żarówka z przesuwaniem myszy](../ide/media/vs2015_lightbulb_hover.png)

- Na lewym marginesie edytora, gdy przesuwany jest karetka (kursor) do odpowiedniego wiersza kodu

Możesz również nacisnąć klawisz **Ctrl** + **.** w dowolnym miejscu w wierszu, aby wyświetlić listę dostępnych szybkich działań i refaktoryzacji.

Aby wyświetlić potencjalne poprawki, wybierz strzałkę w dół obok żarówki lub link **Pokaż potencjalne poprawki** . Zostanie wyświetlona lista dostępnych szybkich akcji.

![Rozwinięta żarówka](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu w programie Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Typowe szybkie akcje](../ide/common-quick-actions.md)
- [Style kodu i szybkie akcje](../ide/code-styles-and-code-cleanup.md)
- [Zapis i kod refaktoryzacji (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Refaktoryzacja (Visual Studio dla komputerów Mac)](/visualstudio/mac/refactoring)
