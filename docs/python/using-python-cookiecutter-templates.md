---
title: Użyj szablonów CookieCutter za pomocą języka Python
description: Program Visual Studio obsługuje graficzny rozszerzenia Cookiecutter do odnajdowania szablonów dla kodu w języku Python i twórz projekty na podstawie tych szablonów.
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: eeea19b1d2ff4a4d24f27280a48b9ae673406908
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59366318"
---
# <a name="use-the-cookiecutter-extension"></a>Używanie rozszerzenia Cookiecutter

[Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) zapewnia graficzny interfejs użytkownika do odnalezienia szablonów, wprowadź opcje szablonu oraz tworzenie projektów i plików. On zostało uwzględnione w programie Visual Studio 2017 i nowsze i mogą być zainstalowane oddzielnie we wcześniejszych wersjach programu Visual Studio.

Cookiecutter wymaga języka Python 3.3 lub nowszej (32-bitowy lub 64-bitowy) albo Anaconda 3 4.2 i nowsze (32-bitowy lub 64-bitowych). Jeśli odpowiedni interpreter języka Python jest niedostępna, Visual Studio wyświetlane jest ostrzeżenie. Po zainstalowaniu interpreter języka Python, po uruchomieniu programu Visual Studio, kliknij przycisk **Home** na listwie narzędziowej Cookiecutter do wykrywania interpretera nowo zainstalowany. (Zobacz [środowiska Python](managing-python-environments-in-visual-studio.md) więcej informacji na temat środowisk ogólnie rzecz biorąc.)

Po zakończeniu instalacji wybierz **widoku** > **Eksplorator Cookiecutter** aby otworzyć okno:

![Okno główne Cookiecutter](media/cookiecutter-overview.png)

## <a name="cookiecutter-workflow"></a>Przepływ pracy Cookiecutter

Praca z Cookiecutter jest proces przeglądania i wybierając szablon, klonowanie go na komputerze lokalnym, ustawianie opcji, a następnie utworzenie kodu na podstawie tego szablonu, zgodnie z opisem w kolejnych sekcjach.

### <a name="browse-templates"></a>Przeglądaj szablony

Strona główna Cookiecutter Wyświetla listę szablonów do wyboru, podzielone na następujące grupy:

| Grupa | Opis |
| --- | --- |
| **Zainstalowane** | Szablony, które zostały zainstalowane na komputerze lokalnym. W przypadku szablonu usługi online jako repozytorium zostanie automatycznie sklonowany do podfolderu *~/.cookiecutters*. Usunąć wybranego szablonu zainstalowane, naciskając **Usuń**. |
| **Zalecane** | Szablony są ładowane z kanał zalecane. Domyślne źródło danych jest nadzorowane przez firmę Microsoft. Zobacz [opcje Cookiecutter](#cookiecutter-options) poniżej szczegółowe informacje na temat dostosowywania źródła danych. |
| **GitHub** | Wyniki wyszukiwania usługi GitHub — słowo kluczowe narzędzia cookiecutter. Wyniki z repozytorium GitHub możesz wrócić z podziałem na strony, jeśli będą dostępne, wyniki **obciążenia więcej** pojawia się na końcu listy. |
| **Custom** | Po wprowadzeniu niestandardową lokalizację w polu wyszukiwania, pojawi się w tej grupie. Możesz wpisz pełną ścieżkę do repozytorium GitHub lub pełną ścieżkę do folderu na dysku lokalnym. |

### <a name="cloning"></a>Klonowanie

Po wybraniu szablonu, a następnie **dalej**, Cookiecutter sprawia, że do pracy z lokalną kopię.

Jeśli wybierzesz szablon z **zalecane** lub **GitHub** grupy, lub wprowadź niestandardowy adres URL w polu wyszukiwania i wybrać ten szablon, jej sklonowany i zainstalowania na komputerze lokalnym. Jeśli ten szablon został zainstalowany w poprzedniej sesji programu Visual Studio, zostanie on automatycznie usunięty i został sklonowany najnowszej wersji.

Jeśli wybierzesz szablon z **zainstalowane** grupy, lub wprowadź ścieżkę folderu niestandardowego w polu wyszukiwania, a następnie wybierz ten szablon programu Visual Studio ładuje szablon bez klonowania.

> [!Important]
> Szablonów Cookiecutter są klonowane w jednym folderze *~/.cookiecutters*. Każdy podfolder nosi nazwę po nazwie repozytorium git, która nie obejmuje nazwę użytkownika usługi GitHub. Konflikty może wystąpić, jeśli klonowanie różne szablony o takiej samej nazwie, które pochodzą z różnych autorów. W tym przypadku Cookiecutter zapobiega zastępowaniu istniejący szablon z innego szablonu o takiej samej nazwie. Aby zainstalować innego szablonu, należy najpierw usunąć istniejącą grupę.

### <a name="set-template-options"></a>Ustaw opcje szablonu

Po lokalnym zainstalowaniu szablonu Cookiecutter wyświetla na stronie opcji, w którym można określić, której chcesz Cookiecutter do generowania plików wraz z innymi opcjami:

![Strona opcji Cookiecutter](media/cookiecutter-template-options.png)

Każdy szablon Cookiecutter definiuje swój własny zestaw opcji i określenie wartości domyślnej dla każdego z nich (wyświetlane jako Sugerowany tekst w każdym polu Zapis). Wartość domyślna może być fragment kodu, często w przypadku, gdy jest wartość dynamiczna, która korzysta z innych opcji.

Użytkownik może dostosować domyślne wartości dla określonych opcji przy użyciu pliku konfiguracyjnego użytkownika. Gdy rozszerzenia Cookiecutter wykryje plik konfiguracyjny użytkownika, zastępuje wartości domyślne szablonu przy użyciu wartości domyślnych konfiguracji użytkownika. To zachowanie jest omówiona w [konfiguracji użytkownika](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html) sekcji dokumentacji Cookiecutter.

Jeśli szablon służy do określonego zadania programu Visual Studio do uruchomienia po generowania kodu, dodatkowy **przeprowadzić dodatkowe zadania na ukończenie** opcja jest wyświetlana, która pozwala zrezygnować z tych zadań. Najczęściej używane zadania jest Otwórz przeglądarkę sieci web, otwórz pliki w edytorze, zainstaluj zależności i tak dalej.

### <a name="create"></a>Create

Po ustawieniu opcji wybierz **Utwórz** do generowania kodu (zostanie wyświetlone ostrzeżenie, jeśli folder wyjściowy nie jest pusta). Jeśli znasz z danych wyjściowych tego szablonu, a nie mieć nic przeciwko, zastępując pliki, możesz zignorować to ostrzeżenie. W przeciwnym razie wybierz **anulować**Określ pusty folder, a następnie ręcznie skopiuj utworzone pliki w folderze danych wyjściowych pusty.

Po pomyślnym utworzeniu pliki Cookiecutter udostępnia opcję otwarcia plików w **Eksploratora rozwiązań**:

![Polecenie Eksploratora rozwiązań przedstawiający Cookiecutter](media/cookiecutter-files-created.png)

## <a name="cookiecutter-options"></a>Opcje Cookiecutter

Cookiecutter opcje są dostępne za pośrednictwem **narzędzia** > **opcje** > **Cookiecutter**:

![Opcje Cookiecutter](media/cookiecutter-tools-options.png)

| Opcja | Opis |
| --- | --- |
| **Zaleca się adres URL źródła danych** | Lokalizacja szablonów zalecane źródła danych. Może być adresem URL lub ścieżkę do pliku lokalnego. Adres URL należy pozostawić puste, aby korzystać z programu Microsoft nadzorowana domyślnego źródła danych. Źródło danych udostępnia prostą listę lokalizacji szablonu, oddzielone tabulacji. Do żądania zmiany wyselekcjonowanych kanału informacyjnego, utworzyć żądanie ściągnięcia względem [źródło w witrynie GitHub](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt). |
| **Pokaż Pomoc** | Określa widoczność paska informacji pomocy w górnej części okna Cookiecutter. |

## <a name="optimize-cookiecutter-templates-for-visual-studio"></a>Optymalizowanie szablonów Cookiecutter dla programu Visual Studio

Aby uzyskać podstawowe informacje dotyczące tworzenia szablonów Cookiecutter, zobacz [dokumentacji Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/first_steps.html). Rozszerzenia Cookiecutter dla programu Visual Studio obsługuje szablony utworzone dla Cookiecutter w wersji 1.4.

Domyślne renderowanie zmiennych szablonu jest zależna od typu danych (ciągów lub listy):

- String: Etykieta nazwa zmiennej, pole tekstowe do wprowadzania wartość i znak wodny, wartością domyślną. Etykietki narzędzia w polu tekstowym jest wyświetlana wartość domyślną.
- List: Etykieta nazwa zmiennej, pole kombi na wybranie wartości. Etykietki narzędzia w polu kombi zawiera wartość domyślną.

Można wprowadzić ulepszenia tego renderowanie, określając dodatkowe metadane w swojej *cookiecutter.json* pliku, który jest specyficzne dla programu Visual Studio (i ignorowane przez Cookiecutter interfejsu wiersza polecenia). Wszystkie właściwości są opcjonalne:

| Właściwość | Opis |
| --- | --- |
| Etykieta | Określa, co pojawi się powyżej edytora dla zmiennej, a nie nazwę zmiennej. |
| Opis | Określa etykietkę narzędzia, która pojawia się na formant edycji, a nie wartość domyślna tej zmiennej. |
| Adres URL | Zmienia etykiety, hiperłącza, za pomocą etykietkę narzędzia, która zawiera adres URL. Kliknięcie hiperłącze otwiera użytkownika domyślną przeglądarkę do tego adresu URL. |
| Selektor | Umożliwia dostosowanie edytora dla zmiennej. Następujące selektory są obecnie obsługiwane:<ul><li>`string`: Standardowego pola tekstowego, domyślne dla parametrów.</li><li>`list`: Pole kombi standardowe, domyślnie dla listy.</li><li>`yesno`: Pole kombi wyboru między `y` i `n`, ciągów.</li><li>`odbcConnection`: Pole tekstowe z **...**  przycisku, który wyświetla okno dialogowe połączenia bazy danych.</li></ul> |

Przykład:

```json
{
    "site_name": "web-app",
    "python_version": ["3.5.2", "2.7.12"],
    "use_azure": "y",

    "_visual_studio": {
        "site_name": {
            "label": "Site name",
            "description": "E.g. <site-name>.azurewebsites.net (can only contain alphanumeric characters and `-`)"
        },
        "python_version": {
            "label": "Python version",
            "description": "The version of Python to run the site on"
        },
        "use_azure" : {
            "label": "Use Azure",
            "description": "Include Azure deployment files",
            "selector": "yesno",
            "url": "https://azure.microsoft.com"
        }
    }
}
```

### <a name="run-visual-studio-tasks"></a>Uruchamianie zadań w programie Visual Studio

Cookiecutter ma funkcję o nazwie *przechwytuje Post-Generate* umożliwiająca uruchamiania dowolnego kodu języka Python, po wygenerowaniu plików. Mimo że jest to elastyczny i nie zezwala na łatwy dostęp do programu Visual Studio.

Na przykład możesz otworzyć plik w edytorze programu Visual Studio lub w jego przeglądarki sieci web, wyzwalacza lub interfejsie użytkownika Visual Studio, który monituje użytkownika, aby utworzyć środowisko wirtualne i zainstalować wymagań dotyczących pakietu.

Aby zezwolić na te scenariusze, Visual Studio szuka rozszerzonych metadanych zawartych w *cookiecutter.json* opisujący polecenia do uruchomienia po użytkownik otwiera wygenerowane pliki w **Eksploratora rozwiązań** lub po pliki są dodawane do istniejącego projektu. (Ponownie, użytkownik może zrezygnować z uruchomionych zadań, usuwając zaznaczenie **przeprowadzić dodatkowe zadania na ukończenie** w opcjach szablonu.)

Przykład:

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": "{{cookiecutter._output_folder_path}}\\readme.txt"
    },
    {
        "name": "Cookiecutter.ExternalWebBrowser",
        "args": "https://docs.microsoft.com"
    },
    {
        "name": "Python.InstallProjectRequirements",
        "args": "{{cookiecutter._output_folder_path}}\\dev-requirements.txt"
    }
]
```

Polecenia są określone przez nazwę i powinny używać nazwy (angielski) niezlokalizowana pracować nad zlokalizowane instalacji programu Visual Studio. Można testować i Odkryj nazwy poleceń w programie Visual Studio **polecenia** okna.

Jeśli chcesz przekazać jeden argument, określ ją jako ciąg znaków takich jak w poprzednim przykładzie.

Jeśli nie potrzebujesz przekazać argument, pozostaw to pole ciągiem pustym lub pominąć go w formacie JSON:

```json
"_visual_studio_post_cmds": [
    {
        "name": "View.WebBrowser"
    }
]
```

Skorzystaj z tablicy dla wielu argumentów. Dla przełączników Podziel przełącznika i jego wartość na oddzielne argumenty i Użyj prawidłowego cytowanie. Na przykład:

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": [
            "{{cookiecutter._output_folder_path}}\\read me.txt",
            "/e:",
            "Source Code (text) Editor"
        ]
    }
]
```

Argumenty mogą odwoływać się do innych zmiennych Cookiecutter. W przykładzie powyżej, wewnętrzny `_output_folder_path` zmienna jest używana w celu utworzenia ścieżkę bezwzględną do wygenerowanych plików.

Należy pamiętać, że `Python.InstallProjectRequirements` polecenia działa tylko wtedy, gdy dodawanie plików do istniejącego projektu. To ograniczenie istnieje, ponieważ polecenie jest przetwarzany przez projekt języka Python w **Eksploratora rozwiązań**, i nie ma żadnego projektu do odbierania komunikatów podczas w **Eksploratora rozwiązań**  -   **Widok folderu**. Mamy nadzieję, że można usunąć ograniczenia win w przyszłym wydaniu (i zapewniają lepsze **widok folderu** ogólnie rzecz biorąc obsługuje).

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="error-loading-template"></a>Błąd podczas ładowania szablonu

Niektóre szablony mogą być używane typy nieprawidłowe dane, takie jak atrybut typu wartość logiczna, w ich *cookiecutter.json*. Raport takich przypadkach autorowi szablon, wybierając **problemów** łącze w okienku informacji szablonu.

### <a name="hook-script-failed"></a>Utworzenie punktu zaczepienia skryptu nie powiodło się

Niektóre szablony może używać skryptów po generacji, które nie są zgodne z interfejsem użytkownika Cookiecutter. Na przykład skrypty zapytanie użytkownika o wprowadzenie danych nie powiedzie się, ponieważ nie mieli konsolę terminala.

### <a name="hook-script-not-supported-on-windows"></a>Utworzenie punktu zaczepienia skrypt nie jest obsługiwana na Windows

Jeśli skrypt post jest *SH*, a następnie nie może być skojarzony z aplikacją na komputerze Windows. Mogą pojawić się okno dialogowe Windows pytaniem, aby znaleźć zgodnych aplikacji w Sklepie Windows.

### <a name="templates-with-known-issues"></a>Szablony ze znanymi problemami

Błędy klonowania:

- **wildfish/cookiecutter — Obsługa platformy django — crud** (nieprawidłowy znak `|` nazwę podfolderu)
- **narzędzia cookiecutter pyvanguard** (nieprawidłowy znak `|` nazwę podfolderu)

Błędy ładowania:

- **chrisdev/wagtail-cookiecutter-foundation** (korzysta z typu boolean w *cookiecutter.json*)
- **quintoandar/cookiecutter — system android** (żaden folder szablonu)

Uruchom błędy:

- **iknite/cookiecutter — rozwiązania ansible roli** (wpis punktu zaczepienia skrypt wymaga wprowadzenia danych przez konsoli)
- **benregn/cookiecutter — Obsługa platformy django — ansible** (Jinja błąd)

Zastosowań powłoki bash (nie krytyczne):

- **openstack-dev/cookiecutter**
