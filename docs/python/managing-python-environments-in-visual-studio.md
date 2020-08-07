---
title: Zarządzaj środowiskami i interpreterami języka Python
description: Okno środowiska Python służy do zarządzania środowiskami globalnymi, wirtualnymi i Conda, instalowaniem interpreterów języka Python i pakietów oraz przypisywanie środowisk do projektów programu Visual Studio.
ms.date: 08/06/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 1b6782a95793f222ba15fe8f928ecd9d7337c90f
ms.sourcegitcommit: 50bbb62525c91c5a31bab57e1caf37c5638872c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2020
ms.locfileid: "87913310"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Jak tworzyć środowiska Python i zarządzać nimi w programie Visual Studio

**Środowisko języka Python** to kontekst, w którym uruchamiany jest kod w języku Python, zawierający globalne, wirtualne i Conda środowiska. Środowisko składa się z interpretera, biblioteki (zazwyczaj biblioteki standardowej języka Python) i zestawu zainstalowanych pakietów. Te składniki wspólnie określają, które konstrukcje języka i składnia są prawidłowe, jakie funkcje systemu operacyjnego są dostępne, a także które pakiety mogą być używane.

W programie Visual Studio w systemie Windows należy użyć okna **środowiska języka Python** , zgodnie z opisem w tym artykule, aby zarządzać środowiskami i wybrać jeden z nich jako domyślny dla nowych projektów. Inne aspekty środowisk można znaleźć w następujących artykułach:

- Dla dowolnego projektu można [wybrać określone środowisko](selecting-a-python-environment-for-a-project.md) zamiast używać go domyślnie.

- Aby uzyskać szczegółowe informacje na temat tworzenia i używania środowisk wirtualnych dla projektów języka Python, zobacz [Korzystanie z środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Jeśli chcesz zainstalować pakiety w środowisku, zapoznaj się z informacjami na [karcie pakiety](python-environments-window-tab-reference.md#packages-tab).

- Aby zainstalować inny interpreter języka Python, zobacz [Installing interpreterów języka Python](installing-python-interpreters.md). Ogólnie rzecz biorąc, jeśli pobierasz i uruchamiasz Instalatora dla dystrybucji języka Python linii głównej, program Visual Studio wykryje, że nowa instalacja i środowisko pojawiają się w oknie **środowiska języka Python** i można je wybrać dla projektów.

Jeśli dopiero zaczynasz w języku Python w programie Visual Studio, następujące artykuły pochodzą również z ogólnego tła:

- [Współpraca z językiem Python w programie Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Instalowanie obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md)

::: moniker range="vs-2017"
> [!Note]
> Nie można zarządzać środowiskami dla kodu języka Python, który jest otwierany tylko jako folder **File**przy użyciu  >  polecenia**Otwórz**  >  **folder folderu** . Zamiast tego [Utwórz projekt w języku Python na podstawie istniejącego kodu](quickstart-01-python-in-visual-studio-project-from-existing-code.md) , aby korzystać z funkcji środowiska programu Visual Studio.
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> Środowiska języka Python, które jest otwierane jako folder, można zarządzać za pomocą polecenia **plik**  >  **Otwórz**  >  **folder** . Pasek narzędzi języka Python pozwala przełączać się między wszystkimi wykrytymi środowiskami, a także dodawać nowe środowisko. Informacje o środowisku są przechowywane w PythonSettings.jspliku w folderze Workspace. vs.
::: moniker-end

## <a name="the-python-environments-window"></a>Okno środowiska języka Python

Środowiska, o których wie program Visual Studio, są wyświetlane w oknie **środowiska języka Python** . Aby otworzyć okno, użyj jednej z następujących metod:

- Wybierz polecenie **Wyświetl**  >  **inne**  >  **środowiska języka Python** systemu Windows.
- Kliknij prawym przyciskiem myszy węzeł **środowiska Python** dla projektu w **Eksplorator rozwiązań** i wybierz pozycję **Wyświetl wszystkie środowiska Python**:

    ::: moniker range="vs-2017"
    ![Polecenie Wyświetl wszystkie środowiska w Eksplorator rozwiązań](media/environments/environments-view-all.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Polecenie Wyświetl wszystkie środowiska w Eksplorator rozwiązań](media/environments/environments-view-all-2019.png)
    ::: moniker-end

W obu przypadkach okno **środowiska języka Python** pojawia się razem z **Eksplorator rozwiązań**:

::: moniker range="vs-2017"
![Okno środowisk Python](media/environments/environments-default-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Okno środowisk Python](media/environments/environments-default-view-2019.png)
::: moniker-end

Program Visual Studio szuka zainstalowanych środowisk globalnych przy użyciu rejestru (po [PEP 514](https://www.python.org/dev/peps/pep-0514/)), a także środowisk wirtualnych i środowisk Conda (zobacz [typy środowisk](#types-of-environments)). Jeśli na liście nie ma oczekiwanego środowiska, zobacz [Ręczne identyfikowanie istniejącego środowiska](#manually-identify-an-existing-environment).

Po wybraniu środowiska na liście program Visual Studio wyświetla różne właściwości i polecenia dla tego środowiska na karcie **Przegląd** . Na przykład na obrazie można zobaczyć, że lokalizacja interpretera to *C:\Python36-32*. Cztery polecenia w dolnej części karty **Przegląd** każdy otwiera wiersz polecenia z uruchomionym interpreterem. Aby uzyskać więcej informacji, zobacz [Dokumentacja karty okna środowiska języka Python — Omówienie](python-environments-window-tab-reference.md#overview-tab).

Użyj listy rozwijanej poniżej listy środowisk, aby przełączyć się na różne karty, takie jak **pakiety**i **technologia IntelliSense**. Te karty są również opisane w [dokumentacji karty okna środowiska Python](python-environments-window-tab-reference.md).

Wybranie środowiska nie powoduje zmiany jego relacji z żadnymi projektami. Domyślne środowisko, pokazane na pogrubieniu na liście, jest używane przez program Visual Studio do nowych projektów. Aby użyć innego środowiska z nowymi projektami, użyj polecenia **uczyń to Default Environment for New projects** . W kontekście projektu zawsze możesz wybrać określone środowisko. Aby uzyskać więcej informacji, zobacz [Wybieranie środowiska dla projektu](selecting-a-python-environment-for-a-project.md).

Z prawej strony każdego z wymienionych środowisk jest formant, który otwiera okno **interaktywne** dla tego środowiska. (W programie Visual Studio 2017 15,5 i starszym zostanie wyświetlona inna kontrolka, która Odświeża bazę danych IntelliSense dla tego środowiska. Szczegółowe informacje o bazie danych znajdują się w temacie Informacje o [karcie okna środowiska](python-environments-window-tab-reference.md) .

::: moniker range="vs-2017"
> [!Tip]
> Po rozwinięciu wystarczająco szerokiego okna **środowisk Python** możesz uzyskać pełen wgląd w Twoje środowiska, które może być wygodniejsze do pracy z programem.
>
> ![Widok rozwinięty okna środowiska języka Python](media/environments/environments-expanded-view.png)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Tip]
> Po rozwinięciu wystarczająco szerokiego okna **środowisk Python** możesz uzyskać pełen wgląd w Twoje środowiska, które może być wygodniejsze do pracy z programem.
>
> ![Widok rozwinięty okna środowiska języka Python](media/environments/environments-expanded-view-2019.png)
::: moniker-end

> [!Note]
> Mimo że program Visual Studio uwzględnia opcję pakietów system-lokacja, nie umożliwia zmiany jej w programie Visual Studio.

### <a name="what-if-no-environments-appear"></a>Co zrobić, jeśli nie są wyświetlane żadne środowiska?

Jeśli nie zostaną wyświetlone żadne środowiska, oznacza to, że program Visual Studio nie wykrył instalacji języka Python w standardowych lokalizacjach. Można na przykład zainstalować program Visual Studio 2017 lub nowszy, ale wyczyścił wszystkie opcje interpretera w opcjach Instalatora dla obciążenia w języku Python. Podobnie być może zainstalowano program Visual Studio 2015 lub wcześniejszy, ale nie został on zainstalowany ręcznie (zobacz [Zainstaluj interpretery języka Python](installing-python-interpreters.md)).

Jeśli wiesz, że masz interpreter języka Python na komputerze, ale program Visual Studio (dowolna wersja) nie wykryje go, a następnie użyj polecenia **+ Custom** , aby określić jego lokalizację ręcznie. Zobacz następną sekcję, [ręcznie Zidentyfikuj istniejące środowisko](#manually-identify-an-existing-environment).

> [!Tip]
> Program Visual Studio wykrywa aktualizacje istniejącego interpretera, takie jak uaktualnienie języka Python 2.7.11 do 2.7.14 przy użyciu instalatorów z python.org. W trakcie procesu instalacji starsze środowisko znika z listy **środowiska języka Python** przed pojawieniem się aktualizacji w miejscu.
>
> Jeśli jednak ręcznie przeniesiesz interpreter i jego środowisko przy użyciu systemu plików, program Visual Studio nie będzie znać nowej lokalizacji. Aby uzyskać więcej informacji, zobacz [przenoszenie interpretera](installing-python-interpreters.md#move-an-interpreter).

### <a name="types-of-environments"></a>Typy środowisk

Program Visual Studio może współpracować ze środowiskami globalnymi, wirtualnymi i Conda.

#### <a name="global-environments"></a>Środowiska globalne

Każda instalacja języka Python (na przykład Python 2,7, Python 3,6, Python 3,7, Anaconda 4.4.0 itp.), zobacz [Instalowanie interpreterów języka Python](installing-python-interpreters.md), utrzymuje własne *środowisko globalne*. Każde środowisko składa się z określonego interpretera języka Python, jego standardowej biblioteki, zestawu wstępnie zainstalowanych pakietów oraz wszelkich dodatkowych pakietów instalowanych podczas aktywowania tego środowiska. Zainstalowanie pakietu w środowisku globalnym sprawia, że jest ono dostępne dla wszystkich projektów korzystających z tego środowiska. Jeśli środowisko znajduje się w chronionym obszarze systemu plików (na przykład w *folderze c:\Program Files*), instalowanie pakietów wymaga uprawnień administratora.

Środowiska globalne są dostępne dla wszystkich projektów na komputerze. W programie Visual Studio można wybrać jedno środowisko globalne jako domyślne, które jest używane we wszystkich projektach, chyba że zostanie wybrana inna opcja dla projektu. Aby uzyskać więcej informacji, zobacz [Wybieranie środowiska dla projektu](selecting-a-python-environment-for-a-project.md).

#### <a name="virtual-environments"></a>Środowiska wirtualne

Mimo że praca w środowisku globalnym jest łatwym sposobem na rozpoczęcie pracy, to środowisko będzie w miarę upływu czasu przenoszone z wieloma różnymi pakietami, które zostały zainstalowane dla różnych projektów. Takie bałaganie utrudnia dokładne przetestowanie aplikacji względem określonego zestawu pakietów ze znanymi wersjami, co jest dokładnie rodzajem środowiska skonfigurowanego na serwerze kompilacji lub serwerze sieci Web. Konflikty mogą również wystąpić, jeśli dwa projekty wymagają niezgodnych pakietów lub różnych wersji tego samego pakietu.

Z tego powodu deweloperzy często tworzą *środowisko wirtualne* dla projektu. Środowisko wirtualne jest podfolderem w projekcie, który zawiera kopię określonego interpretera. Podczas aktywowania środowiska wirtualnego wszystkie instalowane pakiety są instalowane tylko w podfolderze tego środowiska. Po uruchomieniu w tym środowisku programu w języku Python wiadomo, że jest on uruchomiony tylko dla tych konkretnych pakietów.

Program Visual Studio zapewnia bezpośrednią pomoc techniczną dla tworzenia środowiska wirtualnego dla projektu. Na przykład w przypadku otwarcia projektu zawierającego *requirements.txt*lub utworzenia projektu na podstawie szablonu zawierającego ten plik program Visual Studio poprosi o automatyczne utworzenie środowiska wirtualnego i zainstalowanie tych zależności.

W dowolnym momencie w otwartym projekcie można utworzyć nowe środowisko wirtualne. W **Eksplorator rozwiązań**rozwiń węzeł projektu, kliknij prawym przyciskiem myszy **środowisko Python**i wybierz polecenie "Dodaj środowisko wirtualne". Aby uzyskać więcej informacji, zobacz [Tworzenie środowiska wirtualnego](/visualstudio/python/selecting-a-python-environment-for-a-project?view=vs-2019#create-a-virtual-environment-1).

Program Visual Studio udostępnia również polecenie generowania pliku *requirements.txt* ze środowiska wirtualnego, co ułatwia ponowne tworzenie środowiska na innych komputerach. Aby uzyskać więcej informacji, zobacz [Korzystanie z środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

#### <a name="conda-environments"></a>Środowiska Conda

Środowisko Conda jest utworzone za pomocą `conda` Narzędzia lub zintegrowanego zarządzania Conda w programie Visual Studio 2017 w wersji 15,7 lub nowszej. (Wymaga Anaconda lub Miniconda, które są dostępne za pomocą Instalatora programu Visual Studio, zobacz [Instalacja](installing-python-support-in-visual-studio.md#visual-studio-2019-and-visual-studio-2017)).

::: moniker range="vs-2017"

1. Wybierz pozycję **+ Utwórz środowisko Conda** w oknie **środowiska języka Python** , co spowoduje otwarcie karty **Utwórz nowe środowisko Conda** :

    ![Utwórz kartę dla nowego środowiska Conda](media/environments/environments-conda-1.png)

1. W polu **Nazwa** wprowadź nazwę środowiska, wybierz podstawowy interpreter języka Python w polu **Python** , a następnie wybierz pozycję **Utwórz**.

1. W oknie **danych wyjściowych** zostanie wyświetlony postęp nowego środowiska z kilkoma instrukcjami interfejsu wiersza polecenia po zakończeniu tworzenia:

    ![Pomyślne utworzenie środowiska Conda](media/environments/environments-conda-2.png)

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
    | Nazwa | Nazwa środowiska Conda. |
    | Dodaj pakiety z | Wybierz **plik środowiska** , jeśli masz plik *Environment. yml* opisujący zależności lub wybierz co najmniej **jedną nazwę pakietu Anaconda** i Wyświetl co najmniej jeden pakiet w języku Python lub wersję języka Python w polu poniżej. Lista pakietów instruuje Conda o utworzeniu środowiska języka Python. Aby zainstalować najnowszą wersję środowiska Python, użyj programu `python` ; Aby zainstalować określoną wersję, użyj `python=,major>.<minor>` programu jako wersji `python=3.7` . Możesz również użyć przycisku pakiet, aby wybrać wersje środowiska Python i wspólne pakiety z serii menu. |
    | Ustaw jako bieżące środowisko | Aktywuje nowe środowisko w wybranym projekcie po utworzeniu środowiska. |
    | Ustaw jako domyślne środowisko dla nowych projektów | Automatycznie ustawia i aktywuje środowisko Conda w każdym nowym projekcie utworzonym w programie Visual Studio. Ta opcja jest taka sama jak w przypadku korzystania z **tego ustawienia domyślne środowisko dla nowych projektów** w oknie **środowiska języka Python** . |
    | Wyświetl w oknie środowiska języka Python | Określa, czy okno **środowiska języka Python** ma być wyświetlane po utworzeniu środowiska. |

    > [!Important]
    > Podczas tworzenia środowiska Conda należy określić co najmniej jedną wersję języka Python lub pakiet języka Python przy użyciu albo `environments.yml` listy pakietów, co zapewnia, że środowisko zawiera środowisko uruchomieniowe języka Python. W przeciwnym razie program Visual Studio zignoruje środowisko: środowisko nie pojawia się w dowolnym miejscu okna **środowiska języka Python** , nie jest ustawiane jako bieżące środowisko dla projektu i nie jest dostępne jako środowisko globalne.
    >
    > Jeśli chcesz utworzyć środowisko Conda bez wersji języka Python, użyj `conda info` polecenia, aby wyświetlić lokalizacje folderów środowiska Conda, a następnie ręcznie usuń podfolder dla środowiska z tej lokalizacji.

1. Wybierz pozycję **Utwórz**i sprawdź postęp w oknie **danych wyjściowych** . Dane wyjściowe obejmują kilka instrukcji interfejsu wiersza polecenia po zakończeniu tworzenia:

    ![Pomyślne utworzenie środowiska Conda](media/environments/environments-conda-2-2019.png)

1. W programie Visual Studio można aktywować środowisko Conda dla projektu, tak jak w przypadku każdego innego środowiska, zgodnie z opisem w artykule [Wybieranie środowiska dla projektu](selecting-a-python-environment-for-a-project.md).

1. Aby zainstalować dodatkowe pakiety w środowisku, użyj [karty pakiety](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

> [!Note]
> Aby uzyskać najlepsze wyniki w środowiskach Conda, użyj Conda 4.4.8 lub nowszych (wersje Conda są inne niż wersje Anaconda). Odpowiednie wersje programu Miniconda (Visual Studio 2019) i Anaconda (Visual Studio 2017) można zainstalować za pomocą Instalatora programu Visual Studio.

Aby wyświetlić wersję Conda, gdzie są przechowywane środowiska Conda i inne informacje, uruchom `conda info` w wierszu polecenia Anaconda (czyli w wierszu polecenia, gdzie Anaconda znajduje się w ścieżce):

```cli
conda info
```

Foldery środowiska Conda są wyświetlane w następujący sposób:

```output
       envs directories : C:\Users\user\.conda\envs
                          c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
```

Ponieważ środowiska Conda nie są przechowywane w projekcie, działają podobnie do środowisk globalnych. Na przykład zainstalowanie nowego pakietu w środowisku Conda sprawia, że pakiet jest dostępny dla wszystkich projektów korzystających z tego środowiska.

W przypadku programu Visual Studio 2017 w wersji 15,6 lub starszej można użyć środowisk Conda, wskazując je ręcznie, zgodnie z opisem w sekcji [Ręczne identyfikowanie istniejącego środowiska](#manually-identify-an-existing-environment).

Program Visual Studio 2017 w wersji 15,7 i nowszych wykrywa środowiska Conda automatycznie i wyświetla je w oknie **środowiska języka Python** zgodnie z opisem w następnej sekcji.

## <a name="manually-identify-an-existing-environment"></a>Ręcznie Zidentyfikuj istniejące środowisko

Wykonaj następujące kroki, aby zidentyfikować środowisko zainstalowane w lokalizacji innej niż standardowa (w tym środowiska Conda w programie Visual Studio 2017 w wersji 15,6 i starszej):

::: moniker range="vs-2017"

1. W oknie **środowiska języka Python** wybierz pozycję **+ niestandardowe** , co spowoduje otwarcie karty **Konfiguracja** :

    ![Widok domyślny dla nowego środowiska niestandardowego](media/environments/environments-custom-1.png)

1. W polu **Opis** wprowadź nazwę środowiska.

1. Wprowadź lub Przeglądaj (za pomocą **...**) ścieżkę interpretera w polu **ścieżka prefiksu** .

1. Jeśli program Visual Studio wykryje interpreter języka Python w tym miejscu (na przykład ścieżkę pokazaną poniżej dla środowiska Conda), włącza polecenie **autowykrywania** . Wybór **autowykrywania** uzupełnia pozostałe pola. Te pola można także wykonać ręcznie.

    ![Włączanie autowykrywania polecenia](media/environments/environments-custom-2.png)

    ![Uzupełnianie pól środowiska po użyciu autowykrywania](media/environments/environments-custom-3.png)

1. Gdy pola zawierają odpowiednie wartości, wybierz pozycję **Zastosuj** , aby zapisać konfigurację. Możesz teraz używać środowiska, takiego jak dowolne inne w programie Visual Studio.

1. Jeśli musisz usunąć ręcznie zidentyfikowane środowisko, wybierz polecenie **Usuń** na karcie **Konfiguracja** . automatycznie wykryte środowiska nie zapewniają tej opcji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie karty](python-environments-window-tab-reference.md#configure-tab).

::: moniker-end

::: moniker range=">=vs-2019"

1. Wybierz pozycję **+ Dodaj środowisko** w oknie **środowiska Python** (lub na pasku narzędzi Python), co spowoduje otwarcie okna dialogowego **Dodawanie środowiska** . W tym oknie dialogowym Wybierz kartę **istniejąca środowisko** :

    ![Istniejąca karta środowiska w oknie dialogowym Dodawanie środowiska](media/environments/environments-custom-1-2019.png)

1. Wybierz listę rozwijaną **środowisko** , a następnie wybierz pozycję **niestandardowe**:

    ![Opcja środowiska niestandardowego w oknie dialogowym Dodawanie środowiska](media/environments/environments-custom-2-2019.png)

1. W podanych polach w oknie dialogowym wpisz lub Przeglądaj (przy użyciu **...**) do ścieżki interpretera pod **ścieżką prefiksu**, która wypełnia większość innych pól. Po przejrzeniu tych wartości i zmodyfikowaniu w razie potrzeby wybierz pozycję **Dodaj**. 

    ![Pola, aby określić szczegóły dla opcji środowiska niestandardowego w oknie dialogowym Dodawanie środowiska](media/environments/environments-custom-3-2019.png)

1. Szczegóły środowiska można w dowolnym momencie przejrzeć i zmodyfikować w oknie **środowiska języka Python** . W tym oknie Wybierz środowisko, a następnie wybierz kartę **Konfiguracja** . Po wprowadzeniu zmian wybierz polecenie **Zastosuj** . Środowisko można także usunąć za pomocą polecenia **Usuń** (niedostępne w przypadku środowisk z autowykrywaniem). Aby uzyskać więcej informacji, zobacz [Konfigurowanie karty](python-environments-window-tab-reference.md#configure-tab).
::: moniker-end

## <a name="fix-or-delete-invalid-environments"></a>Popraw lub Usuń nieprawidłowe środowiska

Jeśli program Visual Studio znajdzie wpisy rejestru dla środowiska, ale ścieżka do interpretera jest nieprawidłowa, w oknie środowiska języka **Python** zostanie wyświetlona nazwa z przekreśloną czcionką:

::: moniker range="vs-2017"
![Okno środowiska języka Python przedstawiające nieprawidłowe środowisko](media/environments/environments-invalid-entry.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Okno środowiska języka Python przedstawiające nieprawidłowe środowisko](media/environments/environments-invalid-entry-2019.png)
::: moniker-end

Aby poprawić środowisko, które chcesz zachować, najpierw spróbuj użyć procesu **naprawy** Instalatora. Program instalacyjny dla standardowego języka Python 3. x, na przykład, zawiera tę opcję.

Aby poprawić środowisko, w którym nie jest dostępna opcja naprawy lub aby usunąć nieprawidłowe środowisko, wykonaj następujące kroki, aby bezpośrednio zmodyfikować rejestr. Program Visual Studio automatycznie aktualizuje okno **środowiska Python** , gdy wprowadzisz zmiany w rejestrze.

1. Uruchom *regedit.exe*.
1. Przejdź do **HKEY_LOCAL_MACHINE \software\python** lub **HKEY_CURRENT_USER \software\python**. W przypadku IronPython należy poszukać polecenia **IronPython** .
1. Rozwiń węzeł, który pasuje do dystrybucji, na przykład **Python Core** dla CPython lub **ContinuumAnalytics** dla Anaconda. W przypadku IronPython rozwiń węzeł numer wersji.
1. Sprawdź wartości w węźle **InstallPath** :

    ![Wpisy rejestru dla typowej instalacji CPython](media/environments/environments-registry-entries.png)

    - Jeśli środowisko nadal istnieje na komputerze, Zmień wartość **ścieżka pliku wykonywalnego** na poprawną lokalizację. W razie potrzeby skoryguj również wartości **(domyślne)** i **WindowedExecutablePath** .
    - Jeśli środowisko nie istnieje już na komputerze i chcesz je usunąć z okna **środowiska języka Python** , Usuń węzeł nadrzędny **InstallPath**, taki jak **3,6** na powyższym obrazie.
    - Nieprawidłowe ustawienia w **HKEY_CURRENT_USER \software\python** zastąpić ustawienia w **HKEY_LOCAL_MACHINE \software\python**
    
## <a name="see-also"></a>Zobacz także

- [Instalowanie interpreterów języka Python](installing-python-interpreters.md)
- [Wybieranie interpretera dla projektu](selecting-a-python-environment-for-a-project.md)
- [Użyj requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Dokumentacja okna środowiska Python](python-environments-window-tab-reference.md)
