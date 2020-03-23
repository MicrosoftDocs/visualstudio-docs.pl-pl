---
title: Python w programie Visual Studio krok 5, instalowanie pakietów
titleSuffix: ''
description: Krok 5 podstawowego przewodnika po możliwościach języka Python w programie Visual Studio, demonstrując funkcje programu Visual Studio do zarządzania pakietami w środowisku języka Python.
ms.date: 03/09/2020
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5e2644ccfff0e7c653f4ce2680299aea95a55ef9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "79372936"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Krok 5: Instalowanie pakietów w środowisku Pythona

**Poprzedni krok: [Uruchamianie kodu w debugerze](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Społeczność programistów Języka Python wyprodukowała tysiące przydatnych pakietów, które można włączyć do własnych projektów. Visual Studio udostępnia interfejs użytkownika do zarządzania pakietami w środowiskach Języka Python.

## <a name="view-environments"></a>Wyświetlanie środowisk

1. Wybierz polecenie menu **Wyświetl** > inne środowiska**języka Windows** > **Python.** Okno **Środowiska języka Python** otwiera się jako element równorzędny dla **Eksploratora rozwiązań** i pokazuje różne dostępne środowiska. Lista zawiera zarówno środowiska zainstalowane przy użyciu instalatora programu Visual Studio, jak i środowiska zainstalowane oddzielnie. Obejmuje to środowiska globalne, wirtualne i conda. Środowisko pogrubione jest domyślnym środowiskiem, które jest używane dla nowych projektów. Aby uzyskać dodatkowe informacje dotyczące pracy ze środowiskami, zobacz [Jak tworzyć środowiska języka Python i zarządzać nimi w środowiskach programu Visual Studio.](managing-python-environments-in-visual-studio.md)

   ![Okna Środowiska języka Python](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > Okno Środowiska języka Python można również otworzyć, klikając okno Eksploratora rozwiązań i używając skrótu klawiaturowego Ctrl+K, Ctrl+.You can also open the Python Environments window by clicking on the Solution Explorer window and using the Ctrl+K, Ctrl+' keyboard shortcut. Jeśli skrót nie działa i nie można znaleźć okna Środowiska Języka Python w menu, możliwe, że nie zainstalowano obciążenia języka Python. Zobacz [Jak zainstalować pomoc techniczną języka Python w programie Visual Studio,](installing-python-support-in-visual-studio.md) aby uzyskać wskazówki dotyczące instalowania języka Python.

2. Karta **Przegląd** środowiska zapewnia szybki dostęp do okna **interaktywnego** dla tego środowiska wraz z folderem instalacyjnym i interpreterami środowiska. Na przykład wybierz otwórz **okno interaktywne** i **interaktywne** okno dla tego określonego środowiska pojawi się w programie Visual Studio.

3. Teraz utwórz nowy projekt za pomocą **pliku** > **nowego** > **projektu**, wybierając szablon aplikacji **języka Python.** W wyświetlonym pliku kodu wklej następujący kod, który tworzy cosine wave, podobnie jak poprzednie kroki samouczka, tylko tym razem wykreślone graficznie. Alternatywnie można użyć projektu, który wcześniej utworzono i zastąpić kod. 

    ```python
    from math import radians
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

4. Po otwarciu projektu Języka Python możesz również otworzyć okno Środowiska Języka Python w Eksploratorze rozwiązań, klikając prawym przyciskiem myszy środowisko Języka Python i wybierając **pozycję Wyświetl wszystkie środowiska Języka Python**

   ![Środowisko](media/environments/environments-view-all-2019.png)

5. Patrząc na okno edytora, można zauważyć, że `numpy` `matplotlib` jeśli najedziesz kursorem na i zaimportować instrukcje, które nie zostały rozwiązane. To dlatego, że pakiety nie zostały zainstalowane w domyślnym środowisku globalnym.

   ![Nierozstrzygnięty import pakietu](media/packages-unresolved-import.png)

## <a name="install-packages-using-the-python-environments-window"></a>Instalowanie pakietów przy użyciu okna Środowiska języka Python

1. W oknie Środowiska języka Python kliknij domyślne środowisko dla nowych projektów języka Python i wybierz kartę **Pakiety.** Zostanie wyświetlona lista pakietów, które są obecnie zainstalowane w środowisku.

   ![Pakiety zainstalowane w środowisku](media/environments/environments-installed-packages-2019.png)

2. Zainstaluj, `matplotlib` wprowadzając jego nazwę w polu wyszukiwania, a następnie wybierając **polecenie Uruchom: pip install matplotlib.** To zainstaluje, `matplotlib`jak również wszelkie pakiety, od `numpy`których zależy (w tym przypadku, który zawiera ).

   ![Instalacja matplotlib w środowisku](media/environments/environments-add-matplotlib-2019.png)

5. Zgoda na podniesienie uprawnień, jeśli zostanie o to poproszony.

6. Po zainstalowaniu pakietu pojawia się w oknie **Środowiska Języka Python.** **X** po prawej stronie pakietu odinstalowuje go.

   ![Zakończenie instalacji matplotlib w środowisku](media/environments/environments-add-matplotlib2-2019.png)

   > [!NOTE]
   > Mały pasek postępu może pojawić się pod środowiskiem, aby wskazać, że visual studio buduje swoją bazę danych IntelliSense dla nowo zainstalowanego pakietu. Karta **IntelliSense** zawiera również bardziej szczegółowe informacje. Należy pamiętać, że dopóki ta baza danych nie zostanie ukończona, funkcje IntelliSense, takie jak automatyczne uzupełnianie i sprawdzanie składni, nie będą aktywne w edytorze dla tego pakietu.
   > 
   > Visual Studio 2017 w wersji 15.6 i nowszych używa innej i szybszej metody pracy z IntelliSense i wyświetla komunikat o tym wpływ na karcie **IntelliSense.**

## <a name="run-the-program"></a>Uruchamianie programu

1. Teraz, [gdy matplotlib](https://matplotlib.org/) jest zainstalowany, uruchom program z (**F5**) lub bez debugera (**Ctrl**+**F5**), aby zobaczyć dane wyjściowe:

   ![Wyjście przykład matplotlib](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Następny krok

> [!div class="nextstepaction"]
> [Praca z Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Głębiej

- [Środowiska Python](managing-python-environments-in-visual-studio.md)
- [Nauka platformy Django w programie Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Nauka platformy Flask w programie Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)
