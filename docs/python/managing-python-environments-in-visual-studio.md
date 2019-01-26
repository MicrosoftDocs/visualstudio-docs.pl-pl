---
title: Zarządzanie środowiskami Python i tłumaczy
description: Użyj okna środowiska Python, aby zarządzać globalnym, wirtualnych i środowisk conda, instalowanie interpreterów języka Python i pakietów i przypisywanie środowisk do projektów programu Visual Studio.
ms.date: 12/07/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: e883cb199ca2959015dac0c6492d19e7875c5ca1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958787"
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

> [!Note]
> Nie można zarządzać środowiskami dla kodu Python, który zostanie otwarty tylko w folderze przy użyciu **pliku** > **Otwórz** > **folderu** polecenia. Zamiast tego [Tworzenie projektu języka Python z istniejącego kodu](quickstart-01-python-in-visual-studio-project-from-existing-code.md) w celu korzystania z funkcji środowiska Visual Studio.

## <a name="the-python-environments-window"></a>W oknie środowiska Python

*(Visual Studio 15.8 stanowią zrzuty ekranu, przedstawione w tej sekcji. Możesz zobaczyć różne interfejsu użytkownika w zależności od używanej wersji programu Visual Studio.)*

Środowiska, w których obsługującemu programu Visual Studio są wyświetlane w **środowiska Python** okna. Aby otworzyć okno, użyj jednej z następujących metod:

- Wybierz **widoku** > **Windows inne** > **środowiska Python** polecenia menu.
- Kliknij prawym przyciskiem myszy **środowiska Python** węzeł projektu w **Eksploratora rozwiązań** i wybierz **wyświetlanie wszystkich środowisk języka Python**:

    ![Wyświetl polecenie wszystkich środowisk w Eksploratorze rozwiązań](media/environments-view-all.png)

W obu przypadkach **środowiska Python** razem zostanie wyświetlone okno **Eksploratora rozwiązań**:

![Okno środowiska Python](media/environments-default-view.png)

Visual Studio szuka zainstalowanych globalnego środowisk za pomocą rejestru (następujących [514 program ten](https://www.python.org/dev/peps/pep-0514/)), oraz środowisk wirtualnych i środowisk conda (zobacz [typów środowisk](#types-of-environments)). Jeśli nie widzisz oczekiwanego środowiska na liście, zobacz [ręcznie Zidentyfikuj istniejące środowisko](#manually-identify-an-existing-environment).

Po wybraniu środowisko na liście programu Visual Studio Wyświetla różnych właściwości i poleceń dla danego środowiska na **Przegląd** kartę. Na przykład widać na ilustracji powyżej to lokalizacja interpreter *C:\Python36-32*. Czterech poleceń w dolnej części **Przegląd** kartę każdego Otwórz wiersz polecenia z interpreterem uruchomiona. Aby uzyskać więcej informacji, zobacz [odniesienie do karty okna dla środowiska Python — omówienie](python-environments-window-tab-reference.md#overview-tab).

Użyj listy rozwijanej poniżej listy środowisk Aby przełączyć się do różnych kartach zawierających takie jak **pakietów**, i **IntelliSense**. Te karty są także opisane w [dokumentacja karcie okna środowiska Python](python-environments-window-tab-reference.md).

Wybierając środowisko nie zmienia jej relacji żadne projekty. Domyślne środowisko wyświetlany czcionką pogrubioną na liście jest tą, która korzysta z programu Visual Studio dla żadnych nowych projektów. Aby użyć innego środowiska za pomocą nowych projektów, użyj **upewnij się, to środowisko domyślne dla nowych projektów** polecenia. W kontekście projektu należy zawsze wybrać określonego środowiska. Aby uzyskać więcej informacji, zobacz [wybierz środowisko dla projektu](selecting-a-python-environment-for-a-project.md).

Z prawej strony każdego wymienionych środowiska jest formant, który otwiera **Interactive** okna dla danego środowiska. (W Visual Studio 2017 15.5 i starszych, inny formant wyświetlany jest odświeża bazy danych IntelliSense dla danego środowiska. Zobacz [dokumentacja karcie okna środowiska](python-environments-window-tab-reference.md#intellisense-tab) szczegółowe informacje o bazie danych.)

> [!Tip]
> Po rozwinięciu **środowiska Python** okna dostatecznie szerokie, otrzymasz pełniejszego wglądu środowiska, które mogą okazać się bardziej wygodne do pracy z.
>
> ![Widok rozszerzony okna środowiska Python](media/environments-expanded-view.png)

> [!Note]
> Mimo że program Visual Studio przestrzega opcję pakiety systemu lokacji, nie udostępnia sposób, aby zmienić go z poziomu programu Visual Studio.

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "Obejrzyj klip wideo") | [Obejrzyj film wideo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) na środowiska Python w programie Visual Studio (2 mln 35s).|

### <a name="what-if-no-environments-appear"></a>Co zrobić, jeśli są wyświetlane nie środowisk?

Jeśli pojawia się nie środowisk, oznacza to, że program Visual Studio nie można wykryć wszelkie instalacje języka Python w lokalizacjach. Na przykład można mieć zainstalowany program Visual Studio 2017 ale wyczyszczone wszystkie opcje interpreter w opcjach Instalatora dla obciążenie języka Python. Podobnie, może zainstalować programu Visual Studio 2015 lub starszym, ale nie zainstalował tłumacza ręcznie (zobacz [Python Zainstaluj interpretery](installing-python-interpreters.md)).

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

Środowiska conda jest utworzony przy użyciu `conda` narzędzia lub za pomocą zintegrowanego narzędzia conda zarządzania w programie Visual Studio 2017 w wersji 15.7 lub nowszej. (Wymaga pakietu Anaconda lub Miniconda; Anaconda jest dostępna za pośrednictwem Instalatora programu Visual Studio, zobacz [instalacji — Visual Studio 2017](installing-python-support-in-visual-studio.md#visual-studio-2017).)

1. Wybierz **+ Utwórz środowisko conda** w **środowiska Python** okna, co spowoduje otwarcie **Tworzenie nowego środowiska conda** karty:

    ![Utwórz kartę dla nowego środowiska conda](media/environments-conda-1.png)

1. Wprowadź nazwę środowiska w **nazwa** Wybierz podstawowy interpreter języka Python w **Python** i wybierz przycisk **Utwórz**.

1. **Dane wyjściowe** okna jest przedstawiony postęp dla nowego środowiska w kilku instrukcje interfejsu wiersza polecenia po ukończeniu tworzenia:

    ![Pomyślne utworzenie środowiska conda](media/environments-conda-2.png)

1. W programie Visual Studio, można uaktywnić środowiska conda, dla projektu, tak jak dowolnego innego środowiska, zgodnie z opisem na [wybierz środowisko dla projektu](selecting-a-python-environment-for-a-project.md).

1. Aby zainstalować pakiety w środowisku, należy użyć [karcie pakiety](python-environments-window-tab-reference.md#packages-tab).

> [!Note]
> Aby uzyskać najlepsze wyniki za pomocą środowisk conda, użyj conda 4.4.8 lub nowszej (wersje conda różnią się od wersji pakietu Anaconda). Instalowanie pakietu Anaconda 5.1 za pomocą Instalatora programu Visual Studio 2017.

Aby wyświetlić wersję conda, gdzie są przechowywane środowisk conda, oraz inne informacje, uruchom `conda info` Anaconda z wiersza polecenia (czyli wiersz polecenia gdzie Anaconda znajduje się w ścieżce):

```cli
conda info
```

Foldery środowiska conda są wyświetlane w następujący sposób:

```output
       envs directories : c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
                          C:\Users\user\.conda\envs
```

Ponieważ środowisk conda nie są przechowywane w projekcie, działają podobnie do globalnego środowisk. Na przykład instalowanie nowego pakietu do środowiska conda udostępnia tego pakietu do wszystkich projektów przy użyciu tego środowiska.

Dla programu Visual Studio 2017 w wersji 15.6 i starszych, można użyć środowisk conda, wskazując je ręcznie, zgodnie z opisem w obszarze [ręcznie Zidentyfikuj istniejące środowisko](#manually-identify-an-existing-environment).

Visual Studio 2017 w wersji 15.7 lub nowszej automatycznie wykrywa środowisk conda i wyświetla je w **środowiska Python** okna zgodnie z opisem w następnej sekcji.

## <a name="manually-identify-an-existing-environment"></a>Ręcznie Zidentyfikuj istniejące środowisko

Wykonaj następujące kroki, aby zidentyfikować środowisku, w którym jest zainstalowany w niestandardowej lokalizacji (w tym środowisk conda w Visual Studio 2017 w wersji 15.6 i starszych):

1. Wybierz **+ niestandardowe** w **środowiska Python** okna, co spowoduje otwarcie **Konfiguruj** karty:

    ![Widok domyślny dla nowego środowiska niestandardowego](media/environments-custom-1.png)

1. Wprowadź nazwę środowiska w **opis** pola.

1. Wpisz lub Przeglądaj (przy użyciu **...** ) do ścieżki interpreter w **ścieżka prefiksu** pola.

1. Jeśli program Visual Studio wykryje interpreter języka Python w tej lokalizacji (np. ścieżka poniżej dla środowiska conda), umożliwia **Autowykrywanie** polecenia. Wybieranie **Autowykrywanie** kończy pozostałych pól. Te pola można również wykonać ręcznie.

    ![Włączanie polecenia automatyczne wykrywanie](media/environments-custom-2.png)

    ![Uzupełnianie pól środowiska po zakończeniu korzystania z automatycznego wykrywania](media/environments-custom-3.png)

1. Po pola zawierają wartości, które mają, wybierz **Zastosuj** Aby zapisać konfigurację. Można teraz używać środowiska, podobnie jak każdy inny w programie Visual Studio.

1. Jeśli musisz usunąć ręcznie zidentyfikowanych środowiska, wybierz opcję **Usuń** na polecenia **Konfiguruj** kartę. Automatycznie wykryte środowiska nie zapewniają tej opcji. Aby uzyskać więcej informacji, zobacz [karty Konfigurowanie](python-environments-window-tab-reference.md#configure-tab).

## <a name="fix-or-delete-invalid-environments"></a>Napraw lub Usuń nieprawidłowe środowisk

Jeśli program Visual Studio znajdzie wpisy rejestru dla środowiska, ale ścieżka do interpretera jest nieprawidłowa, a następnie **środowiska Python** okno zawiera nazwę przy użyciu czcionki przekreślenie:

![W oknie środowiska Python wyświetlane nieprawidłowe środowisko](media/environments-invalid-entry.png)

Aby poprawić środowisko, które chcesz zachować, najpierw spróbuj użyć jego Instalatora **naprawy** procesu. Instalatory dla standardowego języka Python 3.x, na przykład uwzględnić tę opcję.

Aby poprawić środowisko, która nie ma opcji naprawy lub usunąć nieprawidłowe środowisko, wykonaj następujące kroki, aby zmodyfikować rejestr bezpośrednio. Program Visual Studio automatycznie aktualizuje **środowiska Python** okna po wprowadzeniu zmian w rejestrze.

1. Uruchom *regedit.exe*.
1. Przejdź do **HKEY_LOCAL_MACHINE\SOFTWARE\Python** dla 32-bitowego interpretery, lub **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** dla 64-bitowego interpretery. IronPython, znaleźć **IronPython** zamiast tego.
1. Rozwiń węzeł, który pasuje do dystrybucji, taką jak **PythonCore** dla języka CPython lub **ContinuumAnalytics** dla pakietu Anaconda. W przypadku IronPython rozwiń węzeł numeru wersji.
1. Sprawdź wartości w polach **InstallPath** węzła:

    ![Wpisy rejestru dla typowej instalacji języka CPython](media/environments-registry-entries.png)

    - Jeśli środowisko jest nadal istnieje na komputerze, należy zmienić wartość **ExecutablePath** na poprawną lokalizację. Również poprawić **(opcja domyślna)** i **WindowedExecutablePath** wartości zgodnie z potrzebami.
    - Jeśli środowisko już nie istnieje na komputerze i chcesz usunąć go z **środowiska Python** okna, Usuń węzeł nadrzędny **InstallPath**, takich jak **3.6** na powyższej ilustracji.

## <a name="see-also"></a>Zobacz także

- [Zainstaluj interpretery języka Python](installing-python-interpreters.md)
- [Wybierz interpreter dla projektu](selecting-a-python-environment-for-a-project.md)
- [Użyj pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Dokumentacja okna środowiska Python](python-environments-window-tab-reference.md)
