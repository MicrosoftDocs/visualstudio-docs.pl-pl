---
title: Wybieranie interpretera i środowiska języka Python dla projektu
description: Można w szczególności wybrać środowisko Języka Python, w tym Anaconda i środowiska wirtualne, aby zastosować do określonego projektu.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302729"
---
# <a name="how-to-select-a-python-environment-for-a-project"></a>Jak wybrać środowisko Języka Python dla projektu

Cały kod w projekcie Języka Python działa w kontekście określonego środowiska, takiego jak globalne środowisko Języka Python, środowisko Anaconda, środowisko wirtualne lub środowisko conda. Visual Studio używa również tego środowiska do debugowania, importowania i ukończenia elementu członkowskiego, sprawdzania składni i innych zadań, które wymagają usług językowych, które są specyficzne dla wersji języka Python i zestaw zainstalowanych pakietów.

Wszystkie nowe projekty języka Python w programie Visual Studio są początkowo skonfigurowane do używania domyślnego środowiska globalnego, które pojawia się w węźle **Środowiska Języka Python** w **Eksploratorze rozwiązań:**

![Globalne domyślne środowisko języka Python wyświetlane w Eksploratorze rozwiązań](media/environments/environments-project.png)

::: moniker range="vs-2017"
Aby zmienić środowisko dla projektu, kliknij prawym przyciskiem myszy węzeł **Środowiska języka Python** i wybierz polecenie **Dodaj/Usuń środowiska Języka Python**. Z wyświetlona lista, która obejmuje środowiska globalne, wirtualne i conda, wybierz wszystkie te, które mają być wyświetlane w węźle **Środowiska Języka Python:**

![Okno dialogowe Dodawanie/usuwanie środowisk języka Python](media/environments/environments-add-remove.png)

Po wybraniu **przycisku OK**wszystkie wybrane środowiska pojawią się w węźle **Środowiska języka Python.** Aktualnie aktywowane środowisko jest wyświetlane pogrubioną czcionką:

![Wiele środowisk języka Python wyświetlanych w Eksploratorze rozwiązań](media/environments/environments-project-multiple.png)

Aby szybko aktywować inne środowisko, kliknij prawym przyciskiem myszy nazwę tego środowiska i wybierz pozycję **Aktywuj środowisko**. Twój wybór jest zapisywany w projekcie, a środowisko jest aktywowane przy każdym otwarciu projektu w przyszłości. Jeśli wyczyścisz wszystkie opcje w oknie dialogowym **Dodaj/Usuń środowiska Języka Python,** program Visual Studio aktywuje globalne środowisko domyślne.

Menu kontekstowe w węźle **Środowiska języka Python** zawiera również dodatkowe polecenia:

| Polecenie | Opis |
| --- | --- |
| **Dodaj środowisko wirtualne** | Rozpoczyna proces tworzenia nowego środowiska wirtualnego w projekcie. Zobacz [Tworzenie środowiska wirtualnego](#create-a-virtual-environment). |
| **Dodawanie istniejącego środowiska wirtualnego** | Monituje o wybranie folderu zawierającego środowisko wirtualne i dodaje go do listy w obszarze **Środowiska Języka Python**, ale go nie aktywuje. Zobacz [Aktywowanie istniejącego środowiska wirtualnego](#activate-an-existing-virtual-environment). |
| **Tworzenie środowiska Conda** | Przełącza się do *okna* **Środowiska języka Python,** w którym można wprowadzić nazwę dla środowiska i określić jego interpreter podstawowy. Zobacz [środowiska Conda](managing-python-environments-in-visual-studio.md#conda-environments). |
::: moniker-end

::: moniker range=">=vs-2019"
Aby zmienić środowisko dla projektu, kliknij prawym przyciskiem myszy węzeł **Środowiska języka Python** i wybierz polecenie Dodaj **środowisko**lub wybierz pozycję **Dodaj środowisko** z listy rozwijanej środowiska na pasku narzędzi Pythona.

Po przejściu w oknie dialogowym **Dodawanie środowiska** wybierz kartę **Istniejące środowisko,** a następnie wybierz nowe środowisko z listy rozwijanej **Środowisko:**

![Wybieranie środowiska projektu w oknie dialogowym Dodawanie środowisk](media/environments/environments-project-2019.png)

Jeśli do projektu dodano już środowisko inne niż globalne domyślne, może być konieczne aktywowanie nowo dodanego środowiska. Kliknij prawym przyciskiem myszy to środowisko w węźle **Środowiska języka Python** i wybierz polecenie Aktywuj **środowisko**. Aby usunąć środowisko z projektu, wybierz pozycję **Usuń**.

![Aktywowanie i usuwanie środowiska projektu](media/environments/environments-project-add-remove-2019.png)
::: moniker-end

## <a name="use-virtual-environments"></a>Korzystanie ze środowisk wirtualnych

Środowisko wirtualne to unikatowa kombinacja określonego interpretera języka Python i określonego zestawu bibliotek, która różni się od innych środowisk globalnych i conda. Środowisko wirtualne jest specyficzne dla projektu i jest obsługiwane w folderze projektu. Ten folder zawiera zainstalowane biblioteki środowiska wraz z plikiem *pyvenv.cfg,* który określa ścieżkę do *podstawowego interpretera* środowiska w innym miejscu w systemie plików. (Oznacza to, że środowisko wirtualne nie zawiera kopii tłumacza, tylko łącze do niego).)

Zaletą korzystania ze środowiska wirtualnego jest to, że podczas opracowywania projektu w czasie środowisko wirtualne zawsze odzwierciedla dokładne zależności projektu. (Udostępnione środowisko globalne zawiera natomiast dowolną liczbę bibliotek, niezależnie od tego, czy używasz ich w projekcie, czy nie). Następnie można łatwo utworzyć plik *requirements.txt* ze środowiska wirtualnego, który jest następnie używany do ponownej instalacji tych zależności na innym komputerze deweloperskim lub produkcyjnym. Aby uzyskać więcej informacji, zobacz [Zarządzanie wymaganymi pakietami z plikem requirements.txt](managing-required-packages-with-requirements-txt.md).

Po otwarciu projektu w programie Visual Studio, który zawiera plik *requirements.txt,* Visual Studio automatycznie daje możliwość ponownego tworzenia środowiska wirtualnego. Na komputerach, na których program Visual `pip install -r requirements.txt` Studio nie jest zainstalowany, można przywrócić pakiety.

Ponieważ środowisko wirtualne zawiera zakodowane ścieżki do tłumacza podstawowego i ponieważ można odtworzyć środowisko przy użyciu *pliku requirements.txt,* zazwyczaj pomija się cały folder środowiska wirtualnego z kontroli źródła.

W poniższych sekcjach wyjaśniono, jak aktywować istniejące środowisko wirtualne w projekcie i jak utworzyć nowe środowisko wirtualne.

W programie Visual Studio środowisko wirtualne można aktywować dla projektu, jak każdy inny za pośrednictwem **węzła Środowiska Języka Python** w **Eksploratorze rozwiązań.**

Po dodaniu środowiska wirtualnego do projektu pojawia się w oknie **Środowiska języka Python.** Następnie można go aktywować, jak każde inne środowisko i zarządzać jego pakietami.

::: moniker range="vs-2017"
### <a name="create-a-virtual-environment"></a>Tworzenie środowiska wirtualnego

Nowe środowisko wirtualne można utworzyć bezpośrednio w programie Visual Studio w następujący sposób:

1. Kliknij prawym przyciskiem myszy **pozycję Środowiska języka Python** w **Eksploratorze rozwiązań** i wybierz pozycję **Dodaj środowisko wirtualne,** które powoduje wyświetlenie następującego okna dialogowego:

    ![Tworzenie środowiska wirtualnego](media/environments/environments-add-virtual-1.png)

1. W polu **Lokalizacja środowiska wirtualnego** określ ścieżkę dla środowiska wirtualnego. Jeśli określisz tylko nazwę, środowisko wirtualne jest tworzone w ramach bieżącego projektu w podfolderze o tej nazwie.

1. Wybierz środowisko jako podstawowy interpreter i wybierz pozycję **Utwórz**. Visual Studio wyświetla pasek postępu podczas konfigurowania środowiska i pobiera wszystkie niezbędne pakiety. Po zakończeniu środowisko wirtualne pojawia się w oknie **środowiska języka Python** dla projektu zawierającego.

1. Środowisko wirtualne nie jest domyślnie aktywowane. Aby aktywować go dla projektu, kliknij go prawym przyciskiem myszy i wybierz pozycję **Aktywuj środowisko**.

> [!Note]
> Jeśli ścieżka lokalizacji identyfikuje istniejące środowisko wirtualne, program Visual Studio automatycznie wykrywa podstawowy interpreter (używając pliku *orig-prefix.txt* w katalogu *lib* środowiska) i zmienia przycisk **Utwórz** na **Dodaj**.
>
> Jeśli podczas dodawania środowiska wirtualnego istnieje plik *requirements.txt,* w oknie dialogowym **Dodaj środowisko wirtualne** zostanie wyświetlona opcja automatycznego instalowania pakietów, co ułatwia ponowne tworzenie środowiska na innym komputerze:
>
> ![Tworzenie środowiska wirtualnego z plikem requirements.txt](media/environments/environments-requirements-txt.png)
>
> Tak czy inaczej wynik jest taki sam, jak w przypadku użycia polecenia **Dodaj istniejące środowisko wirtualne.**

### <a name="activate-an-existing-virtual-environment"></a>Aktywowanie istniejącego środowiska wirtualnego

Jeśli środowisko wirtualne utworzono już w innym miejscu, można je aktywować dla projektu w następujący sposób:

1. Kliknij prawym przyciskiem myszy **pozycję Środowiska języka Python** w **Eksploratorze rozwiązań** i wybierz pozycję **Dodaj istniejące środowisko wirtualne**.

1. W wyświetlonym oknie dialogowym Przeglądaj przejdź do folderu zawierającego środowisko **wirtualne** i wybierz go, a następnie wybierz przycisk **OK**. Jeśli program Visual Studio wykryje plik *requirements.txt* w tym środowisku, pyta, czy zainstalować te pakiety.

1. Po kilku chwilach środowisko wirtualne pojawia się w węźle **Środowiska Języka Python** w **Eksploratorze rozwiązań**. Środowisko wirtualne nie jest domyślnie aktywowane, więc kliknij je prawym przyciskiem myszy i wybierz **pozycję Aktywuj środowisko**.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="create-a-virtual-environment"></a>Tworzenie środowiska wirtualnego

Nowe środowisko wirtualne można utworzyć bezpośrednio w programie Visual Studio w następujący sposób:

1. Kliknij prawym przyciskiem myszy **pozycję Środowiska języka Python** w **Eksploratorze rozwiązań** i wybierz pozycję **Dodaj środowisko**lub wybierz pozycję Dodaj **środowisko** z listy rozwijanej środowiska na pasku narzędzi Pythona. W wyświetlonym oknie dialogowym **Dodawanie środowiska** wybierz kartę **Środowisko wirtualne:**

    ![Karta Środowisko wirtualne w oknie dialogowym Dodawanie środowiska](media/environments/environments-add-virtual-1-2019.png)

1. Określ nazwę środowiska wirtualnego, wybierz tłumacza podstawowego i sprawdź jego lokalizację. W obszarze **Zainstaluj pakiety z pliku**podaj ścieżkę do pliku *requirements.txt* w razie potrzeby.

1. Przejrzyj inne opcje w oknie dialogowym:

    | Opcja | Opis |
    | --- | --- |
    | Ustaw jako bieżące środowisko | Aktywuje nowe środowisko w wybranym projekcie po utworzeniu środowiska. |
    | Ustawienie jako środowiska domyślnego dla nowych projektów | Automatycznie ustawia i aktywuje środowisko wirtualne w nowych projektach utworzonych w programie Visual Studio. Korzystając z tej opcji, środowisko wirtualne powinny być umieszczane w lokalizacji poza określonym projektem.  |
    | Wyświetl w oknie Środowiska Języka Python | Określa, czy po utworzeniu środowiska ma być otwierane okno **Środowiska języka Python.** |
    | Udostępnianie tego środowiska na całym świecie | Określa, czy środowisko wirtualne działa również jako środowisko globalne. Korzystając z tej opcji, środowisko wirtualne powinny być umieszczane w lokalizacji poza określonym projektem. |

1. Wybierz **pozycję Utwórz,** aby sfinalizować środowisko wirtualne. Visual Studio wyświetla pasek postępu podczas konfigurowania środowiska i pobiera wszystkie niezbędne pakiety. Po zakończeniu środowiska wirtualnego jest aktywowany i pojawia się w węźle **Środowiska języka Python** w **Eksploratorze rozwiązań** i okna **środowiska Python** dla projektu zawierającego.

### <a name="activate-an-existing-virtual-environment"></a>Aktywowanie istniejącego środowiska wirtualnego

Jeśli środowisko wirtualne utworzono już w innym miejscu, można je aktywować dla projektu w następujący sposób:

1. Kliknij prawym przyciskiem myszy **pozycję Środowiska języka Python** w **Eksploratorze rozwiązań** i wybierz pozycję **Dodaj środowisko**.

1. W wyświetlonym oknie dialogowym Przeglądaj przejdź do folderu zawierającego środowisko **wirtualne** i wybierz go, a następnie wybierz przycisk **OK**. Jeśli program Visual Studio wykryje plik *requirements.txt* w tym środowisku, pyta, czy zainstalować te pakiety.

1. Po kilku chwilach środowisko wirtualne pojawia się w węźle **Środowiska Języka Python** w **Eksploratorze rozwiązań**. Środowisko wirtualne nie jest domyślnie aktywowane, więc kliknij je prawym przyciskiem myszy i wybierz **pozycję Aktywuj środowisko**.
::: moniker-end

### <a name="remove-a-virtual-environment"></a>Usuwanie środowiska wirtualnego

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy środowisko wirtualne i wybierz polecenie **Usuń**.

1. Visual Studio pyta, czy usunąć lub usunąć środowisko wirtualne. Wybranie opcji **Usuń** powoduje, że jest on niedostępny dla projektu, ale pozostawia go w systemie plików. Wybranie opcji **Usuń** spowoduje usunięcie środowiska z projektu i usunięcie go z systemu plików. Tłumacz podstawowy pozostaje nienaruszony.

## <a name="view-installed-packages"></a>Wyświetlanie zainstalowanych pakietów

W Eksploratorze rozwiązań rozwiń węzeł dowolnego określonego środowiska, aby szybko wyświetlić pakiety zainstalowane w tym środowisku (co oznacza, że można importować i używać tych pakietów w kodzie, gdy środowisko jest aktywne):

![Pakiety języka Python dla środowiska w Eksploratorze rozwiązań](media/environments/environments-installed-packages.png)

::: moniker range="vs-2017"
Aby zainstalować nowe pakiety, kliknij prawym przyciskiem myszy środowisko i wybierz pozycję **Zainstaluj pakiet Python,** aby przełączyć się na odpowiednią kartę **Pakiety** w oknie **Środowiska Języka Python.** Wprowadź wyszukiwany termin (zwykle nazwę pakietu), a program Visual Studio wyświetla pasujące pakiety.
::: moniker-end
::: moniker range=">=vs-2019"
Aby zainstalować nowe pakiety, kliknij prawym przyciskiem myszy środowisko i wybierz pozycję **Zarządzaj pakietami języka Python** (lub użyj przycisku pakietu na pasku narzędzi Pythona), aby przełączyć się na odpowiednią kartę **Pakiety** w oknie **Środowiska Języka Python.** Po wejściu na kartę **Pakiety** wprowadź wyszukiwany termin (zwykle nazwę pakietu), a program Visual Studio wyświetla pasujące pakiety.
::: moniker-end

W programie Visual Studio pakiety (i zależności) dla większości środowisk są pobierane z [indeksu pakietów Języka Python (PyPI)](https://pypi.org), gdzie można również wyszukiwać dostępne pakiety. Pasek stanu i okno danych wyjściowych programu Visual Studio pokazują informacje o instalacji. Aby odinstalować pakiet, kliknij go prawym przyciskiem myszy i wybierz polecenie **Usuń**.

Menedżer pakietów conda zazwyczaj `https://repo.continuum.io/pkgs/` używa jako kanału domyślnego, ale dostępne są inne kanały. Aby uzyskać więcej informacji, zobacz [Zarządzanie kanałami](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-channels.html) (docs.conda.io).

Należy pamiętać, że wyświetlane wpisy mogą nie zawsze być dokładne, a instalacja i dezinstalacja mogą nie być wiarygodne lub dostępne. Visual Studio używa menedżera pakietów pip, jeśli jest dostępny, i pobiera i instaluje go, gdy jest to wymagane. Visual Studio można również użyć menedżera pakietów easy_install. Wyświetlane są `pip` `easy_install` również pakiety zainstalowane za pomocą wiersza polecenia lub z niego.

Należy również zauważyć, że visual `conda` studio obecnie nie obsługuje przy użyciu do instalowania pakietów w środowisku conda. Zamiast `conda` tego użyj z wiersza polecenia.

> [!Tip]
> Typowym elementem, w której pip nie może zainstalować pakietu, * \** jest sytuacja, w której pakiet zawiera kod źródłowy składników macierzystych w plikach pyd. Bez zainstalowanej wymaganej wersji programu Visual Studio program pip nie można skompilować tych składników. Komunikat o błędzie wyświetlany w tej sytuacji jest **błąd: Nie można znaleźć vcvarsall.bat**. `easy_install`jest często w stanie pobrać wstępnie skompilowane pliki binarne i można [https://www.microsoft.com/download/details.aspx?id=44266](https://www.microsoft.com/download/details.aspx?id=44266)pobrać odpowiedni kompilator dla starszych wersji Pythona z . Aby uzyskać więcej informacji, zobacz [Jak radzić sobie z bólem "nie można znaleźć vcvarsallbat"](https://devblogs.microsoft.com/python/unable-to-find-vcvarsall-bat/) na blogu zespołu narzędzi Pythona.

## <a name="see-also"></a>Zobacz też

- [Zarządzanie środowiskami języka Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Używanie pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Odwołanie do okna Środowiska języka Python](python-environments-window-tab-reference.md)
