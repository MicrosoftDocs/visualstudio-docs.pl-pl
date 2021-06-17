---
title: Zarządzanie interpreterami i środowiskami języka Python
description: Okno Środowiska języka Python służy do zarządzania środowiskami globalnymi, wirtualnymi i conda, instalowania interpreterów i pakietów języka Python oraz przypisywania środowisk do Visual Studio projektów.
ms.date: 08/06/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- python
- data-science
ms.openlocfilehash: 26bcf0fa4d56d4e8df100a0d3e65904d065d8757
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254878"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Jak tworzyć środowiska języka Python i zarządzać nimi w Visual Studio

Środowisko **języka Python** to kontekst, w którym uruchamiasz kod języka Python i obejmuje środowiska globalne, wirtualne i conda. Środowisko składa się z interpretera, biblioteki (zazwyczaj standardowej biblioteki języka Python) i zestawu zainstalowanych pakietów. Te składniki razem określają, które konstrukcje języka i składnia są prawidłowe, jakie funkcje systemu operacyjnego można uzyskać dostęp i których pakietów można użyć.

W Visual Studio w systemie Windows użyj okna Środowiska **języka Python,** zgodnie z opisem w tym artykule, aby zarządzać środowiskami i wybrać je jako domyślne dla nowych projektów. Inne aspekty środowisk można znaleźć w następujących artykułach:

- Dla każdego projektu można wybrać [określone środowisko, zamiast](selecting-a-python-environment-for-a-project.md) używać domyślnego.

- Aby uzyskać szczegółowe informacje na temat tworzenia i używania środowisk wirtualnych dla projektów języka Python, [zobacz Korzystanie ze środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Jeśli chcesz zainstalować pakiety w środowisku, zapoznaj się z [kartą Pakiety](python-environments-window-tab-reference.md#packages-tab).

- Aby zainstalować inny interpreter języka Python, zobacz [Instalowanie interpreterów języka Python.](installing-python-interpreters.md) Ogólnie rzecz biorąc, po pobraniu i uruchomieniu instalatora dla głównej dystrybucji języka Python program Visual Studio wykryje, że nowa instalacja i środowisko są wyświetlane w oknie Środowiska **języka Python** i można je wybrać dla projektów.

Jeśli jesteś nowym użytkownikiem języka Python w języku Visual Studio, następujące artykuły zawierają również ogólne informacje:

- [Praca z językiem Python w programie Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Instalowanie obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md)

::: moniker range="vs-2017"
> [!Note]
> Nie można zarządzać środowiskami dla kodu w języku Python, który jest otwierany tylko jako folder, za pomocą polecenia **Otwórz**  >    >  **folder** pliku. Zamiast tego [utwórz projekt języka Python na pomocą istniejącego kodu,](quickstart-01-python-in-visual-studio-project-from-existing-code.md) aby korzystać z funkcji środowiska Visual Studio.
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> Możesz zarządzać środowiskami dla kodu w języku Python, który jest otwierany jako folder, za pomocą **polecenia Otwórz**  >    >  **folder** pliku. Pasek narzędzi języka Python umożliwia przełączanie się między wszystkimi wykrytymi środowiskami, a także dodawanie nowego środowiska. Informacje o środowisku są przechowywane w PythonSettings.jsw pliku w folderze .vs obszaru roboczego.
::: moniker-end

## <a name="the-python-environments-window"></a>Okno Środowiska Python

Środowiska, które Visual Studio, są wyświetlane w oknie **Środowiska języka** Python. Aby otworzyć okno, użyj jednej z następujących metod:

- Wybierz polecenie **menu View** Other Windows Python Environments (Wyświetl inne  >    >  **środowiska Windows Python).**
- Kliknij prawym przyciskiem myszy węzeł **Środowiska Python** dla projektu w programie **Eksplorator rozwiązań** wybierz pozycję Wyświetl wszystkie **środowiska Python:**

    ::: moniker range="vs-2017"
    ![Polecenie Wyświetl wszystkie środowiska w Eksplorator rozwiązań](media/environments/environments-view-all.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Polecenie Wyświetl wszystkie środowiska w Eksplorator rozwiązań](media/environments/environments-view-all-2019.png)
    ::: moniker-end

W obu przypadkach obok okna **Środowiska języka Python** jest wyświetlane **Eksplorator rozwiązań**:

::: moniker range="vs-2017"
![Okno Środowiska Python](media/environments/environments-default-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Okno Środowiska Python](media/environments/environments-default-view-2019.png)
::: moniker-end

Visual Studio wyszukuje zainstalowane środowiska globalne przy użyciu rejestru (zgodnie z pep [514](https://www.python.org/dev/peps/pep-0514/)) wraz ze środowiskami wirtualnymi i środowiskami Conda (zobacz [Typy środowisk).](#types-of-environments) Jeśli nie widzisz oczekiwanego środowiska na liście, zobacz [Ręczne identyfikowanie istniejącego środowiska.](#manually-identify-an-existing-environment)

Po wybraniu środowiska na liście program Visual Studio różne właściwości i polecenia dla tego środowiska na **karcie Przegląd.** Na przykład na powyższej ilustracji widać, że lokalizacja interpretera to *C:\Python36-32*. Cztery polecenia w dolnej części karty **Przegląd** otwierają wiersz polecenia z uruchomionym interpreterem. Aby uzyskać więcej informacji, zobacz informacje na karcie [okna Środowiska Python — omówienie](python-environments-window-tab-reference.md#overview-tab).

Użyj listy rozwijanej poniżej listy środowisk, aby przełączyć się na różne karty, takie jak **Pakiety** i **IntelliSense.** Te karty są również opisane w sekcji referencyjnej na karcie [Środowiska języka Python](python-environments-window-tab-reference.md)na karcie .

Wybranie środowiska nie zmienia jego relacji z żadnymi projektami. Domyślne środowisko, wyświetlane pogrubioną czcionką na liście, jest środowiskiem, które Visual Studio dla nowych projektów. Aby użyć innego środowiska z nowymi projektami, użyj polecenia Przywłasz to **środowisko domyślne dla nowych** projektów. W kontekście projektu zawsze możesz wybrać określone środowisko. Aby uzyskać więcej informacji, [zobacz Select an environment for a project (Wybieranie środowiska dla projektu).](selecting-a-python-environment-for-a-project.md)

Po prawej stronie każdego wymienionego środowiska znajduje się kontrolka, która otwiera **okno** interaktywne dla tego środowiska. (W Visual Studio 2017 15.5 i starszych zostanie wyświetlona inna kontrolka, która odświeża bazę danych IntelliSense dla tego środowiska. Aby [uzyskać szczegółowe informacje](python-environments-window-tab-reference.md) o bazie danych, zobacz Informacje o karcie okna środowiska).

::: moniker range="vs-2017"
> [!Tip]
> Po rozwinięciu okna **Środowiska języka Python** wystarczająco szerokiego można uzyskać pełniejsze widoki środowisk, z których praca może być wygodniejsza.
>
> ![Rozwinięty widok okna Środowiska Python](media/environments/environments-expanded-view.png)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Tip]
> Po rozwinięciu okna **Środowiska języka Python** wystarczająco szerokiego można uzyskać pełniejsze widoki środowisk, z których praca może być wygodniejsza.
>
> ![Rozwinięty widok okna Środowiska Python](media/environments/environments-expanded-view-2019.png)
::: moniker-end

> [!Note]
> Chociaż Visual Studio z opcją system-site-packages, nie umożliwia zmiany jej z poziomu Visual Studio.

### <a name="what-if-no-environments-appear"></a>Co zrobić, jeśli środowiska nie są wyświetlane?

Jeśli środowiska nie są wyświetlane, oznacza Visual Studio nie można wykryć instalacji języka Python w standardowych lokalizacjach. Na przykład być może zainstalowano program Visual Studio 2017 lub nowszy, ale wyczyszczysz wszystkie opcje interpretera w opcjach instalatora dla obciążenia języka Python. Analogicznie, być może zainstalowano system Visual Studio 2015 lub wcześniej, ale nie zainstalowano interpretera ręcznie (zobacz [Instalowanie interpreterów języka Python).](installing-python-interpreters.md)

Jeśli wiesz, że masz interpreter języka Python na komputerze, ale Visual Studio (w dowolnej wersji) go nie wykrył, użyj polecenia **+ Niestandardowy,** aby ręcznie określić jego lokalizację. Zobacz następną sekcję Ręcznie [zidentyfikuj istniejące środowisko](#manually-identify-an-existing-environment).

> [!Tip]
> Visual Studio wykrywa aktualizacje istniejącego interpretera, takie jak uaktualnienie środowiska Python 2.7.11 do wersji 2.7.14 przy użyciu instalatorów z python.org. Podczas procesu instalacji starsze środowisko znika z listy środowisk **Python,** zanim aktualizacja pojawi się w jego miejscu.
>
> Jeśli jednak ręcznie przeniesiesz interpreter i jego środowisko przy użyciu systemu plików, Visual Studio nie będzie znał nowej lokalizacji. Aby uzyskać więcej informacji, zobacz [Przenoszenie interpretera](installing-python-interpreters.md#move-an-interpreter).

### <a name="types-of-environments"></a>Typy środowisk

Visual Studio może współpracować ze środowiskami globalnymi, wirtualnymi i conda.

#### <a name="global-environments"></a>Środowiska globalne

Każda instalacja języka Python (na przykład Python 2.7, Python 3.6, Python 3.7, Anaconda 4.4.0 itp., zobacz Instalowanie [interpreterów języka Python](installing-python-interpreters.md)) utrzymuje własne *środowisko* globalne . Każde środowisko składa się z określonego interpretera języka Python, jego biblioteki standardowej, zestawu wstępnie zainstalowanych pakietów i wszelkich dodatkowych pakietów instalowanych podczas aktywowania tego środowiska. Zainstalowanie pakietu w środowisku globalnym powoduje, że jest on dostępny dla wszystkich projektów korzystających z tego środowiska. Jeśli środowisko znajduje się w chronionym obszarze systemu plików (na przykład w plikach *c:\program),* instalowanie pakietów wymaga uprawnień administratora.

Środowiska globalne są dostępne dla wszystkich projektów na komputerze. W Visual Studio należy wybrać jedno środowisko globalne jako domyślne, które jest używane dla wszystkich projektów, chyba że zostanie wybrane inne dla projektu. Aby uzyskać więcej informacji, [zobacz Select an environment for a project (Wybieranie środowiska dla projektu).](selecting-a-python-environment-for-a-project.md)

#### <a name="virtual-environments"></a>Środowiska wirtualne

Mimo że praca w środowisku globalnym jest łatwym sposobem rozpoczęcia pracy, to środowisko z czasem stanie się zaśmiecone wieloma różnymi pakietami zainstalowanymi dla różnych projektów. Taki nieład utrudnia dokładne przetestowanie aplikacji pod względem określonego zestawu pakietów o znanych wersjach, czyli dokładnie rodzaju środowiska, które należy skonfigurować na serwerze kompilacji lub serwerze sieci Web. Konflikty mogą również wystąpić, gdy dwa projekty wymagają niezgodnych pakietów lub różnych wersji tego samego pakietu.

Z tego powodu deweloperzy często tworzą środowisko *wirtualne* dla projektu. Środowisko wirtualne to podfolder w projekcie, który zawiera kopię określonego interpretera. Po aktywowaniu środowiska wirtualnego wszystkie instalowane pakiety są instalowane tylko w podfolderze tego środowiska. Po uruchomieniu programu w języku Python w tym środowisku wiadomo, że jest on uruchamiany tylko dla tych określonych pakietów.

Visual Studio zapewnia bezpośrednią obsługę tworzenia środowiska wirtualnego dla projektu. Jeśli na przykład otworzysz projekt zawierający plik *requirements.txt* lub utworzysz projekt na podstawie szablonu zawierającego ten plik, program Visual Studio wyświetli monit o automatyczne utworzenie środowiska wirtualnego i zainstalowanie tych zależności.

W dowolnym momencie w ramach otwartego projektu można utworzyć nowe środowisko wirtualne. W **Eksplorator rozwiązań** rozwiń węzeł projektu, kliknij prawym przyciskiem myszy pozycję Środowiska **języka Python** i wybierz pozycję "Dodaj środowisko wirtualne". Aby uzyskać więcej informacji, zobacz [Tworzenie środowiska wirtualnego.](./selecting-a-python-environment-for-a-project.md?view=vs-2019&preserve-view=true#create-a-virtual-environment-1)

Visual Studio udostępnia również polecenie generowania pliku *requirements.txt* ze środowiska wirtualnego, co ułatwia ponowne utworzenie środowiska na innych komputerach. Aby uzyskać więcej informacji, zobacz [Korzystanie ze środowisk wirtualnych.](selecting-a-python-environment-for-a-project.md#use-virtual-environments)

#### <a name="conda-environments"></a>Środowiska Conda

Środowisko conda to środowisko utworzone przy użyciu narzędzia lub zintegrowane zarządzanie środowiskiem Conda w `conda` programie Visual Studio 2017 w wersji 15.7 lub wyższej. (Wymaga programu Anaconda lub Miniconda, które są dostępne za pośrednictwem instalatora Visual Studio, zobacz [Instalacja).](installing-python-support-in-visual-studio.md#visual-studio-2019-and-visual-studio-2017)

::: moniker range="vs-2017"

1. Wybierz **pozycję + Utwórz środowisko conda w** oknie Środowiska Języka **Python,** co spowoduje otwarcie karty Utwórz nowe środowisko **conda:**

    ![Karta Tworzenie dla nowego środowiska Conda](media/environments/environments-conda-1.png)

1. Wprowadź nazwę środowiska w polu **Nazwa,** wybierz podstawowy interpreter języka Python w polu **Python,** a następnie wybierz pozycję **Utwórz**.

1. W **oknie** Dane wyjściowe jest wyświetlany postęp dla nowego środowiska z kilkoma instrukcjami interfejsu wiersza polecenia po zakończeniu tworzenia:

    ![Pomyślne utworzenie środowiska conda](media/environments/environments-conda-2.png)

1. W Visual Studio można aktywować środowisko conda dla projektu tak samo jak każde inne środowisko, zgodnie z opisem w tece Select an environment for a project (Wybieranie środowiska [dla projektu).](selecting-a-python-environment-for-a-project.md)

1. Aby zainstalować pakiety w środowisku, użyj [karty Pakiety](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

::: moniker range=">=vs-2019"

1. Wybierz **pozycję Dodaj środowisko...** w oknie **Środowiska języka Python** (lub na pasku narzędzi języka Python), co spowoduje otwarcie **okna dialogowego** Dodawanie środowiska. W tym oknie dialogowym wybierz **kartę Środowisko Conda:**

    ![Karta środowiska Conda w oknie dialogowym Dodawanie środowiska](media/environments/environments-conda-1-2019.png)

1. Skonfiguruj następujące pola:

    | Pole | Opis |
    | --- | --- |
    | Project | Projekt, w którym należy utworzyć środowisko (jeśli masz wiele projektów w tym samym Visual Studio rozwiązania). |
    | Nazwa | Nazwa środowiska conda. |
    | Dodawanie pakietów z | Wybierz **pozycję** Plik środowiska, jeśli masz plik *environment.yml* opisujący zależności, lub wybierz co najmniej jedną nazwę pakietu **Anaconda** i w poniższym polu wybierz co najmniej jeden pakiet języka Python lub wersję języka Python. Lista pakietów nakazuje środowisku conda utworzenie środowiska Python. Aby zainstalować najnowszą wersję języka Python, użyj programu , aby `python` zainstalować określoną wersję, użyj `python=,major>.<minor>` programu jako w pliku `python=3.7` . Możesz również użyć przycisku pakietu, aby wybrać wersje języka Python i typowe pakiety z serii menu. |
    | Ustaw jako bieżące środowisko | Aktywuje nowe środowisko w wybranym projekcie po jego utworzeniu. |
    | Ustaw jako środowisko domyślne dla nowych projektów | Automatycznie ustawia i aktywuje środowisko conda we wszystkich nowych projektach utworzonych w programie Visual Studio. Ta opcja jest taka sama jak w przypadku korzystania z okna Przywłasz domyślne środowisko dla nowych **projektów** w **środowiskach** Python. |
    | Okno Widok w środowiskach Python | Określa, czy okno środowiska  **Python ma** być wyświetlane po utworzeniu środowiska. |

    > [!Important]
    > Podczas tworzenia środowiska conda należy określić co najmniej jedną wersję języka Python lub pakiet języka Python przy użyciu jednej z list pakietów, co gwarantuje, że środowisko zawiera `environments.yml` środowisko uruchomieniowe języka Python. W przeciwnym razie Visual Studio środowisko: środowisko nie jest wyświetlane w oknie Środowiska **języka Python,** nie jest ustawione jako bieżące środowisko dla projektu i nie jest dostępne jako środowisko globalne.
    >
    > Jeśli utworzysz środowisko conda bez wersji języka Python, użyj polecenia , aby wyświetlić lokalizacje folderów środowiska Conda, a następnie ręcznie usuń podfolder środowiska z tej `conda info` lokalizacji.

1. Wybierz **pozycję Utwórz** i obserwuj postęp w **oknie Dane** wyjściowe. Dane wyjściowe zawierają kilka instrukcji interfejsu wiersza polecenia po zakończeniu tworzenia:

    ![Pomyślne utworzenie środowiska Conda](media/environments/environments-conda-2-2019.png)

1. W Visual Studio można aktywować środowisko conda dla projektu tak samo jak w przypadku każdego innego środowiska, zgodnie z opisem w tece Select an environment for a project (Wybieranie środowiska [dla projektu).](selecting-a-python-environment-for-a-project.md)

1. Aby zainstalować dodatkowe pakiety w środowisku, użyj [karty Pakiety](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

> [!Note]
> Aby uzyskać najlepsze wyniki w środowiskach Conda, użyj środowiska conda 4.4.8 lub nowszego (wersje conda różnią się od wersji anaconda). Odpowiednie wersje programu Miniconda (Visual Studio 2019) i Anaconda (Visual Studio 2017) można zainstalować za pomocą Visual Studio instalatora.

Aby wyświetlić wersję środowiska conda, w której są przechowywane środowiska conda i inne informacje, uruchom polecenie w wierszu polecenia środowiska Anaconda (czyli wierszu polecenia, w którym znajduje się środowisko `conda info` Anaconda w ścieżce):

```cli
conda info
```

Foldery środowiska conda są wyświetlane w następujący sposób:

```output
       envs directories : C:\Users\user\.conda\envs
                          c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
```

Ponieważ środowiska conda nie są przechowywane w projekcie, działają podobnie do środowisk globalnych. Na przykład zainstalowanie nowego pakietu w środowisku conda sprawia, że pakiet jest dostępny dla wszystkich projektów korzystających z tego środowiska.

W Visual Studio 2017 r. w wersji 15.6 lub starszej można użyć środowisk Conda, wskaż je ręcznie, zgodnie z opisem w tece Ręczne identyfikowanie istniejącego [środowiska.](#manually-identify-an-existing-environment)

Visual Studio 2017 w wersji 15.7 lub nowszej automatycznie wykrywa środowiska conda i wyświetla je w oknie Środowiska **Języka Python** zgodnie z opisem w następnej sekcji.

## <a name="manually-identify-an-existing-environment"></a>Ręczne identyfikowanie istniejącego środowiska

Aby zidentyfikować środowisko zainstalowane w lokalizacji niestandardowych (w tym środowiska conda w programie Visual Studio 2017 w wersji 15.6 i starszych), należy wykonać następujące kroki:

::: moniker range="vs-2017"

1. Wybierz **pozycję + Niestandardowe** w oknie Środowiska języka **Python,** co spowoduje otwarcie **karty Konfiguracja:**

    ![Widok domyślny dla nowego środowiska niestandardowego](media/environments/environments-custom-1.png)

1. Wprowadź nazwę środowiska w polu **Opis.**

1. Wprowadź lub przejdź (przy **użyciu ...**) do ścieżki interpretera w polu **Ścieżka prefiksu.**

1. Jeśli Visual Studio interpreter języka Python w tej lokalizacji (na przykład ścieżka pokazana poniżej dla środowiska Conda), włącza **polecenie Auto Detect (Wykrywanie** automatyczne). Wybranie **opcji Autowykrywaj** kończy pozostałe pola. Te pola można również wypełnić ręcznie.

    ![Włączanie polecenia autowykrywania](media/environments/environments-custom-2.png)

    ![Uzupełnianie pól środowiska po użyciu funkcji automatycznego wykrywania](media/environments/environments-custom-3.png)

1. Gdy pola zawierają odpowiednie wartości, wybierz pozycję **Zastosuj,** aby zapisać konfigurację. Teraz możesz używać środowiska w taki sposób, jak każdego innego Visual Studio.

1. Jeśli musisz usunąć ręcznie zidentyfikowane środowisko, wybierz polecenie **Usuń** na **karcie Konfigurowanie.** W środowiskach wykrywanych automatycznie ta opcja nie jest dostępna. Aby uzyskać więcej informacji, zobacz [Konfigurowanie karty](python-environments-window-tab-reference.md#configure-tab).

::: moniker-end

::: moniker range=">=vs-2019"

1. Wybierz **pozycję Dodaj środowisko...** w **oknie Środowiska języka Python** (lub na pasku narzędzi języka Python), co spowoduje otwarcie okna **dialogowego** Dodawanie środowiska. W tym oknie dialogowym wybierz **kartę Istniejące** środowisko:

    ![Karta Istniejące środowisko w oknie dialogowym Dodawanie środowiska](media/environments/environments-custom-1-2019.png)

1. Wybierz menu **rozwijane Środowisko,** a następnie wybierz pozycję **Niestandardowe:**

    ![Opcja Środowisko niestandardowe w oknie dialogowym Dodawanie środowiska](media/environments/environments-custom-2-2019.png)

1. W polach podanych w oknie dialogowym wprowadź lub przejdź (przy użyciu ... **)** do ścieżki interpretera w obszarze Ścieżka prefiksu **,** która wypełnia większość innych pól. Po przejrzeniu tych wartości i zmodyfikowaniu ich w razie potrzeby wybierz pozycję **Dodaj**.

    ![Pola do określania szczegółów dla opcji środowiska niestandardowego w oknie dialogowym Dodawanie środowiska](media/environments/environments-custom-3-2019.png)

1. Szczegóły środowiska można przeglądać i modyfikować w dowolnym momencie w oknie **Środowiska Python.** W tym oknie wybierz środowisko, a następnie wybierz **kartę** Konfiguracja. Po w związku z wprowadzeniem zmian wybierz **polecenie** Zastosuj. Możesz również usunąć środowisko za pomocą polecenia **Usuń** (niedostępne dla środowisk wykrywanych automatycznie). Aby uzyskać więcej informacji, zobacz [Konfigurowanie karty](python-environments-window-tab-reference.md#configure-tab).
::: moniker-end

## <a name="fix-or-delete-invalid-environments"></a>Naprawianie lub usuwanie nieprawidłowych środowisk

Jeśli Visual Studio wpisy rejestru dla środowiska, ale ścieżka do interpretera jest nieprawidłowa, w oknie Środowiska języka **Python** zostanie pokazana nazwa z przekreśloną czcionką:

::: moniker range="vs-2017"
![Okno Środowiska Python z nieprawidłowym środowiskiem](media/environments/environments-invalid-entry.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Okno Środowiska Python z nieprawidłowym środowiskiem](media/environments/environments-invalid-entry-2019.png)
::: moniker-end

Aby poprawić środowisko, które chcesz zachować, najpierw spróbuj użyć procesu **naprawy** instalatora. Instalatory dla standardowego środowiska Python 3.x zawierają na przykład tę opcję.

Aby poprawić środowisko, które nie ma opcji naprawy lub usunąć nieprawidłowe środowisko, należy wykonać następujące kroki, aby bezpośrednio zmodyfikować rejestr. Visual Studio automatycznie aktualizuje okno **Środowiska języka Python** po wymusze zmian w rejestrze.

1. Uruchom *regedit.exe*.
1. Przejdź do **HKEY_LOCAL_MACHINE\SOFTWARE\Python** lub **HKEY_CURRENT_USER\SOFTWARE\Python**. W przypadku ironPython zamiast tego poszukaj **ironPython.**
1. Rozwiń węzeł, który pasuje do dystrybucji, taki jak **Python Core** for CPython lub **ContinuumAnalytics** for Anaconda. W przypadku aplikacji IronPython rozwiń węzeł numeru wersji.
1. Sprawdź wartości w **węźle InstallPath:**

    ![Wpisy rejestru dla typowej instalacji CPython](media/environments/environments-registry-entries.png)

    - Jeśli środowisko nadal istnieje na komputerze, zmień wartość właściwości **ExecutablePath** na poprawną lokalizację. Popraw również **wartości (Default)** i **WindowedExecutablePath** zgodnie z potrzebami.
    - Jeśli środowisko nie istnieje już na komputerze i chcesz je usunąć z okna Środowiska **języka Python,** usuń węzeł nadrzędny **installPath,** taki jak **3.6** na powyższej ilustracji.
    - Nieprawidłowe ustawienia w **HKEY_CURRENT_USER\SOFTWARE\Python** przesłaniają ustawienia w **HKEY_LOCAL_MACHINE\SOFTWARE\Python**

## <a name="see-also"></a>Zobacz też

- [Instalowanie interpreterów języka Python](installing-python-interpreters.md)
- [Wybieranie interpretera dla projektu](selecting-a-python-environment-for-a-project.md)
- [Używanie requirements.txt zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Informacje o oknach środowisk Python](python-environments-window-tab-reference.md)