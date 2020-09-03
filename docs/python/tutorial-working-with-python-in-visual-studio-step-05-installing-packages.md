---
title: Samouczek Python w programie Visual Studio — krok 5, instalowanie pakietów
titleSuffix: ''
description: Krok 5 podstawowych przewodnika w zakresie możliwości języka Python w programie Visual Studio, pokazujący funkcje programu Visual Studio do zarządzania pakietami w środowisku Python.
ms.date: 03/09/2020
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 32e85f39c4acf9466def24bcfea59bbfd6807a1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88801662"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Krok 5. Instalowanie pakietów w środowisku języka Python

**Poprzedni krok: [Uruchamianie kodu w debugerze](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Społeczność deweloperów języka Python wygenerowała tysiące przydatnych pakietów, które można uwzględnić w własnych projektach. Program Visual Studio udostępnia interfejs użytkownika służący do zarządzania pakietami w środowiskach języka Python.

## <a name="view-environments"></a>Wyświetlanie środowisk

1. Wybierz polecenie **Wyświetl**  >  **inne**  >  **środowiska języka Python** systemu Windows. Okno **środowiska języka Python** otwiera się jako element równorzędny do **Eksplorator rozwiązań** i pokazuje różne dostępne środowiska. Na liście wyświetlane są oba środowiska, które zostały zainstalowane przy użyciu Instalatora programu Visual Studio oraz zainstalowanych osobno. Obejmuje to globalne, wirtualne i Conda środowiska. Środowisko w pogrubieniu jest domyślnym środowiskiem, które jest używane w przypadku nowych projektów. Aby uzyskać dodatkowe informacje na temat pracy ze środowiskami, zobacz [jak tworzyć środowiska Python i zarządzać nimi w środowiskach programu Visual Studio](managing-python-environments-in-visual-studio.md).

   ![Okno środowisk Python](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > Możesz również otworzyć okno środowiska Python, wybierając okno Eksplorator rozwiązań i używając skrótu klawiaturowego **Ctrl + K, CTRL + '** . Jeśli skrót nie działa i nie można znaleźć okna środowiska języka Python w menu, możliwe, że nie zainstalowano obciążenia języka Python. Zobacz [jak zainstalować obsługę języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md) , aby uzyskać wskazówki dotyczące sposobu instalowania języka Python.

2. Karta **Przegląd** środowiska zapewnia szybki dostęp do **interaktywnego** okna dla tego środowiska oraz do folderu instalacji i interpreterów środowiska. Na przykład wybierz pozycję **Otwórz okno interaktywne** i okno **interaktywne** dla tego konkretnego środowiska pojawia się w programie Visual Studio.

3. Teraz Utwórz nowy projekt z **plikiem**  >  **Nowy**  >  **projekt**, wybierając szablon aplikacji języka **Python** . W wyświetlonym pliku kodu wklej następujący kod, który tworzy Wave, podobnie jak poprzednie kroki samouczka, tylko ten czas jest rysowany graficznie. Alternatywnie możesz użyć wcześniej utworzonego projektu i zamienić kod.

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

4. Przy otwartym projekcie języka Python możesz również otworzyć okno środowiska Python z poziomu Eksplorator rozwiązań, klikając prawym przyciskiem myszy **środowisko Python** i wybierając polecenie **Wyświetl wszystkie środowiska Python**

   ![Środowisko](media/environments/environments-view-all-2019.png)

5. Przeglądając okno edytora, Zauważ, że po umieszczeniu wskaźnika myszy na `numpy` `matplotlib` instrukcjach i zaimportowaniu nie są one rozwiązane. Wynika to z faktu, że pakiety nie zostały zainstalowane w domyślnym środowisku globalnym.

   ![Nierozpoznany import pakietu](media/packages-unresolved-import.png)

## <a name="install-packages-using-the-python-environments-window"></a>Instalowanie pakietów przy użyciu okna środowiska języka Python

1. W oknie środowiska języka Python Wybierz domyślne środowisko dla nowych projektów języka Python i wybierz kartę **pakiety** . Zostanie wyświetlona lista pakietów, które są obecnie zainstalowane w środowisku programu.

   ![Pakiety zainstalowane w środowisku](media/environments/environments-installed-packages-2019.png)

2. Zainstaluj program `matplotlib` , wprowadzając jego nazwę w polu wyszukiwania, a następnie wybierając opcję **Uruchom polecenie: pip install matplotlib** . Spowoduje to zainstalowanie `matplotlib` programu oraz wszystkich pakietów, od których zależy (w tym przypadku obejmuje `numpy` ).

   ![Instalowanie matplotlib w środowisku](media/environments/environments-add-matplotlib-2019.png)

5. Jeśli zostanie wyświetlony monit, wyrażanie zgody na podniesienie uprawnień.

6. Po zainstalowaniu pakietu jest on wyświetlany w oknie środowiska języka **Python** . **Symbol X** z prawej strony pakietu Odinstalowuje go.

   ![Zakończenie instalowania matplotlib w środowisku](media/environments/environments-add-matplotlib2-2019.png)

   > [!NOTE]
   > Mały pasek postępu może pojawić się poniżej środowiska, aby wskazać, że program Visual Studio tworzy swoją bazę danych IntelliSense dla nowo zainstalowanego pakietu. Karta **IntelliSense** zawiera również bardziej szczegółowe informacje. Należy pamiętać, że dopóki ta baza danych nie zostanie ukończona, funkcje IntelliSense, takie jak Autouzupełnianie i sprawdzanie składni, nie będą aktywne w edytorze dla tego pakietu.
   >
   > Program Visual Studio 2017 w wersji 15,6 lub nowszej używa innej i szybszej metody do pracy z technologią IntelliSense i wyświetla komunikat w tym efekcie na karcie **IntelliSense** .

## <a name="run-the-program"></a>Uruchamianie programu

1. Teraz, gdy [matplotlib](https://matplotlib.org/) jest zainstalowany, uruchom program z (**F5**) lub bez debugera (**Ctrl** + **F5**), aby wyświetlić dane wyjściowe:

   ![Przykład danych wyjściowych matplotlib](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Następny krok

> [!div class="nextstepaction"]
> [Pracuj z usługą git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Przejdź głębiej

- [Środowiska Python](managing-python-environments-in-visual-studio.md)
- [Nauka platformy Django w programie Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Nauka platformy Flask w programie Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)
