---
title: Szybkie akcje, żarówki i śrubokręty
ms.date: 03/28/2018
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 18df1378218d2188ee78d1b1b2a991e35f5ed689
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666755"
---
# <a name="quick-actions"></a>Szybkie akcje

Szybkie akcje umożliwiają łatwe refaktoryzację, generowanie lub modyfikowanie kodu przy użyciu jednej akcji. Szybkie akcje są dostępne dla C#plików [C++](/cpp/ide/writing-and-refactoring-code-cpp)kodu, i Visual Basic. Niektóre akcje są specyficzne dla języka, a inne dotyczą wszystkich języków.

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
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Refaktoryzacja (Visual Studio dla komputerów Mac)](/visualstudio/mac/refactoring).

Szybkie akcje można stosować przy użyciu żarówki ![light ikonę żarówki ](media/light-bulb-icon.png) lub śrubokręt ![screwdriver ikon ](media/screwdriver-icon.png) ikon lub naciskając klawisz **Ctrl** + **.** gdy kursor znajduje się w wierszu kodu, dla którego akcja jest dostępna. Zostanie wyświetlona żarówka o błędach ![error ikona żarówki ](media/error-light-bulb-icon.png), jeśli istnieje czerwona zygzakowata wskazująca na błąd, a program Visual Studio ma dla tego błędu dostępną poprawkę.

W przypadku dowolnego języka osoby trzecie mogą zapewnić niestandardową diagnostykę i sugestie, na przykład w ramach zestawu SDK, a na podstawie tych reguł są wyświetlane żarówki programu Visual Studio.

## <a name="icons"></a>Ikony

Ikona wyświetlana, gdy szybka akcja jest dostępna, zawiera wskazanie typu poprawki lub refaktoryzacji, która jest dostępna. Ikona ![screwdriver *śrubokręta* ](media/screwdriver-icon.png) ikona wskazuje, że dostępne są akcje umożliwiające zmianę kodu, ale nie należy ich używać. *Żółta* żarówka ![light ikona żarówki ](media/light-bulb-icon.png) ikona wskazuje, że istnieją dostępne akcje, które *należy* wykonać, aby poprawić kod. Ikona żarówki *błędów* ![error ikona żarówki ](media/error-light-bulb-icon.png) ikonie wskazuje, że jest dostępna akcja, która naprawia błąd w kodzie.

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
- [Kod zapisu i refaktoryzacji (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Refaktoryzacja (Visual Studio dla komputerów Mac)](/visualstudio/mac/refactoring)