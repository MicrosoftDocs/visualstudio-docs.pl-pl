---
title: Dokumentacja okna środowiska Python
description: Szczegółowe informacje dotyczące każdej z kart, które są wyświetlane w oknie środowiska Python w programie Visual Studio.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 578f73aabfb8b5a4c8336c8611f634b8947c8885
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59366526"
---
# <a name="python-environments-window-tabs-reference"></a>Dokumentacja karty okna środowiska Python

Aby otworzyć **środowiska Python** okna:

- Wybierz **widoku** > **Windows inne** > **środowiska Python** polecenia menu.
- Kliknij prawym przyciskiem myszy **środowiska Python** węzeł projektu w **Eksploratora rozwiązań** i wybierz **wyświetlanie wszystkich środowisk języka Python**.

Po rozwinięciu **środowiska Python** dostatecznie szerokie okna, te opcje są wyświetlane jako kart, które może się okazać bardziej wygodne do pracy z. W celu uściślenia karty, w tym artykule są wyświetlane w widoku rozszerzonym.

::: moniker range="vs-2017"
![Widok rozszerzony okna środowiska Python](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Widok rozszerzony okna środowiska Python](media/environments/environments-expanded-view-2019.png)
::: moniker-end

## <a name="overview-tab"></a>Karta Przegląd

Zawiera podstawowe informacje i poleceń dla środowiska:

::: moniker range="vs-2017"
![Karta Przegląd środowiska Python](media/environments/environments-overview-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta Przegląd środowiska Python](media/environments/environments-overview-tab-2019.png)
::: moniker-end

| Polecenie | Opis |
| --- | --- |
| **Należy to środowisko domyślne dla nowych projektów** | Ustawia aktywnego środowiska może spowodować, że program Visual Studio (2017 w wersji 15.5 i starszych) krótko przestanie przestać odpowiadać podczas ładowania bazy danych IntelliSense. W środowiskach z wielu pakietów, może być nieodpowiadająca przez dłuższy czas. |
| **Odwiedź witrynę sieci Web dystrybutora** | Otworzy w przeglądarce adres URL podany przez funkcję dystrybucji języka Python. Python 3.x, na przykład, przechodzi do python.org. |
| **Otwórz okno interaktywne** | Otwiera [okna interaktywnego (REPL)](python-interactive-repl-in-visual-studio.md) dla tego środowiska w programie Visual Studio stosowania [skrypty uruchamiania (patrz poniżej)](#startup-scripts). |
| **Eksploruj interaktywne skrypty** | Zobacz [skrypty uruchamiania](#startup-scripts). |
| **Użyj trybu interaktywnego IPython** | Po ustawieniu, zostanie otwarty **Interactive** okna z powłoką IPython domyślnie. Dzięki temu powierzchni wbudowane, a także rozszerzone składni IPython takich jak `name?` Aby wyświetlić Pomoc i `!command` dla poleceń powłoki. Ta opcja jest zalecana, gdy za pomocą dystrybucji pakietu Anaconda, ponieważ wymaga dodatkowych pakietów. Aby uzyskać więcej informacji, zobacz [IPython użycia w oknie interaktywnym](interactive-repl-ipython.md). |
| **Otwórz w programie PowerShell** | Uruchamia interpreter w okno poleceń programu PowerShell. |
| (Folder i program łącza) | Zapewniają szybki dostęp do folderu instalacji środowiska, *python.exe* interpretera i *pythonw.exe* interpretera. Pierwszy otwiera w Eksploratorze Windows, w dwóch ostatnich przypadkach Otwórz okno konsoli. |

### <a name="startup-scripts"></a>Skrypty uruchamiania

W codziennym przepływie pracy, wykorzystywane są interaktywnych okien, prawdopodobnie należy opracować funkcji pomocnika, które regularnie używane. Na przykład, może utworzyć funkcję, która otwiera ramkę danych w programie Excel, a następnie zapisz ten kod jako skrypt do uruchomienia, aby zawsze jest dostępna w **Interactive** okna.

Skrypty uruchamiania zawierają kod, który **Interactive** okna ładuje i uruchamia się automatycznie, w tym importów, definicje funkcji i dosłownie czymkolwiek. Te skrypty są przywoływane na dwa sposoby:

1. Podczas instalowania środowiska Visual Studio tworzy folder *Documents\Visual Studio \<wersji > Skrypty \Python\\\<środowiska >* gdzie &lt;wersji&gt; jest wersja programu Visual Studio (na przykład 2017 lub 2019 r) i &lt;środowiska&gt; jest zgodna z nazwą środowiska. Łatwo można przejść do folderu określonego środowiska z **Eksploruj interaktywne skrypty** polecenia. Po uruchomieniu **Interactive** okna dla danego środowiska, ładuje i uruchamia niezależnie od rodzaju *PY* pliki znajdują się w tym miejscu w kolejności alfabetycznej.

1. **Skrypty** w kontrolce **narzędzia** > **opcje** > **Python**  >  **Interaktywne Windows** kartę (zobacz [opcje interaktywnych okien](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)) należy podać folder dodatkowe skrypty uruchamiania, które są ładowane i uruchamiać we wszystkich środowiskach. Jednak ta funkcja nie działa w chwili obecnej.

## <a name="configure-tab"></a>Karta Konfigurowanie

Jeśli to możliwe, **Konfiguruj** karta zawiera szczegóły, zgodnie z opisem w poniższej tabeli. Jeśli na tej karcie nie jest obecny, oznacza to, czy Visual Studio automatycznie zarządza wszystkie szczegółowe informacje.

::: moniker range="vs-2017"
![Karta Konfigurowanie środowiska Python](media/environments/environments-configure-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta Konfigurowanie środowiska Python](media/environments/environments-configure-tab-2019.png)
::: moniker-end

| Pole | Opis |
| --- | --- |
| **Opis** | Nazwa do nadania środowiska. |
| **Ścieżka prefiksu** | Lokalizacja folderu podstawowego interpretera. Wypełnianie tej wartości, a następnie klikając pozycję **Autowykrywanie**, Visual Studio polegające na próbie wypełnienia w pozostałych polach za Ciebie. |
| **Cesta k interpretu** | Ścieżka do pliku wykonywalnego interpretera często ścieżka prefiksu następuje **python.exe** |
| **Interpreter okna** | Ścieżka do konsoli bez pliku wykonywalnego, często następuje ścieżka prefiksu **pythonw.exe**. |
| **Ścieżka biblioteki**<br/>(jeśli jest dostępny) | Określa katalog główny biblioteki standardowej, ale ta wartość może być ignorowany, jeśli program Visual Studio jest w stanie poprosić bardziej precyzyjne ścieżka interpretera. |
| **Wersja językowa** | Wybranie z menu rozwijanego. |
| **Architektura** | Zwykle wykrywane i automatycznie wypełniane, w przeciwnym razie Określa **32-bitowych** lub **64-bitowych**. |
| **Zmiennej środowiskowej PATH** | Zmienna środowiskowa interpreter używane do wyszukiwania ścieżki wyszukiwania. Program Visual Studio zmienia wartość zmiennej, podczas uruchamiania Python tak, aby zawierała ścieżek wyszukiwania projektu. Zazwyczaj ta właściwość powinna być równa **PYTHONPATH**, ale niektóre interpretery użycie innej wartości. |

## <a name="packages-tab"></a>Karta pakietów

*We wcześniejszych wersjach, również oznaczone jako "pip".*

Zarządza pakiety zainstalowane w środowisku przy użyciu narzędzia pip ( **pakietów (PyPI)** karty) lub conda ( **pakietów (Conda)** karty dla środowisk conda, w programie Visual Studio 2017 wersji 15.7 lub nowszej). Na tej karcie można również wyszukać i zainstalować nowe pakiety, wraz z ich zależnościami.

Pakiety, które są już zainstalowane są wyświetlane z kontrolkami, aby zaktualizować (Strzałka w górę) i Odinstaluj (X okrąg) pakietu:

![Karta pakietów środowiska Python](media/environments/environments-pip-tab-controls.png)

Wprowadzenie filtry termin wyszukiwania listę zainstalowanych pakietów, a także pakietów, które mogą być instalowane z PyPI.

::: moniker range="vs-2017"
![Karta pakietów środowiska Python za pomocą wyszukiwania na "liczba"](media/environments/environments-pip-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta pakietów środowiska Python za pomocą wyszukiwania na "liczba"](media/environments/environments-pip-tab-2019.png)
::: moniker-end

Jak widać na ilustracji powyżej, w wynikach wyszukiwania wyświetlić liczbę pakietów, które pasują do szukanego terminu; pierwszy wpis na liście jest jednak polecenie do uruchomienia **pip install \<name >** bezpośrednio. Jeśli używasz **pakietów (Conda)** kartę, zamiast tego zobacz **zainstalować narzędzia conda \<nazwa >**:

::: moniker range="vs-2017"
![Karta pakiety Conda przedstawiający conda polecenie instalacji](media/environments/environments-conda-tab-install.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta pakiety Conda przedstawiający conda polecenie instalacji](media/environments/environments-conda-tab-install-2019.png)
::: moniker-end

W obu przypadkach można dostosować instalację, dodając argumentów w polu wyszukiwania, po nazwie pakietu. Po dołączeniu argumentów w wynikach wyszukiwania pokazuje **pip install** lub **zainstalować narzędzia conda** następuje zawartość pola wyszukiwania:

::: moniker range="vs-2017"
![Na polecenia instalacji narzędzia pip i conda przy użyciu argumentów](media/environments/environments-pip-tab-arguments.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Na polecenia instalacji narzędzia pip i conda przy użyciu argumentów](media/environments/environments-pip-tab-arguments-2019.png)
::: moniker-end

Instalowanie pakietu tworzy oddzielne podfoldery w tym środowisku *Lib* folder w systemie plików. Na przykład, jeśli masz zainstalowane środowisko Python 3.6 w *c:\Python36*, pakiety są instalowane w *c:\Python36\Lib*; Jeśli masz zainstalowany w Anaconda3 *c:\Program Files\Anaconda3*, a następnie pakiety są instalowane w *c:\Program Files\Anaconda3\Lib*. W przypadku środowisk conda pakiety są instalowane w folderze tego środowiska.

### <a name="grant-administrator-privileges-for-package-install"></a>Udzielanie uprawnień administratora dla pakietu instalacji

Podczas instalowania pakietów w środowisku, w którym znajduje się w obszaru chronionego systemu plików, takich jak *c:\Program Files\Anaconda3\Lib*, należy uruchomić program Visual Studio `pip install` podwyższonym poziomem uprawnień, aby zezwalała na utworzyć podfoldery, pakietu. Gdy wymagana jest podniesienie uprawnień, program Visual Studio wyświetli monit, **może być wymagane uprawnienia administratora, aby zainstalować, zaktualizować lub usunąć pakiety dla tego środowiska**:

![Monit o podniesienie uprawnień dla instalacji pakietu aktualizacji](media/environments/environments-pip-elevate.png)

**Podnieś uprawnienia teraz** udziela uprawnień administracyjnych do narzędzia pip dla jednej operacji podmiotu również na dowolnym systemie operacyjnym, wyświetla monit o uprawnienia. Wybieranie **Kontynuuj bez uprawnień administratora** próby instalacji pakietu, ale narzędzie pip kończy się niepowodzeniem podczas próby takich jak tworzenie folderów z danymi wyjściowymi **błąd: nie można utworzyć "C:\Program Files\Anaconda3\Lib\ Site-packages\png.py ": Odmowa uprawnień.**

Wybieranie **zawsze podniesienie poziomu podczas instalowania lub usuwania pakietów** zapobiega wyświetlaniu w środowisku okna dialogowego. Aby ponownie wyświetlone okno dialogowe, przejdź do **narzędzia** > **opcje** > **Python** > **ogólne**i wybierz przycisk, **zresetować wszystkie okna dialogowe trwale ukryty**.

W tym samym **opcje** karty, możesz również wybrać **pip są zawsze uruchamiane jako administrator** do pomijania w oknie dialogowym dla wszystkich środowisk. Zobacz [opcje — karta Ogólne](python-support-options-and-settings-in-visual-studio.md#general-options).

### <a name="security-restrictions-with-older-versions-of-python"></a>Ograniczenia zabezpieczeń ze starszymi wersjami języka Python

Korzystając z języka Python 2.6, 3.1 i 3.2, Visual Studio wyświetla ostrzeżenie, **ze względu na nowe ograniczenia zabezpieczeń, instalowanie z Internetu może nie działać w tej wersji języka Python**:

![Komunikat dotyczący pip instalowanie ograniczenia przy użyciu starszej wersji języka Python](media/environments/environments-old-version-restriction.png)

Przyczyna to ostrzeżenie jest to, że z tych starszych wersji języka Python, `pip install` nie zawiera obsługę dla zabezpieczeń TLS (Transport Layer) 1.2, który jest wymagany do pobierania pakietów ze źródła pakietu, pypi.org. Niestandardowe kompilacje języka Python może obsługiwać protokół TLS 1.2 w którym to przypadku `pip install` mogą działać.

Może być możliwe pobranie odpowiedniego *get pip.py* pakietu z [bootstrap.pypa.io](https://bootstrap.pypa.io/), ręcznie Pobierz pakiet z [pypi.org](https://pypi.org/), a następnie zainstaluj pakiet z tej lokalnej kopii.

Zalecenia, jednak jest po prostu uaktualnić do środowisko Python 2.7 lub 3.3 +, w którym nie ma przypadków to ostrzeżenie.

::: moniker range="vs-2017"
## <a name="intellisense-tab"></a>Karta IntelliSense

Przedstawia bieżący stan bazy danych uzupełniania IntelliSense:

![Karta IntelliSense środowiska Python](media/environments/environments-intellisense-tab.png)

- W programie Visual Studio 2017 w wersji 15.5 i starszych wersjach uzupełnianiu IntelliSense zależą od bazy danych, która jest zostały skompilowane dla tej biblioteki. Tworzenia bazy danych jest wykonywane w tle, gdy biblioteka jest zainstalowany, ale może zająć trochę czasu i mogą być niekompletne po rozpoczęciu pisania kodu.
- Visual Studio 2017 w wersji 15.6 i nowsze używa metody szybciej, aby zapewnić uzupełnień, które nie zależą od bazy danych domyślnie. Z tego powodu karcie jest oznaczona etykietą **IntelliSense [baza danych wyłączone]**. Aby umożliwić bazy danych, usuwając zaznaczenie opcji **narzędzia** > **opcje** > **Python**  >   **Eksperymentalne** > **Użyj nowego stylu funkcji IntelliSense dla środowisk**.

Gdy program Visual Studio wykryje nowe środowisko (lub dodać jeden), automatycznie rozpoczyna do skompilowania bazy danych, analizując plików źródłowych w bibliotece. Ten proces może potrwać od chwilę na godzinę lub dłużej w zależności od tego, co jest zainstalowany. (Anaconda, na przykład jest dostarczany z wielu bibliotek i zajmuje trochę czasu, aby skompilować bazy danych) Po wykonaniu tych czynności, Uzyskaj szczegółowe IntelliSense i nie trzeba ponownie Odśwież bazy danych (przy użyciu **Odśwież DB** przycisk) aż do zainstalowania nad dodatkowymi bibliotekami.

Biblioteki, dla których jeszcze nie zostały skompilowane danych są oznaczone **!**; Jeśli bazy danych środowiska nie została ukończona, **!** również obok niego zostanie wyświetlony na liście głównego środowiska.

::: moniker-end

## <a name="see-also"></a>Zobacz także

- [Zarządzanie środowiskami Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Wybieranie interpretera dla projektu](selecting-a-python-environment-for-a-project.md)
- [Użyj pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
