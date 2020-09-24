---
title: Debugowanie testów jednostkowych za pomocą narzędzia Eksplorator testów
description: Dowiedz się, jak debugować testy jednostkowe za pomocą Eksploratora testów w programie Visual Studio.
ms.date: 07/14/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b811cc3538e3bbb108e50acf50c2fe7a977fe3d
ms.sourcegitcommit: da7f093db52df5dcd67e0a030e616b307f0dc2a8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2020
ms.locfileid: "91211290"
---
# <a name="debug-and-analyze-unit-tests-with-test-explorer"></a>Debugowanie i analizowanie testów jednostkowych za pomocą Eksploratora testów

Możesz użyć Eksploratora testów, aby rozpocząć sesję debugowania dla testów. Przechodzenie przez kod za pomocą debugera programu Visual Studio bezproblemowo przeprowadzi Cię z powrotem między testami jednostkowymi i badanym projektem. Aby rozpocząć debugowanie:

1. W edytorze programu Visual Studio Ustaw punkt przerwania w co najmniej jednej metodzie testowej, która ma być debugowana.

    > [!NOTE]
    > Ponieważ metody testowe mogą być uruchamiane w dowolnej kolejności, należy ustawić punkty przerwania we wszystkich metodach testowych, które mają być debugowane.

::: moniker range="vs-2017"
2. W Eksploratorze testów wybierz metody testowe, a następnie wybierz **Debuguj wybrane testy** w menu po kliknięciu prawym przyciskiem myszy.
::: moniker-end
::: moniker range=">=vs-2019"
2. W Eksploratorze testów wybierz metody testowe, a następnie wybierz polecenie **Debuguj** w menu po kliknięciu prawym przyciskiem myszy.

   ![Szczegóły wykonania testu](../test/media/vs-2019/test-explorer-debug.png)
::: moniker-end

   Aby uzyskać więcej informacji o debugerze, zobacz [debugowanie w programie Visual Studio](../debugger/debugger-feature-tour.md).

## <a name="diagnose-test-method-performance-issues"></a>Diagnozuj problemy z wydajnością metody testowej

::: moniker range="vs-2017"
Aby zdiagnozować Dlaczego metoda testowa trwa zbyt wiele czasu, wybierz metodę w Eksploratorze testów, a następnie wybierz pozycję **profil wybrany test** w menu po kliknięciu prawym przyciskiem myszy. Zobacz [raport profilowania Instrumentacji](../profiling/understanding-instrumentation-data-values.md?view=vs-2017&preserve-view=true).
::: moniker-end

::: moniker range=">=vs-2019"
Aby zdiagnozować Dlaczego metoda testowa trwa zbyt wiele czasu, wybierz metodę w Eksploratorze testów, a następnie wybierz pozycję **profil** w menu po kliknięciu prawym przyciskiem myszy. Zobacz [raport profilowania Instrumentacji](../profiling/understanding-instrumentation-data-values.md?view=vs-2017&preserve-view=true).
::: moniker-end

> [!NOTE]
> Ta funkcja nie jest obecnie obsługiwana w przypadku platformy .NET Core.

## <a name="see-also"></a>Zobacz też

- [Testowanie jednostkowe kodu](../test/unit-test-your-code.md)
- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)
- [Eksplorator testów — często zadawane pytania](test-explorer-faq.md)
