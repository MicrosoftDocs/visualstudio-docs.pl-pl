---
title: IPython REPL (okno interaktywne)
description: Użyj interaktywnego okna programu Visual Studio w trybie IPython dla przyjaznego dla użytkownika interaktywnego środowiska programistycznego z funkcjami interaktywnego przetwarzania równoległego.
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8b4510ed738fdd2b33389ab4242dbde86cffff8c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62957750"
---
# <a name="use-ipython-in-the-interactive-window"></a>Używanie IPython w oknie Interaktywna

Okno **Interaktywne** programu Visual Studio w trybie IPython to zaawansowane, ale przyjazne dla użytkownika interaktywne środowisko programistyczne z funkcjami interactive parallel computing. W tym artykule oględy przy użyciu IPython w visual studio **interaktywne** okno, w którym wszystkie funkcje [okna](python-interactive-repl-in-visual-studio.md) interaktywne są również dostępne.

W tym instruktażu należy zainstalować środowisko [Anaconda,](https://www.continuum.io) które zawiera IPython i niezbędne biblioteki.

> [!Note]
> IronPython nie obsługuje IPython, pomimo faktu, że można go wybrać w formularzu **Opcje interaktywne.** Aby uzyskać więcej informacji, zobacz [żądanie funkcji](https://github.com/Microsoft/PTVS/issues/84).

1. Otwórz program Visual Studio, przełącz się do okna **Środowiska języka Python** (**Wyświetl** > inne**środowiska języka****Windows** > Python ) i wybierz środowisko Anaconda.

2. Sprawdź **pakiety (Conda)** kartę (które mogą pojawić się jako **pip** `matplotlib` lub **pakiety)** dla tego środowiska, aby upewnić się, że `ipython` i są wymienione. Jeśli nie, zainstaluj je tutaj. (Zobacz [okna środowiska Python - pakiety kartę](python-environments-window-tab-reference.md).)

3. Wybierz kartę **Przegląd** i wybierz pozycję **Użyj trybu interaktywnego IPython**. (W programie Visual Studio 2015 wybierz pozycję **Konfiguruj opcje interaktywne,** aby otworzyć okno dialogowe **Opcje,** a następnie ustaw **tryb interaktywny** na **IPython**i wybierz przycisk **OK**).

4. Wybierz **otwórz okno interaktywne,** aby przywołać okno **interaktywne** w trybie IPython. Może być konieczne zresetowanie okna, jeśli właśnie zmieniono tryb interaktywny; może być również konieczne naciśnięcie klawisza **Enter,** jeśli pojawi się tylko >>> monit, aby uzyskać monit, taki jak **w [2]**.

    ![Interaktywne okno w trybie IPython](media/ipython-repl-03.png)

5. Wprowadź następujący kod:

   ```python
   import matplotlib.pyplot as plt
   import numpy as np

   x = np.linspace(0, 5, 10)
   y = x ** 2
   plt.plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
   ```

6. Po wprowadzeniu ostatniego wiersza powinien zostać wyświetlony wykres wbudowany (który można zmienić, przeciągając w razie potrzeby w prawym dolnym rogu).

    ![Wykres wbudowany w oknie interaktywnym](media/ipython-repl-04.png)

7. Zamiast wpisywać w REPL, można zamiast pisać kod w edytorze, zaznaczyć go, kliknąć prawym przyciskiem myszy i wybrać polecenie **Wyślij do interaktywnej** (lub naciśnij **klawisz Ctrl**+**Enter**). Spróbuj wkleić poniższy kod do nowego pliku w edytorze, zaznaczając go za pomocą **klawisza Ctrl**+**A,** a następnie wysyłając do okna **Interaktywne.** (Visual Studio wysyła kod jako jedną jednostkę, aby uniknąć dając wykresy pośrednie lub częściowe. A jeśli nie masz otwartego projektu Języka Python z wybranym innym środowiskiem, program Visual Studio otwiera okno **interaktywne** dla dowolnego środowiska wybranego jako domyślne w oknie **Środowiska Języka Python.)**

    ```python
    from mpl_toolkits.mplot3d import Axes3D
    import matplotlib.pyplot as plt
    import numpy as np
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
        xs = np.arange(20)
        ys = np.random.rand(20)
        # You can provide either a single color or an array. To demonstrate this,
        # the first bar of each set is colored cyan.
        cs = [c] * len(xs)
        cs[0] = 'c'
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X')
    ax.set_ylabel('Y')
    ax.set_zlabel('Z')
    plt.show()
    ```

    ![Wysyłanie kodu z edytora do okna interaktywnego](media/ipython-repl-05.png)

8. Aby wyświetlić wykresy poza **interakcyjnym** oknie, uruchom kod zamiast tego za pomocą polecenia **Debugowanie** > **start bez debugowania.**

IPython ma wiele innych przydatnych funkcji, takich jak ucieczka do powłoki systemowej, zastępowanie zmiennych, przechwytywanie danych wyjściowych itp. Więcej informacji można znaleźć w [dokumentacji IPython.](https://ipython.org/documentation.html)

## <a name="see-also"></a>Zobacz też

- Aby łatwo i bez instalacji korzystać z usługi Jupyter, wypróbuj bezpłatną [usługę hostowana notesów platformy Azure,](https://notebooks.azure.com/) która umożliwia przechowywanie i udostępnianie notesów innym osobom.

- [Maszyna wirtualna do nauki o danych platformy Azure](/azure/machine-learning/data-science-virtual-machine/overview) jest również wstępnie skonfigurowana do uruchamiania notesów jupytera wraz z szeroką gamą innych narzędzi do nauki o danych.
