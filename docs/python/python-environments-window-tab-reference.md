---
title: Dokumentacja okna środowiska Python
description: Szczegółowe informacje na temat każdej karty, która pojawia się w oknie środowiska Python w programie Visual Studio.
ms.date: 03/18/2019
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: f08709c5231b2981db67900f47b49503269e948b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545499"
---
# <a name="python-environments-window-tabs-reference"></a>Dokumentacja kart okna środowiska języka Python

Aby otworzyć okno **środowiska języka Python** :

- Wybierz polecenie **Wyświetl**  >  **inne**  >  **środowiska języka Python** systemu Windows.
- Kliknij prawym przyciskiem myszy węzeł **środowiska Python** dla projektu w **Eksplorator rozwiązań** i wybierz polecenie **Wyświetl wszystkie środowiska Python**.

Po rozwinięciu wystarczającej ilości okna **środowiska Python** te opcje są wyświetlane jako karty, które mogą okazać się wygodniejsze do pracy z programem. W przypadku przejrzystości karty w tym artykule są wyświetlane w widoku rozszerzonym.

::: moniker range="vs-2017"
![Widok rozwinięty okna środowiska języka Python](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Widok rozwinięty okna środowiska języka Python](media/environments/environments-expanded-view-2019.png)
::: moniker-end

## <a name="overview-tab"></a>Karta przegląd

Zawiera podstawowe informacje i polecenia dotyczące środowiska:

::: moniker range="vs-2017"
![Karta przegląd środowiska języka Python](media/environments/environments-overview-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta przegląd środowiska języka Python](media/environments/environments-overview-tab-2019.png)
::: moniker-end

| Polecenie | Opis |
| --- | --- |
| **Ustaw to środowisko jako domyślne dla nowych projektów** | Ustawia aktywne środowisko, które może spowodować, że program Visual Studio (2017 wersja 15,5 i wcześniejszy) przestanie odpowiadać podczas ładowania bazy danych IntelliSense. Środowiska z wieloma pakietami mogą nie odpowiadać na dłużej. |
| **Odwiedź witrynę sieci Web dystrybutora** | Otwiera przeglądarkę pod adresem URL dostarczonym przez dystrybucję języka Python. Na przykład w języku Python 3. x jest to python.org. |
| **Otwórz okno interaktywne** | Otwiera [okno interaktywne (REPL)](python-interactive-repl-in-visual-studio.md) dla tego środowiska w programie Visual Studio, stosując wszystkie [skrypty uruchamiania (patrz poniżej)](#startup-scripts). |
| **Eksploruj skrypty interaktywne** | Zobacz [skrypty uruchamiania](#startup-scripts). |
| **Użyj trybu interaktywnego IPython** | Po ustawieniu program domyślnie otwiera okno **interaktywne** z IPython. Pozwala to na wykresy wbudowane, a także rozszerzoną składnię IPython, taką jak `name?` Wyświetlanie pomocy i `!command` poleceń powłoki. Ta opcja jest zalecana w przypadku korzystania z dystrybucji Anaconda, ponieważ wymaga dodatkowych pakietów. Aby uzyskać więcej informacji, zobacz [Korzystanie z IPython w oknie interaktywnym](interactive-repl-ipython.md). |
| **Otwórz w programie PowerShell** | Uruchamia interpreter w oknie poleceń programu PowerShell. |
| (Linki folderów i programów) | Zapewnianie szybkiego dostępu do folderu instalacyjnego środowiska, interpretera *python.exe* i interpretera *pythonw.exe* . Pierwszy raz zostanie otwarty w Eksploratorze Windows, a druga dwa otwiera okno konsoli. |

### <a name="startup-scripts"></a>Skrypty uruchamiania

Gdy korzystasz z interaktywnego systemu Windows w codziennym przepływie pracy, najkorzystniej opracowujesz funkcje pomocnika, które są regularnie używane. Można na przykład utworzyć funkcję otwierającą ramkę danych w programie Excel, a następnie zapisać ten kod jako skrypt uruchamiania, aby był on zawsze dostępny w oknie **interaktywnym** .

Skrypty uruchamiania zawierają kod, który okno **interaktywne** ładuje i uruchamia automatycznie, w tym Importy, definicje funkcji i dosłownie inne elementy. Takie skrypty są przywoływane na dwa sposoby:

1. Po zainstalowaniu środowiska program Visual Studio tworzy folder *Documents\Visual Studio \<version> \Python \\ \<environment> scripts* , w którym jest to wersja programu &lt; &gt; Visual Studio (na przykład 2017 lub 2019), a &lt; środowisko jest &gt; zgodne z nazwą środowiska. Możesz łatwo przejść do folderu specyficznego dla środowiska za pomocą polecenia **Eksploruj skrypty interaktywne** . Po uruchomieniu **interaktywnego** okna dla tego środowiska są ładowane i *uruchamiane niezależnie od* tego, czy w porządku alfabetycznym znajdują się pliki o określonej godzinie.

1. Kontrolka **skrypty** w obszarze **Narzędzia**  >  **Opcje**  >  **Python**  >  **Interactive Windows** karta (zobacz [interaktywne Opcje systemu Windows](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)) służy do określania dodatkowego folderu dla skryptów uruchamiania ładowanych i uruchamianych we wszystkich środowiskach. Jednak ta funkcja nie działa w obecnym czasie.

## <a name="configure-tab"></a>Konfiguruj kartę

Jeśli jest dostępna, karta **Konfiguracja** zawiera szczegółowe informacje zgodnie z opisem w poniższej tabeli. Jeśli ta karta nie jest obecna, oznacza to, że program Visual Studio zarządza wszystkimi szczegółami automatycznie.

::: moniker range="vs-2017"
![Karta Konfigurowanie środowisk języka Python](media/environments/environments-configure-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta Konfigurowanie środowisk języka Python](media/environments/environments-configure-tab-2019.png)
::: moniker-end

| Pole | Opis |
| --- | --- |
| **Opis** | Nazwa, która ma zostać nadana środowisku. |
| **Ścieżka prefiksu** | Podstawowa lokalizacja folderu interpretera. Wypełniając tę wartość i klikając pozycję **Autowykrywanie**, program Visual Studio próbuje wypełnić inne pola. |
| **Ścieżka interpretera** | Ścieżka do pliku wykonywalnego interpretera, zwykle ścieżki prefiksu, po którym następuje **python.exe** |
| **Interpreter okna** | Ścieżka do pliku wykonywalnego, który nie jest konsolą, często ścieżki prefiksu, po którym następuje **pythonw.exe**. |
| **Ścieżka biblioteki**<br/>(jeśli jest dostępny) | Określa katalog główny biblioteki standardowej, ale ta wartość może zostać zignorowana, jeśli program Visual Studio może zażądać bardziej dokładnej ścieżki od interpretera. |
| **Wersja językowa** | Wybrane z menu rozwijanego. |
| **Architektura** | Zwykle wykrywane i wypełniane automatycznie; w przeciwnym razie określa **32-bitowe** lub **64-bitowe**. |
| **Zmienna środowiskowa Path** | Zmienna środowiskowa, której interpreter używa do znajdowania ścieżek wyszukiwania. Program Visual Studio zmienia wartość zmiennej podczas uruchamiania języka Python, aby zawierała ścieżki wyszukiwania projektu. Zazwyczaj ta właściwość powinna być ustawiona na **PYTHONPATH**, ale niektóre interpretery używają innej wartości. |

## <a name="packages-tab"></a>Karta pakiety

*Również etykieta "PIP" we wcześniejszych wersjach.*

Zarządza pakietami zainstalowanymi w środowisku przy użyciu funkcji PIP (karta **pakiety (PyPI)** lub Conda ( **pakiety (Conda)** na karcie środowiska Conda w programie Visual Studio 2017 w wersji 15,7 i nowszych). Na tej karcie można również wyszukiwać i instalować nowe pakiety, w tym ich zależności.

Pakiety, które są już zainstalowane, są wyświetlane z kontrolkami do zaktualizowania (Strzałka w górę) i dezinstalacji (X w okręgu) pakietu:

![Karta pakiety środowisk Python](media/environments/environments-pip-tab-controls.png)

Wprowadzenie terminu wyszukiwania umożliwia filtrowanie listy zainstalowanych pakietów oraz pakietów, które można zainstalować z PyPI.

::: moniker range="vs-2017"
![Karta pakiety środowiska Python z wyszukiwaniem "num"](media/environments/environments-pip-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta pakiety środowiska Python z wyszukiwaniem "num"](media/environments/environments-pip-tab-2019.png)
::: moniker-end

Jak widać na powyższym obrazie, wyniki wyszukiwania pokazują liczbę pakietów pasujących do terminu wyszukiwania. pierwszy wpis na liście jest jednak poleceniem do uruchomienia programu **pip install \<name> ** . Jeśli korzystasz z karty **pakiety (Conda)** , zamiast tego zobaczysz pozycję **Conda \<name> Install **:

::: moniker range="vs-2017"
![Karta pakiety Conda przedstawiające polecenie instalacji Conda](media/environments/environments-conda-tab-install.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta pakiety Conda przedstawiające polecenie instalacji Conda](media/environments/environments-conda-tab-install-2019.png)
::: moniker-end

W obu przypadkach instalacja może zostać dostosowana przez dodanie argumentów w polu wyszukiwania po nazwie pakietu. Po dołączeniu argumentów wyniki wyszukiwania pokazują instalację **PIP** lub **instalację Conda** , a następnie zawartość pola wyszukiwania:

::: moniker range="vs-2017"
![Używanie argumentów w poleceniach instalacji PIP i Conda](media/environments/environments-pip-tab-arguments.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Używanie argumentów w poleceniach instalacji PIP i Conda](media/environments/environments-pip-tab-arguments-2019.png)
::: moniker-end

Zainstalowanie pakietu tworzy podfoldery w folderze *lib* środowiska w systemie plików. Na przykład jeśli masz zainstalowany język Python 3,6 w *c:\Python36*, pakiety są instalowane w *c:\Python36\Lib*; Jeśli zainstalowano program Anaconda3 w *katalogu C:\Program Files\Anaconda3* , pakiety są instalowane w *katalogu c:\Program Files\Anaconda3\Lib*. W przypadku środowisk Conda pakiety są instalowane w folderze tego środowiska.

### <a name="grant-administrator-privileges-for-package-install"></a>Przyznaj uprawnienia administratora na potrzeby instalacji pakietu

W przypadku instalowania pakietów w środowisku, które znajduje się w chronionym obszarze systemu plików, na przykład *C:\Program Files\Anaconda3\Lib*, program Visual Studio musi `pip install` zostać uruchomiony z podwyższonym poziomem uprawnień, aby umożliwić mu Tworzenie podfolderów pakietów. Gdy wymagane jest podniesienie uprawnień, program Visual Studio wyświetli monit, **Aby zainstalować, zaktualizować lub usunąć pakiety dla tego środowiska, może być wymagane uprawnienia administratora**.

![Monit o podniesienie uprawnień dla instalacji pakietu](media/environments/environments-pip-elevate.png)

**Podwyższanie poziomu teraz** przyznaje uprawnienia administracyjne do PIP dla pojedynczej operacji, z uwzględnieniem również wszelkich wierszy systemu operacyjnego w celu uzyskania uprawnień. Wybranie pozycji **Kontynuuj bez uprawnień administratora** próbuje zainstalować pakiet, ale w przypadku próby utworzenia folderów z danymi wyjściowymi, takich jak **błąd: nie można utworzyć folderu "C:\Program Files\Anaconda3\Lib\site-packages\png.py": Brak uprawnień.**

Wybranie opcji **zawsze Podnieś poziom uprawnień podczas instalowania lub usuwania pakietów** uniemożliwia wyświetlanie okna dialogowego dla danego środowiska. Aby ponownie wyświetlić okno dialogowe, przejdź do opcji **Narzędzia**  >  **Opcje**  >  **Python**  >  **Ogólne** i wybierz przycisk, **Zresetuj wszystkie trwale ukryte okna dialogowe**.

Na tej samej karcie **Opcje** można również wybrać opcję **Zawsze uruchamiaj PIP jako administrator** , aby pominąć okno dialogowe dla wszystkich środowisk. Zobacz [Opcje — Karta Ogólne](python-support-options-and-settings-in-visual-studio.md#general-options).

### <a name="security-restrictions-with-older-versions-of-python"></a>Ograniczenia zabezpieczeń ze starszymi wersjami języka Python

W przypadku korzystania z języków Python 2,6, 3,1 i 3,2 program Visual Studio wyświetla ostrzeżenie, **ze względu na nowe ograniczenia zabezpieczeń, instalowanie z Internetu może nie funkcjonować w tej wersji języka Python**:

![Komunikat dotyczący ograniczeń instalacji PIP przy użyciu starszej wersji języka Python](media/environments/environments-old-version-restriction.png)

Przyczyną tego ostrzeżenia jest to, że w przypadku tych starszych wersji języka Python `pip install` nie jest obsługiwana warstwa zabezpieczeń transportu (TLS) 1,2, która jest wymagana do pobierania pakietów ze źródła pakietu, PyPi.org. Niestandardowe kompilacje w języku Python mogą obsługiwać protokoły TLS 1,2, w których `pip install` może to być możliwe.

Można pobrać odpowiednie *Get-PIP.py* pakietu z [Bootstrap.pypa.IO](https://bootstrap.pypa.io/), ręcznie pobrać pakiet z [PyPi.org](https://pypi.org/), a następnie zainstalować pakiet z tej kopii lokalnej.

Zaleca się jednak po prostu uaktualnienie do języka Python 2,7 lub 3.3 +, w tym przypadku ostrzeżenie nie pojawia się.

::: moniker range="vs-2017"
## <a name="intellisense-tab"></a>Karta IntelliSense

Pokazuje bieżący stan bazy danych uzupełniania IntelliSense:

![Karta IntelliSense środowiska Python](media/environments/environments-intellisense-tab.png)

- W programie Visual Studio 2017 w wersji 15,5 i starszych wersje zaawansowania funkcji IntelliSense zależą od bazy danych, która została skompilowana dla tej biblioteki. Kompilowanie bazy danych odbywa się w tle, gdy biblioteka jest zainstalowana, ale może zająć trochę czasu i może nie zostać ukończona po rozpoczęciu pisania kodu.
- Program Visual Studio 2017 w wersji 15,6 lub nowszej używa szybszej metody, aby zapewnić uzupełnianie, które nie zależą domyślnie od bazy danych. Z tego powodu karta jest oznaczona jako **IntelliSense [baza danych jest wyłączona]**. Bazę danych można włączyć, usuwając zaznaczenie opcji **Narzędzia**w języku  >  **Options**  >  **Python**  >  **eksperymentalne**  >  **Używanie nowego stylu IntelliSense dla środowisk**.

Kiedy program Visual Studio wykrywa nowe środowisko (lub dodaje je), automatycznie rozpoczyna Kompilowanie bazy danych przez analizowanie plików źródłowych biblioteki. Ten proces może potrwać od minuty do godziny lub dłużej, w zależności od tego, co jest zainstalowane. (Anaconda, na przykład, zawiera wiele bibliotek i zajmuje trochę czasu na skompilowanie bazy danych). Po zakończeniu otrzymasz szczegółową funkcję IntelliSense i nie trzeba ponownie odświeżyć bazy danych (za pomocą przycisku **Odśwież bazę danych** ) do momentu zainstalowania większej liczby bibliotek.

Biblioteki, dla których dane nie zostały skompilowane, są oznaczone symbolem **!**; Jeśli baza danych środowiska nie została ukończona, **!** obok niego pojawia się również na liście środowisko główne.

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Zarządzanie środowiskami języka Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Wybieranie interpretera dla projektu](selecting-a-python-environment-for-a-project.md)
- [Użyj requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
