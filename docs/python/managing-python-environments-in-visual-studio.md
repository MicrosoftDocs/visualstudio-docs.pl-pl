---
title: Zarządzanie środowiskami Python i tłumaczy
description: Użyj okna środowiska Python, aby zarządzać globalnym, wirtualnych i środowisk conda, instalowanie interpreterów języka Python i pakietów i przypisywanie środowisk do projektów programu Visual Studio.
ms.date: 08/06/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: d1826981f29ebfc29e7e5d28aa32fbff8c74ea5a
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69585391"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Jak utworzyć i zarządzać środowiskami Python w programie Visual Studio

Python *środowiska* jest kontekst, w którym uruchamianie kodu języka Python i obejmuje globalnego, wirtualnych i środowisk conda. Środowisko składa się z tłumacza, biblioteki (zwykle Biblioteka standardowa języka Python) i zestaw zainstalowanych pakietów. Te składniki określają ze sobą, które konstrukcji języka i składni są prawidłowe, jakiego systemu operacyjnego funkcji można uzyskać dostęp i które pakietów, możesz użyć.

W programie Visual Studio, Windows, możesz użyć **środowiska Python** okna, zgodnie z opisem w tym artykule, aby zarządzać środowiskami i wybierz jedną jako domyślne dla nowych projektów. Inne aspekty środowiskach znajdują się w następujących artykułach:

- Dla każdego projektu w serwisie można [wybierz określone środowisko](selecting-a-python-environment-for-a-project.md) zamiast Użyj wartości domyślnej.

- Aby uzyskać więcej informacji dotyczących tworzenia i używania środowisk wirtualnych dla projektów języka Python, zobacz [korzystanie ze środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Aby zainstalować pakiety w środowisku, zapoznaj się [pakietów karcie odwołania](python-environments-window-tab-reference.md#packages-tab).

- Aby zainstalować inną interpreter języka Python, zobacz [Python Zainstaluj interpretery](installing-python-interpreters.md). Ogólnie rzecz biorąc, jeśli Pobierz i uruchom program instalacyjny dla linii głównej dystrybucji języka Python, Visual Studio wykryje, czy nowa instalacja i środowiska znajduje się w **środowiska Python** okna i można wybrać dla projektów.

Jeśli jesteś nowym użytkownikiem języka Python w programie Visual Studio, z ogólne udostępniają następujące artykuły:

- [Praca z językiem Python w programie Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Instalowanie obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md)

::: moniker range="vs-2017"
> [!Note]
> Nie można zarządzać środowiskami dla kodu Python, który zostanie otwarty tylko w folderze przy użyciu **pliku** > **Otwórz** > **folderu** polecenia. Zamiast tego [Tworzenie projektu języka Python z istniejącego kodu](quickstart-01-python-in-visual-studio-project-from-existing-code.md) w celu korzystania z funkcji środowiska Visual Studio.
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> Środowiska języka Python, które jest otwierane jako folder, można zarządzać za pomocą polecenia **plik** > **Otwórz** > **folder** . Pasek narzędzi języka Python pozwala przełączać się między wszystkimi wykrytymi środowiskami, a także dodawać nowe środowisko. Informacje o środowisku są przechowywane w pliku PythonSettings. JSON w folderze Workspace. vs.
::: moniker-end

## <a name="the-python-environments-window"></a>W oknie środowiska Python

Środowiska, w których obsługującemu programu Visual Studio są wyświetlane w **środowiska Python** okna. Aby otworzyć okno, użyj jednej z następujących metod:

- Wybierz **widoku** > **Windows inne** > **środowiska Python** polecenia menu.
- Kliknij prawym przyciskiem myszy **środowiska Python** węzeł projektu w **Eksploratora rozwiązań** i wybierz **wyświetlanie wszystkich środowisk języka Python**:

    ::: moniker range="vs-2017"
    ![Wyświetl polecenie wszystkich środowisk w Eksploratorze rozwiązań](media/environments/environments-view-all.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Wyświetl polecenie wszystkich środowisk w Eksploratorze rozwiązań](media/environments/environments-view-all-2019.png)
    ::: moniker-end

W obu przypadkach **środowiska Python** razem zostanie wyświetlone okno **Eksploratora rozwiązań**:

::: moniker range="vs-2017"
![Okno środowiska Python](media/environments/environments-default-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Okno środowiska Python](media/environments/environments-default-view-2019.png)
::: moniker-end

Visual Studio szuka zainstalowanych globalnego środowisk za pomocą rejestru (następujących [514 program ten](https://www.python.org/dev/peps/pep-0514/)), oraz środowisk wirtualnych i środowisk conda (zobacz [typów środowisk](#types-of-environments)). Jeśli nie widzisz oczekiwanego środowiska na liście, zobacz [ręcznie Zidentyfikuj istniejące środowisko](#manually-identify-an-existing-environment).

Po wybraniu środowisko na liście programu Visual Studio Wyświetla różnych właściwości i poleceń dla danego środowiska na **Przegląd** kartę. Na przykład widać na ilustracji powyżej to lokalizacja interpreter *C:\Python36-32*. Czterech poleceń w dolnej części **Przegląd** kartę każdego Otwórz wiersz polecenia z interpreterem uruchomiona. Aby uzyskać więcej informacji, zobacz [odniesienie do karty okna dla środowiska Python — omówienie](python-environments-window-tab-reference.md#overview-tab).

Użyj listy rozwijanej poniżej listy środowisk Aby przełączyć się do różnych kartach zawierających takie jak **pakietów**, i **IntelliSense**. Te karty są także opisane w [dokumentacja karcie okna środowiska Python](python-environments-window-tab-reference.md).

Wybranie środowiska nie powoduje zmiany jego relacji z żadnymi projektami. Domyślne środowisko wyświetlany czcionką pogrubioną na liście jest tą, która korzysta z programu Visual Studio dla żadnych nowych projektów. Aby użyć innego środowiska za pomocą nowych projektów, użyj **upewnij się, to środowisko domyślne dla nowych projektów** polecenia. W kontekście projektu należy zawsze wybrać określonego środowiska. Aby uzyskać więcej informacji, zobacz [wybierz środowisko dla projektu](selecting-a-python-environment-for-a-project.md).

Z prawej strony każdego wymienionych środowiska jest formant, który otwiera **Interactive** okna dla danego środowiska. (W Visual Studio 2017 15.5 i starszych, inny formant wyświetlany jest odświeża bazy danych IntelliSense dla danego środowiska. Zobacz [dokumentacja karcie okna środowiska](python-environments-window-tab-reference.md#intellisense-tab) szczegółowe informacje o bazie danych.)

::: moniker range="vs-2017"
> [!Tip]
> Po rozwinięciu **środowiska Python** okna dostatecznie szerokie, otrzymasz pełniejszego wglądu środowiska, które mogą okazać się bardziej wygodne do pracy z.
>
> ![Widok rozszerzony okna środowiska Python](media/environments/environments-expanded-view.png)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Tip]
> Po rozwinięciu **środowiska Python** okna dostatecznie szerokie, otrzymasz pełniejszego wglądu środowiska, które mogą okazać się bardziej wygodne do pracy z.
>
> ![Widok rozszerzony okna środowiska Python](media/environments/environments-expanded-view-2019.png)
::: moniker-end

> [!Note]
> Mimo że program Visual Studio przestrzega opcję pakiety systemu lokacji, nie udostępnia sposób, aby zmienić go z poziomu programu Visual Studio.

### <a name="what-if-no-environments-appear"></a>Co zrobić, jeśli są wyświetlane nie środowisk?

Jeśli pojawia się nie środowisk, oznacza to, że program Visual Studio nie można wykryć wszelkie instalacje języka Python w lokalizacjach. Można na przykład zainstalować program Visual Studio 2017 lub nowszy, ale wyczyścił wszystkie opcje interpretera w opcjach Instalatora dla obciążenia w języku Python. Podobnie, może zainstalować programu Visual Studio 2015 lub starszym, ale nie zainstalował tłumacza ręcznie (zobacz [Python Zainstaluj interpretery](installing-python-interpreters.md)).

Jeśli znasz interpreter języka Python jest zainstalowana na komputerze, ale Visual Studio (dowolna wersja) nie wykrywały go, a następnie użyj **+ niestandardowe** polecenie, aby ręcznie określić jego lokalizację. Zobacz następną sekcję [ręcznie Zidentyfikuj istniejące środowisko](#manually-identify-an-existing-environment).

> [!Tip]
> Program Visual Studio wykryje aktualizacji do istniejących interpretera, takich jak uaktualnianie Python 2.7.11 do 2.7.14 przy użyciu instalatory z python.org. W procesie instalacji starsze środowisko znika z **środowiska Python** listę aktualizacji, który pojawia się w tym miejscu.
>
> Jednak jeśli ręcznie przenieść tłumacza i lokalne środowisko przy użyciu systemu plików programu Visual Studio nie będzie wiadomo, nowej lokalizacji. Aby uzyskać więcej informacji, zobacz [Przenieś tłumacza](installing-python-interpreters.md#move-an-interpreter).

### <a name="types-of-environments"></a>Typy środowiska

Program Visual Studio może współpracować z globalnego, wirtualnej i środowisk conda.

#### <a name="global-environments"></a>Globalne środowiska

Każda instalacja języka Python (na przykład środowisko Python 2.7, środowiska Python 3.6, 3.7 języka Python, Anaconda 4.4.0 itp., zobacz [Python Zainstaluj interpretery](installing-python-interpreters.md)) zachowuje swój własny *środowisku globalnym*. Każde środowisko składa się z określonych interpreter języka Python, jego biblioteki standardowej, zestaw wstępnie zainstalowanych pakietów i dodatkowych pakietów, instalowanych podczas aktywacji tego środowiska. Instalowanie pakietu w środowisku globalnym udostępnia je do wszystkich projektów przy użyciu tego środowiska. Jeśli środowisko znajduje się w chronionej obszaru systemu plików (w ramach *c:\program files*, na przykład), a następnie instalowania pakietów wymaga uprawnień administratora.

Globalne środowiska są dostępne dla wszystkich projektów na tym komputerze. W programie Visual Studio wybierz opcję jednego środowiska globalnego jako domyślny, który jest używany dla wszystkich projektów, chyba że zdecydujesz inną dla projektu. Aby uzyskać więcej informacji, zobacz [wybierz środowisko dla projektu](selecting-a-python-environment-for-a-project.md).

#### <a name="virtual-environments"></a>Środowiska wirtualne

Mimo, że praca w środowisku globalnym to prosty sposób na rozpoczęcie pracy, środowisku wraz z upływem czasu zapełnić wiele różnych pakietach, które zostały zainstalowane dla różnych projektów. Takie zaśmiecania utrudnia dokładnie przetestuj aplikację przed określony zestaw pakietów z wersjami znanych dokładnie rodzaj środowiska, które należy skonfigurować na serwerze kompilacji lub serwer sieci web. Również może wystąpić konflikt, jeśli dwa projekty wymagają niezgodne pakiety lub różne wersje tego samego pakietu.

Z tego powodu, deweloperzy często tworzyć *środowiska wirtualnego* dla projektu. Środowisko wirtualne jest podfolderem w projekcie, który zawiera kopię określonego interpretera. Gdy aktywujesz środowiska wirtualnego, wszelkich pakietów, instalowanych są instalowane tylko w tym środowisku podfolderze. Następnie uruchom program Python, w tym środowisku, wiedzieć, czy działa względem tylko określonych pakietów.

Program Visual Studio umożliwia bezpośrednie tworzenie środowiska wirtualnego dla projektu. Na przykład po otwarciu projektu, który zawiera *requirements.txt*, lub Utwórz projekt z szablonu, który zawiera ten plik, Visual Studio wyświetli monit o automatyczne tworzenie środowiska wirtualnego i zainstalować te zależności .

W dowolnym momencie w otwartym projekcie możesz utworzyć nowe środowisko wirtualne. W **Eksploratora rozwiązań**, rozwiń węzeł projektu, kliknij prawym przyciskiem myszy **środowiska Python**i wybierz pozycję "Dodaj środowisko wirtualne". Aby uzyskać więcej informacji, zobacz [Utwórz środowisko wirtualne](selecting-a-python-environment-for-a-project.md#create-a-virtual-environment).

Visual Studio udostępnia również polecenie, aby wygenerować *requirements.txt* pliku ze środowiska wirtualnego, dzięki czemu można łatwo odtworzyć środowiska na innych komputerach. Aby uzyskać więcej informacji, zobacz [korzystanie ze środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

#### <a name="conda-environments"></a>Środowisk Conda

Środowiska conda jest utworzony przy użyciu `conda` narzędzia lub za pomocą zintegrowanego narzędzia conda zarządzania w programie Visual Studio 2017 w wersji 15.7 lub nowszej. (Wymaga Anaconda lub Miniconda, które są dostępne za pomocą Instalatora programu Visual Studio, zobacz [Instalacja](installing-python-support-in-visual-studio.md#visual-studio-2019-and-visual-studio-2017)).

::: moniker range="vs-2017"

1. Wybierz **+ Utwórz środowisko conda** w **środowiska Python** okna, co spowoduje otwarcie **Tworzenie nowego środowiska conda** karty:

    ![Utwórz kartę dla nowego środowiska conda](media/environments/environments-conda-1.png)

1. Wprowadź nazwę środowiska w **nazwa** Wybierz podstawowy interpreter języka Python w **Python** i wybierz przycisk **Utwórz**.

1. **Dane wyjściowe** okna jest przedstawiony postęp dla nowego środowiska w kilku instrukcje interfejsu wiersza polecenia po ukończeniu tworzenia:

    ![Pomyślne utworzenie środowiska conda](media/environments/environments-conda-2.png)

1. W programie Visual Studio, można uaktywnić środowiska conda, dla projektu, tak jak dowolnego innego środowiska, zgodnie z opisem na [wybierz środowisko dla projektu](selecting-a-python-environment-for-a-project.md).

1. Aby zainstalować pakiety w środowisku, należy użyć [karcie pakiety](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

::: moniker range=">=vs-2019"

1. Wybierz pozycję **+ Dodaj środowisko** w oknie **środowiska Python** (lub na pasku narzędzi Python), co spowoduje otwarcie okna dialogowego **Dodawanie środowiska** . W tym oknie dialogowym Wybierz kartę **środowisko Conda** :

    ![Karta środowisko Conda w oknie dialogowym Dodawanie środowiska](media/environments/environments-conda-1-2019.png)

1. Skonfiguruj następujące pola:

    | Pole | Opis |
    | --- | --- |
    | Projekt | Projekt, w którym ma zostać utworzone środowisko (Jeśli masz wiele projektów w tym samym rozwiązaniu programu Visual Studio). |
    | Nazwa | Nazwa środowiska Conda. |
    | Dodaj pakiety z | Wybierz **plik środowiska** , jeśli masz plik *Environment. yml* opisujący zależności lub wybierz co najmniej **jedną nazwę pakietu Anaconda** i Wyświetl co najmniej jeden pakiet w języku Python lub wersję języka Python w polu poniżej. Lista pakietów instruuje Conda o utworzeniu środowiska języka Python. Aby zainstalować najnowszą wersję środowiska Python, użyj `python`programu; aby zainstalować określoną wersję, użyj `python=,major>.<minor>` programu `python=3.7`jako wersji. Możesz również użyć przycisku pakiet, aby wybrać wersje środowiska Python i wspólne pakiety z serii menu. |
    | Ustaw jako bieżące środowisko | Aktywuje nowe środowisko w wybranym projekcie po utworzeniu środowiska. |
    | Ustaw jako domyślne środowisko dla nowych projektów | Automatycznie ustawia i aktywuje środowisko Conda w każdym nowym projekcie utworzonym w programie Visual Studio. Ta opcja jest taka sama jak w przypadku korzystania z **tego ustawienia domyślne środowisko dla nowych projektów** w oknie **środowiska języka Python** . |
    | Wyświetl w oknie środowiska języka Python | Określa, czy okno **środowiska języka Python** ma być wyświetlane po utworzeniu środowiska. |

    > [!Important]
    > Podczas tworzenia środowiska Conda należy określić co najmniej jedną wersję języka Python lub pakiet języka Python przy użyciu albo `environments.yml` listy pakietów, co zapewnia, że środowisko zawiera środowisko uruchomieniowe języka Python. W przeciwnym razie program Visual Studio zignoruje środowisko: środowisko nie pojawia się w dowolnym miejscu okna **środowiska języka Python** , nie jest ustawiane jako bieżące środowisko dla projektu i nie jest dostępne jako środowisko globalne.
    >
    > Jeśli chcesz utworzyć środowisko Conda bez wersji języka Python, użyj `conda info` polecenia, aby wyświetlić lokalizacje folderów środowiska Conda, a następnie ręcznie usuń podfolder dla środowiska z tej lokalizacji.

1. Wybierz pozycję **Utwórz**i sprawdź postęp w oknie **danych wyjściowych** . Dane wyjściowe obejmują kilka instrukcji interfejsu wiersza polecenia po zakończeniu tworzenia:

    ![Pomyślne utworzenie środowiska conda](media/environments/environments-conda-2-2019.png)

1. W programie Visual Studio, można uaktywnić środowiska conda, dla projektu, tak jak dowolnego innego środowiska, zgodnie z opisem na [wybierz środowisko dla projektu](selecting-a-python-environment-for-a-project.md).

1. Aby zainstalować dodatkowe pakiety w środowisku, użyj [karty pakiety](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

> [!Note]
> Aby uzyskać najlepsze wyniki za pomocą środowisk conda, użyj conda 4.4.8 lub nowszej (wersje conda różnią się od wersji pakietu Anaconda). Odpowiednie wersje programu Miniconda (Visual Studio 2019) i Anaconda (Visual Studio 2017) można zainstalować za pomocą Instalatora programu Visual Studio.

Aby wyświetlić wersję conda, gdzie są przechowywane środowisk conda, oraz inne informacje, uruchom `conda info` Anaconda z wiersza polecenia (czyli wiersz polecenia gdzie Anaconda znajduje się w ścieżce):

```cli
conda info
```

Foldery środowiska conda są wyświetlane w następujący sposób:

```output
       envs directories : C:\Users\user\.conda\envs
                          c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
```

Ponieważ środowisk conda nie są przechowywane w projekcie, działają podobnie do globalnego środowisk. Na przykład instalowanie nowego pakietu do środowiska conda udostępnia tego pakietu do wszystkich projektów przy użyciu tego środowiska.

Dla programu Visual Studio 2017 w wersji 15.6 i starszych, można użyć środowisk conda, wskazując je ręcznie, zgodnie z opisem w obszarze [ręcznie Zidentyfikuj istniejące środowisko](#manually-identify-an-existing-environment).

Visual Studio 2017 w wersji 15.7 lub nowszej automatycznie wykrywa środowisk conda i wyświetla je w **środowiska Python** okna zgodnie z opisem w następnej sekcji.

## <a name="manually-identify-an-existing-environment"></a>Ręcznie Zidentyfikuj istniejące środowisko

Wykonaj następujące kroki, aby zidentyfikować środowisku, w którym jest zainstalowany w niestandardowej lokalizacji (w tym środowisk conda w Visual Studio 2017 w wersji 15.6 i starszych):

::: moniker range="vs-2017"

1. Wybierz **+ niestandardowe** w **środowiska Python** okna, co spowoduje otwarcie **Konfiguruj** karty:

    ![Widok domyślny dla nowego środowiska niestandardowego](media/environments/environments-custom-1.png)

1. Wprowadź nazwę środowiska w **opis** pola.

1. Wpisz lub Przeglądaj (przy użyciu **...** ) do ścieżki interpreter w **ścieżka prefiksu** pola.

1. Jeśli program Visual Studio wykryje interpreter języka Python w tej lokalizacji (np. ścieżka poniżej dla środowiska conda), umożliwia **Autowykrywanie** polecenia. Wybieranie **Autowykrywanie** kończy pozostałych pól. Te pola można również wykonać ręcznie.

    ![Włączanie polecenia automatyczne wykrywanie](media/environments/environments-custom-2.png)

    ![Uzupełnianie pól środowiska po zakończeniu korzystania z automatycznego wykrywania](media/environments/environments-custom-3.png)

1. Po pola zawierają wartości, które mają, wybierz **Zastosuj** Aby zapisać konfigurację. Można teraz używać środowiska, podobnie jak każdy inny w programie Visual Studio.

1. Jeśli musisz usunąć ręcznie zidentyfikowanych środowiska, wybierz opcję **Usuń** na polecenia **Konfiguruj** kartę. Automatycznie wykryte środowiska nie zapewniają tej opcji. Aby uzyskać więcej informacji, zobacz [karty Konfigurowanie](python-environments-window-tab-reference.md#configure-tab).

::: moniker-end

::: moniker range=">=vs-2019"

1. Wybierz pozycję **+ Dodaj środowisko** w oknie **środowiska Python** (lub na pasku narzędzi Python), co spowoduje otwarcie okna dialogowego **Dodawanie środowiska** . W tym oknie dialogowym Wybierz kartę **istniejąca środowisko** :

    ![Istniejąca karta środowiska w oknie dialogowym Dodawanie środowiska](media/environments/environments-custom-1-2019.png)

1. Wybierz listę rozwijaną **środowisko** , a następnie wybierz pozycję **niestandardowe**:

    ![Opcja środowiska niestandardowego w oknie dialogowym Dodawanie środowiska](media/environments/environments-custom-2-2019.png)

1. W podanych polach w oknie dialogowym wpisz lub Przeglądaj (przy użyciu **...** ) do ścieżki interpretera pod ścieżką prefiksu, która wypełnia większość innych pól. Po przejrzeniu tych wartości i zmodyfikowaniu w razie potrzeby wybierz pozycję **Dodaj**. 

    ![Pola, aby określić szczegóły dla opcji środowiska niestandardowego w oknie dialogowym Dodawanie środowiska](media/environments/environments-custom-3-2019.png)

1. Szczegóły środowiska można w dowolnym momencie przejrzeć i zmodyfikować w oknie **środowiska języka Python** . W tym oknie Wybierz środowisko, a następnie wybierz kartę **Konfiguracja** . Po wprowadzeniu zmian wybierz polecenie **Zastosuj** . Środowisko można także usunąć za pomocą polecenia **Usuń** (niedostępne w przypadku środowisk z autowykrywaniem). Aby uzyskać więcej informacji, zobacz [karty Konfigurowanie](python-environments-window-tab-reference.md#configure-tab).
::: moniker-end

## <a name="fix-or-delete-invalid-environments"></a>Napraw lub Usuń nieprawidłowe środowisk

Jeśli program Visual Studio znajdzie wpisy rejestru dla środowiska, ale ścieżka do interpretera jest nieprawidłowa, a następnie **środowiska Python** okno zawiera nazwę przy użyciu czcionki przekreślenie:

::: moniker range="vs-2017"
![W oknie środowiska Python wyświetlane nieprawidłowe środowisko](media/environments/environments-invalid-entry.png)
::: moniker-end
::: moniker range=">=vs-2019"
![W oknie środowiska Python wyświetlane nieprawidłowe środowisko](media/environments/environments-invalid-entry-2019.png)
::: moniker-end

Aby poprawić środowisko, które chcesz zachować, najpierw spróbuj użyć jego Instalatora **naprawy** procesu. Instalatory dla standardowego języka Python 3.x, na przykład uwzględnić tę opcję.

Aby poprawić środowisko, która nie ma opcji naprawy lub usunąć nieprawidłowe środowisko, wykonaj następujące kroki, aby zmodyfikować rejestr bezpośrednio. Program Visual Studio automatycznie aktualizuje **środowiska Python** okna po wprowadzeniu zmian w rejestrze.

1. Uruchom *regedit.exe*.
1. Przejdź do **HKEY_LOCAL_MACHINE\SOFTWARE\Python**. IronPython, znaleźć **IronPython** zamiast tego.
1. Rozwiń węzeł, który pasuje do dystrybucji, na przykład **Python Core** dla CPython lub **ContinuumAnalytics** dla Anaconda. W przypadku IronPython rozwiń węzeł numeru wersji.
1. Sprawdź wartości w polach **InstallPath** węzła:

    ![Wpisy rejestru dla typowej instalacji języka CPython](media/environments/environments-registry-entries.png)

    - Jeśli środowisko jest nadal istnieje na komputerze, należy zmienić wartość **ExecutablePath** na poprawną lokalizację. Również poprawić **(opcja domyślna)** i **WindowedExecutablePath** wartości zgodnie z potrzebami.
    - Jeśli środowisko już nie istnieje na komputerze i chcesz usunąć go z **środowiska Python** okna, Usuń węzeł nadrzędny **InstallPath**, takich jak **3.6** na powyższej ilustracji.

## <a name="see-also"></a>Zobacz także

- [Zainstaluj interpretery języka Python](installing-python-interpreters.md)
- [Wybierz interpreter dla projektu](selecting-a-python-environment-for-a-project.md)
- [Użyj pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Dokumentacja okna środowiska Python](python-environments-window-tab-reference.md)
