---
title: Program IPython REPL (okno interaktywne)
description: Okno interaktywne Visual Studio w trybie IPython na użytek środowisku przyjazny dla użytkownika opracowywanie interakcyjne funkcje interaktywne przetwarzania równoległego.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 84e93d06e294ef11cc345eb4c443845421a8f834
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067806"
---
# <a name="use-ipython-in-the-interactive-window"></a>Użycie IPython w oknie interaktywnym

Visual Studio **Interactive** okno w trybie IPython jest środowisko opracowywanie interakcyjne zaawansowane jeszcze przyjazny dla użytkownika, które oferuje funkcje interaktywne przetwarzania równoległego. W tym artykule przedstawiono, w programie Visual Studio przy użyciu IPython **Interactive** okna, w którym wszystkie zwykłych [okna interaktywnego](python-interactive-repl-in-visual-studio.md) funkcje są również dostępne.

W tym przewodniku powinny mieć [Anaconda](https://www.continuum.io) zainstalowane, środowisko, w tym IPython i wymagane biblioteki.

> [!Note]
> IronPython nie obsługuje IPython, pomimo faktu, że możesz wybrać go na **interaktywnych opcji** formularza. Aby uzyskać więcej informacji, zobacz [zgłoszenie dotyczące funkcji](https://github.com/Microsoft/PTVS/issues/84).

1. Otwórz program Visual Studio, przełącz się do **środowiska Python** okna (**widoku** > **Windows inne** > **środowiska Python** ) i wybierz środowisko pakietu Anaconda.

2. Sprawdź **pakietów (Conda)** kartę (która może być wyświetlana jako **pip** lub **pakietów**) dla tego środowiska upewnić się, że `ipython` i `matplotlib` są wyświetlane. Jeśli nie, zainstaluj je tutaj. (Zobacz [windows środowiska Python — karta pakiety](python-environments-window-tab-reference.md).)

3. Wybierz **Przegląd** kartę, a następnie wybierz pozycję **IPython Użyj trybu interaktywnego**. (W programie Visual Studio 2015 wybierz **skonfigurować opcje interakcyjne** można otworzyć **opcje** okno dialogowe, a następnie ustaw **trybu interaktywnego** do **IPython**i wybierz **OK**).

4. Wybierz **Otwórz okno interaktywne** aby przywołać **Interactive** okna w trybie IPython. Może być konieczne zresetowanie okna, jeśli tryb interakcyjny; właśnie zostały zmienione być może trzeba będzie również naciśnij **Enter** czy tylko >>> zostanie wyświetlony monit, dzięki czemu otrzymasz monit podobny **w [2]**.

    ![Okno interaktywne w trybie IPython](media/ipython-repl-03.png)

5. Wprowadź następujący kod:

   ```python
   import matplotlib.pyplot as plt
   import numpy as np
  
   x = np.linspace(0, 5, 10)
   y = x ** 2
   plt.plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
   ```

6. Po wprowadzeniu ostatni wiersz, powinien zostać wyświetlony wykres wbudowane, (które można zmienić rozmiar, przeciągając w prawym dolnym rogu, w razie potrzeby).

    ![Wbudowane wykresu w oknie interaktywnym](media/ipython-repl-04.png)

7. Zamiast wpisywać w rozwiązaniu REPL, zamiast tego można napisać kod w edytorze, zaznacz go, kliknij prawym przyciskiem myszy i wybierz **Wyślij do środowiska interaktywnego** polecenie (lub naciśnij **Ctrl**+**Enter**). Spróbuj wkleić poniższy kod do nowego pliku w edytorze, wybierając je z **Ctrl**+**A**, następnie wysłanie do **Interactive** okna. (Visual Studio wysyła kod jako jedną jednostkę, aby uniknąć, umożliwiając wykresy pośrednie lub jego część. A jeśli nie masz projektu języka Python Otwórz w innym środowisku, wybrana, program Visual Studio otwiera **Interactive** niezależnie od środowiska jest wybrany jako domyślny w oknie **środowiska Python**okna.)

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

8. Aby zobaczyć wykresy poza **Interactive** oknie Uruchamianie kodu, zamiast przy użyciu **debugowania** > **Uruchom bez debugowania** polecenia.

Program IPython ma wielu innych przydatnych funkcji, takich jak anulowanie w powłoce systemu podstawienie zmiennej przechwytywanie danych wyjściowych, itp. Zapoznaj się [dokumentacji IPython](https://ipython.org/documentation.html) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

- Aby łatwo i bez konieczności instalacji, należy użyć programu Jupyter, wypróbuj bezpłatnie [usługi hostowanej notesów usługi Azure](https://notebooks.azure.com/) umożliwiający przechowywać i udostępniać innym użytkownikom notesów programu.

- [Maszyny wirtualnej do nauki o danych platformy Azure](/azure/machine-learning/data-science-virtual-machine/overview) również jest wstępnie skonfigurowana do uruchamiania aplikacji Jupyter notebooks wraz z szerokiej gamy innych narzędzi do analizy danych.
