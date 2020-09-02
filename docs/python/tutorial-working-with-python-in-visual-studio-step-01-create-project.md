---
title: Samouczek Python w programie Visual Studio — krok 1, tworzenie projektu
titleSuffix: ''
description: Omówienie i krok 1 podstawowego przewodnika dotyczącego możliwości języka Python w programie Visual Studio, w tym wymagania wstępne i tworzenie nowego projektu w języku Python.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62430747"
---
# <a name="tutorial-work-with-python-in-visual-studio"></a>Samouczek: współpraca z językiem Python w programie Visual Studio

Python to popularny język programowania, który jest niezawodny, elastyczny, łatwy do uczenia się, bezpłatny do użycia we wszystkich systemach operacyjnych i obsługiwany przez zarówno silną społeczność deweloperów, jak i wiele bezpłatnych bibliotek. Język obsługuje wszystkie rodzaje opracowywania, w tym aplikacje sieci Web, usługi sieci Web, aplikacje klasyczne, skrypty i obliczenia naukowe, które są używane przez wielu uniwersytetów, naukowców, profesjonalnych deweloperów i informatyków.

Program Visual Studio zapewnia obsługę języków pierwszej klasy dla języka Python. Ten samouczek przeprowadzi Cię przez następujące kroki:

- [Krok 0: instalacja](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [Krok 1. Tworzenie projektu w języku Python (ten artykuł)](#step-1-create-a-new-python-project)
- [Krok 2. Pisanie i uruchamianie kodu, aby zobaczyć Visual Studio IntelliSense w pracy](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [Krok 3. Tworzenie większej ilości kodu w oknie interaktywnym REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [Krok 4. Uruchamianie ukończonego programu w debugerze programu Visual Studio](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [Krok 5. Instalowanie pakietów i zarządzanie środowiskami języka Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [Krok 6. Współpraca z usługą git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

[!INCLUDE[tutorial-prereqs](includes/tutorial-prereqs.md)]

## <a name="step-1-create-a-new-python-project"></a>Krok 1. Tworzenie nowego projektu w języku Python

*Projekt* polega na tym, jak program Visual Studio zarządza wszystkimi plikami, które łączą się w celu utworzenia pojedynczej aplikacji, w tym kodu źródłowego, zasobów, konfiguracji itd. Projekt formalizes i utrzymuje relacje między wszystkimi plikami projektu a także zasobami zewnętrznymi, które są współużytkowane przez wiele projektów. W związku z tym projekty umożliwiają łatwe rozszerzanie i zwiększanie znacznie łatwiejszego zarządzania relacjami projektu w folderach ad hoc, skryptach, plikach tekstowych, a nawet na własnych kwestiach.

Ten samouczek rozpoczyna się od prostego projektu zawierającego pojedynczy, pusty plik kodu.

1. W programie Visual Studio wybierz pozycję **plik**  >  **Nowy**  >  **projekt** (**Ctrl** + **SHIFT** + **N**), co spowoduje wyświetlenie okna dialogowego **Nowy projekt** . W tym miejscu przeglądasz szablony w różnych językach, a następnie wybierzesz jeden dla projektu i określ, gdzie program Visual Studio umieści pliki.

1. Aby wyświetlić szablony języka Python, wybierz opcję **zainstalowane**środowisko  >  **Python** po lewej stronie lub wyszukaj ciąg "Python". Korzystanie z wyszukiwania to doskonały sposób na znalezienie szablonu, gdy nie można zapamiętać jego lokalizacji w drzewie języków.

    ![Okno dialogowe Nowy projekt z pokazanymi projektami języka Python](media/vs-getting-started-python-01-new-project.png)

    Zwróć uwagę, jak obsługa języka Python w programie Visual Studio obejmuje wiele szablonów projektów, w tym aplikacji sieci Web, przy użyciu butelek, kolb i platform Django. Na potrzeby tego instruktażu należy jednak zacząć od pustego projektu.

1. Wybierz szablon **aplikacja** w języku Python, określ nazwę projektu, a następnie wybierz **przycisk OK**.

1. Po kilku chwilach program Visual Studio wyświetli strukturę projektu w oknie **Eksplorator rozwiązań** (1). Domyślny plik kodu jest otwarty w edytorze (2). Pojawia się również okno **Właściwości** (3), aby wyświetlić dodatkowe informacje dotyczące dowolnego elementu wybranego w **Eksplorator rozwiązań**, w tym dokładnej lokalizacji na dysku.

    ![Eksplorator rozwiązań z projektem języka Python](media/vs-getting-started-python-02-windows.png)

1. Poświęć kilka minut, aby zaznajomić się z **Eksplorator rozwiązań**, który umożliwia przeglądanie plików i folderów w projekcie.

    ![Eksplorator rozwiązań rozwinięte, aby pokazać różne funkcje](media/vs-getting-started-python-03-solution-explorer.png)

    (1) wyróżnione czcionką pogrubioną jest projektem, przy użyciu nazwy podanych w oknie dialogowym **Nowy projekt** . Na dysku ten projekt jest reprezentowany przez plik *. pyproj* w folderze projektu.

    (2) na najwyższym poziomie jest *rozwiązaniem*, które domyślnie ma taką samą nazwę jak projekt. Rozwiązanie reprezentowane przez plik *. sln* na dysku jest kontenerem dla co najmniej jednego powiązanego projektu. Przykładowo, jeśli piszesz rozszerzenie C++ dla aplikacji w języku Python, ten projekt C++ może znajdować się w tym samym rozwiązaniu. Rozwiązanie może również zawierać projekt dla usługi sieci Web, wraz z projektami dla dedykowanych programów testowych.

    (3) w projekcie widoczne są pliki źródłowe, w tym przypadku tylko jeden plik *. PR* . Wybranie pliku powoduje wyświetlenie jego właściwości w oknie **Właściwości** . Dwukrotne kliknięcie pliku powoduje otwarcie go w dowolny sposób, który jest odpowiedni dla tego pliku.

    (4) również w projekcie jest węzłem **środowiska Python** . Gdy zostanie rozwinięte, zobaczysz interpretery języka Python, które są dostępne dla Ciebie. Rozwiń węzeł interpreter, aby wyświetlić biblioteki, które są zainstalowane w tym środowisku (5).

    Kliknij prawym przyciskiem myszy dowolny węzeł lub element w **Eksplorator rozwiązań** , aby uzyskać dostęp do menu odpowiednich poleceń. Na przykład polecenie **Zmień** nazwę pozwala zmienić nazwę dowolnego węzła lub elementu, łącznie z projektem i rozwiązaniem.

## <a name="next-step"></a>Następny krok

> [!div class="nextstepaction"]
> [Zapisz i uruchom kod](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>Przejdź głębiej

- [Projekty języka Python w programie Visual Studio](managing-python-projects-in-visual-studio.md).
- [Dowiedz się więcej o języku Python w python.org](https://www.python.org)
- [Python for początkując](https://www.python.org/about/gettingstarted/) (Python.org)
