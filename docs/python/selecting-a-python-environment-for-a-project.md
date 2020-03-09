---
title: Wybierz interpreter języka Python i środowiska dla projektu
description: Musisz wybrać środowisko Python, w tym Anaconda i środowisk wirtualnych, aby zastosować do określonego projektu.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 34ceb2ec7cc923f6642977cf4c70fbfae07bf523
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409623"
---
# <a name="how-to-select-a-python-environment-for-a-project"></a>Jak wybrać środowisko Python dla projektu

Cały kod w projekcie języka Python jest uruchamiany w kontekście określonego środowiska, takie jak globalnego środowisko Python, środowisko Anaconda, środowisko wirtualne lub środowiska conda. Visual Studio używa także środowisko do debugowania, importowania i zakończenia elementu członkowskiego, sprawdzanie składni i innych zadań, które wymagają usług językowych, które są specyficzne dla środowiska Python w wersji i zestaw zainstalowanych pakietów.

Wszystkie nowe projekty w języku Python w programie Visual Studio są początkowo skonfigurowane do używania domyślnego środowiska globalnego, które jest wyświetlane w węźle **środowiska Python** w **Eksplorator rozwiązań**:

![Środowiska Python domyślnie globalne wyświetlane w Eksploratorze rozwiązań](media/environments/environments-project.png)

::: moniker range="vs-2017"
Aby zmienić środowisko dla projektu, kliknij prawym przyciskiem myszy węzeł **środowiska Python** i wybierz polecenie **Dodaj/Usuń środowiska Python**. Z wyświetlonej listy, która zawiera globalne, wirtualne i Conda środowiska, zaznacz wszystkie te, które mają być wyświetlane w węźle **środowiska języka Python** :

![Okno dialogowe Dodawanie/usuwanie środowiska Python](media/environments/environments-add-remove.png)

Po wybraniu **przycisku OK**wszystkie wybrane środowiska będą widoczne w węźle **środowiska języka Python** . Obecnie aktywowanego środowiska zostanie wyświetlony pogrubioną czcionką:

![Wiele środowisk języka Python, wyświetlane w Eksploratorze rozwiązań](media/environments/environments-project-multiple.png)

Aby szybko aktywować inne środowisko, kliknij prawym przyciskiem myszy nazwę tego środowiska i wybierz polecenie **Aktywuj środowisko**. Wybór zostaje zapisana wraz z projektu i środowiska jest aktywowany przy każdym otwarciu projektu w przyszłości. W przypadku wyczyszczenia wszystkich opcji w oknie dialogowym **Dodawanie/usuwanie środowisk Python** program Visual Studio aktywuje globalne środowisko domyślne.

Menu kontekstowe w węźle **środowiska Python** zawiera również dodatkowe polecenia:

| Polecenie | Opis |
| --- | --- |
| **Dodawanie środowiska wirtualnego** | Rozpocznie się proces tworzenia nowego środowiska wirtualnego w projekcie. Zobacz [Tworzenie środowiska wirtualnego](#create-a-virtual-environment). |
| **Dodaj istniejące środowisko wirtualne** | Wyświetla komunikat z prośbą o wybranie folderu zawierającego środowisko wirtualne i dodanie go do listy w obszarze **środowiska Python**, ale nie aktywuje go. Zobacz [Aktywowanie istniejącego środowiska wirtualnego](#activate-an-existing-virtual-environment). |
| **Utwórz środowisko Conda** | Przełącza do okna **środowiska Python** , w którym należy wprowadzić nazwę środowiska i określić jego interpreter podstawowy. Zobacz [środowiska Conda](managing-python-environments-in-visual-studio.md#conda-environments). |
::: moniker-end

::: moniker range=">=vs-2019"
Aby zmienić środowisko dla projektu, kliknij prawym przyciskiem myszy węzeł **środowiska Python** i wybierz polecenie **Dodaj środowisko**lub wybierz pozycję **Dodaj środowisko** z listy rozwijanej środowisko na pasku narzędzi języka Python.

W oknie dialogowym **Dodawanie środowiska** wybierz kartę **istniejące środowisko** , a następnie wybierz nowe środowisko z listy rozwijanej **środowisko** :

![Wybieranie środowiska projektu w oknie dialogowym Dodaj środowiska](media/environments/environments-project-2019.png)

Jeśli do projektu zostało już dodane środowisko inne niż globalne, może być konieczne aktywowanie nowo dodanego środowiska. Kliknij prawym przyciskiem myszy środowisko w węźle **środowiska Python** i wybierz polecenie **Aktywuj środowisko**. Aby usunąć środowisko z projektu, wybierz pozycję **Usuń**.

![Aktywowanie i usuwanie środowiska projektu](media/environments/environments-project-add-remove-2019.png)
::: moniker-end

## <a name="use-virtual-environments"></a>Korzystanie ze środowisk wirtualnych

Środowisko wirtualne ma unikatową kombinację określonych interpreter języka Python i określony zbiór bibliotek, który różni się od innych środowisk globalnych i conda. Środowisko wirtualne jest specyficzne dla projektu i są przechowywane w folderze projektu. Ten folder zawiera zainstalowane biblioteki środowiska wraz z plikiem *pyvenv. cfg* , który określa ścieżkę do *interpretera podstawowego* środowiska w innym miejscu w systemie plików. (Oznacza to, że środowisko wirtualne nie zawiera kopię interpretera tylko łącza do niego).

Korzyścią z używania środowiska wirtualnego jest, że podczas tworzenia projektu wraz z upływem czasu, środowisko wirtualne zawsze odzwierciedla dokładnie zależności projektu. (Udostępnione środowisko globalne, z drugiej strony, zawiera dowolną liczbę bibliotek, niezależnie od tego, czy są one używane w projekcie, czy nie). Następnie można łatwo utworzyć plik *Requirements. txt* w środowisku wirtualnym, który jest następnie używany do ponownej instalacji tych zależności na innym komputerze deweloperskim lub produkcyjnym. Aby uzyskać więcej informacji, zobacz [Zarządzanie wymaganymi pakietami przy użyciu wymagań. txt](managing-required-packages-with-requirements-txt.md).

Po otwarciu projektu w programie Visual Studio, który zawiera plik *Requirements. txt* , program Visual Studio automatycznie udostępnia opcję ponownego tworzenia środowiska wirtualnego. Na komputerach, na których nie zainstalowano programu Visual Studio, można przywrócić pakiety przy użyciu `pip install -r requirements.txt`.

Ponieważ środowisko wirtualne zawiera zakodowaną ścieżkę do interpretera podstawowego, a ponieważ można odtworzyć środowisko przy użyciu programu *Requirements. txt*, zazwyczaj pominięto cały folder środowiska wirtualnego z kontroli źródła.

W poniższych sekcjach opisano, jak aktywować istniejącego środowiska wirtualnego w projekcie oraz sposób tworzenia nowego środowiska wirtualnego.

W programie Visual Studio środowisko wirtualne można aktywować dla projektu, podobnie jak w przypadku węzła **środowiska Python** w **Eksplorator rozwiązań**.

Po dodaniu środowiska wirtualnego do projektu pojawia się ono w oknie środowiska języka **Python** . Następnie można aktywować go jak dowolnego innego środowiska i możesz zarządzać jego pakietów.

::: moniker range="vs-2017"
### <a name="create-a-virtual-environment"></a>Tworzenie środowiska wirtualnego

Nowe środowisko wirtualne można utworzyć bezpośrednio w programie Visual Studio w następujący sposób:

1. Kliknij prawym przyciskiem myszy środowisko **Python** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj środowisko wirtualne**, które powoduje wyświetlenie następującego okna dialogowego:

    ![Tworzenie środowiska wirtualnego](media/environments/environments-add-virtual-1.png)

1. W polu **Lokalizacja środowiska wirtualnego** określ ścieżkę dla środowiska wirtualnego. Jeśli określisz tylko nazwę, środowisko wirtualne jest tworzony w ramach bieżącego projektu w podfolderze o tej nazwie.

1. Wybierz środowisko jako interpreter podstawowy i wybierz pozycję **Utwórz**. Visual Studio Wyświetla pasek postępu, gdy go skonfiguruje środowiska i pobierze wszystkie niezbędne pakiety. Po zakończeniu środowisko wirtualne jest wyświetlane w oknie **środowiska języka Python** dla projektu zawierającego.

1. Środowisko wirtualne nie została aktywowana domyślnie. Aby aktywować go dla projektu, kliknij go prawym przyciskiem myszy i wybierz polecenie **Aktywuj środowisko**.

> [!Note]
> Jeśli ścieżka lokalizacji identyfikuje istniejące środowisko wirtualne, program Visual Studio automatycznie wykryje interpreter podstawowy (przy użyciu pliku *ORIG-prefix. txt* w katalogu *lib* środowiska) i zmieni przycisk **Utwórz** , aby **dodać**.
>
> Jeśli plik *Requirements. txt* istnieje podczas dodawania środowiska wirtualnego, w oknie dialogowym **Dodawanie środowiska wirtualnego** zostanie wyświetlona opcja automatycznej instalacji pakietów, co ułatwia ponowne utworzenie środowiska na innym komputerze:
>
> ![Tworzenie środowiska wirtualnego z pliku requirements.txt](media/environments/environments-requirements-txt.png)
>
> W obu przypadkach wynik jest taki sam jak w przypadku użycia polecenia **Dodaj istniejące środowisko wirtualne** .

### <a name="activate-an-existing-virtual-environment"></a>Aktywuj istniejącego środowiska wirtualnego

Jeśli już utworzono wirtualnego środowiska w innym miejscu, możesz to zrobić dla projektu w następujący sposób:

1. Kliknij prawym przyciskiem myszy **środowisko Python** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj istniejące środowisko wirtualne**.

1. W wyświetlonym oknie dialogowym **przeglądania** przejdź do folderu zawierającego środowisko wirtualne i wybierz go, a następnie wybierz **przycisk OK**. Jeśli program Visual Studio wykryje plik *Requirements. txt* w tym środowisku, zostanie wyświetlony monit z pytaniem, czy zainstalować te pakiety.

1. Po kilku chwilach środowisko wirtualne jest wyświetlane w węźle **środowiska Python** w **Eksplorator rozwiązań**. Środowisko wirtualne nie jest domyślnie aktywowane, więc kliknij je prawym przyciskiem myszy i wybierz polecenie **Aktywuj środowisko**.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="create-a-virtual-environment"></a>Tworzenie środowiska wirtualnego

Nowe środowisko wirtualne można utworzyć bezpośrednio w programie Visual Studio w następujący sposób:

1. Kliknij prawym przyciskiem myszy **środowisko Python** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj środowisko**lub wybierz pozycję **Dodaj środowisko** z listy rozwijanej środowiska na pasku narzędzi języka Python. W wyświetlonym oknie dialogowym **Dodawanie środowiska** wybierz kartę **środowisko wirtualne** :

    ![Karta środowisko wirtualne okna dialogowego Dodawanie środowiska](media/environments/environments-add-virtual-1-2019.png)

1. Określ nazwę środowiska wirtualnego, wybierz interpreter podstawowy i sprawdź jego lokalizację. W obszarze **Instaluj pakiety z pliku**podaj ścieżkę do pliku *Requirements. txt* w razie potrzeby.

1. Zapoznaj się z innymi opcjami w oknie dialogowym:

    | Opcja | Opis |
    | --- | --- |
    | Ustaw jako bieżące środowisko | Aktywuje nowe środowisko w wybranym projekcie po utworzeniu środowiska. |
    | Ustaw jako domyślne środowisko dla nowych projektów | Automatycznie ustawia i aktywuje środowisko wirtualne w nowych projektach utworzonych w programie Visual Studio. W przypadku korzystania z tej opcji środowisko wirtualne należy umieścić w lokalizacji poza określonym projektem.  |
    | Wyświetl w oknie środowiska języka Python | Określa, czy okno **środowiska języka Python** ma być otwierane po utworzeniu środowiska. |
    | Udostępnij to środowisko globalnie | Określa, czy środowisko wirtualne działa również jako środowisko globalne. W przypadku korzystania z tej opcji środowisko wirtualne należy umieścić w lokalizacji poza określonym projektem. |

1. Wybierz pozycję **Utwórz** , aby zakończyć środowisko wirtualne. Visual Studio Wyświetla pasek postępu, gdy go skonfiguruje środowiska i pobierze wszystkie niezbędne pakiety. Po zakończeniu środowisko wirtualne jest uaktywniane i pojawia się w węźle **środowiska Python** w **Eksplorator rozwiązań** oraz w oknie **środowiska Python** dla projektu zawierającego.

### <a name="activate-an-existing-virtual-environment"></a>Aktywuj istniejącego środowiska wirtualnego

Jeśli już utworzono wirtualnego środowiska w innym miejscu, możesz to zrobić dla projektu w następujący sposób:

1. Kliknij prawym przyciskiem myszy **środowisko Python** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj środowisko**.

1. W wyświetlonym oknie dialogowym **przeglądania** przejdź do folderu zawierającego środowisko wirtualne i wybierz go, a następnie wybierz **przycisk OK**. Jeśli program Visual Studio wykryje plik *Requirements. txt* w tym środowisku, zostanie wyświetlony monit z pytaniem, czy zainstalować te pakiety.

1. Po kilku chwilach środowisko wirtualne jest wyświetlane w węźle **środowiska Python** w **Eksplorator rozwiązań**. Środowisko wirtualne nie jest domyślnie aktywowane, więc kliknij je prawym przyciskiem myszy i wybierz polecenie **Aktywuj środowisko**.
::: moniker-end

### <a name="remove-a-virtual-environment"></a>Usuwanie środowiska wirtualnego

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy środowisko wirtualne i wybierz polecenie **Usuń**.

1. Program Visual Studio zapyta, czy usuwanie środowiska wirtualnego. Wybranie pozycji **Usuń** sprawia, że jest ona niedostępna dla projektu, ale pozostawia ją w systemie plików. Wybranie opcji **Usuń** powoduje usunięcie środowiska z projektu i usunięcie go z systemu plików. Podstawowy interpreter pozostaje bez zmian.

## <a name="view-installed-packages"></a>Wyświetl zainstalowane pakiety

W Eksploratorze rozwiązań rozwiń węzeł w danym środowisku, aby szybko wyświetlić pakiety, które są zainstalowane w tym środowisku (tzn. można importować i użyć tych pakietów w kodzie, gdy środowisko jest aktywny):

![Pakiety języka Python dla środowiska w Eksploratorze rozwiązań](media/environments/environments-installed-packages.png)

::: moniker range="vs-2017"
Aby zainstalować nowe pakiety, kliknij prawym przyciskiem myszy środowisko i wybierz polecenie **Zainstaluj pakiet języka Python** , aby przełączyć się na kartę odpowiednie **pakiety** w oknie **środowiska języka Python** . Wprowadź wyszukiwania termin (zazwyczaj nazwa pakietu) i Visual Studio Wyświetla zgodnych pakietów.
::: moniker-end
::: moniker range=">=vs-2019"
Aby zainstalować nowe pakiety, kliknij prawym przyciskiem myszy środowisko i wybierz polecenie **Zarządzaj pakietami języka Python** (lub użyj przycisku pakiet na pasku narzędzi Python), aby przełączyć się na kartę odpowiednie **pakiety** w oknie **środowiska języka Python** . Na karcie **pakiety** wprowadź wyszukiwany termin (zazwyczaj nazwę pakietu), a program Visual Studio Wyświetla pasujące pakiety.
::: moniker-end

W programie Visual Studio pakiety (i zależności) dla większości środowisk są pobierane z [indeksu pakietów języka Python (PyPI)](https://pypi.org), gdzie można również wyszukiwać dostępne pakiety. Pasek stanu programu Visual Studio i okno dane wyjściowe zawierają informacje o instalacji. Aby odinstalować pakiet, kliknij go prawym przyciskiem myszy i wybierz polecenie **Usuń**.

Menedżer pakietów Conda ogólnie używa `https://repo.continuum.io/pkgs/` jako domyślnego kanału, ale dostępne są inne kanały. Aby uzyskać więcej informacji, zobacz [Manage Channels](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-channels.html) (docs.Conda.IO).

Należy pamiętać, że wyświetlane wpisy nie zawsze są dokładne i instalowania i odinstalowywania może nie być niezawodne lub są dostępne. Program Visual Studio korzysta z Menedżera pakietów pip, jeśli to możliwe i pobiera i instaluje je, gdy jest to wymagane. Program Visual Studio umożliwia również easy_install Menedżera pakietów. Wyświetlane są również pakiety zainstalowane przy użyciu `pip` lub `easy_install` z wiersza polecenia.

Należy również zauważyć, że program Visual Studio nie obsługuje obecnie korzystania z `conda`, aby zainstalować pakiety w środowisku Conda. Zamiast tego użyj `conda` z wiersza polecenia.

> [!Tip]
> Typowa sytuacja, w której nie można zainstalować pakietu przez program PIP, ma miejsce, gdy pakiet zawiera kod źródłowy dla składników natywnych w plikach *\*. PYD* . Bez wymaganą wersję zainstalowanego programu Visual Studio narzędzia pip, nie można skompilować tych składników. Komunikat o błędzie wyświetlany w tej sytuacji jest **następujący: nie można odnaleźć vcvarsall. bat**. `easy_install` często pobiera wstępnie skompilowane pliki binarne i można pobrać odpowiedni kompilator dla starszych wersji języka Python z [https://www.microsoft.com/download/details.aspx?id=44266](https://www.microsoft.com/download/details.aspx?id=44266). Aby uzyskać więcej informacji, zobacz [temat jak radzić sobie z "znalezieniem vcvarsallbat"](https://devblogs.microsoft.com/python/unable-to-find-vcvarsall-bat/) w blogu zespołu narzędzi Python.

## <a name="see-also"></a>Zobacz też

- [Zarządzanie środowiskami języka Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Użyj programu Requirements. txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Dokumentacja okna środowiska Python](python-environments-window-tab-reference.md)
