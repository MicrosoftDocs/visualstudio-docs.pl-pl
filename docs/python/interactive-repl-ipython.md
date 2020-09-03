---
title: IPython REPL (Okno interaktywne)
description: Korzystaj z okna interaktywnego programu Visual Studio w trybie IPython dla przyjaznych dla użytkownika środowisk programistycznych interaktywnych z interaktywnymi funkcjami przetwarzania równoległego.
ms.date: 01/28/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: b1fe36a4ee74ca1b41c1db1d79a6e4683c1f2b1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542431"
---
# <a name="use-ipython-in-the-interactive-window"></a>Użyj IPython w oknie interaktywnym

Okno **interaktywne** programu Visual Studio w trybie IPython jest zaawansowanym, ale przyjaznym dla użytkownika środowiskiem programistycznym, które ma interaktywne funkcje przetwarzania równoległego. W tym artykule opisano użycie IPython w oknie **interaktywnym** programu Visual Studio, w którym są również dostępne wszystkie zwykłe funkcje [okna interaktywnego](python-interactive-repl-in-visual-studio.md) .

W tym instruktażu należy zainstalować środowisko [Anaconda](https://www.continuum.io) , które obejmuje IPython i niezbędne biblioteki.

> [!Note]
> IronPython nie obsługuje IPython, pomimo faktu, że można go wybrać w formularzu **opcji interaktywnych** . Aby uzyskać więcej informacji, zobacz [żądanie dotyczące funkcji](https://github.com/Microsoft/PTVS/issues/84).

1. Otwórz program Visual Studio, przejdź do okna **środowiska Python** (**Wyświetl**  >  **inne**  >  **środowiska Windows Python**) i wybierz środowisko Anaconda.

2. Sprawdź kartę **pakiety (Conda)** (która może być wyświetlana jako **PIP** lub **Packages**) dla tego środowiska, aby upewnić się, że `ipython` i `matplotlib` są wymienione na liście. Jeśli nie, zainstaluj je tutaj. (Zobacz [środowisko języka Python Windows-Packages Tab](python-environments-window-tab-reference.md)).

3. Wybierz kartę **Przegląd** i wybierz opcję **Użyj trybu interaktywnego IPython**. (W programie Visual Studio 2015 wybierz pozycję **Konfiguruj opcje interaktywne** , aby otworzyć okno dialogowe **Opcje** , a następnie ustaw **tryb interaktywny** na **IPython**, a następnie wybierz **przycisk OK**).

4. Wybierz pozycję **Otwórz okno interaktywne** , aby wyświetlić okno **interaktywne** w trybie IPython. Jeśli zmieniono tryb interaktywny, może być konieczne zresetowanie okna. może być również konieczne naciśnięcie klawisza **Enter** w przypadku wyświetlenia tylko monitu >>> , aby uzyskać monit jak **w przypadku [2]**.

    ![Okno interaktywne w trybie IPython](media/ipython-repl-03.png)

5. Wprowadź następujący kod:

   ```python
   import matplotlib.pyplot as plt
   import numpy as np

   x = np.linspace(0, 5, 10)
   y = x ** 2
   plt.plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
   ```

6. Po wprowadzeniu ostatniego wiersza powinien zostać wyświetlony wykres wbudowany (którego rozmiar można zmienić, przeciągając w prawym dolnym rogu, w razie potrzeby).

    ![Wykres wbudowany w oknie interaktywnym](media/ipython-repl-04.png)

7. Zamiast wpisywać w REPL, możesz zamiast tego napisać kod w edytorze, zaznacz go, kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Wyślij do interaktywnego** polecenia (lub naciśnij klawisz **Ctrl** + **Enter**). Spróbuj wkleić poniższy kod do nowego pliku w edytorze, wybierając go z **klawiszem Ctrl** + **a**, a następnie wysyłając do okna **interaktywnego** . (Program Visual Studio wysyła kod jako jedną jednostkę, aby uniknąć podawania pośrednich lub częściowych wykresów. Jeśli nie masz otwartego projektu języka Python z wybranym innym środowiskiem, program Visual Studio otwiera okno **interaktywne** dla dowolnego środowiska, które jest wybrane jako domyślne w oknie **środowiska języka Python** .

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

8. Aby wyświetlić wykresy poza oknem **interaktywnym** , należy zamiast tego uruchomić kod przy użyciu polecenia **Debug**  >  **Start bez debugowania** .

IPython ma wiele innych użytecznych funkcji, takich jak ucieczki do powłoki systemowej, podstawienia zmiennych, przechwytywania danych wyjściowych itp. Więcej informacji można znaleźć w [dokumentacji IPython](https://ipython.org/documentation.html) .

## <a name="see-also"></a>Zobacz też

- Aby korzystać z Jupyter z łatwością i bez instalacji, wypróbuj bezpłatną [Azure Notebooks hostowaną usługę](https://notebooks.azure.com/) , która umożliwia utrzymywanie i udostępnianie notesów innym osobom.

- [Usługa Azure Data Science Virtual Machine](/azure/machine-learning/data-science-virtual-machine/overview) jest również wstępnie skonfigurowana do uruchamiania notesów Jupyter oraz szerokiej gamy innych narzędzi do nauki o danych.
