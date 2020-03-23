---
title: Korzystanie z szablonów CookieCutter w języku Python
description: Visual Studio obsługuje graficzne rozszerzenie Cookiecutter do odnajdywać szablony dla kodu języka Python i tworzyć projekty z tych szablonów.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62832196"
---
# <a name="use-the-cookiecutter-extension"></a>Użyj rozszerzenia Cookiecutter

[Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) udostępnia graficzny interfejs użytkownika do odnajdowania szablonów, opcji szablonów wejściowych oraz tworzenia projektów i plików. Jest dołączony do programu Visual Studio 2017 i nowszych i może być zainstalowany oddzielnie we wcześniejszych wersjach programu Visual Studio.

Cookiecutter wymaga języka Python 3.3 lub nowszego (32-bitowy lub 64-bitowy) lub Anaconda 3 4.2 lub nowszym (32-bitowy lub 64-bitowy). Jeśli odpowiedni interpreter języka Python nie jest dostępny, program Visual Studio wyświetla ostrzeżenie. Jeśli zainstalujesz interpreter języka Python, gdy program Visual Studio jest uruchomiony, kliknij przycisk **Narzędzia domowe** na pasku narzędzi Cookiecutter, aby wykryć nowo zainstalowany interpreter. (Zobacz [środowiska Języka Python,](managing-python-environments-in-visual-studio.md) aby uzyskać więcej informacji na temat środowisk w ogóle.)

Po zainstalowaniu wybierz **pozycję Wyświetl** > **Eksploratora cookiecutter,** aby otworzyć jego okno:

![Okno główne cookiecutter](media/cookiecutter-overview.png)

## <a name="cookiecutter-workflow"></a>Przepływ pracy cookiecutter

Praca z Cookiecutter to proces przeglądania i wybierania szablonu, klonowania go na komputerze lokalnym, ustawiania opcji, a następnie tworzenia kodu z tego szablonu, zgodnie z opisem w kolejnych sekcjach.

### <a name="browse-templates"></a>Przeglądaj szablony

Na stronie głównej Cookiecutter wyświetlana jest lista szablonów do wyboru, zorganizowanych w następujące grupy:

| Grupa | Opis |
| --- | --- |
| **Zainstalowane** | Szablony zainstalowane na komputerze lokalnym. Gdy używany jest szablon online, jego repozytorium jest automatycznie klonowane do podfolderu *~/.cookiecutters*. Wybrany zainstalowany szablon można usunąć, naciskając klawisz **Delete**. |
| **Zalecane** | Szablony załadowane z zalecanego pliku danych. Domyślny kanał informacyjny jest nadzorowany przez firmę Microsoft. Zobacz [opcje Cookiecutter](#cookiecutter-options) poniżej, aby uzyskać szczegółowe informacje na temat dostosowywania pliku danych. |
| **GitHub** | Wyniki wyszukiwania GitHub dla słowa kluczowego cookiecutter. Wyniki z GitHub wrócić na strony, jeśli więcej wyników są dostępne, **Load More** pojawia się na końcu listy. |
| **Niestandardowy** | Po wprowadzeniu lokalizacji niestandardowej w polu wyszukiwania jest wyświetlana w tej grupie. Można wpisać pełną ścieżkę do repozytorium GitHub lub pełną ścieżkę do folderu na dysku lokalnym. |

### <a name="cloning"></a>Klonowanie

Po wybraniu szablonu, po którym następuje **następny,** Cookiecutter tworzy lokalną kopię do pracy.

Jeśli wybierzesz szablon z grup **Zalecane lub** **GitHub** lub wprowadzisz niestandardowy adres URL w polu wyszukiwania i wybierzesz ten szablon, zostanie on sklonowany i zainstalowany na komputerze lokalnym. Jeśli ten szablon został zainstalowany w poprzedniej sesji programu Visual Studio, jest automatycznie usuwany, a najnowsza wersja jest klonowana.

Jeśli wybierzesz szablon z grupy **Zainstalowane** lub wprowadzisz ścieżkę folderu niestandardowego w polu wyszukiwania i wybierzesz ten szablon, program Visual Studio ładuje ten szablon bez klonowania.

> [!Important]
> Szablony cookiecutter są klonowane w jednym folderze *~/.cookiecutters*. Każdy podfolder jest nazwany po nazwie repozytorium git, która nie zawiera nazwy użytkownika GitHub. Konflikty mogą wystąpić, jeśli sklonujesz różne szablony o tej samej nazwie, które pochodzą od różnych autorów. W takim przypadku cookiecutter uniemożliwia zastąpienie istniejącego szablonu innym szablonem o tej samej nazwie. Aby zainstalować drugi szablon, należy najpierw usunąć istniejący.

### <a name="set-template-options"></a>Ustawianie opcji szablonu

Po zainstalowaniu szablonu lokalnie, Cookiecutter wyświetla stronę opcji, gdzie można określić, gdzie chcesz Cookiecutter do generowania plików wraz z innymi opcjami:

![Strona opcji cookiecutter](media/cookiecutter-template-options.png)

Każdy szablon Cookiecutter definiuje własny zestaw opcji i określa wartość domyślną dla każdego z nich (wyświetlaną jako sugerowany tekst w każdym polu wpisu). Wartość domyślna może być fragment kodu, często, gdy jest to wartość dynamiczna, która używa innych opcji.

Można dostosować wartości domyślne dla określonych opcji za pomocą pliku konfiguracji użytkownika. Gdy rozszerzenie Cookiecutter wykryje plik konfiguracji użytkownika, zastępuje domyślne wartości szablonu wartościami domyślnymi konfiguracyjność użytkownika. To zachowanie zostało omówione w sekcji [Konfiguracja użytkownika](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html) w dokumentacji cookiecutter.

Jeśli szablon określa określone zadania programu Visual Studio do uruchomienia po generowaniu kodu, pojawi się dodatkowa opcja **Uruchom dodatkowe zadania po zakończeniu,** która umożliwia rezygnację z tych zadań. Najczęstszym zastosowaniem zadań jest otwieranie przeglądarki sieci Web, otwieranie plików w edytorze, instalowanie zależności itd.

### <a name="create"></a>Utwórz

Po ustawieniu opcji wybierz pozycję **Utwórz,** aby wygenerować kod (ostrzeżenie jest wyświetlane, jeśli folder wyjściowy nie jest pusty). Jeśli znasz dane wyjściowe szablonu i nie masz nic przeciwko nadpisywaniem plików, możesz odrzucić ostrzeżenie. W przeciwnym razie wybierz pozycję **Anuluj**, określ pusty folder, a następnie ręcznie skopiuj utworzone pliki do niepustego folderu wyjściowego.

Po pomyślnym utworzeniu plików, Cookiecutter udostępnia opcję otwierania plików w **Eksploratorze rozwiązań:**

![Cookiecutter z poleceniem Eksploratora rozwiązań](media/cookiecutter-files-created.png)

## <a name="cookiecutter-options"></a>Opcje cookiecutter

Opcje Cookiecutter są dostępne za pośrednictwem opcji **Tools** > **Options** > **Cookiecutter:**

![Opcje cookiecutter](media/cookiecutter-tools-options.png)

| Opcja | Opis |
| --- | --- |
| **Zalecany adres URL kanału informacyjnego** | Lokalizacja zalecanego pliku danych szablonów. Może to być adres URL lub ścieżka do pliku lokalnego. Pozostaw pusty adres URL, aby użyć domyślnego wyselekcjonowanego źródła danych firmy Microsoft. Plik danych zawiera prostą listę lokalizacji szablonów, oddzielonych nowymi liniami. Aby zażądać zmian w wyselekcjonowanym kanale, należy złożyć żądanie ściągnięcia względem [źródła w usłudze GitHub](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt). |
| **Pokaż Pomoc** | Służy do sterowania widocznością paska informacji pomocy w górnej części okna pliku cookiecutter. |

## <a name="optimize-cookiecutter-templates-for-visual-studio"></a>Optymalizuj szablony cookiecutter dla programu Visual Studio

Podstawy tworzenia szablonu cookiecutter można znaleźć w [dokumentacji cookiecutter](https://cookiecutter.readthedocs.io/en/latest/first_steps.html). Rozszerzenie Cookiecutter dla programu Visual Studio obsługuje szablony utworzone dla cookiecutter w wersji 1.4.

Domyślne renderowanie zmiennych szablonu zależy od typu danych (ciągu lub listy):

- Ciąg: Etykieta dla nazwy zmiennej, pole tekstowe do wprowadzania wartości i znak wodny z wartością domyślną. Etykietka narzędzia w polu tekstowym zawiera wartość domyślną.
- Lista: Etykieta dla nazwy zmiennej, pole kombi do wybierania wartości. Etykietka narzędzia w polu kombi zawiera wartość domyślną.

Jest możliwe, aby poprawić tego renderowania, określając dodatkowe metadane w pliku *cookiecutter.json,* który jest specyficzny dla programu Visual Studio (i ignorowane przez cookiecutter cli). Wszystkie właściwości są opcjonalne:

| Właściwość | Opis |
| --- | --- |
| Label | Określa, co pojawia się nad edytorem zmiennej, a nie nazwą zmiennej. |
| Opis | Określa etykietkę narzędzia wyświetlaną w formancie edycji, a nie wartość domyślną dla tej zmiennej. |
| Adres URL | Zmienia etykietę w hiperłącze z etykietą z etykietą zawierającą adres URL. Kliknięcie hiperłącza powoduje otwarcie domyślnej przeglądarki użytkownika na ten adres URL. |
| Selektor | Umożliwia dostosowanie edytora dla zmiennej. Następujące selektory są obecnie obsługiwane:<ul><li>`string`: Standardowe pole tekstowe, domyślne dla ciągów.</li><li>`list`: Standardowe pole kombi, domyślne dla list.</li><li>`yesno`: Pole kombi `y` do `n`wyboru między i , dla ciągów.</li><li>`odbcConnection`: Pole tekstowe z przyciskiem **...,** który powoduje wyświetlenie okna dialogowego połączenia z bazą danych.</li></ul> |

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

Cookiecutter ma funkcję o nazwie *Post-Generate Hooks,* która pozwala na uruchamianie dowolnego kodu Pythona po wygenerowaniu plików. Chociaż elastyczne, nie zezwala na łatwy dostęp do programu Visual Studio.

Na przykład można otworzyć plik w edytorze Programu Visual Studio lub w przeglądarce sieci web lub wyzwolić interfejs użytkownika programu Visual Studio, który monituje użytkownika o utworzenie środowiska wirtualnego i zainstalowanie wymagań dotyczących pakietu.

Aby zezwolić na te scenariusze, visual studio szuka rozszerzonych metadanych w *pliku cookiecutter.json,* który opisuje polecenia do uruchomienia po użytkownik otwiera wygenerowane pliki w **Eksploratorze rozwiązań** lub po pliki są dodawane do istniejącego projektu. (Ponownie użytkownik może zrezygnować z uruchamiania zadań, **czyszcząc uruchom dodatkowe zadania po zakończeniu** w opcjach szablonu).

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

Polecenia są określone według nazwy i należy użyć nazwy nielokalizowane (angielski) do pracy na zlokalizowanych instalacji programu Visual Studio. Nazwy poleceń programu Visual **Studio** można testować i odnajdywanie.

Jeśli chcesz przekazać pojedynczy argument, należy określić go jako ciąg, jak w poprzednim przykładzie.

Jeśli nie musisz przekazywać argumentu, pozostaw go pustym ciągiem lub pomiń go z JSON:

```json
"_visual_studio_post_cmds": [
    {
        "name": "View.WebBrowser"
    }
]
```

Użyj tablicy dla wielu argumentów. W przypadku przełączników podziel przełącznik i jego wartość na oddzielne argumenty i użyj właściwego cytowanie. Przykład:

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

Argumenty mogą odnosić się do innych zmiennych Cookiecutter. W powyższych przykładach `_output_folder_path` zmienna wewnętrzna jest używana do tworzenia ścieżki bezwzględnej do generowanych plików.

Należy zauważyć, że `Python.InstallProjectRequirements` polecenie działa tylko podczas dodawania plików do istniejącego projektu. To ograniczenie istnieje, ponieważ polecenie jest przetwarzane przez projekt Języka Python w **Eksploratorze rozwiązań**i nie ma żadnego projektu, aby otrzymać wiadomość w widoku - **folderu** **Eksploratora rozwiązań**. Mamy nadzieję usunąć ograniczenie wygrać przyszłą wersję (i zapewnić lepszą obsługę **widoku folderu** w ogóle).

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="error-loading-template"></a>Wystąpił błąd podczas ładowania szablonu

Niektóre szablony mogą używać nieprawidłowych typów danych, takich jak logiczne, w pliku *cookiecutter.json*. Zgłoś takie wystąpienia autorowi szablonu, wybierając łącze **Problemy** w okienku informacji o szablonie.

### <a name="hook-script-failed"></a>Skrypt haka nie powiódł się

Niektóre szablony mogą używać skryptów po generacji, które nie są zgodne z interfejsem cookiecutter. Na przykład skrypty, które kwerendy użytkownika do danych wejściowych nie powiedzie się z powodu braku konsoli terminala.

### <a name="hook-script-not-supported-on-windows"></a>Skrypt haka nie jest obsługiwany w systemie Windows

Jeśli skrypt post jest *.sh*, to nie może być skojarzony z aplikacją na komputerze z systemem Windows. W sklepie Windows może zostać wyświetlone okno dialogowe systemu Windows z prośbą o znalezienie zgodnej aplikacji.

### <a name="templates-with-known-issues"></a>Szablony ze znanymi problemami

Błędy klonowania:

- **wildfish/cookiecutter-django-crud** (nieprawidłowy znak `|` w nazwie podfolderu)
- **cookiecutter-pyvanguard (nieprawidłowy** znak `|` w nazwie podfolderu)

Awarie obciążenia:

- **chrisdev/wagtail-cookiecutter-foundation** (używa typu logicznego w *pliku cookiecutter.json*)
- **quintoandar/cookiecutter-android** (brak folderu szablonów)

Błędy uruchamiania:

- **iknite/cookiecutter-ansible-role** (skrypt haka postu wymaga danych wejściowych konsoli)
- **benregn/cookiecutter-django-ansible** (błąd Jinja)

Używa bash (nie śmiertelne):

- **openstack-dev/cookiecutter**
