---
title: Instalowanie obsługi języka Python
description: Jak zainstalować program Python Tools for Visual Studio (PTVS) w programie Visual Studio 2017, 2015, 2013, 2012 i 2010, w tym opcje i lokalizacje instalacji.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 09fb452d579130cdf6597ada3af509b35f24ff43
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254813"
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>Jak zainstalować obsługę języka Python w programie Visual Studio systemie Windows

Aby zainstalować obsługę języka Python dla Visual Studio (znanej również jako Python Tools for Visual Studio lub PTVS), postępuj zgodnie z instrukcjami w sekcji zgodnej z wersją Visual Studio:

- [Visual Studio 2017 i Visual Studio 2019](#visual-studio-2017-and-2019)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 i starsze](#visual-studio-2013-and-earlier)

Aby szybko przetestować obsługę języka Python po zakończeniu kroków instalacji, otwórz okno Python Interactive (Interaktywne) języka **Python,** naciskając **klawisz Alt** + **I** i wprowadzając . `2+2` Jeśli nie widzisz danych wyjściowych , `4` sprawdź ponownie kroki.

> [!Tip]
> Obciążenie języka Python zawiera przydatne rozszerzenie Cookiecutter, które udostępnia graficzny interfejs użytkownika do odnajdywania szablonów, opcji szablonów wejściowych oraz tworzenia projektów i plików. Aby uzyskać szczegółowe informacje, zobacz [Use Cookiecutter (Używanie cookiecutter).](using-python-cookiecutter-templates.md)

> [!Note]
> Obsługa języka Python nie jest obecnie dostępna w Visual Studio dla komputerów Mac, ale jest dostępna na komputerach Mac i w systemie Linux za pośrednictwem Visual Studio Code. Zobacz [pytania i odpowiedzi.](overview-of-python-tools-for-visual-studio.md#questions-and-answers)

<a name="visual-studio-2017-and-2019"></a>
## <a name="visual-studio-2019-and-visual-studio-2017"></a>Visual Studio 2019 i Visual Studio 2017

1. Pobierz i uruchom najnowszą wersję Visual Studio instalatora. Jeśli masz już Visual Studio, uruchom polecenie Instalator programu Visual Studio, wybierz  opcję Modyfikuj (zobacz Modyfikowanie Visual Studio [)](../install/modify-visual-studio.md)i przejdź do kroku 2.

    > [!div class="nextstepaction"]
    > [Instalowanie programu Visual Studio 2019 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Wersja Community jest dla poszczególnych deweloperów, uczenia na potrzeby zajęć, badań akademickich i open source rozwoju. W przypadku innych zastosowań zainstaluj [program Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) lub Visual Studio [2019 Enterprise.](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

1. Instalator przedstawia listę obciążeń, które są grupami powiązanych opcji dla określonych obszarów programisticznych. W przypadku języka Python wybierz obciążenie **Programowanie w języku Python.**

    ![Obciążenie programowania w języku Python w Visual Studio instalatora](media/installation-python-workload.png)

    ::: moniker range="vs-2017"
    Opcjonalnie: jeśli pracujesz z nauką o danych, weź pod uwagę również obciążenie Aplikacje do **analizy i przetwarzania danych.** To obciążenie obejmuje obsługę języków Python, R i F#. Aby uzyskać więcej informacji, zobacz [Obciążenie aplikacji analizy i przetwarzania danych](data-science-and-analytical-applications-workload.md).

    > [!Note]
    > Obciążenia języka Python i nauki o danych są dostępne tylko w Visual Studio 2017 w wersji 15.2 i nowszych.

    ::: moniker-end

    ::: moniker range=">=vs-2019"
    Opcjonalnie: jeśli pracujesz z nauką o danych, weź pod uwagę również obciążenie Aplikacje do **analizy i przetwarzania danych.** To obciążenie obejmuje obsługę języków Python i F#. Aby uzyskać więcej informacji, zobacz [Obciążenie aplikacji analizy i przetwarzania danych](data-science-and-analytical-applications-workload.md).
    ::: moniker-end

1. Po prawej stronie instalatora wybierz dodatkowe opcje, jeśli to konieczne. Pomiń ten krok, aby zaakceptować opcje domyślne.

    ::: moniker range="vs-2017"
    ![Opcje programowania w języku Python Visual Studio instalatora](media/installation-python-options.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    ![Opcje programowania w języku Python w Visual Studio 2019 r.](media/installation-python-options-2019.png)
    ::: moniker-end

    ::: moniker range="<=vs-2017"
    | Opcja | Opis |
    | --- | --- |
    | Dystrybucje języka Python | Wybierz dowolną kombinację dostępnych opcji, takich jak warianty 32-bitowe i 64-bitowe wersji języka Python 2, Python 3, Miniconda, Anaconda2 i Anaconda3, z których planujesz pracować. Każdy z nich zawiera interpreter, środowisko uruchomieniowe i biblioteki dystrybucji. Anaconda to otwarta platforma nauki o danych, która zawiera szeroką gamę wstępnie zainstalowanych pakietów. (Możesz wrócić do instalatora Visual Studio w dowolnym momencie, aby dodać lub usunąć dystrybucje).  **Uwaga:** jeśli zainstalowano dystrybucję poza instalatorem Visual Studio, nie ma potrzeby sprawdzania równoważnej opcji w tym miejscu. Visual Studio automatycznie wykrywa istniejące instalacje języka Python. Zobacz [okno Środowiska języka Python](managing-python-environments-in-visual-studio.md#the-python-environments-window). Ponadto jeśli jest dostępna nowsza wersja języka Python niż pokazana w instalatorze, możesz zainstalować tę wersję oddzielnie i Visual Studio ją wykryć. |
    | **Obsługa szablonów Cookiecutter** | Instaluje graficzny interfejs użytkownika Cookiecutter, aby odnajdywać szablony, opcje szablonów wejściowych oraz tworzyć projekty i pliki. Zobacz [Use the Cookiecutter extension (Używanie rozszerzenia Cookiecutter).](using-python-cookiecutter-templates.md) |
    | **Obsługa sieci Web w języku Python** | Instaluje narzędzia do tworzenia aplikacji internetowych, w tym obsługę edytowania kodu HTML, CSS i JavaScript, wraz z szablonami dla projektów korzystających ze platform Bottle, Flask i Django. Zobacz [Python web project templates (Szablony projektów internetowych języka Python).](python-web-application-project-templates.md) |
    | **Obsługa IoT w języku Python** | Obsługuje programowanie dla systemu Windows IoT Core przy użyciu języka Python. |
    | **Natywne narzędzia programskie języka Python** | Instaluje kompilator języka C++ i inne składniki niezbędne do tworzenia natywnych rozszerzeń dla języka Python. Zobacz [Create a C++ extension for Python (Tworzenie rozszerzenia C++ dla języka Python).](working-with-c-cpp-python-in-visual-studio.md) Zainstaluj również obciążenie **Tworzenie aplikacji klasycznych w języku C++,** aby uzyskać pełną obsługę języka C++. |
    | **Azure Cloud Services podstawowe narzędzia** | Zapewnia dodatkową obsługę programowania dla Azure Cloud Services w języku Python. Zobacz [Projekty usług w chmurze platformy Azure.](python-azure-cloud-service-project-template.md) |
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    | Opcja | Opis |
    | --- | --- |
    | Dystrybucje języka Python | Wybierz dowolną kombinację dostępnych opcji, takich jak warianty 32-bitowe i 64-bitowe wersji języka Python 2, Python 3, Miniconda, Anaconda2 i Anaconda3, z których planujesz pracować. Każdy z nich zawiera interpreter, środowisko uruchomieniowe i biblioteki dystrybucji. Anaconda to otwarta platforma nauki o danych, która zawiera szeroką gamę wstępnie zainstalowanych pakietów. (Możesz wrócić do instalatora Visual Studio w dowolnym momencie, aby dodać lub usunąć dystrybucje).  **Uwaga:** jeśli zainstalowano dystrybucję poza instalatorem Visual Studio, nie ma potrzeby sprawdzania równoważnej opcji w tym miejscu. Visual Studio automatycznie wykrywa istniejące instalacje języka Python. Zobacz [okno Środowiska języka Python](managing-python-environments-in-visual-studio.md#the-python-environments-window). Ponadto jeśli jest dostępna nowsza wersja języka Python niż pokazana w instalatorze, możesz zainstalować tę wersję oddzielnie i Visual Studio ją wykryć. |
    | **Obsługa szablonów Cookiecutter** | Instaluje graficzny interfejs użytkownika Cookiecutter, aby odnajdywać szablony, opcje szablonów wejściowych oraz tworzyć projekty i pliki. Zobacz [Use the Cookiecutter extension (Używanie rozszerzenia Cookiecutter).](using-python-cookiecutter-templates.md) |
    | **Obsługa sieci Web w języku Python** | Instaluje narzędzia do tworzenia aplikacji internetowych, w tym obsługę edytowania kodu HTML, CSS i JavaScript, wraz z szablonami dla projektów korzystających ze platform Bottle, Flask i Django. Zobacz [Python web project templates (Szablony projektów internetowych języka Python).](python-web-application-project-templates.md) |
    | **Natywne narzędzia programskie języka Python** | Instaluje kompilator języka C++ i inne składniki niezbędne do tworzenia natywnych rozszerzeń dla języka Python. Zobacz [Create a C++ extension for Python (Tworzenie rozszerzenia C++ dla języka Python).](working-with-c-cpp-python-in-visual-studio.md) Zainstaluj również obciążenie **Tworzenie aplikacji klasycznych w języku C++,** aby uzyskać pełną obsługę języka C++. |
    ::: moniker-end

1. Po zakończeniu instalacji instalator udostępnia opcje modyfikowania, uruchamiania, naprawiania lub odinstalowywania Visual Studio. Przycisk **Modyfikuj** zmienia się na **Aktualizuj,** gdy aktualizacje Visual Studio są dostępne dla wszystkich zainstalowanych składników. (Opcja **Modyfikuj** jest następnie dostępna w menu rozwijanych). Możesz również uruchomić program Visual Studio instalatora z menu **Start** systemu Windows, wyszukując pozycję "Visual Studio".

    ![Uruchamianie, modyfikowanie, modyfikowanie lub odinstalowywanie Visual Studio z instalatora](media/installation-vs-launch.png)

### <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli wystąpią problemy z instalowaniem lub uruchamianiem języka Python w Visual Studio, spróbuj wykonać następujące czynności:

- Ustal, czy ten sam błąd występuje przy użyciu interfejsu wiersza polecenia języka Python, *to* python.exez wiersza polecenia.
- Użyj opcji [**Napraw**](../install/repair-visual-studio.md) w instalatorze Visual Studio instalacji.
- Napraw lub ponownie zainstaluj język Python **za pomocą ustawień**& funkcji  >  **w** systemie Windows.

**Przykładowy** błąd: Nie można uruchomić procesu interakcyjnego: System.ComponentModel.Win32Exception (0x80004005): Nieznany błąd (0xc0000135) na stronie Microsoft.PythonTools.Repl.PythonInteractiveEvaluator.d__43.MoveNext().

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Uruchom instalatora Visual Studio za pomocą **Panel sterowania > i** funkcji, wybierając pozycję **Microsoft Visual Studio 2015,** a następnie pozycję **Zmień.**

1. W instalatorze wybierz pozycję **Modyfikuj.**

1. Wybierz **pozycję Języki**  >  **programowania Python Tools for Visual Studio** a następnie pozycję **Dalej:**

    ![Opcja PTVS w instalatorze Visual Studio 2015](media/installation-vs2015.png)

1. Po Visual Studio instalacji zainstaluj [wybranego interpretera języka Python.](installing-python-interpreters.md) Visual Studio 2015 obsługuje tylko język Python 3.5 i starsze; Nowsze wersje generują komunikat, taki jak **Nieobsługiwany język Python w wersji 3.6).** Jeśli interpreter jest już zainstalowany i Visual Studio nie wykrywa go automatycznie, zobacz Ręczne identyfikowanie [istniejącego środowiska.](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 i starsze

1. Zainstaluj odpowiednią wersję Python Tools for Visual Studio dla swojej wersji programu Visual Studio:

    - Visual Studio 2013: [PTVS 2.2.2 dla Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2.2). Okno **dialogowe** File New Project  >  **(Nowy** projekt Visual Studio 2013) zawiera skrót do tego procesu.
    - Visual Studio 2010 i 2012: [PTVS 2.1.1 for Visual Studio 2010 and 2012](https://github.com/Microsoft/PTVS/releases/v2.1.1)

1. [Zainstaluj wybranego interpretera języka Python.](installing-python-interpreters.md) Jeśli masz już zainstalowany interpreter i Visual Studio nie wykrywa go automatycznie, zobacz [Ręczne identyfikowanie istniejącego środowiska.](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)

## <a name="install-locations"></a>Lokalizacje instalacji

Domyślnie obsługa języka Python jest instalowana dla wszystkich użytkowników na komputerze.

W przypadku Visual Studio 2019 i Visual Studio 2017 obciążenie języka Python jest instalowane w folderze *%ProgramFiles(x86)%\Microsoft Visual Studio \\<VS_version>\\<VS_edition>Common7\IDE\Extensions\Microsoft\Python,* gdzie VS_version &lt; to &gt; 2019 lub 2017, a VS_edition to Community, Professional lub &lt; &gt; Enterprise.

W Visual Studio 2015 i starszych wersjach ścieżki instalacji są następujące:

- 32-bitowe:
  - Ścieżka: *%Program Files(x86)%\Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio \\<PTVS_ver>*
  - Lokalizacja rejestru ścieżki: **HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\\<VS_ver>\InstallDir**
- 64-bitowe:
  - Ścieżka: *%Program Files%\Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio \\<PTVS_ver>*
  - Lokalizacja rejestru ścieżki: **HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\\<VS_ver>\InstallDir**

gdzie:

- &lt;VS_ver &gt; to:
  - 14.0 dla Visual Studio 2015
  - 12.0 dla Visual Studio 2013
  - 11.0 dla Visual Studio 2012
  - 10.0 dla Visual Studio 2010 r.
- &lt;PTVS_ver to numer wersji, taki jak &gt; 2.2.2, 2.1.1, 2.0, 1.5, 1.1 lub 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Instalacje specyficzne dla użytkownika (wersja 1.5 i starsze)

Python Tools for Visual Studio wersji 1.5 lub starszej dozwolonej tylko dla bieżącego użytkownika. W takim przypadku ścieżka instalacji to *%LocalAppData%\Microsoft\VisualStudio \\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio \\<PTVS_ver>* gdzie VS_ver i PTVS_ver są takie same, jak opisano &lt; &gt; &lt; &gt; powyżej.
