---
title: Python w programie Visual Studio krok 1, tworzenie projektu
titleSuffix: ''
description: Omówienie i krok 1 podstawowego przewodnika po możliwościach języka Python w programie Visual Studio, w tym wymagania wstępne i tworzenie nowego projektu języka Python.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ed4fdbfe7090a66d955461f2c3a394f6fb661c5a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "62430747"
---
# <a name="tutorial-work-with-python-in-visual-studio"></a>Samouczek: Praca z Pythonem w programie Visual Studio

Python to popularny język programowania, który jest niezawodny, elastyczny, łatwy do nauczenia się, darmowy w użyciu we wszystkich systemach operacyjnych i wspierany zarówno przez silną społeczność programistów, jak i wiele darmowych bibliotek. Język obsługuje wszystkie żyrowi rozwoju, w tym aplikacje internetowe, usługi internetowe, aplikacje komputerowe, skrypty i obliczenia naukowe i jest używany przez wiele uniwersytetów, naukowców, przypadkowych programistów i profesjonalnych programistów.

Visual Studio zapewnia pierwszorzędną obsługę języka dla języka Python. W tym samouczku przedstawiono następujące kroki:

- [Krok 0: Instalacja](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [Krok 1: Tworzenie projektu języka Python (ten artykuł)](#step-1-create-a-new-python-project)
- [Krok 2: Napisz i uruchom kod, aby zobaczyć Visual Studio IntelliSense w pracy](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [Krok 3: Tworzenie większej ilości kodu w interaktywnym oknie REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [Krok 4: Uruchom ukończony program w debugerze programu Visual Studio](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [Krok 5: Instalowanie pakietów i zarządzanie środowiskami Pythona](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [Krok 6: Praca z Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

[!INCLUDE[tutorial-prereqs](includes/tutorial-prereqs.md)]

## <a name="step-1-create-a-new-python-project"></a>Krok 1: Tworzenie nowego projektu Języka Python

*Projekt* jest jak Visual Studio zarządza wszystkie pliki, które łączą się w celu uzyskania pojedynczej aplikacji, w tym kod źródłowy, zasoby, konfiguracje i tak dalej. Projekt formalizuje i utrzymuje relację między wszystkimi plikami projektu, a także zasobami zewnętrznymi, które są współużytkowane między wieloma projektami. W związku z tym projekty umożliwiają aplikacji bezproblemowe rozszerzanie i rozwijanie się znacznie łatwiej niż zwykłe zarządzanie relacjami projektu w folderach ad hoc, skryptach, plikach tekstowych, a nawet własnym umyśle.

W tym samouczku zaczynasz od prostego projektu zawierającego pojedynczy, pusty plik kodu.

1. W programie Visual Studio wybierz **pozycję Plik** > **nowego** > **projektu** **(Ctrl**+**Shift**+**N),** które powoduje wyświetlanie okna dialogowego Nowy **projekt.** W tym miejscu można przeglądać szablony w różnych językach, a następnie wybrać jeden dla projektu i określić, gdzie program Visual Studio umieszcza pliki.

1. Aby wyświetlić szablony Języka Python, wybierz **pozycję Zainstalowany** > **Python** po lewej stronie lub wyszukaj hasło "Python". Korzystanie z wyszukiwania to świetny sposób na znalezienie szablonu, gdy nie pamiętasz jego lokalizacji w drzewie języków.

    ![Nowe okno dialogowe projektu z pokazanymi projektami języka Python](media/vs-getting-started-python-01-new-project.png)

    Zwróć uwagę, jak python wsparcie w programie Visual Studio zawiera szereg szablonów projektu, w tym aplikacji sieci web przy użyciu Bottle, Flask i Django struktur. Na potrzeby tego przewodnika, jednak zacznijmy od pustego projektu.

1. Wybierz szablon **aplikacji języka Python,** określ nazwę projektu i wybierz **przycisk OK**.

1. Po kilku chwilach visual studio pokazuje strukturę projektu w oknie **Eksploratora rozwiązań** (1). Domyślny plik kodu jest otwarty w edytorze (2). Okno **Właściwości** (3) pojawia się również, aby wyświetlić dodatkowe informacje dla każdego elementu wybranego w **Eksploratorze rozwiązań,** w tym jego dokładną lokalizację na dysku.

    ![Eksplorator rozwiązań z projektem języka Python](media/vs-getting-started-python-02-windows.png)

1. Poświęć kilka chwil na zapoznanie się z **Eksploratorem rozwiązań,** czyli w miejscu przeglądania plików i folderów w projekcie.

    ![Eksplorator rozwiązań został rozwinięty w celu wyświetlenia różnych funkcji](media/vs-getting-started-python-03-solution-explorer.png)

    (1) Wyróżniony pogrubioną czcionką jest twój projekt, używając nazwy nadany w oknie dialogowym **Nowy projekt.** Na dysku ten projekt jest reprezentowany przez plik *pyproj* w folderze projektu.

    (2) Na najwyższym poziomie jest *rozwiązanie,* które domyślnie ma taką samą nazwę jak projekt. Rozwiązanie, reprezentowane przez plik *.sln* na dysku, jest kontenerem dla jednego lub więcej powiązanych projektów. Na przykład jeśli piszesz rozszerzenie C++ dla aplikacji języka Python, ten projekt języka C++ może przebywać w ramach tego samego rozwiązania. Rozwiązanie może również zawierać projekt dla usługi sieci web, wraz z projektami dla dedykowanych programów testowych.

    (3) W projekcie widzisz pliki źródłowe, w tym przypadku tylko jeden plik *py.* Wybranie pliku powoduje wyświetlenie jego właściwości w oknie **Właściwości.** Dwukrotne kliknięcie pliku powoduje otwarcie go w dowolny sposób dla danego pliku.

    (4) Również w ramach projektu jest węzeł **Środowiska Python.** Po rozwinięciu zostaną wyświetlone interpretery języka Python, które są dostępne dla Ciebie. Rozwiń węzeł interpretera, aby wyświetlić biblioteki zainstalowane w tym środowisku (5).

    Kliknij prawym przyciskiem myszy dowolny węzeł lub element w **Eksploratorze rozwiązań,** aby uzyskać dostęp do menu odpowiednich poleceń. Na przykład zmień **nazwę** polecenia umożliwia zmianę nazwy dowolnego węzła lub elementu, w tym projektu i rozwiązania.

## <a name="next-step"></a>Następny krok

> [!div class="nextstepaction"]
> [Pisanie i uruchamianie kodu](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>Głębiej

- [Projekty języka Python w programie Visual Studio](managing-python-projects-in-visual-studio.md).
- [Dowiedz się więcej o języku Python na python.org](https://www.python.org)
- [Python dla początkujących](https://www.python.org/about/gettingstarted/) (python.org)
