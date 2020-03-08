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
ms.openlocfilehash: 5e269e19a09aec157e38eaf8938b5995c2647803
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408413"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Jak utworzyć i zarządzać środowiskami Python w programie Visual Studio

*Środowisko* języka Python to kontekst, w którym uruchamiany jest kod w języku Python, zawierający globalne, wirtualne i Conda środowiska. Środowisko składa się z tłumacza, biblioteki (zwykle Biblioteka standardowa języka Python) i zestaw zainstalowanych pakietów. Te składniki określają ze sobą, które konstrukcji języka i składni są prawidłowe, jakiego systemu operacyjnego funkcji można uzyskać dostęp i które pakietów, możesz użyć.

W programie Visual Studio w systemie Windows należy użyć okna **środowiska języka Python** , zgodnie z opisem w tym artykule, aby zarządzać środowiskami i wybrać jeden z nich jako domyślny dla nowych projektów. Inne aspekty środowiskach znajdują się w następujących artykułach:

- Dla dowolnego projektu można [wybrać określone środowisko](selecting-a-python-environment-for-a-project.md) zamiast używać go domyślnie.

- Aby uzyskać szczegółowe informacje na temat tworzenia i używania środowisk wirtualnych dla projektów języka Python, zobacz [Korzystanie z środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Jeśli chcesz zainstalować pakiety w środowisku, zapoznaj się z informacjami na [karcie pakiety](python-environments-window-tab-reference.md#packages-tab).

- Aby zainstalować inny interpreter języka Python, zobacz [Installing interpreterów języka Python](installing-python-interpreters.md). Ogólnie rzecz biorąc, jeśli pobierasz i uruchamiasz Instalatora dla dystrybucji języka Python linii głównej, program Visual Studio wykryje, że nowa instalacja i środowisko pojawiają się w oknie **środowiska języka Python** i można je wybrać dla projektów.

Jeśli jesteś nowym użytkownikiem języka Python w programie Visual Studio, z ogólne udostępniają następujące artykuły:

- [Współpraca z językiem Python w programie Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Instalowanie obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md)

::: moniker range="vs-2017"
> [!Note]
> Nie można zarządzać środowiskami dla kodu języka Python, który jest otwierany tylko jako folder przy użyciu **pliku** > **Otwórz** > **folder** . Zamiast tego [Utwórz projekt w języku Python na podstawie istniejącego kodu](quickstart-01-python-in-visual-studio-project-from-existing-code.md) , aby korzystać z funkcji środowiska programu Visual Studio.
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> Można zarządzać środowiskami dla kodu języka Python, który jest otwierany jako folder przy użyciu **pliku** > **Otwórz** > **folder** . Pasek narzędzi języka Python pozwala przełączać się między wszystkimi wykrytymi środowiskami, a także dodawać nowe środowisko. Informacje o środowisku są przechowywane w pliku PythonSettings. JSON w folderze Workspace. vs.
::: moniker-end

## <a name="the-python-environments-window"></a>W oknie środowiska Python

Środowiska, o których wie program Visual Studio, są wyświetlane w oknie **środowiska języka Python** . Aby otworzyć okno, użyj jednej z następujących metod:

- Wybierz polecenie menu **widok** > **inne środowiska Windows** > **Python** .
- Kliknij prawym przyciskiem myszy węzeł **środowiska Python** dla projektu w **Eksplorator rozwiązań** i wybierz pozycję **Wyświetl wszystkie środowiska Python**:

    ::: moniker range="vs-2017"
    ![Wyświetl polecenie wszystkich środowisk w Eksploratorze rozwiązań](media/environments/environments-view-all.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Wyświetl polecenie wszystkich środowisk w Eksploratorze rozwiązań](media/environments/environments-view-all-2019.png)
    ::: moniker-end

W obu przypadkach okno **środowiska języka Python** pojawia się razem z **Eksplorator rozwiązań**:

::: moniker range="vs-2017"
![Okno środowiska Python](media/environments/environments-default-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Okno środowiska Python](media/environments/environments-default-view-2019.png)
::: moniker-end

Program Visual Studio szuka zainstalowanych środowisk globalnych przy użyciu rejestru (po [PEP 514](https://www.python.org/dev/peps/pep-0514/)), a także środowisk wirtualnych i środowisk Conda (zobacz [typy środowisk](#types-of-environments)). Jeśli na liście nie ma oczekiwanego środowiska, zobacz [Ręczne identyfikowanie istniejącego środowiska](#manually-identify-an-existing-environment).

Po wybraniu środowiska na liście program Visual Studio wyświetla różne właściwości i polecenia dla tego środowiska na karcie **Przegląd** . Na przykład na obrazie można zobaczyć, że lokalizacja interpretera to *C:\Python36-32*. Cztery polecenia w dolnej części karty **Przegląd** każdy otwiera wiersz polecenia z uruchomionym interpreterem. Aby uzyskać więcej informacji, zobacz [Dokumentacja karty okna środowiska języka Python — Omówienie](python-environments-window-tab-reference.md#overview-tab).

Użyj listy rozwijanej poniżej listy środowisk, aby przełączyć się na różne karty, takie jak **pakiety**i **technologia IntelliSense**. Te karty są również opisane w [dokumentacji karty okna środowiska Python](python-environments-window-tab-reference.md).

Wybranie środowiska nie powoduje zmiany jego relacji z żadnymi projektami. Domyślne środowisko wyświetlany czcionką pogrubioną na liście jest tą, która korzysta z programu Visual Studio dla żadnych nowych projektów. Aby użyć innego środowiska z nowymi projektami, użyj polecenia **uczyń to Default Environment for New projects** . W kontekście projektu należy zawsze wybrać określonego środowiska. Aby uzyskać więcej informacji, zobacz [Wybieranie środowiska dla projektu](selecting-a-python-environment-for-a-project.md).

Z prawej strony każdego z wymienionych środowisk jest formant, który otwiera okno **interaktywne** dla tego środowiska. (W Visual Studio 2017 15.5 i starszych, inny formant wyświetlany jest odświeża bazy danych IntelliSense dla danego środowiska. Szczegółowe informacje o bazie danych znajdują się w temacie Informacje o [karcie okna środowiska](python-environments-window-tab-reference.md) .

::: moniker range="vs-2017"
> [!Tip]
> Po rozwinięciu wystarczająco szerokiego okna **środowisk Python** możesz uzyskać pełen wgląd w Twoje środowiska, które może być wygodniejsze do pracy z programem.
>
> ![Widok rozszerzony okna środowiska Python](media/environments/environments-expanded-view.png)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Tip]
> Po rozwinięciu wystarczająco szerokiego okna **środowisk Python** możesz uzyskać pełen wgląd w Twoje środowiska, które może być wygodniejsze do pracy z programem.
>
> ![Widok rozszerzony okna środowiska Python](media/environments/environments-expanded-view-2019.png)
::: moniker-end

> [!Note]
> Mimo że program Visual Studio przestrzega opcję pakiety systemu lokacji, nie udostępnia sposób, aby zmienić go z poziomu programu Visual Studio.

### <a name="what-if-no-environments-appear"></a>Co zrobić, jeśli są wyświetlane nie środowisk?

Jeśli pojawia się nie środowisk, oznacza to, że program Visual Studio nie można wykryć wszelkie instalacje języka Python w lokalizacjach. Można na przykład zainstalować program Visual Studio 2017 lub nowszy, ale wyczyścił wszystkie opcje interpretera w opcjach Instalatora dla obciążenia w języku Python. Podobnie być może zainstalowano program Visual Studio 2015 lub wcześniejszy, ale nie został on zainstalowany ręcznie (zobacz [Zainstaluj interpretery języka Python](installing-python-interpreters.md)).

Jeśli wiesz, że masz interpreter języka Python na komputerze, ale program Visual Studio (dowolna wersja) nie wykryje go, a następnie użyj polecenia **+ Custom** , aby określić jego lokalizację ręcznie. Zobacz następną sekcję, [ręcznie Zidentyfikuj istniejące środowisko](#manually-identify-an-existing-environment).

> [!Tip]
> Program Visual Studio wykrywa aktualizacje istniejącego interpretera, takie jak uaktualnienie języka Python 2.7.11 do 2.7.14 przy użyciu instalatorów z python.org. W trakcie procesu instalacji starsze środowisko znika z listy **środowiska języka Python** przed pojawieniem się aktualizacji w miejscu.
>
> Jednak jeśli ręcznie przenieść tłumacza i lokalne środowisko przy użyciu systemu plików programu Visual Studio nie będzie wiadomo, nowej lokalizacji. Aby uzyskać więcej informacji, zobacz [przenoszenie interpretera](installing-python-interpreters.md#move-an-interpreter).

### <a name="types-of-environments"></a>Typy środowiska

Program Visual Studio może współpracować z globalnego, wirtualnej i środowisk conda.

#### <a name="global-environments"></a>Globalne środowiska

Każda instalacja języka Python (na przykład Python 2,7, Python 3,6, Python 3,7, Anaconda 4.4.0 itp.), zobacz [Instalowanie interpreterów języka Python](installing-python-interpreters.md), utrzymuje własne *środowisko globalne*. Każde środowisko składa się z określonych interpreter języka Python, jego biblioteki standardowej, zestaw wstępnie zainstalowanych pakietów i dodatkowych pakietów, instalowanych podczas aktywacji tego środowiska. Instalowanie pakietu w środowisku globalnym udostępnia je do wszystkich projektów przy użyciu tego środowiska. Jeśli środowisko znajduje się w chronionym obszarze systemu plików (na przykład w *folderze c:\Program Files*), instalowanie pakietów wymaga uprawnień administratora.

Globalne środowiska są dostępne dla wszystkich projektów na tym komputerze. W programie Visual Studio wybierz opcję jednego środowiska globalnego jako domyślny, który jest używany dla wszystkich projektów, chyba że zdecydujesz inną dla projektu. Aby uzyskać więcej informacji, zobacz [Wybieranie środowiska dla projektu](selecting-a-python-environment-for-a-project.md).

#### <a name="virtual-environments"></a>Środowiska wirtualne

Mimo, że praca w środowisku globalnym to prosty sposób na rozpoczęcie pracy, środowisku wraz z upływem czasu zapełnić wiele różnych pakietach, które zostały zainstalowane dla różnych projektów. Takie zaśmiecania utrudnia dokładnie przetestuj aplikację przed określony zestaw pakietów z wersjami znanych dokładnie rodzaj środowiska, które należy skonfigurować na serwerze kompilacji lub serwer sieci web. Również może wystąpić konflikt, jeśli dwa projekty wymagają niezgodne pakiety lub różne wersje tego samego pakietu.

Z tego powodu deweloperzy często tworzą *środowisko wirtualne* dla projektu. Środowisko wirtualne jest podfolderem w projekcie, który zawiera kopię określonego interpretera. Gdy aktywujesz środowiska wirtualnego, wszelkich pakietów, instalowanych są instalowane tylko w tym środowisku podfolderze. Następnie uruchom program Python, w tym środowisku, wiedzieć, czy działa względem tylko określonych pakietów.

Program Visual Studio umożliwia bezpośrednie tworzenie środowiska wirtualnego dla projektu. Na przykład w przypadku otwarcia projektu zawierającego plik *Requirements. txt*lub utworzenia projektu na podstawie szablonu, który zawiera tego pliku, program Visual Studio poprosi o automatyczne utworzenie środowiska wirtualnego i zainstalowanie tych zależności.

W dowolnym momencie w otwartym projekcie możesz utworzyć nowe środowisko wirtualne. W **Eksplorator rozwiązań**rozwiń węzeł projektu, kliknij prawym przyciskiem myszy **środowisko Python**i wybierz polecenie "Dodaj środowisko wirtualne". Aby uzyskać więcej informacji, zobacz [Tworzenie środowiska wirtualnego](/visualstudio/python/selecting-a-python-environment-for-a-project?view=vs-2019#create-a-virtual-environment-1).

Program Visual Studio udostępnia również polecenie generujące plik *Requirements. txt* w środowisku wirtualnym, co ułatwia ponowne tworzenie środowiska na innych komputerach. Aby uzyskać więcej informacji, zobacz [Korzystanie z środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

#### <a name="conda-environments"></a>Środowisk Conda

Środowisko Conda jest tworzone za pomocą narzędzia `conda` lub zintegrowanego zarządzania Conda w programie Visual Studio 2017 w wersji 15,7 lub nowszej. (Wymaga Anaconda lub Miniconda, które są dostępne za pomocą Instalatora programu Visual Studio, zobacz [Instalacja](installing-python-support-in-visual-studio.md#visual-studio-2019-and-visual-studio-2017)).

::: moniker range="vs-2017"

1. Wybierz pozycję **+ Utwórz środowisko Conda** w oknie **środowiska języka Python** , co spowoduje otwarcie karty **Utwórz nowe środowisko Conda** :

    ![Utwórz kartę dla nowego środowiska conda](media/environments/environments-conda-1.png)

1. W polu **Nazwa** wprowadź nazwę środowiska, wybierz podstawowy interpreter języka Python w polu **Python** , a następnie wybierz pozycję **Utwórz**.

1. W oknie **danych wyjściowych** zostanie wyświetlony postęp nowego środowiska z kilkoma instrukcjami interfejsu wiersza polecenia po zakończeniu tworzenia:

    ![Pomyślne utworzenie środowiska conda](media/environments/environments-conda-2.png)

1. W programie Visual Studio można aktywować środowisko Conda dla projektu, tak jak w przypadku każdego innego środowiska, zgodnie z opisem w artykule [Wybieranie środowiska dla projektu](selecting-a-python-environment-for-a-project.md).

1. Aby zainstalować pakiety w środowisku, użyj [karty pakiety](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

::: moniker range=">=vs-2019"

1. Wybierz pozycję **+ Dodaj środowisko** w oknie **środowiska Python** (lub na pasku narzędzi Python), co spowoduje otwarcie okna dialogowego **Dodawanie środowiska** . W tym oknie dialogowym Wybierz kartę **środowisko Conda** :

    ![Karta środowisko Conda w oknie dialogowym Dodawanie środowiska](media/environments/environments-conda-1-2019.png)

1. Skonfiguruj następujące pola:

    | Pole | Opis |
    | --- | --- |
    | Project | Projekt, w którym ma zostać utworzone środowisko (Jeśli masz wiele projektów w tym samym rozwiązaniu programu Visual Studio). |
    | Name (Nazwa) | Nazwa środowiska Conda. |
    | Dodaj pakiety z | Wybierz **plik środowiska** , jeśli masz plik *Environment. yml* opisujący zależności lub wybierz co najmniej **jedną nazwę pakietu Anaconda** i Wyświetl co najmniej jeden pakiet w języku Python lub wersję języka Python w polu poniżej. Lista pakietów instruuje Conda o utworzeniu środowiska języka Python. Aby zainstalować najnowszą wersję środowiska Python, użyj `python`; Aby zainstalować określoną wersję, użyj `python=,major>.<minor>` jak w programie `python=3.7`. Możesz również użyć przycisku pakiet, aby wybrać wersje środowiska Python i wspólne pakiety z serii menu. |
    | Ustaw jako bieżące środowisko | Aktywuje nowe środowisko w wybranym projekcie po utworzeniu środowiska. |
    | Ustaw jako domyślne środowisko dla nowych projektów | Automatycznie ustawia i aktywuje środowisko Conda w każdym nowym projekcie utworzonym w programie Visual Studio. Ta opcja jest taka sama jak w przypadku korzystania z **tego ustawienia domyślne środowisko dla nowych projektów** w oknie **środowiska języka Python** . |
    | Wyświetl w oknie środowiska języka Python | Określa, czy okno **środowiska języka Python** ma być wyświetlane po utworzeniu środowiska. |

    > [!Important]
    > W przypadku tworzenia środowiska Conda należy określić co najmniej jedną wersję języka Python lub pakiet języka Python przy użyciu `environments.yml` lub listy pakietów, co zapewnia, że środowisko będzie zawierało środowisko uruchomieniowe języka Python. W przeciwnym razie program Visual Studio zignoruje środowisko: środowisko nie pojawia się w dowolnym miejscu okna **środowiska języka Python** , nie jest ustawiane jako bieżące środowisko dla projektu i nie jest dostępne jako środowisko globalne.
    >
    > Jeśli chcesz utworzyć środowisko Conda bez wersji języka Python, użyj polecenia `conda info`, aby wyświetlić lokalizacje folderów środowiska Conda, a następnie ręcznie usuń podfolder dla środowiska z tej lokalizacji.

1. Wybierz pozycję **Utwórz**i sprawdź postęp w oknie **danych wyjściowych** . Dane wyjściowe obejmują kilka instrukcji interfejsu wiersza polecenia po zakończeniu tworzenia:

    ![Pomyślne utworzenie środowiska conda](media/environments/environments-conda-2-2019.png)

1. W programie Visual Studio można aktywować środowisko Conda dla projektu, tak jak w przypadku każdego innego środowiska, zgodnie z opisem w artykule [Wybieranie środowiska dla projektu](selecting-a-python-environment-for-a-project.md).

1. Aby zainstalować dodatkowe pakiety w środowisku, użyj [karty pakiety](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

> [!Note]
> Aby uzyskać najlepsze wyniki za pomocą środowisk conda, użyj conda 4.4.8 lub nowszej (wersje conda różnią się od wersji pakietu Anaconda). Odpowiednie wersje programu Miniconda (Visual Studio 2019) i Anaconda (Visual Studio 2017) można zainstalować za pomocą Instalatora programu Visual Studio.

Aby wyświetlić wersję Conda, gdzie są przechowywane środowiska Conda i inne informacje, uruchom `conda info` w wierszu polecenia Anaconda (oznacza to, że w wierszu polecenia, gdzie Anaconda znajduje się w ścieżce):

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

W przypadku programu Visual Studio 2017 w wersji 15,6 lub starszej można użyć środowisk Conda, wskazując je ręcznie, zgodnie z opisem w sekcji [Ręczne identyfikowanie istniejącego środowiska](#manually-identify-an-existing-environment).

Program Visual Studio 2017 w wersji 15,7 i nowszych wykrywa środowiska Conda automatycznie i wyświetla je w oknie **środowiska języka Python** zgodnie z opisem w następnej sekcji.

## <a name="manually-identify-an-existing-environment"></a>Ręcznie Zidentyfikuj istniejące środowisko

Wykonaj następujące kroki, aby zidentyfikować środowisku, w którym jest zainstalowany w niestandardowej lokalizacji (w tym środowisk conda w Visual Studio 2017 w wersji 15.6 i starszych):

::: moniker range="vs-2017"

1. W oknie **środowiska języka Python** wybierz pozycję **+ niestandardowe** , co spowoduje otwarcie karty **Konfiguracja** :

    ![Widok domyślny dla nowego środowiska niestandardowego](media/environments/environments-custom-1.png)

1. W polu **Opis** wprowadź nazwę środowiska.

1. Wprowadź lub Przeglądaj (za pomocą **...** ) ścieżkę interpretera w polu **ścieżka prefiksu** .

1. Jeśli program Visual Studio wykryje interpreter języka Python w tym miejscu (na przykład ścieżkę pokazaną poniżej dla środowiska Conda), włącza polecenie **autowykrywania** . Wybór **autowykrywania** uzupełnia pozostałe pola. Te pola można również wykonać ręcznie.

    ![Włączanie polecenia automatyczne wykrywanie](media/environments/environments-custom-2.png)

    ![Uzupełnianie pól środowiska po zakończeniu korzystania z automatycznego wykrywania](media/environments/environments-custom-3.png)

1. Gdy pola zawierają odpowiednie wartości, wybierz pozycję **Zastosuj** , aby zapisać konfigurację. Można teraz używać środowiska, podobnie jak każdy inny w programie Visual Studio.

1. Jeśli musisz usunąć ręcznie zidentyfikowane środowisko, wybierz polecenie **Usuń** na karcie **Konfiguracja** . automatycznie wykryte środowiska nie zapewniają tej opcji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie karty](python-environments-window-tab-reference.md#configure-tab).

::: moniker-end

::: moniker range=">=vs-2019"

1. Wybierz pozycję **+ Dodaj środowisko** w oknie **środowiska Python** (lub na pasku narzędzi Python), co spowoduje otwarcie okna dialogowego **Dodawanie środowiska** . W tym oknie dialogowym Wybierz kartę **istniejąca środowisko** :

    ![Istniejąca karta środowiska w oknie dialogowym Dodawanie środowiska](media/environments/environments-custom-1-2019.png)

1. Wybierz listę rozwijaną **środowisko** , a następnie wybierz pozycję **niestandardowe**:

    ![Opcja środowiska niestandardowego w oknie dialogowym Dodawanie środowiska](media/environments/environments-custom-2-2019.png)

1. W podanych polach w oknie dialogowym wpisz lub Przeglądaj (przy użyciu **...** ) do ścieżki interpretera pod **ścieżką prefiksu**, która wypełnia większość innych pól. Po przejrzeniu tych wartości i zmodyfikowaniu w razie potrzeby wybierz pozycję **Dodaj**. 

    ![Pola, aby określić szczegóły dla opcji środowiska niestandardowego w oknie dialogowym Dodawanie środowiska](media/environments/environments-custom-3-2019.png)

1. Szczegóły środowiska można w dowolnym momencie przejrzeć i zmodyfikować w oknie **środowiska języka Python** . W tym oknie Wybierz środowisko, a następnie wybierz kartę **Konfiguracja** . Po wprowadzeniu zmian wybierz polecenie **Zastosuj** . Środowisko można także usunąć za pomocą polecenia **Usuń** (niedostępne w przypadku środowisk z autowykrywaniem). Aby uzyskać więcej informacji, zobacz [Konfigurowanie karty](python-environments-window-tab-reference.md#configure-tab).
::: moniker-end

## <a name="fix-or-delete-invalid-environments"></a>Napraw lub Usuń nieprawidłowe środowisk

Jeśli program Visual Studio znajdzie wpisy rejestru dla środowiska, ale ścieżka do interpretera jest nieprawidłowa, w oknie środowiska języka **Python** zostanie wyświetlona nazwa z przekreśloną czcionką:

::: moniker range="vs-2017"
![W oknie środowiska Python wyświetlane nieprawidłowe środowisko](media/environments/environments-invalid-entry.png)
::: moniker-end
::: moniker range=">=vs-2019"
![W oknie środowiska Python wyświetlane nieprawidłowe środowisko](media/environments/environments-invalid-entry-2019.png)
::: moniker-end

Aby poprawić środowisko, które chcesz zachować, najpierw spróbuj użyć procesu **naprawy** Instalatora. Instalatory dla standardowego języka Python 3.x, na przykład uwzględnić tę opcję.

Aby poprawić środowisko, która nie ma opcji naprawy lub usunąć nieprawidłowe środowisko, wykonaj następujące kroki, aby zmodyfikować rejestr bezpośrednio. Program Visual Studio automatycznie aktualizuje okno **środowiska Python** , gdy wprowadzisz zmiany w rejestrze.

1. Uruchom *regedit. exe*.
1. Przejdź do **HKEY_LOCAL_MACHINE \software\python**. W przypadku IronPython należy poszukać polecenia **IronPython** .
1. Rozwiń węzeł, który pasuje do dystrybucji, na przykład **Python Core** dla CPython lub **ContinuumAnalytics** dla Anaconda. W przypadku IronPython rozwiń węzeł numeru wersji.
1. Sprawdź wartości w węźle **InstallPath** :

    ![Wpisy rejestru dla typowej instalacji języka CPython](media/environments/environments-registry-entries.png)

    - Jeśli środowisko nadal istnieje na komputerze, Zmień wartość **ścieżka pliku wykonywalnego** na poprawną lokalizację. W razie potrzeby skoryguj również wartości **(domyślne)** i **WindowedExecutablePath** .
    - Jeśli środowisko nie istnieje już na komputerze i chcesz je usunąć z okna **środowiska języka Python** , Usuń węzeł nadrzędny **InstallPath**, taki jak **3,6** na powyższym obrazie.

## <a name="see-also"></a>Zobacz też

- [Zainstaluj interpretery języka Python](installing-python-interpreters.md)
- [Wybierz interpreter dla projektu](selecting-a-python-environment-for-a-project.md)
- [Użyj programu Requirements. txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Dokumentacja okna środowiska Python](python-environments-window-tab-reference.md)
