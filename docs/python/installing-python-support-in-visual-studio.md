---
title: Instalowanie obsługi języka Python
description: Jak zainstalować narzędzia Python Tools for Visual Studio (PTVS) w programie Visual Studio 2017, 2015, 2013, 2012 i 2010, łącznie z opcjami i lokalizacje instalacji.
ms.date: 12/06/2018
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
ms.openlocfilehash: e306bffe8f2cd59332f367822cd90b54b44b7635
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063758"
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>Jak zainstalować obsługę języka Python w programie Visual Studio na Windows

Aby zainstalować obsługę języka Python dla programu Visual Studio (znany także jako narzędzi Python Tools for Visual Studio lub PTVS), postępuj zgodnie z instrukcjami w sekcji, który odpowiada używanej wersji programu Visual Studio:

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 lub starszej](#visual-studio-2013-and-earlier)

Aby szybko przetestować, obsługa w języku Python po wykonaniu kroków instalacji, należy otworzyć **Python Interactive** okna, naciskając klawisz **Alt**+**I** i wprowadzając `2+2`. Jeśli nie widzisz dane wyjściowe `4`, sprawdź ponownie etapami.

> [!Tip]
> Obciążenie języka Python zawiera pomocnego rozszerzenia Cookiecutter, która zapewnia graficzny interfejs użytkownika do odnalezienia szablonów, wprowadź opcje szablonu oraz tworzenie projektów i plików. Aby uzyskać więcej informacji, zobacz [Cookiecutter użyj](using-python-cookiecutter-templates.md).

> [!Note]
> Obsługa w języku Python nie jest obecnie dostępna w programie Visual Studio dla komputerów Mac, ale jest dostępna na komputerach Mac i Linux za pomocą programu Visual Studio Code. Zobacz [pytań i odpowiedzi](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. Pobrać i uruchomić najnowszą wersję Instalatora programu Visual Studio 2017. Jeśli masz już zainstalowany program Visual Studio, uruchom Instalatora programu Visual Studio, wybierz opcję **Modyfikuj** opcji (zobacz [modyfikowanie programu Visual Studio](../install/modify-visual-studio.md)) i przejdź do kroku 2.

    > [!div class="nextstepaction"]
    > [Zainstaluj program Visual Studio Community 2017 r.](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Wersja Community to dla indywidualnych deweloperów, edukacyjne, badań akademickich i programowania typu open source. Do innych celów, należy zainstalować [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) lub [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted).

1. Instalator przedstawia listy obciążeń, powiązane opcje obszary rozwoju określonych grup. Dla języka Python, wybierz **programowania w języku Python** obciążenia.

    ![Obciążenie programowania języka Python w Instalatorze programu Visual Studio](media/installation-python-workload.png)

    Opcjonalnie: Jeśli pracujesz z analizy danych, należy również rozważyć **aplikacji analitycznych i naukowych opracowań danych** obciążenia. To obciążenie obejmuje obsługę języka Python, a także języka R i F# języków. Aby uzyskać więcej informacji, zobacz [obciążenie dla aplikacji analitycznych i naukowych opracowań danych](../rtvs/data-science-and-analytical-applications-workload.md).

    > [!Note]
    > Obciążenia języka Python i nauki o danych są dostępne tylko w przypadku programu Visual Studio 2017 wersja 15.2 i nowszych wersjach.

1. Po prawej stronie Instalatora wybierz dodatkowe opcje, w razie potrzeby. Pomiń ten krok, aby zaakceptować wartości domyślne.

    ![Możliwości programowania języka Python w Instalatorze programu Visual Studio](media/installation-python-options.png)

    | Opcja | Opis |
    | --- | --- |
    | Dystrybucje języka Python | Wybierz dowolną kombinację wariantów 32-bitowych i 64-bitowe języka Python 2, 3 języka Python, anaconda2, wersja i Anaconda3 dystrybucji, które zamierzasz pracować. Każde zawiera obsługę dystrybucji interpreter środowiska uruchomieniowego i bibliotek. Anaconda, to w szczególności platforma analizy otwartej obsługi danych, która zawiera szereg wstępnie zainstalowane pakiety. (Można zwrócić do Instalatora programu Visual Studio w dowolnym momencie, aby dodać lub usunąć dystrybucje.)  **Uwaga**: po zainstalowaniu dystrybucji poza Instalatora programu Visual Studio, czy nie ma potrzeby Sprawdź tutaj opcji równoważne. Program Visual Studio automatycznie wykrywa istniejącej instalacji środowiska Python. Zobacz [okna środowiska Python](managing-python-environments-in-visual-studio.md#the-python-environments-window). Ponadto jeśli nowszą wersję języka Python jest dostępny od przedstawionego w oknie Instalatora tej wersji można zainstalować oddzielnie i Visual Studio wykryje go. |
    | **Obsługa szablonów Cookiecutter** | Instaluje Cookiecutter graficznego interfejsu użytkownika, aby odnaleźć szablonów, wprowadź opcje szablonu i tworzenie projektów i plików. Zobacz [używanie rozszerzenia Cookiecutter](using-python-cookiecutter-templates.md). |
    | **Obsługa sieci web w języku Python** | Instaluje narzędzia do tworzenia aplikacji internetowych, w tym HTML, CSS i JavaScript, edycję, wraz z szablonów dla projektów przy użyciu platformy Bottle, Flask i Django. Zobacz [internetowa szablony projektów w języku Python](python-web-application-project-templates.md). |
    | **Obsługa IoT w języku Python** | Obsługuje rozwój systemu Windows IoT Core przy użyciu języka Python. |
    | **Narzędzia do programowania natywnego języka Python** | Instaluje kompilator języka C++ i innych niezbędnych składników, aby tworzyć natywne rozszerzenia języka Python. Zobacz [Tworzenie rozszerzenia C++ dla języka Python](working-with-c-cpp-python-in-visual-studio.md). Zainstaluj również **programowanie aplikacji klasycznych w języku C++** obciążenia pełną obsługę języka C++. |
    | **Podstawowe narzędzia usługi Azure Cloud Services** | Zapewnia dodatkową obsługę dla deweloperów usług Azure Cloud Services w języku Python. Zobacz [projektów usług w chmurze Azure](python-azure-cloud-service-project-template.md). |

1. Po zakończeniu instalacji Instalator oferuje opcje, aby zmodyfikować, uruchamianie, napraw lub odinstaluj program Visual Studio. **Modyfikuj** przycisku zmienia się na **aktualizacji** po aktualizacji do programu Visual Studio są dostępne dla żadnych zainstalowanych składników. ( **Modyfikuj** opcja jest dostępna w menu rozwijanym.) Można również uruchomić program Visual Studio i Instalator Windows **Start** menu, wyszukując "Visual Studio".

    ![Uruchamianie, modyfikowanie, modyfikowania lub odinstalowywania programu Visual Studio z poziomu Instalatora](media/installation-vs-launch.png)

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "Obejrzyj klip wideo") | [Obejrzyj film wideo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Installing-Visual-Studio-Python-Support-go1id3LWE_1705918567) na temat instalowania obsługi języka Python w programie Visual Studio.|

### <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli napotkasz problemy, instalowanie i uruchamianie języka Python w programie Visual Studio, spróbuj wykonać następujące czynności:

- Określić, czy ten sam błąd występuje przy użyciu interfejsu wiersza polecenia języka Python, to znaczy, działająca *python.exe* z poziomu wiersza polecenia.
- Użyj [ **naprawy** ](../install/repair-visual-studio.md) opcji w Instalatorze programu Visual Studio.
- Naprawić lub zainstalować ponownie języka Python za pomocą **ustawienia** > **aplikacje i funkcje** w Windows.

**Przykład błędu**: nie można uruchomić procesu interaktywnego: System.ComponentModel.Win32Exception (0x80004005): nieznany błąd (0xc0000135) Microsoft.PythonTools.Repl.PythonInteractiveEvaluator.d__43.MoveNext().

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Uruchamianie Instalatora programu Visual Studio za pośrednictwem **Panel sterowania > programy i funkcje**, wybierając opcję **Microsoft Visual Studio 2015** i następnie **zmiany**.

1. W oknie Instalatora wybierz **Modyfikuj**.

1. Wybierz **języki programowania** > **narzędzi Python Tools for Visual Studio** i następnie **dalej**:

    ![Opcja PTVS w Instalatorze programu Visual Studio 2015](media/installation-vs2015.png)

1. Po zakończeniu instalacji programu Visual Studio, [interpreter języka Python wybranym](installing-python-interpreters.md). Program Visual Studio 2015 obsługuje tylko język Python 3.5 i starszych; nowsze wersje generować komunikat podobny do **nieobsługiwanego języka Python w wersji 3.6**). Jeśli masz już zainstalowany interpretera i programu Visual Studio nie wykrywały go automatycznie, zobacz [ręcznie Zidentyfikuj istniejące środowisko](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 lub starszej

1. Dla używanej wersji programu Visual Studio, należy zainstalować odpowiednią wersję narzędzia języka Python dla programu Visual Studio:

    - Visual Studio 2013: [PTVS 2.2 for Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2). **Pliku** > **nowy projekt** okna dialogowego w programie Visual Studio 2013 zapewnia skrótu dla tego procesu.
    - Program Visual Studio 2012: [PTVS 2.1 dla programu Visual Studio 2012](https://pytools.codeplex.com/downloads/get/920478)
    - Program Visual Studio 2010: [PTVS 2.1 dla programu Visual Studio 2010](https://pytools.codeplex.com/downloads/get/920479)

1. [Instalowanie interpretera języka Python w wybranym](installing-python-interpreters.md). Jeśli masz już zainstalowany interpretera i programu Visual Studio nie wykrywały go automatycznie, zobacz [ręcznie Zidentyfikuj istniejące środowisko](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="install-locations"></a>Lokalizacje instalacji

Domyślnie obsługa w języku Python jest zainstalowany dla wszystkich użytkowników na komputerze.

Dla programu Visual Studio 2017, obciążenie języka Python jest zainstalowany w *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\\< VS_edition > Common7\IDE\Extensions\Microsoft\Python* gdzie &lt;VS_edition &gt; jest Community, Professional lub Enterprise.

Dla programu Visual Studio 2015 i starszych ścieżek instalacji są następujące:

- 32-bitowe:
  - Ścieżka: *% Program pliki (x86) %\Microsoft Visual Studio \<VS_ver > \Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\\< PTVS_ver >*
  - Lokalizacja rejestru ścieżki: **HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\\\InstallDir < VS_ver >**
- 64-bitowe:
  - Ścieżka: *% Program Files%\Microsoft Visual Studio \<VS_ver > \Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\\< PTVS_ver >*
  - Lokalizacja rejestru ścieżki: **HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\\\InstallDir < VS_ver >**

gdzie:

- &lt;VS_ver&gt; jest:
  - 14.0 dla programu Visual Studio 2015
  - 12.0 for Visual Studio 2013
  - 11.0 dla programu Visual Studio 2012
  - 10.0 dla programu Visual Studio 2010
- &lt;PTVS_ver&gt; jest numer wersji, takich jak 2.2, 2.1, 2.0, 1.5, 1.1 i 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Instalacje specyficzne dla użytkownika (1,5 raza więcej i starszych)

Narzędzia Python Tools for Visual Studio w wersji 1.5 i starszych dozwolone instalacji dla bieżącego użytkownika, w którym to przypadku ścieżka instalacji jest *%LocalAppData%\Microsoft\VisualStudio\\narzędzia \Extensions\Microsoft\Python < VS_ver > dla programu Visual Studio\\< PTVS_ver >* gdzie &lt;VS_ver&gt; i &lt;PTVS_ver&gt; są takie same, jak opisano powyżej.

