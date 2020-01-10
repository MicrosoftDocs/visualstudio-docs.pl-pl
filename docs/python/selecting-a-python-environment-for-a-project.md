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
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848425"
---
# <a name="how-to-select-a-python-environment-for-a-project"></a>Jak wybrać środowisko Python dla projektu

Cały kod w projekcie języka Python jest uruchamiany w kontekście określonego środowiska, takie jak globalnego środowisko Python, środowisko Anaconda, środowisko wirtualne lub środowiska conda. Visual Studio używa także środowisko do debugowania, importowania i zakończenia elementu członkowskiego, sprawdzanie składni i innych zadań, które wymagają usług językowych, które są specyficzne dla środowiska Python w wersji i zestaw zainstalowanych pakietów.

Nowe projekty języka Python w programie Visual Studio początkowo są skonfigurowane do używania domyślnej globalnej środowisko, w którym pojawia się w obszarze **środowiska Python** w węźle **Eksploratora rozwiązań**:

![Środowiska Python domyślnie globalne wyświetlane w Eksploratorze rozwiązań](media/environments/environments-project.png)

::: moniker range="vs-2017"
Aby zmienić środowisko dla projektu, kliknij prawym przyciskiem myszy **środowiska Python** a następnie wybierz węzeł **środowiska Python Dodaj/Usuń**. Z wyświetlonej listy, która obejmuje globalnego, wirtualnych i środowisk conda, zaznacz wszystkie te, które mają być wyświetlane w obszarze **środowiska Python** węzła:

![Okno dialogowe Dodawanie/usuwanie środowiska Python](media/environments/environments-add-remove.png)

Po wybraniu **OK**, wybranych środowisk są wyświetlane w obszarze **środowiska Python** węzła. Obecnie aktywowanego środowiska zostanie wyświetlony pogrubioną czcionką:

![Wiele środowisk języka Python, wyświetlane w Eksploratorze rozwiązań](media/environments/environments-project-multiple.png)

Aby uaktywnić szybkie innego środowiska, kliknij prawym przyciskiem myszy nazwę tego środowiska, a następnie wybierz **środowiska Aktywuj**. Wybór zostaje zapisana wraz z projektu i środowiska jest aktywowany przy każdym otwarciu projektu w przyszłości. Jeśli usuniesz zaznaczenie wszystkich opcji w **środowiska Python Dodaj/Usuń** okno dialogowe, Visual Studio aktywuje środowiska domyślnego globalnego.

Menu kontekstowe **środowiska Python** węzła zawiera także dodatkowe polecenia:

| Polecenie | Opis |
| --- | --- |
| **Dodawanie środowiska wirtualnego** | Rozpocznie się proces tworzenia nowego środowiska wirtualnego w projekcie. Zobacz [Utwórz środowisko wirtualne](#create-a-virtual-environment). |
| **Dodawanie istniejącego środowiska wirtualnego** | Monit o wybranie folder zawierający środowisko wirtualne i dodaje go do listy w obszarze **środowiska Python**, ale nie aktywować. Zobacz [aktywować istniejącego środowiska wirtualnego](#activate-an-existing-virtual-environment). |
| **Tworzenie środowiska Conda** | Przełącza do **środowiska Python** *okna* w którym należy wprowadzić nazwę środowiska i określić jego podstawowy interpreter. Zobacz [środowisk Conda](managing-python-environments-in-visual-studio.md#conda-environments). |
::: moniker-end

::: moniker range=">=vs-2019"
Aby zmienić środowisko dla projektu, kliknij prawym przyciskiem myszy węzeł **środowiska Python** i wybierz polecenie **Dodaj środowisko**lub wybierz pozycję **Dodaj środowisko** z listy rozwijanej środowisko na pasku narzędzi języka Python.

W oknie dialogowym **Dodawanie środowiska** wybierz kartę **istniejące środowisko** , a następnie wybierz nowe środowisko z listy rozwijanej **środowisko** :

![Wybieranie środowiska projektu w oknie dialogowym Dodaj środowiska](media/environments/environments-project-2019.png)

Jeśli do projektu zostało już dodane środowisko inne niż globalne, może być konieczne aktywowanie nowo dodanego środowiska. Kliknij prawym przyciskiem myszy środowisko w węźle **środowiska Python** i wybierz polecenie **Aktywuj środowisko**. Aby usunąć środowisko z projektu, wybierz pozycję **Usuń**.

![Aktywowanie i usuwanie środowiska projektu](media/environments/environments-project-add-remove-2019.png)
::: moniker-end

## <a name="use-virtual-environments"></a>Korzystanie ze środowisk wirtualnych

Środowisko wirtualne ma unikatową kombinację określonych interpreter języka Python i określony zbiór bibliotek, który różni się od innych środowisk globalnych i conda. Środowisko wirtualne jest specyficzne dla projektu i są przechowywane w folderze projektu. Ten folder zawiera środowisko biblioteki zainstalowane wraz z *pyvenv.cfg* pliku, który określa ścieżkę w środowisku *podstawowy interpreter* innym miejscu w systemie plików. (Oznacza to, że środowisko wirtualne nie zawiera kopię interpretera tylko łącza do niego).

Korzyścią z używania środowiska wirtualnego jest, że podczas tworzenia projektu wraz z upływem czasu, środowisko wirtualne zawsze odzwierciedla dokładnie zależności projektu. (Udostępnione środowisko globalne, z drugiej strony, zawiera dowolną liczbę bibliotek, niezależnie od tego, czy są one używane w projekcie, czy nie). Następnie można łatwo utworzyć plik *Requirements. txt* w środowisku wirtualnym, który jest następnie używany do ponownej instalacji tych zależności na innym komputerze deweloperskim lub produkcyjnym. Aby uzyskać więcej informacji, zobacz [zarządzania wymagane pakiety przy użyciu pliku requirements.txt](managing-required-packages-with-requirements-txt.md).

Po otwarciu projektu w programie Visual Studio, który zawiera *requirements.txt* plików, programu Visual Studio automatycznie udostępnia opcję do odtworzenia w środowisku wirtualnym. Komputery, na którym nie zainstalowano programu Visual Studio, można użyć `pip install -r requirements.txt` próbie przywrócenia pakietów.

Ponieważ środowisko wirtualne zawiera ustalona ścieżka do interpretera podstawowej i Utwórz ponownie używając środowiska *requirements.txt*, zwykle pominąć folderu całego środowiska wirtualnego z kontroli źródła.

W poniższych sekcjach opisano, jak aktywować istniejącego środowiska wirtualnego w projekcie oraz sposób tworzenia nowego środowiska wirtualnego.

W programie Visual Studio, można aktywować środowisko wirtualne dla projektu, jak każdy inny za pośrednictwem **środowiska Python** w węźle **Eksploratora rozwiązań**.

Po środowisko wirtualne zostanie dodany do projektu, pojawi się on **środowiska Python** okna. Następnie można aktywować go jak dowolnego innego środowiska i możesz zarządzać jego pakietów.

::: moniker range="vs-2017"
### <a name="create-a-virtual-environment"></a>Tworzenie środowiska wirtualnego

Nowe środowisko wirtualne można utworzyć bezpośrednio w programie Visual Studio w następujący sposób:

1. Kliknij prawym przyciskiem myszy **środowiska Python** w **Eksploratora rozwiązań** i wybierz **Dodawanie środowiska wirtualnego**, co spowoduje uruchomienie następujące okno dialogowe:

    ![Tworzenie środowiska wirtualnego](media/environments/environments-add-virtual-1.png)

1. W **lokalizacji środowiska wirtualnego** pola, określ ścieżkę dla środowiska wirtualnego. Jeśli określisz tylko nazwę, środowisko wirtualne jest tworzony w ramach bieżącego projektu w podfolderze o tej nazwie.

1. Wybierz środowisko jako podstawowy interpreter, a następnie wybierz pozycję **Utwórz**. Visual Studio Wyświetla pasek postępu, gdy go skonfiguruje środowiska i pobierze wszystkie niezbędne pakiety. Po zakończeniu środowisko wirtualne jest wyświetlane w oknie **środowiska języka Python** dla projektu zawierającego.

1. Środowisko wirtualne nie została aktywowana domyślnie. Aby go uaktywnić dla projektu, kliknij go prawym przyciskiem myszy i wybierz **aktywować środowisko**.

> [!Note]
> Jeśli ścieżka lokalizacji identyfikuje istniejącego środowiska wirtualnego, Visual Studio automatycznie wykrywa podstawowy interpreter (przy użyciu *orig prefix.txt* plików w środowisku *lib* katalogu) i zmiany **Utwórz** przycisk, aby **Dodaj**.
>
> Jeśli *requirements.txt* plik istnieje w środowisku wirtualnym, dodając **Dodawanie środowiska wirtualnego** Wyświetla okno dialogowe możliwość pakiety są instalowane automatycznie, dzięki czemu można łatwo odtworzyć środowisko na innym komputerze:
>
> ![Tworzenie środowiska wirtualnego z pliku requirements.txt](media/environments/environments-requirements-txt.png)
>
> W obu przypadkach efekt jest taki sam jak w przypadku **Dodawanie istniejącego środowiska wirtualnego** polecenia.

### <a name="activate-an-existing-virtual-environment"></a>Aktywuj istniejącego środowiska wirtualnego

Jeśli już utworzono wirtualnego środowiska w innym miejscu, możesz to zrobić dla projektu w następujący sposób:

1. Kliknij prawym przyciskiem myszy **środowiska Python** w **Eksploratora rozwiązań** i wybierz **Dodawanie istniejącego środowiska wirtualnego**.

1. W **Przeglądaj** wyświetlonym oknie dialogowym Przejdź do i wybierz folder, który zawiera środowiska wirtualnego, a wybierz **OK**. Jeśli program Visual Studio wykryje *requirements.txt* pliku w tym środowisku go zapyta, czy zainstalować te pakiety.

1. Po kilku chwilach środowisko wirtualne jest wyświetlane w obszarze **środowiska Python** w węźle **Eksploratora rozwiązań**. Środowisko wirtualne nie została aktywowana domyślnie, więc kliknij ją prawym przyciskiem myszy i wybierz pozycję **aktywować środowisko**.
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

1. W **Przeglądaj** wyświetlonym oknie dialogowym Przejdź do i wybierz folder, który zawiera środowiska wirtualnego, a wybierz **OK**. Jeśli program Visual Studio wykryje *requirements.txt* pliku w tym środowisku go zapyta, czy zainstalować te pakiety.

1. Po kilku chwilach środowisko wirtualne jest wyświetlane w obszarze **środowiska Python** w węźle **Eksploratora rozwiązań**. Środowisko wirtualne nie została aktywowana domyślnie, więc kliknij ją prawym przyciskiem myszy i wybierz pozycję **aktywować środowisko**.
::: moniker-end

### <a name="remove-a-virtual-environment"></a>Usuwanie środowiska wirtualnego

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy środowisko wirtualne i wybierz **Usuń**.

1. Program Visual Studio zapyta, czy usuwanie środowiska wirtualnego. Wybieranie **Usuń** staje się niedostępny do projektu, ale pozostawia je w systemie plików. Wybieranie **Usuń** usuwa środowisko z projektu i usuwa go z systemu plików. Podstawowy interpreter pozostaje bez zmian.

## <a name="view-installed-packages"></a>Wyświetl zainstalowane pakiety

W Eksploratorze rozwiązań rozwiń węzeł w danym środowisku, aby szybko wyświetlić pakiety, które są zainstalowane w tym środowisku (tzn. można importować i użyć tych pakietów w kodzie, gdy środowisko jest aktywny):

![Pakiety języka Python dla środowiska w Eksploratorze rozwiązań](media/environments/environments-installed-packages.png)

::: moniker range="vs-2017"
Aby zainstalować nowe pakiety, kliknij prawym przyciskiem myszy środowisko i wybierz polecenie **Zainstaluj pakiet języka Python** , aby przełączyć się na kartę odpowiednie **pakiety** w oknie **środowiska języka Python** . Wprowadź wyszukiwania termin (zazwyczaj nazwa pakietu) i Visual Studio Wyświetla zgodnych pakietów.
::: moniker-end
::: moniker range=">=vs-2019"
Aby zainstalować nowe pakiety, kliknij prawym przyciskiem myszy środowisko i wybierz polecenie **Zarządzaj pakietami języka Python** (lub użyj przycisku pakiet na pasku narzędzi Python), aby przełączyć się na kartę odpowiednie **pakiety** w oknie **środowiska języka Python** . Na karcie **pakiety** wprowadź wyszukiwany termin (zazwyczaj nazwę pakietu), a program Visual Studio Wyświetla pasujące pakiety.
::: moniker-end

W programie Visual Studio pakiety (i zależności) dla większości środowisk są pobierane z [indeksu pakietów języka Python (PyPI)](https://pypi.org), gdzie można również wyszukiwać dostępne pakiety. Pasek stanu programu Visual Studio i okno dane wyjściowe zawierają informacje o instalacji. Aby odinstalować pakiet, kliknij go prawym przyciskiem myszy i wybierz **Usuń**.

Menedżer pakietów Conda ogólnie używa `https://repo.continuum.io/pkgs/` jako domyślnego kanału, ale dostępne są inne kanały. Aby uzyskać więcej informacji, zobacz [Manage Channels](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-channels.html) (docs.Conda.IO).

Należy pamiętać, że wyświetlane wpisy nie zawsze są dokładne i instalowania i odinstalowywania może nie być niezawodne lub są dostępne. Program Visual Studio korzysta z Menedżera pakietów pip, jeśli to możliwe i pobiera i instaluje je, gdy jest to wymagane. Program Visual Studio umożliwia również easy_install Menedżera pakietów. Zainstalowane pakiety przy użyciu `pip` lub `easy_install` z wiersza polecenia są również wyświetlane.

Też pamiętać, że program Visual Studio nie obecnie obsługuje `conda` zainstalować pakiety do środowiska conda. Użyj `conda` polecenia zamiast tego wiersza.

> [!Tip]
> Typowe sytuacji, w którym pip kończy się niepowodzeniem do zainstalowania pakietu jest, gdy pakiet zawiera kod źródłowy składnikami macierzystymi w  *\*.pyd* plików. Bez wymaganą wersję zainstalowanego programu Visual Studio narzędzia pip, nie można skompilować tych składników. Komunikat o błędzie wyświetlany w takiej sytuacji **błąd: nie można odnaleźć vcvarsall.bat**. `easy_install` często jest w stanie pobrać wstępnie skompilowanych plików binarnych, możesz również pobrać odpowiedni kompilatora dla starszych wersji języka Python z [ https://www.microsoft.com/download/details.aspx?id=44266 ](https://www.microsoft.com/download/details.aspx?id=44266). Aby uzyskać więcej informacji, zobacz [radzenia sobie z problemów z "nie można odnaleźć vcvarsallbat"](https://devblogs.microsoft.com/python/unable-to-find-vcvarsall-bat/) na Python tools blog zespołu.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie środowiskami Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Użyj pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Dokumentacja okna środowiska Python](python-environments-window-tab-reference.md)
