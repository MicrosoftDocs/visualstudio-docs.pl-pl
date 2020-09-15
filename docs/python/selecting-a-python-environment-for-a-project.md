---
title: Wybierz środowisko Python dla projektu
description: W szczególności można wybrać środowisko Python, w tym Anaconda i środowiska wirtualne, aby zastosować je do określonego projektu.
ms.date: 03/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 46b0a8005ea76445a1d6205c8635963dbaedd0d4
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2020
ms.locfileid: "90097037"
---
# <a name="how-to-select-a-python-environment-for-a-project"></a>Jak wybrać środowisko Python dla projektu

Cały kod w projekcie w języku Python działa w kontekście określonego środowiska, takiego jak globalne środowisko Python, środowisko Anaconda, środowisko wirtualne lub środowisko Conda. Program Visual Studio używa również tego środowiska do debugowania, importowania i uzupełniania elementów członkowskich, sprawdzania składni oraz innych zadań, które wymagają usług językowych specyficznych dla wersji języka Python i zestawu zainstalowanych pakietów.

Wszystkie nowe projekty w języku Python w programie Visual Studio są początkowo skonfigurowane do używania domyślnego środowiska globalnego, które jest wyświetlane w węźle **środowiska Python** w **Eksplorator rozwiązań**:

![Globalne domyślne środowisko języka Python pokazane w Eksplorator rozwiązań](media/environments/environments-project.png)

::: moniker range="vs-2017"
Aby zmienić środowisko dla projektu, kliknij prawym przyciskiem myszy węzeł **środowiska Python** i wybierz polecenie **Dodaj/Usuń środowiska Python**. Z wyświetlonej listy, która zawiera globalne, wirtualne i Conda środowiska, zaznacz wszystkie te, które mają być wyświetlane w węźle **środowiska języka Python** :

![Okno dialogowe Dodawanie/usuwanie środowisk Python](media/environments/environments-add-remove.png)

Po wybraniu **przycisku OK**wszystkie wybrane środowiska będą widoczne w węźle **środowiska języka Python** . Aktualnie aktywowane środowisko jest pogrubione:

![W Eksplorator rozwiązań przedstawiono wiele środowisk Python](media/environments/environments-project-multiple.png)

Aby szybko aktywować inne środowisko, kliknij prawym przyciskiem myszy nazwę tego środowiska i wybierz polecenie **Aktywuj środowisko**. Wybór jest zapisywany w projekcie i środowisko jest uaktywniane za każdym razem, gdy otworzysz projekt w przyszłości. W przypadku wyczyszczenia wszystkich opcji w oknie dialogowym **Dodawanie/usuwanie środowisk Python** program Visual Studio aktywuje globalne środowisko domyślne.

Menu kontekstowe w węźle **środowiska Python** zawiera również dodatkowe polecenia:

| Polecenie | Opis |
| --- | --- |
| **Dodawanie środowiska wirtualnego** | Rozpoczyna proces tworzenia nowego środowiska wirtualnego w projekcie. Zobacz [Tworzenie środowiska wirtualnego](#create-a-virtual-environment). |
| **Dodaj istniejące środowisko wirtualne** | Wyświetla komunikat z prośbą o wybranie folderu zawierającego środowisko wirtualne i dodanie go do listy w obszarze **środowiska Python**, ale nie aktywuje go. Zobacz [Aktywowanie istniejącego środowiska wirtualnego](#activate-an-existing-virtual-environment). |
| **Utwórz środowisko Conda** | Przełącza do okna **środowiska Python** *window* , w którym należy wprowadzić nazwę środowiska i określić jego interpreter podstawowy. Zobacz [środowiska Conda](managing-python-environments-in-visual-studio.md#conda-environments). |
::: moniker-end

::: moniker range=">=vs-2019"
Aby zmienić środowisko dla projektu, kliknij prawym przyciskiem myszy węzeł **środowiska Python** i wybierz polecenie **Dodaj środowisko**. Możesz również wybrać opcję **Dodaj środowisko** z listy rozwijanej środowisko na pasku narzędzi języka Python.

W oknie dialogowym **Dodawanie środowiska** wybierz kartę **istniejące środowisko** , a następnie wybierz nowe środowisko z listy rozwijanej **środowisko** :

![Wybieranie środowiska projektu w oknie dialogowym Dodaj środowiska](media/environments/environments-project-2019.png)

Jeśli do projektu zostało już dodane środowisko inne niż globalne, może być konieczne aktywowanie nowo dodanego środowiska. Kliknij prawym przyciskiem myszy środowisko w węźle **środowiska Python** i wybierz polecenie **Aktywuj środowisko**. Aby usunąć środowisko z projektu, wybierz pozycję **Usuń**.

![Aktywowanie i usuwanie środowiska projektu](media/environments/environments-project-add-remove-2019.png)
::: moniker-end

## <a name="use-virtual-environments"></a>Korzystanie z środowisk wirtualnych

Środowisko wirtualne jest unikatowym połączeniem określonego interpretera języka Python i określonym zestawem bibliotek, które różnią się od innych środowisk globalnych i Conda. Środowisko wirtualne jest specyficzne dla projektu i jest przechowywane w folderze projektu. Ten folder zawiera zainstalowane biblioteki środowiska wraz z plikiem *pyvenv. cfg* , który określa ścieżkę do *interpretera podstawowego* środowiska w innym miejscu w systemie plików. (Oznacza to, że środowisko wirtualne nie zawiera kopii interpretera, tylko link do niego).

Zaletą korzystania ze środowiska wirtualnego jest to, że podczas tworzenia projektu w miarę upływu czasu środowisko wirtualne zawsze odzwierciedla dokładne zależności projektu. (Udostępnione środowisko globalne, z drugiej strony, zawiera dowolną liczbę bibliotek, niezależnie od tego, czy są one używane w projekcie, czy nie). Następnie można łatwo utworzyć plik *requirements.txt* ze środowiska wirtualnego, który jest następnie używany do ponownej instalacji tych zależności na innym komputerze deweloperskim lub produkcyjnym. Aby uzyskać więcej informacji, zobacz [Zarządzanie wymaganymi pakietami za pomocą requirements.txt](managing-required-packages-with-requirements-txt.md).

Po otwarciu projektu w programie Visual Studio, który zawiera plik *requirements.txt* , program Visual Studio automatycznie udostępnia opcję ponownego tworzenia środowiska wirtualnego. Na komputerach, na których nie zainstalowano programu Visual Studio, można użyć `pip install -r requirements.txt` programu do przywrócenia pakietów.

Ze względu na to, że środowisko wirtualne zawiera trwale zakodowaną ścieżkę do interpretera podstawowego, a ponieważ można odtworzyć środowisko przy użyciu *requirements.txt*, zazwyczaj pominięto cały folder środowiska wirtualnego z kontroli źródła.

W poniższych sekcjach wyjaśniono, jak aktywować istniejące środowisko wirtualne w projekcie i jak utworzyć nowe środowisko wirtualne.

W programie Visual Studio środowisko wirtualne można aktywować dla projektu, podobnie jak w przypadku węzła **środowiska Python** w **Eksplorator rozwiązań**.

Po dodaniu środowiska wirtualnego do projektu pojawia się ono w oknie środowiska języka **Python** . Następnie można ją aktywować podobnie jak dowolne inne środowisko i zarządzać swoimi pakietami.

::: moniker range="vs-2017"
### <a name="create-a-virtual-environment"></a>Tworzenie środowiska wirtualnego

Nowe środowisko wirtualne można utworzyć bezpośrednio w programie Visual Studio w następujący sposób:

1. Kliknij prawym przyciskiem myszy środowisko **Python** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj środowisko wirtualne**, które powoduje wyświetlenie następującego okna dialogowego:

    ![Tworzenie środowiska wirtualnego](media/environments/environments-add-virtual-1.png)

1. W polu **Lokalizacja środowiska wirtualnego** określ ścieżkę dla środowiska wirtualnego. Jeśli określisz tylko nazwę, środowisko wirtualne jest tworzone w ramach bieżącego projektu w podfolderze o tej nazwie.

1. Wybierz środowisko jako interpreter podstawowy i wybierz pozycję **Utwórz**. Program Visual Studio Wyświetla pasek postępu podczas konfigurowania środowiska i pobiera wszystkie niezbędne pakiety. Po zakończeniu środowisko wirtualne jest wyświetlane w oknie **środowiska języka Python** dla projektu zawierającego.

1. Środowisko wirtualne nie jest domyślnie aktywowane. Aby uaktywnić środowisko wirtualne dla projektu, kliknij go prawym przyciskiem myszy i wybierz polecenie **Aktywuj środowisko**.

> [!Note]
> Jeśli ścieżka lokalizacji identyfikuje istniejące środowisko wirtualne, program Visual Studio automatycznie wykryje interpreter podstawowy (przy użyciu pliku *orig-prefix.txt* w katalogu *lib* środowiska) i zmieni przycisk **Utwórz** , aby **dodać**.
>
> Jeśli podczas dodawania środowiska wirtualnego istnieje plik *requirements.txt* , w oknie dialogowym **Dodawanie środowiska wirtualnego** zostanie wyświetlona opcja automatycznej instalacji pakietów, co ułatwia ponowne utworzenie środowiska na innym komputerze:
>
> ![Utwórz środowisko wirtualne przy użyciu requirements.txt](media/environments/environments-requirements-txt.png)
>
> W obu przypadkach wynik jest taki sam jak w przypadku użycia polecenia **Dodaj istniejące środowisko wirtualne** .

### <a name="activate-an-existing-virtual-environment"></a>Aktywuj istniejące środowisko wirtualne

Jeśli środowisko wirtualne zostało już utworzone w innym miejscu, można je aktywować w projekcie w następujący sposób:

1. Kliknij prawym przyciskiem myszy **środowisko Python** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj istniejące środowisko wirtualne**.

1. W wyświetlonym oknie dialogowym **przeglądania** przejdź do folderu zawierającego środowisko wirtualne i wybierz go, a następnie wybierz **przycisk OK**. Jeśli program Visual Studio wykryje plik *requirements.txt* w tym środowisku, zostanie wyświetlony monit z pytaniem, czy zainstalować te pakiety.

1. Po kilku chwilach środowisko wirtualne jest wyświetlane w węźle **środowiska Python** w **Eksplorator rozwiązań**. Środowisko wirtualne nie jest domyślnie aktywowane, więc kliknij je prawym przyciskiem myszy i wybierz polecenie **Aktywuj środowisko**.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="create-a-virtual-environment"></a>Tworzenie środowiska wirtualnego

Nowe środowisko wirtualne można utworzyć bezpośrednio w programie Visual Studio w następujący sposób:

1. Kliknij prawym przyciskiem myszy **środowisko Python** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj środowisko**lub wybierz pozycję **Dodaj środowisko** z listy rozwijanej środowiska na pasku narzędzi języka Python. W wyświetlonym oknie dialogowym **Dodawanie środowiska** wybierz kartę **środowisko wirtualne** :

    ![Karta środowisko wirtualne okna dialogowego Dodawanie środowiska](media/environments/environments-add-virtual-1-2019.png)

1. Określ nazwę środowiska wirtualnego, wybierz interpreter podstawowy i sprawdź jego lokalizację. W obszarze **Instaluj pakiety z pliku**podaj ścieżkę do pliku *requirements.txt* w razie potrzeby.

1. Zapoznaj się z innymi opcjami w oknie dialogowym:

    | Opcja | Opis |
    | --- | --- |
    | Ustaw jako bieżące środowisko | Aktywuje nowe środowisko w wybranym projekcie po utworzeniu środowiska. |
    | Ustaw jako domyślne środowisko dla nowych projektów | Automatycznie ustawia i aktywuje środowisko wirtualne w nowych projektach utworzonych w programie Visual Studio. W przypadku korzystania z tej opcji środowisko wirtualne należy umieścić w lokalizacji poza określonym projektem.  |
    | Wyświetl w oknie środowiska języka Python | Określa, czy okno **środowiska języka Python** ma być otwierane po utworzeniu środowiska. |
    | Udostępnij to środowisko globalnie | Określa, czy środowisko wirtualne działa również jako środowisko globalne. W przypadku korzystania z tej opcji środowisko wirtualne należy umieścić w lokalizacji poza określonym projektem. |

1. Wybierz pozycję **Utwórz** , aby zakończyć środowisko wirtualne. Program Visual Studio Wyświetla pasek postępu podczas konfigurowania środowiska i pobiera wszystkie niezbędne pakiety. Po zakończeniu środowisko wirtualne jest uaktywniane i pojawia się w węźle **środowiska Python** w **Eksplorator rozwiązań** oraz w oknie **środowiska Python** dla projektu zawierającego.

### <a name="activate-an-existing-virtual-environment"></a>Aktywuj istniejące środowisko wirtualne

Jeśli środowisko wirtualne zostało już utworzone w innym miejscu, można je aktywować w projekcie w następujący sposób:

1. Kliknij prawym przyciskiem myszy **środowisko Python** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj środowisko**.

1. W wyświetlonym oknie dialogowym **przeglądania** przejdź do folderu zawierającego środowisko wirtualne i wybierz go, a następnie wybierz **przycisk OK**. Jeśli program Visual Studio wykryje plik *requirements.txt* w tym środowisku, zostanie wyświetlony monit z pytaniem, czy zainstalować te pakiety.

1. Po kilku chwilach środowisko wirtualne jest wyświetlane w węźle **środowiska Python** w **Eksplorator rozwiązań**. Środowisko wirtualne nie jest domyślnie aktywowane, więc kliknij je prawym przyciskiem myszy i wybierz polecenie **Aktywuj środowisko**.
::: moniker-end

### <a name="remove-a-virtual-environment"></a>Usuwanie środowiska wirtualnego

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy środowisko wirtualne i wybierz polecenie **Usuń**.

1. Program Visual Studio pyta, czy należy usunąć lub usunąć środowisko wirtualne. Wybranie pozycji **Usuń** sprawia, że jest ona niedostępna dla projektu, ale pozostawia ją w systemie plików. Wybranie opcji **Usuń** powoduje usunięcie środowiska z projektu i usunięcie go z systemu plików. Nie dotyczy to interpretera podstawowego.

## <a name="view-installed-packages"></a>Wyświetl zainstalowane pakiety

W Eksplorator rozwiązań rozwiń wszystkie węzły określonego środowiska, aby szybko wyświetlić pakiety, które są zainstalowane w tym środowisku (co oznacza, że możesz importować i używać tych pakietów w kodzie, gdy środowisko jest aktywne):

![Pakiety języka Python dla środowiska w Eksplorator rozwiązań](media/environments/environments-installed-packages.png)

::: moniker range="vs-2017"
Aby zainstalować nowe pakiety, kliknij prawym przyciskiem myszy środowisko i wybierz polecenie **Zainstaluj pakiet języka Python** , aby przełączyć się na kartę odpowiednie **pakiety** w oknie **środowiska języka Python** . Wprowadź wyszukiwany termin (zazwyczaj nazwę pakietu), a program Visual Studio Wyświetla pasujące pakiety.
::: moniker-end
::: moniker range=">=vs-2019"
Aby zainstalować nowe pakiety, kliknij prawym przyciskiem myszy środowisko i wybierz polecenie **Zarządzaj pakietami języka Python** (lub użyj przycisku pakiet na pasku narzędzi Python), aby przełączyć się na kartę odpowiednie **pakiety** w oknie **środowiska języka Python** . Na karcie **pakiety** wprowadź wyszukiwany termin (zazwyczaj nazwę pakietu), a program Visual Studio Wyświetla pasujące pakiety.
::: moniker-end

W programie Visual Studio pakiety (i zależności) dla większości środowisk są pobierane z [indeksu pakietów języka Python (PyPI)](https://pypi.org), gdzie można również wyszukiwać dostępne pakiety. Pasek stanu programu Visual Studio i okno dane wyjściowe zawierają informacje o instalacji. Aby odinstalować pakiet, kliknij go prawym przyciskiem myszy i wybierz polecenie **Usuń**.

Menedżer pakietów Conda zazwyczaj używa `https://repo.continuum.io/pkgs/` jako domyślny kanał, ale dostępne są inne kanały. Aby uzyskać więcej informacji, zobacz [Manage Channels](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-channels.html) (docs.Conda.IO).

Należy pamiętać, że wyświetlane wpisy mogą być niedokładne, a instalacja i Dezinstalacja może być niezawodna lub niedostępna. Program Visual Studio używa Menedżera pakietów PIP, jeśli jest dostępny, a następnie pobiera i instaluje je w razie potrzeby. Program Visual Studio może również korzystać z Menedżera pakietów easy_install. Wyświetlane są również pakiety zainstalowane przy użyciu `pip` lub `easy_install` z wiersza polecenia.

Należy również zauważyć, że program Visual Studio nie obsługuje obecnie korzystania `conda` z programu w celu zainstalowania pakietów w środowisku Conda. `conda`Zamiast tego użyj z wiersza polecenia.

> [!Tip]
> Typowa sytuacja, w której nie można zainstalować pakietu przez program PIP, ma miejsce, gdy pakiet zawiera kod źródłowy dla składników natywnych w plikach * \* . PYD* . Bez zainstalowanej wymaganej wersji programu Visual Studio program PIP nie może skompilować tych składników. Komunikat o błędzie wyświetlany w tej sytuacji jest **następujący: nie można odnaleźć vcvarsall.bat**. `easy_install` Program często może pobrać wstępnie skompilowane pliki binarne i pobrać odpowiedni kompilator dla starszych wersji języka Python z programu [https://www.microsoft.com/download/details.aspx?id=44266](https://www.microsoft.com/download/details.aspx?id=44266) . Aby uzyskać więcej informacji, zobacz [temat jak radzić sobie z "znalezieniem vcvarsallbat"](https://devblogs.microsoft.com/python/unable-to-find-vcvarsall-bat/) w blogu zespołu narzędzi Python.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie środowiskami języka Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Użyj requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Dokumentacja okna środowiska Python](python-environments-window-tab-reference.md)
