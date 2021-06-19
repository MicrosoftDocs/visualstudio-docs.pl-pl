---
title: Python w Visual Studio samouczku, krok 1, tworzenie projektu
titleSuffix: ''
description: Omówienie i krok 1 podstawowego przewodnika po możliwościach języka Python w języku Visual Studio, w tym wymagania wstępne i tworzenie nowego projektu języka Python.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: vs-acquisition
ms.workload:
- python
- data-science
ms.openlocfilehash: 927faad404e50a4cf31579c56882bf50208bbb21
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390701"
---
# <a name="tutorial-work-with-python-in-visual-studio"></a>Samouczek: praca z językiem Python na Visual Studio

Python to popularny język programowania, który jest niezawodny, elastyczny, łatwy do nauczenia się, może być używany we wszystkich systemach operacyjnych i jest obsługiwany zarówno przez silną społeczność deweloperów, jak i wiele bezpłatnych bibliotek. Język obsługuje wszelkiego rodzaju rozwój, w tym aplikacje internetowe, usługi internetowe, aplikacje klasyczne, skrypty i obliczenia naukowe. Jest on używany przez wiele uniwersytetów, naukowców, zwykłych deweloperów i profesjonalnych deweloperów.

Visual Studio zapewnia najwyższej klasy obsługę języka dla języka Python. Ten samouczek przeprowadzi Cię przez następujące kroki:

- [Krok 0. Instalacja](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [Krok 1. Tworzenie projektu w języku Python (w tym artykule)](#step-1-create-a-new-python-project)
- [Krok 2. Pisanie i uruchamianie kodu w celu Visual Studio funkcji IntelliSense w pracy](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [Krok 3. Tworzenie większej liczby kodu w oknie Interactive REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [Krok 4. Uruchamianie ukończonego programu w Visual Studio debugowania](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [Krok 5. Instalowanie pakietów i zarządzanie środowiskami Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [Krok 6. Praca z repozytorium Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

[!INCLUDE[tutorial-prereqs](includes/tutorial-prereqs.md)]

## <a name="step-1-create-a-new-python-project"></a>Krok 1. Tworzenie nowego projektu w języku Python

Projekt *to* sposób, Visual Studio wszystkimi plikami, które są ze sobą połączone, aby utworzyć pojedynczą aplikację, w tym kod źródłowy, zasoby, konfiguracje i tak dalej. Projekt sformalizuje i utrzymuje relację między wszystkimi plikami projektu, a także zasobami zewnętrznymi, które są współdzielone przez wiele projektów. W związku z tym projekty umożliwiają aplikacji łatwe rozszerzanie i rozwijanie się znacznie łatwiej niż po prostu zarządzanie relacjami projektu w folderach ad hoc, skryptach, plikach tekstowych, a nawet własnego zdania.

W tym samouczku zaczniesz od prostego projektu zawierającego pojedynczy, pusty plik kodu.

1. W Visual Studio pozycję **File**  >  **New**  >  **Project** (Nowy projekt)**(Ctrl** + **Shift** + **N),** co pozwala wyprowadzić **okno dialogowe Nowy** projekt. W tym miejscu przeglądasz szablony w różnych językach, a następnie wybierasz jeden z nich dla projektu i określasz, gdzie Visual Studio pliki.

1. Aby wyświetlić szablony języka Python, wybierz **pozycję Zainstalowany** język Python po lewej stronie lub wyszukaj pozycję  >   "Python". Użycie wyszukiwania to doskonały sposób na znalezienie szablonu, gdy nie można zapamiętać jego lokalizacji w drzewie języków.

    ![Okno dialogowe Nowy projekt z widocznymi projektami języka Python](media/vs-getting-started-python-01-new-project.png)

    Zwróć uwagę, że obsługa języka Python Visual Studio zawiera wiele szablonów projektów, w tym aplikacji internetowych korzystających ze środowisk Bottle, Flask i Django. Jednak na potrzeby tego przewodnika zacznijmy od pustego projektu.

1. Wybierz szablon **Aplikacja w języku Python,** określ nazwę projektu, a następnie wybierz przycisk **OK.**

1. Po kilku chwilach Visual Studio strukturę projektu w  oknie Eksplorator rozwiązań (1). Domyślny plik kodu jest otwarty w edytorze (2). Zostanie **wyświetlone** okno Właściwości (3) z dodatkowymi informacjami dla dowolnego elementu wybranego w Eksplorator rozwiązań **,** w tym jego dokładną lokalizację na dysku.

    ![Eksplorator rozwiązań przy użyciu projektu języka Python](media/vs-getting-started-python-02-windows.png)

1. Poświęć chwilę, aby zaznajomić się z Eksplorator rozwiązań **,** w którym przeglądasz pliki i foldery w projekcie.

    ![Eksplorator rozwiązań rozwinięty w celu pokazania różnych funkcji](media/vs-getting-started-python-03-solution-explorer.png)

    (1) Wyróżnione pogrubioną czcionką jest twój projekt, używając nazwy nadaowej w **oknie dialogowym Nowy** projekt. Na dysku ten projekt jest reprezentowany przez plik *pyproj* w folderze projektu.

    (2) Na najwyższym poziomie znajduje się rozwiązanie *,* które domyślnie ma taką samą nazwę jak projekt. Rozwiązanie reprezentowane przez plik *sln* na dysku jest kontenerem dla co najmniej jednego powiązanego projektu. Jeśli na przykład napiszesz rozszerzenie języka C++ dla aplikacji w języku Python, ten projekt języka C++ może znajdować się w tym samym rozwiązaniu. Rozwiązanie może również zawierać projekt dla usługi internetowej oraz projekty dedykowanych programów testowych.

    (3) W obszarze projektu zobaczysz pliki źródłowe, w tym przypadku tylko jeden *plik PY.* Wybranie pliku powoduje wyświetlenie jego właściwości w **oknie** Właściwości. Dwukrotne kliknięcie pliku otwiera go w dowolny sposób odpowiedni dla tego pliku.

    (4) W projekcie znajduje się również węzeł **Środowiska języka Python.** Po rozwinięciu zostaną wyświetlony interpretery języka Python, które są dla Ciebie dostępne. Rozwiń węzeł interpretera, aby wyświetlić biblioteki zainstalowane w tym środowisku (5).

    Kliknij prawym przyciskiem myszy dowolny węzeł lub element w **Eksplorator rozwiązań,** aby uzyskać dostęp do menu odpowiednich poleceń. Na przykład polecenie **Zmień** nazwę umożliwia zmianę nazwy dowolnego węzła lub elementu, w tym projektu i rozwiązania.

## <a name="next-step"></a>Następny krok

> [!div class="nextstepaction"]
> [Pisanie i uruchamianie kodu](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>Głębiej

- [Projekty języka Python w programie Visual Studio](managing-python-projects-in-visual-studio.md).
- [Dowiedz się więcej o języku Python na python.org](https://www.python.org)
- [Python dla początkujących](https://www.python.org/about/gettingstarted/) (python.org)
