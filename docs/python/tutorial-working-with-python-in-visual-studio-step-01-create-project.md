---
title: Język Python w programie Visual Studio — samouczek krok 1, Utwórz projekt
titleSuffix: ''
description: Przegląd i krok 1 core Przewodnik po funkcji języka Python w programie Visual Studio, w tym wymagania wstępne i tworzenia nowego projektu języka Python.
ms.date: 01/28/2019
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 23f843c745d672d9aa4f8dcbfec9c25f7ba98919
ms.sourcegitcommit: 34940a18f5b03a59567f54c7024a0b16d4272f1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56155217"
---
# <a name="tutorial-work-with-python-in-visual-studio"></a>Samouczek: Praca z językiem Python w programie Visual Studio

Język Python jest popularnych języków programowania, które jest niezawodne, elastyczne, można łatwo dowiedzieć się, bezpłatnie do użycia we wszystkich systemach operacyjnych i obsługiwane przez społeczność deweloperów silne i wielu bezpłatnych bibliotek. Język obsługuje wszystkich sposobów rozwoju, w tym aplikacje sieci web, usług sieci web, aplikacje klasyczne, skryptów i obliczeń naukowych i jest używany przez wiele uniwersytety, analitykom, zwykłych deweloperów i podobne profesjonalnych deweloperów.

Visual Studio zapewnia najwyższej jakości obsługę języka Python. Ten samouczek przeprowadzi Cię przez następujące kroki:

- [Krok 0: Instalacja](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [Krok 1: Tworzenie projektu języka Python (w tym artykule)](#step-1-create-a-new-python-project)
- [Krok 2: Pisanie i uruchamianie kodu, aby zobaczyć funkcji IntelliSense Visual Studio w miejscu pracy](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [Krok 3: Utwórz więcej kodu w okna interaktywnego REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [Krok 4: Uruchom program ukończone w debugerze programu Visual Studio](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [Krok 5: Instalowanie pakietów i zarządzanie środowiskami Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [Krok 6: Praca z usługą Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

[!INCLUDE[tutorial-prereqs](includes/tutorial-prereqs.md)]

## <a name="step-1-create-a-new-python-project"></a>Krok 1. Utwórz nowy projekt języka Python

A *projektu* jest jak Visual Studio zarządza wszystkie pliki, które łączą się do tworzenia pojedynczej aplikacji, łącznie z kodu źródłowego, zasobów, konfiguracji i tak dalej. Projekt rozmieszczony i obsługuje relacje między projektu wszystkie pliki, a także zasobów zewnętrznych, które są współużytkowane przez wiele projektów. W efekcie projektów umożliwia aplikacji bez wysiłku rozwoju, i poszerzenia znacznie łatwiejsze niż po prostu zarządzanie relacjami projektu w folderach ad-hoc, skrypty, pliki tekstowe i nawet własne zdania.

W tym samouczku zaczynać prosty projekt zawierający pojedynczy pusty plik kodu.

1. W programie Visual Studio, wybierz **pliku** > **New** > **projektu** (**Ctrl** + **Shift**+**N**), co spowoduje uruchomienie **nowy projekt** okna dialogowego. W tym miejscu możesz przeglądać szablony wielu różnych językach, a następnie wybierz jedną dla projektu i określ, gdzie umieszcza pliki w programie Visual Studio.

1. Zaznacz, aby wyświetlić szablony Python **zainstalowane** > **Python** po lewej lub wyszukaj "Python". Przy użyciu wyszukiwania jest doskonałym sposobem na znajdowanie szablonu, jeśli nie pamiętasz lokalizacji w drzewie języków.

    ![Okno dialogowe nowego projektu za pomocą projektów języka Python pokazano](media/vs-getting-started-python-01-new-project.png)

    Zwróć uwagę, jak obsługa w języku Python w programie Visual Studio zawiera kilka szablonów projektu, w tym aplikacje sieci web przy użyciu platformy Bottle, Flask i Django. Na potrzeby tego przewodnika, Zacznijmy od pustego projektu.

1. Wybierz **aplikację w języku Python** szablonu, podaj nazwę dla projektu, a następnie wybierz **OK**.

1. Po kilku chwilach programu Visual Studio pokazuje strukturę projektu w **Eksploratora rozwiązań** okna (1). Domyślny plik kodu jest otwarty w edytorze, (2). **Właściwości** okna (3) również pojawi się dodatkowe informacje dla każdego elementu wybranego w **Eksploratora rozwiązań**, łącznie z jego dokładnej lokalizacji na dysku.

    ![Eksplorator rozwiązań z projektu języka Python](media/vs-getting-started-python-02-windows.png)

1. Zapoznaj się z może chwilę potrwać **Eksploratora rozwiązań**, czyli, gdzie przeglądać pliki i foldery w projekcie.

    ![Rozszerzona w Eksploratorze rozwiązań, aby wyświetlić różne funkcje](media/vs-getting-started-python-03-solution-explorer.png)

    (1) wyróżniony pogrubioną czcionką jest projektu, przy użyciu nazwę nadaną w **nowy projekt** okna dialogowego. Na dysku, ten projekt jest reprezentowany przez *.pyproj* pliku w folderze projektu.

    (2) przy najwyższym poziomie jest *rozwiązania*, która domyślnie ma taką samą nazwę jak projektu. To rozwiązanie, reprezentowane przez *.sln* plików na dysku, to kontener dla jednego lub kilku powiązanych projektów. Na przykład jeśli piszesz rozszerzenie języka C++ dla aplikacji języka Python projektu C++ może znajdują się w tym samym rozwiązaniu. Rozwiązanie może również zawierać projekt usługi sieci web, wraz z projektów dla programów dedykowanych testu.

    (3) w ramach projektu Zobacz pliki źródłowe, w tym przypadku jest tylko jeden *PY* pliku. Wybranie pliku powoduje wyświetlenie jego właściwości w **właściwości** okna. Dwukrotne kliknięcie pliku otwierany w sposób, który jest odpowiedni dla tego pliku.

    (4) również w projekcie jest **środowiska Python** węzła. Po rozwinięciu zostanie wyświetlony interpreterów języka Python, które są dostępne dla Ciebie. Rozwiń węzeł interpreter w taki sposób, aby zobaczyć bibliotek, które są zainstalowane w tym środowisku (5).

    Kliknij prawym przyciskiem myszy dowolny węzeł lub elementu w **Eksploratora rozwiązań** na dostęp do menu odpowiednich poleceń. Na przykład **Zmień nazwę** polecenie pozwala zmienić nazwę węzła lub elementu, w tym projektu i rozwiązania.

## <a name="next-step"></a>Następny krok

> [!div class="nextstepaction"]
> [Pisanie i uruchamianie kodu](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>Przejdź dalej

- [Projekty Python w programie Visual Studio](managing-python-projects-in-visual-studio.md).
- [Dowiedz się więcej o języku Python w witrynie python.org](https://www.python.org)
- [Python dla początkujących](https://www.python.org/about/gettingstarted/) (python.org)
