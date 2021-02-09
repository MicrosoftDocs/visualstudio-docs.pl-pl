---
title: Korzystanie z szablonów CookieCutter w języku Python
description: Program Visual Studio obsługuje rozszerzenie Cookiecutter graficzne w celu odnajdywania szablonów dla kodu języka Python i tworzenia projektów na podstawie tych szablonów.
ms.date: 01/28/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 08ae2e13f094535eae0447cc3b8d4acf4c806a99
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920617"
---
# <a name="use-the-cookiecutter-extension"></a>Użyj rozszerzenia Cookiecutter

[Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) udostępnia graficzny interfejs użytkownika umożliwiający odnajdywanie szablonów, opcji szablonów wejściowych i tworzenie projektów i plików. Jest on dołączony do programu Visual Studio 2017 lub nowszego i można go zainstalować oddzielnie we wcześniejszych wersjach programu Visual Studio.

Cookiecutter wymaga języka Python 3,3 lub nowszego (32-bit lub 64-bitowy) lub Anaconda 3 4,2 lub nowszego (32-bit lub 64-bit). Jeśli odpowiedni interpreter języka Python nie jest dostępny, program Visual Studio wyświetli ostrzeżenie. Jeśli instalujesz interpreter języka Python, a program Visual Studio jest uruchomiony, wybierz przycisk **Strona główna** na pasku narzędzi Cookiecutter, aby wykryć nowo zainstalowany interpreter. (Zobacz [środowiska Python](managing-python-environments-in-visual-studio.md) , aby uzyskać więcej informacji na temat ogólnych środowisk).

Po zainstalowaniu wybierz pozycję **Wyświetl**  >  **Cookiecutter Explorer** , aby otworzyć jej okno:

![Okno główne Cookiecutter](media/cookiecutter-overview.png)

## <a name="cookiecutter-workflow"></a>Przepływ pracy Cookiecutter

Praca z programem Cookiecutter to proces przeglądania i wybierania szablonu, klonowania go na komputerze lokalnym, ustawiania opcji, a następnie tworzenia kodu z tego szablonu zgodnie z opisem w poniższych sekcjach.

### <a name="browse-templates"></a>Przeglądaj szablony

Na stronie głównej Cookiecutter zostanie wyświetlona lista szablonów do wyboru, zorganizowanych w następujące grupy:

| Grupa | Opis |
| --- | --- |
| **Zainstalowane** | Szablony, które zostały zainstalowane na komputerze lokalnym. Gdy szablon online jest używany, jego repozytorium jest automatycznie klonowane do podfolderu *~/.cookiecutters*. Wybrany zainstalowany szablon można usunąć, naciskając klawisz **delete**. |
| **Zalecane** | Szablony załadowane z zalecanego źródła danych. Domyślne źródło danych jest nadzorowane przez firmę Microsoft. Aby uzyskać szczegółowe informacje na temat dostosowywania źródła danych, zobacz poniższe [Opcje Cookiecutter](#cookiecutter-options) . |
| **GitHub** | Wyniki wyszukiwania usługi GitHub dla słowa kluczowego cookiecutter. Wyniki z serwisu GitHub są podzielone na strony, jeśli są dostępne więcej wyników, **obciążenie** nie pojawia się na końcu listy. |
| **Niestandardowe** | Po wprowadzeniu niestandardowej lokalizacji w polu wyszukiwania pojawia się ona w tej grupie. Możesz wpisać pełną ścieżkę do repozytorium GitHub lub pełną ścieżkę do folderu na dysku lokalnym. |

### <a name="cloning"></a>Klonowanie

Po wybraniu szablonu, po którym następuje wartość **Next**, Cookiecutter tworzy kopię lokalną do działania.

Jeśli wybierzesz szablon z grupy **zalecane** lub **GitHub** lub wprowadzisz niestandardowy adres URL w polu wyszukiwania i wybierzesz ten szablon, zostanie on sklonowany i zainstalowany na komputerze lokalnym. Jeśli ten szablon został zainstalowany w poprzedniej sesji programu Visual Studio, zostanie automatycznie usunięty i zostanie sklonowana Najnowsza wersja.

Jeśli wybierzesz szablon z **zainstalowanej** grupy lub wprowadzisz w polu wyszukiwania niestandardową ścieżkę do folderu, a następnie wybierzesz ten szablon, program Visual Studio ładuje ten szablon bez klonowania.

> [!Important]
> Szablony Cookiecutter są klonowane w ramach jednego folderu *~/.cookiecutters*. Każdy podfolder ma nazwę po nazwie repozytorium git, która nie zawiera nazwy użytkownika usługi GitHub. Konflikty mogą wystąpić w przypadku klonowania różnych szablonów o tej samej nazwie, które pochodzą od różnych autorów. W takim przypadku Cookiecutter uniemożliwia zastąpienie istniejącego szablonu innym szablonem o tej samej nazwie. Aby zainstalować inny szablon, należy najpierw usunąć istniejący.

### <a name="set-template-options"></a>Ustawianie opcji szablonu

Gdy szablon zostanie zainstalowany lokalnie, Cookiecutter wyświetla stronę opcji, na której można określić, gdzie chcesz Cookiecutter generować pliki wraz z innymi opcjami:

![Strona opcji Cookiecutter](media/cookiecutter-template-options.png)

Każdy szablon Cookiecutter definiuje własny zestaw opcji i określa wartość domyślną dla każdej z nich (wyświetlaną jako sugerowany tekst w każdym polu wpisu). Wartość domyślna może być fragmentem kodu, często gdy jest to wartość dynamiczna korzystająca z innych opcji.

Istnieje możliwość dostosowania wartości domyślnych dla konkretnych opcji za pomocą pliku konfiguracji użytkownika. Gdy rozszerzenie Cookiecutter wykrywa plik konfiguracji użytkownika, zastępuje domyślne wartości szablonu wartościami domyślnymi konfiguracji użytkownika. To zachowanie jest omówione w sekcji [Konfiguracja użytkownika](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html) w dokumentacji Cookiecutter.

Jeśli szablon określa konkretne zadania programu Visual Studio do uruchomienia po generowaniu kodu, zostanie wyświetlona dodatkowa opcja **Uruchom dodatkowe zadania przy zakończeniu** , która umożliwia rezygnację z tych zadań. Najczęstszym sposobem korzystania z zadań jest otwarcie przeglądarki sieci Web, otwarcie plików w edytorze, zainstalowanie zależności i tak dalej.

### <a name="create"></a>Utwórz

Po ustawieniu opcji wybierz pozycję **Utwórz** , aby wygenerować kod (ostrzeżenie jest wyświetlane, jeśli folder wyjściowy nie jest pusty). Jeśli znasz dane wyjściowe szablonu i nie zastąpisz plików, możesz odrzucić ostrzeżenie. W przeciwnym razie wybierz pozycję **Anuluj**, określ pusty folder, a następnie ręcznie Skopiuj utworzone pliki do niepustego folderu wyjściowego.

Po pomyślnym utworzeniu plików Cookiecutter udostępnia opcję otwierania plików w **Eksplorator rozwiązań**:

![Cookiecutter pokazujący polecenie Eksplorator rozwiązań](media/cookiecutter-files-created.png)

## <a name="cookiecutter-options"></a>Opcje Cookiecutter

Opcje Cookiecutter są dostępne za poorednictwem  >  **opcji** narzędzia  >  **Cookiecutter**:

![Opcje Cookiecutter](media/cookiecutter-tools-options.png)

| Opcja | Opis |
| --- | --- |
| **Adres URL zalecanego kanału informacyjnego** | Lokalizacja kanałów informacyjnych zalecanych szablonów. Może to być adres URL lub ścieżka do pliku lokalnego. Pozostaw pusty adres URL, aby użyć domyślnego źródła danych nadzorowanych firmy Microsoft. Kanał informacyjny zapewnia prostą listę lokalizacji szablonów, rozdzielonych znakami nowego wiersza. Aby zażądać zmian w źródle danych nadzorowanych, Utwórz żądanie ściągnięcia względem [źródła w serwisie GitHub](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt). |
| **Wyświetlanie pomocy** | Kontroluje widoczność paska informacji pomocy w górnej części okna Cookiecutter. |

## <a name="optimize-cookiecutter-templates-for-visual-studio"></a>Optymalizowanie szablonów Cookiecutter dla programu Visual Studio

Podstawowe informacje na temat tworzenia szablonu Cookiecutter można znaleźć w [dokumentacji Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/first_steps.html). Rozszerzenie Cookiecutter dla programu Visual Studio obsługuje szablony utworzone dla Cookiecutter v 1.4.

Domyślne renderowanie zmiennych szablonu zależy od typu danych (ciąg lub lista):

- Ciąg: etykieta dla nazwy zmiennej, pola tekstowego służącego do wprowadzania wartości i znaku wodnego pokazującego wartość domyślną. Etykietka narzędzia w polu tekstowym zawiera wartość domyślną.
- List: etykieta dla nazwy zmiennej, pola kombi do wybierania wartości. Etykietka narzędzia w polu kombi pokazuje wartość domyślną.

To renderowanie można ulepszyć, określając dodatkowe metadane w *cookiecutter.js* pliku, który jest specyficzny dla programu Visual Studio (i ignorowany przez interfejs wiersza polecenia Cookiecutter). Wszystkie właściwości są opcjonalne:

| Właściwość | Opis |
| --- | --- |
| Etykieta | Określa, co pojawia się powyżej edytora dla zmiennej, zamiast nazwy zmiennej. |
| Opis | Określa etykietkę narzędzia, która pojawia się w kontrolce Edycja zamiast wartości domyślnej dla tej zmiennej. |
| Adres URL | Zmienia etykietę w hiperłącze przy użyciu etykietki narzędzia, która zawiera adres URL. Wybranie hiperłącza spowoduje otwarcie domyślnej przeglądarki użytkownika dla tego adresu URL. |
| Selektor | Umożliwia dostosowanie edytora dla zmiennej. Następujące selektory są obecnie obsługiwane:<ul><li>`string`: Standardowe pole tekstowe, domyślne dla ciągów.</li><li>`list`: Standardowe pole kombi, domyślnie dla list.</li><li>`yesno`: Pole kombi do wyboru między `y` i `n` , dla ciągów.</li><li>`odbcConnection`: Pole tekstowe z przyciskiem **...** , które powoduje wyświetlenie okna dialogowego połączenia bazy danych.</li></ul> |

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

### <a name="run-visual-studio-tasks"></a>Uruchamianie zadań programu Visual Studio

Cookiecutter ma funkcję o nazwie *Hook-Generating* , która umożliwia uruchamianie dowolnego kodu w języku Python po wygenerowaniu plików. Chociaż elastyczny, nie pozwala na łatwy dostęp do programu Visual Studio.

Na przykład możesz chcieć otworzyć plik w edytorze programu Visual Studio lub w przeglądarce sieci Web lub wyzwolić interfejs użytkownika programu Visual Studio, który będzie monitował użytkownika o utworzenie środowiska wirtualnego i Instalowanie wymagań pakietu.

Aby zezwolić na te scenariusze, program Visual Studio szuka rozszerzonych metadanych w *cookiecutter.jsna temat* opisujące polecenia do uruchomienia, gdy użytkownik otworzy wygenerowane pliki w **Eksplorator rozwiązań** lub po dodaniu plików do istniejącego projektu. (W tym celu użytkownik może zrezygnować z uruchamiania zadań, czyszcząc **polecenie Uruchom dodatkowe zadania po zakończeniu** w obszarze Opcje szablonu).

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

Polecenia są określone przez nazwę i powinny używać nazwy niezlokalizowanej (angielskiej) do pracy z zlokalizowanymi instalacjami programu Visual Studio. Nazwy poleceń można testować i odnajdywać w oknie **poleceń** programu Visual Studio.

Jeśli chcesz przekazać pojedynczy argument, określ go jako ciąg podobny do powyższego przykładu.

Jeśli nie musisz przekazać argumentu, pozostaw pusty ciąg lub Pomiń go w kodzie JSON:

```json
"_visual_studio_post_cmds": [
    {
        "name": "View.WebBrowser"
    }
]
```

Użyj tablicy dla wielu argumentów. W przypadku przełączników należy podzielić przełącznik i jego wartość na oddzielne argumenty i użyć odpowiednich cudzysłowów. Na przykład:

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

Argumenty mogą odwoływać się do innych zmiennych Cookiecutter. W powyższych przykładach `_output_folder_path` zmienna wewnętrzna służy do tworzenia ścieżki bezwzględnej do wygenerowanych plików.

Należy zauważyć, że `Python.InstallProjectRequirements` polecenie działa tylko w przypadku dodawania plików do istniejącego projektu. To ograniczenie istnieje, ponieważ polecenie jest przetwarzane przez projekt w języku Python w **Eksplorator rozwiązań** i nie ma projektu do odebrania komunikatu w widoku **Eksplorator rozwiązań**  -  **folderu**. Mamy nadzieję, że firma Microsoft czeka na usunięcie tego ograniczenia w przyszłości. 

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="error-loading-template"></a>Wystąpił błąd podczas ładowania szablonu

Niektóre szablony mogą używać nieprawidłowych typów danych, takich jak wartość logiczna, w *cookiecutter.js*. Zgłoś takie wystąpienia do autora szablonu, wybierając link **problemy** w okienku informacje o szablonie.

### <a name="hook-script-failed"></a>Niepowodzenie skryptu haka

Niektóre szablony mogą używać skryptów po generacji, które nie są zgodne z interfejsem użytkownika Cookiecutter. Na przykład skrypty, które wysyłają zapytania do użytkownika w celu niepowodzenia, z powodu braku konsoli terminalowej.

### <a name="hook-script-not-supported-on-windows"></a>Skrypt punktu zaczepienia nie jest obsługiwany w systemie Windows

Jeśli skrypt post to *. sh*, może nie być skojarzony z aplikacją na komputerze z systemem Windows. Może zostać wyświetlone okno dialogowe systemu Windows z prośbą o znalezienie zgodnej aplikacji w Sklepie Windows.

### <a name="templates-with-known-issues"></a>Szablony ze znanymi problemami

Błędy klonowania:

- **wildfish/cookiecutter-Django-CRUD** (nieprawidłowy znak `|` w nazwie podfolderu)
- **cookiecutter-pyvanguard** (nieprawidłowy znak `|` w nazwie podfolderu)

Błędy ładowania:

- **chrisdev/Wagtail-cookiecutter-Foundation** (używa typu boolean w *cookiecutter.json*)
- **quintoandar/cookiecutter — Android** (brak folderu szablonów)

Błędy przebiegu:

- **iknite/cookiecutter-rozwiązania ansible — rola** (skrypt po Hook wymaga wprowadzenia danych przez konsolę)
- **benregn/cookiecutter-Django-rozwiązania ansible** (błąd jinja)

Używa bash (niekrytyczne):

- **OpenStack — dev/cookiecutter**
