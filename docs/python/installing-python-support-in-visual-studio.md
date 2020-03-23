---
title: Pomoc techniczna aplikacji Install Python
description: Jak zainstalować narzędzia Python dla programu Visual Studio (PTVS) w programie Visual Studio 2017, 2015, 2013, 2012 i 2010, w tym opcje i lokalizacje instalacji.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 15869119ea867e41d3b91a1f046d1ffb995cd4e4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75398421"
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>Jak zainstalować pomoc techniczną języka Python w programie Visual Studio w systemie Windows

Aby zainstalować obsługę języka Python dla programu Visual Studio (znanego również jako Narzędzia Python dla programu Visual Studio lub PTVS), postępuj zgodnie z instrukcjami w sekcji, która pasuje do twojej wersji programu Visual Studio:

- [Visual Studio 2017 i Visual Studio 2019](#visual-studio-2017-and-2019)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 i starsze](#visual-studio-2013-and-earlier)

Aby szybko przetestować obsługę języka Python po wykonaniu kroków instalacji, `2+2`otwórz okno **Python Interactive,** naciskając klawisz **Alt**+**I** i wprowadzając . Jeśli nie widzisz danych wyjściowych `4`, sprawdź ponownie swoje kroki.

> [!Tip]
> Obciążenie języka Python zawiera pomocne rozszerzenie Cookiecutter, które zapewnia graficzny interfejs użytkownika do odnajdywać szablony, opcje szablonów wejściowych i tworzyć projekty i pliki. Aby uzyskać szczegółowe informacje, zobacz [Korzystanie z cookiecutter](using-python-cookiecutter-templates.md).

> [!Note]
> Obsługa języka Python nie jest obecnie dostępna w programie Visual Studio dla komputerów Mac, ale jest dostępna na komputerach Mac i Linux za pośrednictwem programu Visual Studio Code. Zobacz [pytania i odpowiedzi](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="visual-studio-2017-and-2019"></a>
## <a name="visual-studio-2019-and-visual-studio-2017"></a>Visual Studio 2019 i Visual Studio 2017

1. Pobierz i uruchom najnowszy instalator programu Visual Studio. Jeśli masz już zainstalowany program Visual Studio, uruchom Instalatora programu Visual Studio, wybierz opcję **Modyfikuj** (zobacz [Modyfikowanie programu Visual Studio](../install/modify-visual-studio.md)) i przejdź do kroku 2.

    > [!div class="nextstepaction"]
    > [Instalowanie społeczności programu Visual Studio 2019](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Edycja społeczności jest dla poszczególnych programistów, uczenia się w klasie, badań akademickich i rozwoju open source. W przypadku innych zastosowań należy zainstalować program [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) lub Visual Studio [2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted).

1. Instalator przedstawia listę obciążeń, które są grupami powiązanych opcji dla określonych obszarów rozwoju. W przypadku języka Python wybierz obciążenie **programistyczne języka Python.**

    ![Obciążenie programistyczne języka Python w instalatorze programu Visual Studio](media/installation-python-workload.png)

    ::: moniker range="vs-2017"
    Opcjonalnie: jeśli pracujesz z nauki o danych, należy również wziąć pod uwagę **analizy danych i analizy aplikacji** obciążenia. To obciążenie obejmuje obsługę języków Python, R i F#. Aby uzyskać więcej informacji, zobacz [Analiza danych i obciążenie aplikacji analitycznych](data-science-and-analytical-applications-workload.md).

    > [!Note]
    > Obciążenia python i data science są dostępne tylko w programie Visual Studio 2017 w wersji 15.2 i nowszych.

    ::: moniker-end

    ::: moniker range=">=vs-2019"
    Opcjonalnie: jeśli pracujesz z nauki o danych, należy również wziąć pod uwagę **analizy danych i analizy aplikacji** obciążenia. To obciążenie obejmuje obsługę języków Python i F#. Aby uzyskać więcej informacji, zobacz [Analiza danych i obciążenie aplikacji analitycznych](data-science-and-analytical-applications-workload.md).
    ::: moniker-end

1. Po prawej stronie instalatora wybierz dodatkowe opcje w razie potrzeby. Pomiń ten krok, aby zaakceptować opcje domyślne.

    ::: moniker range="vs-2017"
    ![Opcje tworzenia języka Python w instalatorze programu Visual Studio](media/installation-python-options.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    ![Opcje tworzenia języka Python w instalatorze programu Visual Studio 2019](media/installation-python-options-2019.png)
    ::: moniker-end

    ::: moniker range="<=vs-2017"
    | Opcja | Opis |
    | --- | --- |
    | Dystrybucje języka Python | Wybierz dowolną kombinację dostępnych opcji, takich jak 32-bitowe i 64-bitowe warianty dystrybucji Python 2, Python 3, Miniconda, Anaconda2 i Anaconda3, z którymi zamierzasz pracować. Każdy z nich zawiera interpreter dystrybucji, środowisko uruchomieniowe i biblioteki. Anaconda, w szczególności, jest otwartą platformą do nauki o danych, która zawiera szeroką gamę wstępnie zainstalowanych pakietów. (W dowolnym momencie można powrócić do instalatora programu Visual Studio, aby dodać lub usunąć dystrybucje).  **Uwaga:** Jeśli zainstalowano dystrybucję poza instalatorem programu Visual Studio, nie ma potrzeby sprawdzania równoważnej opcji w tym miejscu. Program Visual Studio automatycznie wykrywa istniejące instalacje języka Python. Zobacz [okno Środowiska Pythona](managing-python-environments-in-visual-studio.md#the-python-environments-window). Ponadto jeśli nowsza wersja języka Python jest dostępna niż to, co jest wyświetlane w instalatorze, można zainstalować tę wersję oddzielnie i Visual Studio wykryje go. |
    | **Obsługa szablonów cookiecutter** | Instaluje graficzny interfejs użytkownika Cookiecutter, aby odnajdować szablony, opcje szablonów wejściowych i tworzyć projekty i pliki. Zobacz [Korzystanie z rozszerzenia Cookiecutter](using-python-cookiecutter-templates.md). |
    | **Pomoc techniczna języka Python** | Instaluje narzędzia do tworzenia stron internetowych, w tym obsługę edycji HTML, CSS i JavaScript, wraz z szablonami dla projektów wykorzystujących struktury Bottle, Flask i Django. Zobacz [szablony projektów sieci Web języka Python](python-web-application-project-templates.md). |
    | **Pomoc techniczna aplikacji Python IoT** | Obsługuje tworzenie rdzenia IoT systemu Windows przy użyciu języka Python. |
    | **Natywne narzędzia programistyczne Języka Python** | Instaluje kompilator C++ i inne składniki niezbędne do tworzenia natywnych rozszerzeń dla języka Python. Zobacz [Tworzenie rozszerzenia C++ dla języka Python](working-with-c-cpp-python-in-visual-studio.md). Zainstaluj również programowy programu Desktop z obciążeniem **języka C++** w celu uzyskania pełnej obsługi języka C++. |
    | **Podstawowe narzędzia usług w chmurze azure** | Zapewnia dodatkową obsługę dla deweloperów usług w chmurze Azure w języku Python. Zobacz [projekty usług w chmurze platformy Azure](python-azure-cloud-service-project-template.md). |
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    | Opcja | Opis |
    | --- | --- |
    | Dystrybucje języka Python | Wybierz dowolną kombinację dostępnych opcji, takich jak 32-bitowe i 64-bitowe warianty dystrybucji Python 2, Python 3, Miniconda, Anaconda2 i Anaconda3, z którymi zamierzasz pracować. Każdy z nich zawiera interpreter dystrybucji, środowisko uruchomieniowe i biblioteki. Anaconda, w szczególności, jest otwartą platformą do nauki o danych, która zawiera szeroką gamę wstępnie zainstalowanych pakietów. (W dowolnym momencie można powrócić do instalatora programu Visual Studio, aby dodać lub usunąć dystrybucje).  **Uwaga:** Jeśli zainstalowano dystrybucję poza instalatorem programu Visual Studio, nie ma potrzeby sprawdzania równoważnej opcji w tym miejscu. Program Visual Studio automatycznie wykrywa istniejące instalacje języka Python. Zobacz [okno Środowiska Pythona](managing-python-environments-in-visual-studio.md#the-python-environments-window). Ponadto jeśli nowsza wersja języka Python jest dostępna niż to, co jest wyświetlane w instalatorze, można zainstalować tę wersję oddzielnie i Visual Studio wykryje go. |
    | **Obsługa szablonów cookiecutter** | Instaluje graficzny interfejs użytkownika Cookiecutter, aby odnajdować szablony, opcje szablonów wejściowych i tworzyć projekty i pliki. Zobacz [Korzystanie z rozszerzenia Cookiecutter](using-python-cookiecutter-templates.md). |
    | **Pomoc techniczna języka Python** | Instaluje narzędzia do tworzenia stron internetowych, w tym obsługę edycji HTML, CSS i JavaScript, wraz z szablonami dla projektów wykorzystujących struktury Bottle, Flask i Django. Zobacz [szablony projektów sieci Web języka Python](python-web-application-project-templates.md). |
    | **Natywne narzędzia programistyczne Języka Python** | Instaluje kompilator C++ i inne składniki niezbędne do tworzenia natywnych rozszerzeń dla języka Python. Zobacz [Tworzenie rozszerzenia C++ dla języka Python](working-with-c-cpp-python-in-visual-studio.md). Zainstaluj również programowy programu Desktop z obciążeniem **języka C++** w celu uzyskania pełnej obsługi języka C++. |
    | **Podstawowe narzędzia usług w chmurze azure** | Zapewnia dodatkową obsługę dla deweloperów usług w chmurze Azure w języku Python. Zobacz [projekty usług w chmurze platformy Azure](python-azure-cloud-service-project-template.md). |
    ::: moniker-end

1. Po instalacji instalator udostępnia opcje modyfikowania, uruchamiania, naprawy lub odinstalowywania programu Visual Studio. Przycisk **Modyfikuj** zmienia się **na Aktualizuj,** gdy aktualizacje programu Visual Studio są dostępne dla wszystkich zainstalowanych składników. (Opcja **Modyfikuj** jest następnie dostępna w menu rozwijanym). Program Visual Studio i instalator można również uruchomić z menu **Start** systemu Windows, wyszukując w programie "Visual Studio".

    ![Uruchamianie, modyfikowanie, modyfikowanie lub odinstalowywanie programu Visual Studio z instalatora](media/installation-vs-launch.png)

### <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli wystąpią problemy z instalacją lub uruchomieniem języka Python w programie Visual Studio, spróbuj wykonać następujące czynności:

- Określ, czy ten sam błąd występuje przy użyciu interfejsu wiersza polecenia języka Python, czyli *uruchamiania pliku python.exe* z wiersza polecenia.
- Użyj opcji [**Napraw**](../install/repair-visual-studio.md) w instalatorze programu Visual Studio.
- Napraw lub zainstaluj ponownie pythona za pomocą **aplikacji &** > funkcji w**systemie** Windows.

**Przykładowy błąd:** Nie można uruchomić procesu interaktywnego: System.ComponentModel.Win32Exception (0x80004005): Nieznany błąd (0xc0000135) w witrynie Microsoft.PythonTools.Repl.PythonInteractiveEEvaluator.d__43.MoveNext().

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Uruchom instalator programu Visual Studio za pomocą **Panelu sterowania > programów i funkcji**, wybierając pozycję Microsoft Visual Studio **2015,** a następnie **zmień**.

1. W instalatorze wybierz pozycję **Modyfikuj**.

1. Wybierz **języki** > programowania**Narzędzia Python dla programu Visual Studio,** a następnie **dalej:**

    ![Opcja PTVS w instalatorze programu Visual Studio 2015](media/installation-vs2015.png)

1. Po zakończeniu instalacji programu Visual Studio [zainstaluj wybraną interpreter języka Python.](installing-python-interpreters.md) Visual Studio 2015 obsługuje tylko Python 3.5 i wcześniej; nowsze wersje generują komunikat, taki jak **nieobsługicony Python w wersji 3.6**). Jeśli masz już zainstalowany interpreter, a program Visual Studio nie wykrywa go automatycznie, zobacz [Ręczne identyfikowanie istniejącego środowiska](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 i starsze

1. Zainstaluj odpowiednią wersję programu Python Tools for Visual Studio dla swojej wersji programu Visual Studio:

    - Visual Studio 2013: [PTVS 2.2.2 dla programu Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2.2). Okno dialogowe **Plik** > **nowego projektu** w programie Visual Studio 2013 zawiera skrót do tego procesu.
    - Visual Studio 2010 i 2012: [PTVS 2.1.1 dla programu Visual Studio 2010 i 2012](https://github.com/Microsoft/PTVS/releases/v2.1.1)

1. [Zainstaluj wybranego interpretatora Języka Python.](installing-python-interpreters.md) Jeśli masz już zainstalowany interpreter, a program Visual Studio nie wykrywa go automatycznie, zobacz [Ręczne identyfikowanie istniejącego środowiska](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="install-locations"></a>Lokalizacje instalacji

Domyślnie obsługa języka Python jest instalowana dla wszystkich użytkowników na komputerze.

W programach Visual Studio 2019 i Visual Studio 2017 obciążenie języka Python jest instalowane w *programie %ProgramFiles(x86)%\Microsoft Visual\\ Studio<VS_version>\\><VS_edition>Common7\IDE\Extensions\Microsoft\Python,* gdzie&gt; &lt;VS_version&gt; to 2019 lub 2017, a &lt;VS_edition to Społeczność, Professional lub Enterprise.

W programie Visual Studio 2015 i wcześniejszych ścieżki instalacji są następujące:

- 32-bitowe:
  - Ścieżka: *%Program Files(x86)%\Microsoft \<Visual Studio VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for\\ Visual Studio<PTVS_ver>*
  - Lokalizacja rejestru ścieżki: **HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\\<VS_ver>\InstallDir**
- 64-bitowe:
  - Ścieżka: *%Program Files%\Microsoft \<Visual Studio VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for\\ Visual Studio<PTVS_ver>*
  - Lokalizacja rejestru ścieżki: **HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\\<VS_ver>\InstallDir**

gdzie:

- &lt;VS_ver&gt; jest:
  - 14.0 dla programu Visual Studio 2015
  - 12.0 dla programu Visual Studio 2013
  - 11.0 dla programu Visual Studio 2012
  - 10.0 dla programu Visual Studio 2010
- &lt;PTVS_ver&gt; jest numerem wersji, takim jak 2.2.2, 2.1.1, 2.0, 1.5, 1.1 lub 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Instalacje specyficzne dla użytkownika (1.5 i starsze)

Narzędzia Języka Python dla programu Visual Studio 1.5 i wcześniej dozwolone instalacji tylko dla bieżącego użytkownika, w którym to przypadku ścieżka instalacji jest *\\ %LocalAppData%\Microsoft\VisualStudio<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\\<PTVS_ver>* gdzie &lt;VS_ver&gt; i &lt;PTVS_ver&gt; są takie same, jak opisano powyżej.
