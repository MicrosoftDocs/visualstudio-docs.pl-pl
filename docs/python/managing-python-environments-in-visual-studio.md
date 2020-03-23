---
title: Zarządzanie środowiskami i tłumaczami języka Python
description: Okno Środowiska języka Python służy do zarządzania środowiskami globalnymi, wirtualnymi i conda, instalowania interpreterów i pakietów języka Python oraz przypisywania środowisk do projektów programu Visual Studio.
ms.date: 08/06/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 5e269e19a09aec157e38eaf8938b5995c2647803
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302834"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Jak tworzyć środowiska języka Python i zarządzać nimi w programie Visual Studio

*Środowisko* Języka Python to kontekst, w którym uruchamiasz kod języka Python i obejmuje środowiska globalne, wirtualne i conda. Środowisko składa się z interpretera, biblioteki (zazwyczaj biblioteki standardowej języka Python) i zestawu zainstalowanych pakietów. Te składniki razem określają, które konstrukcje języka i składnia są prawidłowe, jakie funkcje systemu operacyjnego można uzyskać dostęp i które pakiety można użyć.

W programie Visual Studio w systemie Windows, należy użyć okna **środowiska języka Python,** zgodnie z opisem w tym artykule, do zarządzania środowiskami i wybrać jeden jako domyślny dla nowych projektów. Inne aspekty środowiska znajdują się w następujących artykułach:

- Dla każdego danego projektu można [wybrać określone środowisko,](selecting-a-python-environment-for-a-project.md) a nie używać wartości domyślnej.

- Aby uzyskać szczegółowe informacje na temat tworzenia i używania środowisk wirtualnych dla projektów języka Python, zobacz [Używanie środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Jeśli chcesz zainstalować pakiety w środowisku, zapoznaj się z [dokumentacją karty Pakiety](python-environments-window-tab-reference.md#packages-tab).

- Aby zainstalować inny interpreter języka Python, zobacz [Instalowanie tłumaczy języka Python](installing-python-interpreters.md). Ogólnie rzecz biorąc, jeśli pobierzesz i uruchomisz instalator dla dystrybucji języka Python linii głównej, program Visual Studio wykryje, że nowa instalacja i środowisko pojawia się w oknie **Środowiska języka Python** i mogą być wybrane dla projektów.

Jeśli jesteś nowy w Pythonie w programie Visual Studio, następujące artykuły zawierają również z ogólnego tła:

- [Praca z pythonem w programie Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Instalowanie obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md)

::: moniker range="vs-2017"
> [!Note]
> Nie można zarządzać środowiskami dla kodu Języka Python, który jest otwierany tylko jako folder za pomocą polecenia**Folder otwierania** >  **pliku.** > **Folder** Zamiast tego [utwórz projekt języka Python z istniejącego kodu,](quickstart-01-python-in-visual-studio-project-from-existing-code.md) aby cieszyć się funkcjami środowiska programu Visual Studio.
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> Można zarządzać środowiskami dla kodu języka Python, który jest otwierany jako folder za pomocą polecenia **File** > **Open** > **Folder.** Pasek narzędzi języka Python umożliwia przełączanie między wszystkimi wykrytymi środowiskami, a także dodawanie nowego środowiska. Informacje o środowisku są przechowywane w pliku PythonSettings.json w folderze Workspace .vs.
::: moniker-end

## <a name="the-python-environments-window"></a>Okno Środowiska języka Python

Środowiska, o których program Visual Studio wie, są wyświetlane w oknie **Środowiska języka Python.** Aby otworzyć okno, użyj jednej z następujących metod:

- Wybierz polecenie menu **Wyświetl** > inne środowiska**języka Windows** > **Python.**
- Kliknij prawym przyciskiem myszy węzeł **Środowiska języka Python** dla projektu w **Eksploratorze rozwiązań** i wybierz pozycję **Wyświetl wszystkie środowiska języka Python:**

    ::: moniker range="vs-2017"
    ![Wyświetl wszystkie środowiska, polecenie w Eksploratorze rozwiązań](media/environments/environments-view-all.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Wyświetl wszystkie środowiska, polecenie w Eksploratorze rozwiązań](media/environments/environments-view-all-2019.png)
    ::: moniker-end

W obu przypadkach obok **Eksploratora rozwiązań**pojawia się okno **Środowiska Języka Python:**

::: moniker range="vs-2017"
![Okna Środowiska języka Python](media/environments/environments-default-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Okna Środowiska języka Python](media/environments/environments-default-view-2019.png)
::: moniker-end

Program Visual Studio wyszukuje zainstalowane środowiska globalne przy użyciu rejestru (zgodnie z [PEP 514),](https://www.python.org/dev/peps/pep-0514/)wraz ze środowiskami wirtualnymi i środowiskami conda (zobacz [Typy środowisk).](#types-of-environments) Jeśli na liście nie widać oczekiwanego środowiska, zobacz [Ręczne identyfikowanie istniejącego środowiska](#manually-identify-an-existing-environment).

Po wybraniu środowiska na liście program Visual Studio wyświetla różne właściwości i polecenia dla tego środowiska na karcie **Przegląd.** Na przykład na powyższym obrazie widać, że lokalizacją tłumacza jest *C:\Python36-32*. Cztery polecenia u dołu karty **Przegląd** otwierają wiersz polecenia z uruchomionym interpreterem. Aby uzyskać więcej informacji, zobacz [Odwołanie do karty okna środowiska języka Python — omówienie](python-environments-window-tab-reference.md#overview-tab).

Użyj listy rozwijanej poniżej listy środowisk, aby przełączyć się na różne karty, takie jak **Pakiety**i **IntelliSense**. Te karty są również opisane w [odwołaniu do karty okna środowiska Pythona](python-environments-window-tab-reference.md).

Wybranie środowiska nie zmienia jego relacji do żadnych projektów. Domyślne środowisko, wyświetlane pogrubioną czcionką na liście, jest tym, które program Visual Studio używa dla wszystkich nowych projektów. Aby użyć innego środowiska z nowymi projektami, użyj **polecenia Ustaw to jako środowisko domyślne dla nowych projektów.** W kontekście projektu zawsze można wybrać określone środowisko. Aby uzyskać więcej informacji, zobacz [Wybieranie środowiska dla projektu](selecting-a-python-environment-for-a-project.md).

Po prawej stronie każdego wymienionego środowiska znajduje się formant, który otwiera **okno interaktywne** dla tego środowiska. (W programie Visual Studio 2017 15.5 i wcześniejszych pojawia się inny formant, który odświeża bazę danych IntelliSense dla tego środowiska. Zobacz [okna środowiska, aby uzyskać szczegółowe](python-environments-window-tab-reference.md) informacje na temat bazy danych.)

::: moniker range="vs-2017"
> [!Tip]
> Po rozwinięciu okna **środowiska Języka Python** wystarczająco szeroki, otrzymasz pełniejszy widok środowisk, które mogą okazać się bardziej wygodne do pracy.
>
> ![Widok rozwinięty okna środowiska języka Python](media/environments/environments-expanded-view.png)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Tip]
> Po rozwinięciu okna **środowiska Języka Python** wystarczająco szeroki, otrzymasz pełniejszy widok środowisk, które mogą okazać się bardziej wygodne do pracy.
>
> ![Widok rozwinięty okna środowiska języka Python](media/environments/environments-expanded-view-2019.png)
::: moniker-end

> [!Note]
> Mimo że visual studio szanuje opcję pakietów lokacji systemu, nie zapewnia sposobu, aby zmienić go z poziomu programu Visual Studio.

### <a name="what-if-no-environments-appear"></a>Co zrobić, jeśli nie pojawiają się żadne środowiska?

Jeśli nie są wyświetlane żadne środowiska, oznacza to, że program Visual Studio nie może wykryć żadnych instalacji języka Python w standardowych lokalizacjach. Na przykład być może zainstalowano program Visual Studio 2017 lub nowszy, ale wyczyściłeś wszystkie opcje interpretera w opcjach instalatora dla obciążenia języka Python. Podobnie być może zainstalowano program Visual Studio 2015 lub wcześniej, ale nie zainstalowano interpretera ręcznie (zobacz [Instalowanie interpreterów języka Python](installing-python-interpreters.md)).

Jeśli wiesz, że masz interpreter języka Python na komputerze, ale Visual Studio (dowolna wersja) nie wykrył go, a następnie użyj **+ Niestandardowe** polecenia, aby określić jego lokalizację ręcznie. Zobacz następną sekcję [Ręcznie identyfikować istniejące środowisko](#manually-identify-an-existing-environment).

> [!Tip]
> Program Visual Studio wykrywa aktualizacje istniejącego interpretera, takie jak uaktualnianie języka Python 2.7.11 do 2.7.14 przy użyciu instalatorów z python.org. Podczas procesu instalacji starsze środowisko znika z listy **Środowiska języka Python,** zanim aktualizacja pojawi się w jego miejsce.
>
> Jeśli jednak ręcznie przeniesiesz interpreter i jego środowisko przy użyciu systemu plików, program Visual Studio nie będzie znał nowej lokalizacji. Aby uzyskać więcej informacji, zobacz [Przenoszenie tłumacza](installing-python-interpreters.md#move-an-interpreter).

### <a name="types-of-environments"></a>Rodzaje środowisk

Visual Studio może pracować ze środowiskami globalnymi, wirtualnymi i conda.

#### <a name="global-environments"></a>Środowiska globalne

Każda instalacja Języka Python (na przykład Python 2.7, Python 3.6, Python 3.7, Anaconda 4.4.0 itp., zobacz [Zainstaluj tłumaczy Pythona)](installing-python-interpreters.md)utrzymuje własne *globalne środowisko*. Każde środowisko składa się z określonego interpretera języka Python, jego standardowej biblioteki, zestawu wstępnie zainstalowanych pakietów i wszelkich dodatkowych pakietów instalowanych podczas aktywacji tego środowiska. Zainstalowanie pakietu w środowisku globalnym udostępnia go wszystkim projektom korzystającym z tego środowiska. Jeśli środowisko znajduje się w chronionym obszarze systemu plików (na przykład w *plikach c:\program),* instalacja pakietów wymaga uprawnień administratora.

Środowiska globalne są dostępne dla wszystkich projektów na komputerze. W programie Visual Studio wybierz jedno środowisko globalne jako domyślne, które jest używane dla wszystkich projektów, chyba że specjalnie wybierzesz inny dla projektu. Aby uzyskać więcej informacji, zobacz [Wybieranie środowiska dla projektu](selecting-a-python-environment-for-a-project.md).

#### <a name="virtual-environments"></a>Środowiska wirtualne

Chociaż praca w środowisku globalnym jest łatwym sposobem na rozpoczęcie pracy, to środowisko to z czasem stanie się zaśmiecone wieloma różnymi pakietami zainstalowanymi dla różnych projektów. Taki bałagan utrudnia dokładne przetestowanie aplikacji względem określonego zestawu pakietów ze znanymi wersjami, które jest dokładnie tym, które jest środowiskiem skonfigurowanym na serwerze kompilacji lub serwerze sieci web. Konflikty mogą również wystąpić, gdy dwa projekty wymagają niezgodnych pakietów lub różnych wersji tego samego pakietu.

Z tego powodu deweloperzy często tworzą *środowisko wirtualne* dla projektu. Środowisko wirtualne jest podfolderem w projekcie, który zawiera kopię określonego interpretera. Po aktywowaniu środowiska wirtualnego wszystkie instalowane pakiety są instalowane tylko w podfolderze tego środowiska. Po uruchomieniu programu Python w tym środowisku, wiesz, że jest uruchomiony tylko z tych określonych pakietów.

Visual Studio zapewnia bezpośrednie wsparcie dla tworzenia środowiska wirtualnego dla projektu. Na przykład po otwarciu projektu, który zawiera *requirements.txt*lub utworzyć projekt z szablonu, który zawiera ten plik, Visual Studio monituje o automatyczne utworzenie środowiska wirtualnego i zainstalowanie tych zależności.

W dowolnym momencie w ramach otwartego projektu można utworzyć nowe środowisko wirtualne. W **Eksploratorze rozwiązań**rozwiń węzeł projektu, kliknij prawym przyciskiem myszy **pozycję Środowiska języka Python**i wybierz polecenie "Dodaj środowisko wirtualne". Aby uzyskać więcej informacji, zobacz [Tworzenie środowiska wirtualnego](/visualstudio/python/selecting-a-python-environment-for-a-project?view=vs-2019#create-a-virtual-environment-1).

Program Visual Studio udostępnia również polecenie generowania pliku *requirements.txt* ze środowiska wirtualnego, co ułatwia ponowne tworzenie środowiska na innych komputerach. Aby uzyskać więcej informacji, zobacz [Używanie środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

#### <a name="conda-environments"></a>Środowiska Conda

Środowisko conda jest środowiskiem `conda` utworzonym przy użyciu narzędzia lub ze zintegrowanym zarządzaniem conda w programie Visual Studio 2017 w wersji 15.7 lub nowszej. (Wymaga Anaconda lub Miniconda, które są dostępne za pośrednictwem instalatora programu Visual Studio, zobacz [Instalacja](installing-python-support-in-visual-studio.md#visual-studio-2019-and-visual-studio-2017).)

::: moniker range="vs-2017"

1. Wybierz **+ Utwórz środowisko conda** w oknie **Środowiska Języka Python,** które otwiera kartę **Utwórz nowe środowisko conda:**

    ![Tworzenie karty dla nowego środowiska conda](media/environments/environments-conda-1.png)

1. Wprowadź nazwę środowiska w polu **Nazwa,** wybierz podstawowy interpreter języka Python w polu **Python** i wybierz pozycję **Utwórz**.

1. Okno **Dane wyjściowe** pokazuje postęp dla nowego środowiska, z kilkoma instrukcjami interfejsu wiersza polecenia po zakończeniu tworzenia:

    ![Udane stworzenie środowiska conda](media/environments/environments-conda-2.png)

1. W programie Visual Studio można aktywować środowisko conda dla projektu, tak jak w każdym innym środowisku opisanym w [programie Wybierz środowisko dla projektu.](selecting-a-python-environment-for-a-project.md)

1. Aby zainstalować pakiety w środowisku, użyj [karty Pakiety](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

::: moniker range=">=vs-2019"

1. Wybierz **+ Dodaj środowisko** w oknie Środowiska języka **Python** (lub z paska narzędzi Python), który otwiera okno dialogowe **Dodawanie środowiska.** W tym oknie dialogowym wybierz kartę **Środowisko Conda:**

    ![Karta Środowisko Conda w oknie dialogowym Dodawanie środowiska](media/environments/environments-conda-1-2019.png)

1. Skonfiguruj następujące pola:

    | Pole | Opis |
    | --- | --- |
    | Project | Projekt, w którym można utworzyć środowisko (jeśli masz wiele projektów w tym samym rozwiązaniu programu Visual Studio). |
    | Nazwa | Nazwa środowiska conda. |
    | Dodawanie pakietów z | Wybierz **plik środowiska,** jeśli masz plik *environment.yml* opisujący zależności lub wybierz **jedną lub więcej nazw pakietów Anaconda** i wyświetl co najmniej jeden pakiet Języka Python lub wersję języka Python w polu poniżej. Lista pakietów nakazuje conda utworzyć środowisko Języka Python. Aby zainstalować najnowszą wersję `python`Pythona, użyj ; , aby zainstalować określoną wersję, użyj `python=,major>.<minor>` jak w `python=3.7`. Można również użyć przycisku pakietu, aby wybrać wersje Pythona i typowe pakiety z serii menu. |
    | Ustaw jako bieżące środowisko | Aktywuje nowe środowisko w wybranym projekcie po utworzeniu środowiska. |
    | Ustawienie jako środowiska domyślnego dla nowych projektów | Automatycznie ustawia i aktywuje środowisko conda w nowych projektach utworzonych w programie Visual Studio. Ta opcja jest taka sama jak przy użyciu **Make this domyślne środowisko dla nowych projektów** w środowisku **Pythona** okna. |
    | Wyświetl w oknie Środowiska Języka Python | Określa, czy po utworzeniu środowiska ma być wyświetlane okno **Środowiska języka Python.** |

    > [!Important]
    > Podczas tworzenia środowiska conda, należy określić co najmniej jedną wersję `environments.yml` języka Python lub pakiet Python przy użyciu albo lub listy pakietów, która zapewnia, że środowisko zawiera środowisko wykonawcze Języka Python. W przeciwnym razie visual studio ignoruje środowisko: środowisko nie pojawia się w dowolnym miejscu okna **środowiska Języka Python,** nie jest ustawiony jako bieżące środowisko dla projektu i nie jest dostępne jako środowisko globalne.
    >
    > Jeśli zdarzy ci się utworzyć środowisko conda `conda info` bez wersji języka Python, użyj polecenia, aby wyświetlić lokalizacje folderów środowiska conda, a następnie ręcznie usuń podfolder dla środowiska z tej lokalizacji.

1. Wybierz **opcję Utwórz**i obserwuj postęp w oknie **Dane wyjściowe.** Dane wyjściowe zawierają kilka instrukcji interfejsu wiersza polecenia po zakończeniu tworzenia:

    ![Udane stworzenie środowiska conda](media/environments/environments-conda-2-2019.png)

1. W programie Visual Studio można aktywować środowisko conda dla projektu, tak jak w każdym innym środowisku opisanym w [programie Wybierz środowisko dla projektu.](selecting-a-python-environment-for-a-project.md)

1. Aby zainstalować dodatkowe pakiety w środowisku, użyj [karty Pakiety](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

> [!Note]
> Aby uzyskać najlepsze wyniki w środowiskach conda, należy użyć conda 4.4.8 lub nowszej (wersje conda różnią się od wersji Anaconda). Za pomocą instalatora programu Visual Studio można zainstalować odpowiednie wersje programu Miniconda (Visual Studio 2019) i Anaconda (Visual Studio 2017).

Aby wyświetlić wersję conda, w której przechowywane są środowiska `conda info` conda i inne informacje, uruchom w wierszu polecenia Anaconda (czyli wierszu polecenia, w którym anakonda znajduje się w ścieżce):

```cli
conda info
```

Foldery środowiska conda są wyświetlane w następujący sposób:

```output
       envs directories : C:\Users\user\.conda\envs
                          c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
```

Ponieważ środowiska conda nie są przechowywane w projekcie, działają podobnie do środowisk globalnych. Na przykład zainstalowanie nowego pakietu w środowisku conda udostępnia ten pakiet wszystkim projektom korzystającym z tego środowiska.

W programie Visual Studio 2017 w wersji 15.6 lub starszej można użyć środowisk conda, wskazując je ręcznie, zgodnie z opisem w [obszarze Ręcznie identyfikować istniejące środowisko](#manually-identify-an-existing-environment).

Visual Studio 2017 w wersji 15.7 i nowszych wykrywa środowiska conda automatycznie i wyświetla je w oknie **Środowiska języka Python,** jak opisano w następnej sekcji.

## <a name="manually-identify-an-existing-environment"></a>Ręczne identyfikowanie istniejącego środowiska

Poniższe kroki można wykonać, aby zidentyfikować środowisko zainstalowane w niestandardowej lokalizacji (w tym środowiska conda w programie Visual Studio 2017 w wersji 15.6 lub starszej):

::: moniker range="vs-2017"

1. Wybierz **+ Niestandardowe** w oknie **Środowiska Języka Python,** które otwiera kartę **Konfiguruj:**

    ![Widok domyślny dla nowego środowiska niestandardowego](media/environments/environments-custom-1.png)

1. Wprowadź nazwę środowiska w polu **Opis.**

1. Umożliwia wprowadzanie lub przeglądanie (za pomocą **...**) ścieżki interpretera w polu **Ścieżka prefiksu.**

1. Jeśli program Visual Studio wykryje interpretera języka Python w tej lokalizacji (na przykład ścieżkę pokazaną poniżej dla środowiska conda), włącza polecenie **Auto Detect.** Wybranie **opcji Automatyczne wykrywanie** powoduje zakończenie pozostałych pól. Pola te można również wypełnić ręcznie.

    ![Włączanie polecenia Automatyczne wykrywanie](media/environments/environments-custom-2.png)

    ![Uzupełnianie pól środowiska po użyciu automatycznego wykrywania](media/environments/environments-custom-3.png)

1. Gdy pola zawierają żądane wartości, wybierz pozycję **Zastosuj,** aby zapisać konfigurację. Teraz można używać środowiska, jak każdy inny w programie Visual Studio.

1. Jeśli chcesz usunąć ręcznie zidentyfikowane środowisko, wybierz polecenie **Usuń** na karcie **Konfiguruj.** Aby uzyskać więcej informacji, zobacz [konfigurowanie karty](python-environments-window-tab-reference.md#configure-tab).

::: moniker-end

::: moniker range=">=vs-2019"

1. Wybierz **+ Dodaj środowisko** w oknie Środowiska języka **Python** (lub z paska narzędzi Python), który otwiera okno dialogowe **Dodawanie środowiska.** W tym oknie dialogowym wybierz kartę **Istniejące środowisko:**

    ![Karta Istniejące środowisko w oknie dialogowym Dodawanie środowiska](media/environments/environments-custom-1-2019.png)

1. Wybierz pozycję rozwijaną **Środowisko,** a następnie wybierz pozycję **Niestandardowe:**

    ![Opcja Środowisko niestandardowe w oknie dialogowym Dodawanie środowiska](media/environments/environments-custom-2-2019.png)

1. W podanych polach w oknie dialogowym wprowadź lub przejrzyj (używając **...**) ścieżkę interpretera w **obszarze Ścieżka prefiksu**, która wypełnia większość innych pól. Po przejrzeniu tych wartości i zmodyfikowaniu w razie potrzeby wybierz pozycję **Dodaj**. 

    ![Pola do określania szczegółów opcji środowiska niestandardowego w oknie dialogowym Dodawanie środowiska](media/environments/environments-custom-3-2019.png)

1. Szczegóły środowiska można przejrzeć i zmodyfikować w dowolnym **momencie** w oknie Środowiska Pythona. W tym oknie wybierz środowisko, a następnie wybierz kartę **Konfiguruj.** Po wszłoniu zmian wybierz polecenie **Zastosuj.** Środowisko można również usunąć za pomocą polecenia **Usuń** (niedostępne dla środowisk wykrywanych automatycznie). Aby uzyskać więcej informacji, zobacz [konfigurowanie karty](python-environments-window-tab-reference.md#configure-tab).
::: moniker-end

## <a name="fix-or-delete-invalid-environments"></a>Naprawianie lub usuwanie nieprawidłowych środowisk

Jeśli program Visual Studio znajdzie wpisy rejestru dla środowiska, ale ścieżka do interpretera jest nieprawidłowa, wówczas okno **Środowiska języka Python** wyświetla nazwę z czcionką przekreśloną:

::: moniker range="vs-2017"
![Okno Środowiska języka Python z nieprawidłowym środowiskiem](media/environments/environments-invalid-entry.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Okno Środowiska języka Python z nieprawidłowym środowiskiem](media/environments/environments-invalid-entry-2019.png)
::: moniker-end

Aby poprawić środowisko, które chcesz zachować, najpierw spróbuj użyć procesu **naprawy** instalatora. Instalatorzy dla standardowego Pythona 3.x, na przykład, obejmują tę opcję.

Aby poprawić środowisko, które nie ma opcji naprawy lub usunąć nieprawidłowe środowisko, należy wykonać następujące kroki, aby bezpośrednio zmodyfikować rejestr. Program Visual Studio automatycznie **aktualizuje** okno Środowiska języka Python po wprowadzeniu zmian w rejestrze.

1. Uruchom *plik regedit.exe*.
1. Przejdź do **HKEY_LOCAL_MACHINE\SOFTWARE\Python**. Dla IronPython, poszukaj **IronPython** zamiast.
1. Rozwiń węzeł, który pasuje do dystrybucji, takich jak **Python Core** dla CPython lub **ContinuumAnalytics** dla Anakondy. W przypadku ironpython rozwiń węzeł numeru wersji.
1. Sprawdź wartości w węźle **InstallPath:**

    ![Wpisy rejestru dla typowej instalacji CPython](media/environments/environments-registry-entries.png)

    - Jeśli środowisko nadal istnieje na komputerze, zmień wartość **Programu ExecutablePath** na właściwą lokalizację. W razie potrzeby popraw również wartości **(Domyślne)** i **WindowedExecutablePath.**
    - Jeśli środowisko nie istnieje już na komputerze i chcesz usunąć je z okna **Środowiska języka Python,** usuń węzeł nadrzędny **InstallPath**, taki jak **3.6** na powyższej ilustracji.

## <a name="see-also"></a>Zobacz też

- [Instalowanie interpreterów języka Python](installing-python-interpreters.md)
- [Wybieranie interpretera dla projektu](selecting-a-python-environment-for-a-project.md)
- [Używanie pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Odwołanie do okna Środowiska języka Python](python-environments-window-tab-reference.md)
