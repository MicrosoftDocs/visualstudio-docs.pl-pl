---
title: Zainstaluj obsługę języka Python
description: Jak zainstalować Python Tools for Visual Studio (PTVS) w programie Visual Studio 2017, 2015, 2013, 2012 i 2010, w tym opcje i lokalizacje instalacji.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e0c1cf29c7579978d5992de46b14c01fee0799c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881649"
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>Jak zainstalować obsługę języka Python w programie Visual Studio w systemie Windows

Aby zainstalować obsługę języka Python dla programu Visual Studio (znanego również jako Python Tools for Visual Studio lub PTVS), postępuj zgodnie z instrukcjami w sekcji, które pasują do używanej wersji programu Visual Studio:

- [Visual Studio 2017 i Visual Studio 2019](#visual-studio-2017-and-2019)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 i starsze](#visual-studio-2013-and-earlier)

Aby szybko przetestować obsługę języka Python po wykonaniu kroków instalacji, Otwórz okno **interaktywne języka Python** , naciskając klawisz **Alt** + **i** i wprowadzając polecenie `2+2` . Jeśli nie widzisz danych wyjściowych `4` , sprawdź ponownie kroki.

> [!Tip]
> Obciążenie języka Python obejmuje pomocne rozszerzenie Cookiecutter, które zapewnia graficzny interfejs użytkownika do odnajdowania szablonów, opcji szablonu wejściowego i tworzenia projektów i plików. Aby uzyskać szczegółowe informacje, zobacz [use Cookiecutter](using-python-cookiecutter-templates.md).

> [!Note]
> Obsługa języka Python nie jest obecnie dostępna w Visual Studio dla komputerów Mac, ale jest dostępna na komputerach Mac i w systemie Linux przez Visual Studio Code. Zapoznaj się [z pytaniami i odpowiedziami](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="visual-studio-2017-and-2019"></a>
## <a name="visual-studio-2019-and-visual-studio-2017"></a>Visual Studio 2019 i Visual Studio 2017

1. Pobierz i uruchom najnowszy Instalator programu Visual Studio. Jeśli masz już zainstalowany program Visual Studio, uruchom Instalator programu Visual Studio, wybierz opcję **Modify** (zobacz [Modyfikacja programu Visual Studio](../install/modify-visual-studio.md)) i przejdź do kroku 2.

    > [!div class="nextstepaction"]
    > [Zainstaluj społeczność programu Visual Studio 2019](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Wersja Community jest przeznaczony dla indywidualnych deweloperów, uczenia klasowego, badań akademickich i opracowywania rozwiązań open source. Aby uzyskać inne zastosowania, zainstaluj [program Visual studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) lub [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted).

1. Instalator przedstawia listę obciążeń, które są grupami powiązanych opcji dla określonych obszarów deweloperskich. Dla języka Python wybierz obciążenie **programowanie** w języku Python.

    ![Obciążenie programowanie w języku Python w Instalatorze programu Visual Studio](media/installation-python-workload.png)

    ::: moniker range="vs-2017"
    Opcjonalnie: Jeśli pracujesz z analizą danych, weź również pod uwagę obciążenie **aplikacji analizy i przetwarzania danych** . To obciążenie obejmuje obsługę języków Python, R i F #. Aby uzyskać więcej informacji, zobacz obciążenie dotyczące analizy [danych i aplikacji analitycznych](data-science-and-analytical-applications-workload.md).

    > [!Note]
    > Obciążenia Python i analizy danych są dostępne tylko w programie Visual Studio 2017 w wersji 15,2 lub nowszej.

    ::: moniker-end

    ::: moniker range=">=vs-2019"
    Opcjonalnie: Jeśli pracujesz z analizą danych, weź również pod uwagę obciążenie **aplikacji analizy i przetwarzania danych** . To obciążenie obejmuje obsługę języków Python i F #. Aby uzyskać więcej informacji, zobacz obciążenie dotyczące analizy [danych i aplikacji analitycznych](data-science-and-analytical-applications-workload.md).
    ::: moniker-end

1. Po prawej stronie Instalatora wybierz dodatkowe opcje w razie potrzeby. Pomiń ten krok, aby zaakceptować opcje domyślne.

    ::: moniker range="vs-2017"
    ![Opcje programowania w języku Python w Instalatorze programu Visual Studio](media/installation-python-options.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    ![Opcje programowania w języku Python w Instalatorze programu Visual Studio 2019](media/installation-python-options-2019.png)
    ::: moniker-end

    ::: moniker range="<=vs-2017"
    | Opcja | Opis |
    | --- | --- |
    | Dystrybucje języka Python | Wybierz dowolną kombinację dostępnych opcji, takich jak 32-bitowe i 64-bitowe, dla których planujesz współpracować, z których korzystasz. Każdy z nich zawiera interpreter, środowisko uruchomieniowe i biblioteki dystrybucji. Anaconda, w odróżnieniu od tego, czy jest to otwarta platforma do nauki o danych, która obejmuje szeroką gamę wstępnie zainstalowanych pakietów. (W dowolnym momencie możesz powrócić do Instalatora programu Visual Studio, aby dodać lub usunąć dystrybucje).  **Uwaga**: Jeśli zainstalowano dystrybucję poza instalatorem programu Visual Studio, nie ma potrzeby zaznaczania opcji równoważnej w tym miejscu. Program Visual Studio automatycznie wykrywa istniejące instalacje języka Python. Zobacz [okno środowiska języka Python](managing-python-environments-in-visual-studio.md#the-python-environments-window). Ponadto, jeśli jest dostępna nowsza wersja języka Python niż wyświetlana w instalatorze, można zainstalować tę wersję oddzielnie, a program Visual Studio wykryje ją. |
    | **Obsługa szablonów Cookiecutter** | Instaluje graficzny interfejs użytkownika Cookiecutter w celu odnajdywania szablonów, opcji szablonu danych wejściowych i tworzenia projektów i plików. Zobacz [Korzystanie z rozszerzenia Cookiecutter](using-python-cookiecutter-templates.md). |
    | **Obsługa sieci Web w języku Python** | Instaluje narzędzia do programowania w sieci Web, w tym obsługę edycji HTML, CSS i JavaScript, wraz z szablonami dla projektów korzystających z butelek, kolb i platform Django. Zobacz [Szablony projektów sieci Web](python-web-application-project-templates.md)w języku Python. |
    | **Obsługa IoT w języku Python** | Obsługuje programowanie podstawowe w systemie Windows IoT przy użyciu języka Python. |
    | **Natywne narzędzia programistyczne języka Python** | Instaluje kompilator C++ i inne niezbędne składniki do tworzenia natywnych rozszerzeń języka Python. Zobacz [Tworzenie rozszerzenia C++ dla języka Python](working-with-c-cpp-python-in-visual-studio.md). Zainstaluj także **Programowanie aplikacji klasycznych w języku c++** , aby zapewnić pełną obsługę języka c++. |
    | **Podstawowe narzędzia Cloud Services platformy Azure** | Zapewnia dodatkową pomoc techniczną dla deweloperów platformy Azure Cloud Services w języku Python. Zobacz [projekty usługi w chmurze platformy Azure](python-azure-cloud-service-project-template.md). |
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    | Opcja | Opis |
    | --- | --- |
    | Dystrybucje języka Python | Wybierz dowolną kombinację dostępnych opcji, takich jak 32-bitowe i 64-bitowe, dla których planujesz współpracować, z których korzystasz. Każdy z nich zawiera interpreter, środowisko uruchomieniowe i biblioteki dystrybucji. Anaconda, w odróżnieniu od tego, czy jest to otwarta platforma do nauki o danych, która obejmuje szeroką gamę wstępnie zainstalowanych pakietów. (W dowolnym momencie możesz powrócić do Instalatora programu Visual Studio, aby dodać lub usunąć dystrybucje).  **Uwaga**: Jeśli zainstalowano dystrybucję poza instalatorem programu Visual Studio, nie ma potrzeby zaznaczania opcji równoważnej w tym miejscu. Program Visual Studio automatycznie wykrywa istniejące instalacje języka Python. Zobacz [okno środowiska języka Python](managing-python-environments-in-visual-studio.md#the-python-environments-window). Ponadto, jeśli jest dostępna nowsza wersja języka Python niż wyświetlana w instalatorze, można zainstalować tę wersję oddzielnie, a program Visual Studio wykryje ją. |
    | **Obsługa szablonów Cookiecutter** | Instaluje graficzny interfejs użytkownika Cookiecutter w celu odnajdywania szablonów, opcji szablonu danych wejściowych i tworzenia projektów i plików. Zobacz [Korzystanie z rozszerzenia Cookiecutter](using-python-cookiecutter-templates.md). |
    | **Obsługa sieci Web w języku Python** | Instaluje narzędzia do programowania w sieci Web, w tym obsługę edycji HTML, CSS i JavaScript, wraz z szablonami dla projektów korzystających z butelek, kolb i platform Django. Zobacz [Szablony projektów sieci Web](python-web-application-project-templates.md)w języku Python. |
    | **Natywne narzędzia programistyczne języka Python** | Instaluje kompilator C++ i inne niezbędne składniki do tworzenia natywnych rozszerzeń języka Python. Zobacz [Tworzenie rozszerzenia C++ dla języka Python](working-with-c-cpp-python-in-visual-studio.md). Zainstaluj także **Programowanie aplikacji klasycznych w języku c++** , aby zapewnić pełną obsługę języka c++. |
    | **Podstawowe narzędzia Cloud Services platformy Azure** | Zapewnia dodatkową pomoc techniczną dla deweloperów platformy Azure Cloud Services w języku Python. Zobacz [projekty usługi w chmurze platformy Azure](python-azure-cloud-service-project-template.md). |
    ::: moniker-end

1. Po instalacji Instalator udostępnia opcje umożliwiające modyfikację, uruchomienie, naprawę lub odinstalowanie programu Visual Studio. Przycisk **Modyfikuj** zmienia **się, gdy aktualizacje programu** Visual Studio są dostępne dla zainstalowanych składników programu. (Opcja **Modyfikuj** jest następnie dostępna w menu rozwijanym). Możesz również uruchomić program Visual Studio i Instalatora z menu **Start** systemu Windows, wyszukując "Visual Studio".

    ![Uruchamianie, modyfikowanie, modyfikowanie lub odinstalowywanie programu Visual Studio z Instalatora](media/installation-vs-launch.png)

### <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli wystąpią problemy z instalowaniem lub uruchamianiem języka Python w programie Visual Studio, spróbuj wykonać następujące czynności:

- Ustal, czy ten sam błąd występuje przy użyciu interfejsu wiersza polecenia języka Python, czyli uruchomionego *python.exe* z wiersza poleceń.
- Użyj opcji [**napraw**](../install/repair-visual-studio.md) w Instalatorze programu Visual Studio.
- Napraw lub ponownie zainstaluj środowisko Python za poorednictwem **ustawień**  >  **aplikacje & funkcje** w systemie Windows.

**Przykładowy błąd**: nie można uruchomić procesu interaktywnego: System. ComponentModel. Win32Exception (0x80004005): nieznany błąd (0xc0000135) w Microsoft.PythonTools.REPL.PythonInteractiveEvaluator.d__43. MoveNext ().

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Uruchom Instalatora programu Visual Studio za pomocą **Panelu sterowania > programy i funkcje**, wybierając pozycję **Microsoft Visual Studio 2015** , a następnie pozycję **Zmień**.

1. W instalatorze wybierz pozycję **Modyfikuj**.

1. Wybierz **Języki programowania**  >  **Python Tools for Visual Studio** a następnie kliknij przycisk **dalej**:

    ![Opcja PTVS w Instalatorze programu Visual Studio 2015](media/installation-vs2015.png)

1. Po zakończeniu instalacji programu Visual Studio [Zainstaluj wybrany interpreter języka Python](installing-python-interpreters.md). Program Visual Studio 2015 obsługuje tylko środowisko Python 3,5 i starsze. późniejsze wersje generują komunikat, taki jak **nieobsługiwana wersja języka Python 3,6**). Jeśli masz już zainstalowany interpreter, a program Visual Studio nie wykryje go automatycznie, zobacz [Ręczne identyfikowanie istniejącego środowiska](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 i starsze

1. Zainstaluj odpowiednią wersję Python Tools for Visual Studio dla używanej wersji programu Visual Studio:

    - Visual Studio 2013: [PTVS 2.2.2 dla Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2.2). Okno dialogowe **plik**  >  **nowego projektu** w Visual Studio 2013 zawiera skrót do tego procesu.
    - Visual Studio 2010 i 2012: [PTVS 2.1.1 for Visual studio 2010 i 2012](https://github.com/Microsoft/PTVS/releases/v2.1.1)

1. [Zainstaluj wybrany interpreter języka Python](installing-python-interpreters.md). Jeśli masz już zainstalowany interpreter, a program Visual Studio nie wykryje go automatycznie, zobacz [Ręczne identyfikowanie istniejącego środowiska](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="install-locations"></a>Lokalizacje instalacji

Domyślnie obsługa języka Python jest instalowana dla wszystkich użytkowników na komputerze.

W przypadku programu Visual Studio 2019 i Visual Studio 2017 obciążenie języka Python jest instalowane w lokalizacji *% ProgramFiles (x86)% \ Microsoft Visual Studio \\<VS_version>\\<* VS_edition>Common7\IDE\Extensions\Microsoft\Python &lt; , gdzie VS_version &gt; 2019 lub 2017, a &lt; VS_edition &gt; to Community, Professional lub Enterprise.

W przypadku programu Visual Studio 2015 i jego wcześniejszych wersji ścieżki instalacji są następujące:

- 32-bitowa:
  - Ścieżka: *% Program Files (x86)% \ Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio \\<PTVS_ver>*
  - Lokalizacja rejestru ścieżki: **HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\\<VS_ver> \installdir**
- 64-bitowa:
  - Ścieżka: *% Program Files%\Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\Python Tools for visual studio \\<PTVS_ver>*
  - Lokalizacja rejestru ścieżki: **HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\\<VS_ver> \installdir**

gdzie:

- &lt;VS_ver &gt; :
  - 14,0 dla programu Visual Studio 2015
  - 12,0 dla Visual Studio 2013
  - 11,0 dla programu Visual Studio 2012
  - 10,0 dla programu Visual Studio 2010
- &lt;PTVS_ver &gt; to numer wersji, taki jak 2.2.2, 2.1.1, 2,0, 1,5, 1,1 lub 1,0.

### <a name="user-specific-installations-15-and-earlier"></a>Instalacje specyficzne dla użytkownika (1,5 i starsze)

Python Tools for Visual Studio 1,5 i wcześniejsza dozwolona instalacja dla bieżącego użytkownika. w takim przypadku ścieżka instalacji to *%LocalAppData%\Microsoft\VisualStudio \\<VS_ver> narzędzia \extensions\microsoft\python Tools for Visual Studio \\<PTVS_ver>* , gdzie &lt; VS_ver &gt; i &lt; PTVS_ver &gt; są takie same, jak opisano powyżej.
