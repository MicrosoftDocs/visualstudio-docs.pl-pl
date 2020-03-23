---
title: Odwołanie do okna środowiska języka Python
description: Szczegóły dotyczące każdej z kart, które pojawiają się w oknie środowiska języka Python w programie Visual Studio.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302771"
---
# <a name="python-environments-window-tabs-reference"></a>Odwołanie do kart okien środowiska języka Python

Aby otworzyć okno **Środowiska języka Python:**

- Wybierz polecenie menu **Wyświetl** > inne środowiska**języka Windows** > **Python.**
- Kliknij prawym przyciskiem myszy węzeł **Środowiska języka Python** dla projektu w **Eksploratorze rozwiązań** i wybierz pozycję **Wyświetl wszystkie środowiska języka Python**.

Jeśli rozwiniesz okno **Środowiska Języka Python** wystarczająco szerokie, te opcje są wyświetlane jako karty, które mogą okazać się wygodniejsze do pracy. Dla jasności karty w tym artykule są wyświetlane w widoku rozwiniętym.

::: moniker range="vs-2017"
![Widok rozwinięty okna środowiska języka Python](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Widok rozwinięty okna środowiska języka Python](media/environments/environments-expanded-view-2019.png)
::: moniker-end

## <a name="overview-tab"></a>Karta Przegląd

Zawiera podstawowe informacje i polecenia dla środowiska:

::: moniker range="vs-2017"
![Karta Omówienie środowisk języka Python](media/environments/environments-overview-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta Omówienie środowisk języka Python](media/environments/environments-overview-tab-2019.png)
::: moniker-end

| Polecenie | Opis |
| --- | --- |
| **Ustaw to środowisko jako domyślne dla nowych projektów** | Ustawia aktywne środowisko, które może spowodować, że program Visual Studio (2017 w wersji 15.5 lub starszych) na krótko stanie się nie reaguje podczas ładowania bazy danych IntelliSense. Środowiska z wieloma pakietami mogą dłużej nie reagować. |
| **Odwiedź stronę dystrybutora** | Otwiera przeglądarkę do adresu URL dostarczonego przez dystrybucję języka Python. Python 3.x, na przykład, idzie do python.org. |
| **Otwórz okno interaktywne** | Otwiera [okno interaktywne (REPL)](python-interactive-repl-in-visual-studio.md) dla tego środowiska w programie Visual Studio, stosując wszystkie [skrypty startowe (patrz poniżej).](#startup-scripts) |
| **Eksplorowanie skryptów interaktywnych** | Zobacz [skrypty startowe](#startup-scripts). |
| **Korzystanie z trybu interaktywnego IPython** | Po ustawieniu domyślnie otwiera okno **Interaktywne** z funkcją IPython. Umożliwia to wykresy wbudowane, a także rozszerzoną składnię `name?` IPython, taką jak wyświetlanie pomocy i `!command` poleceń powłoki. Ta opcja jest zalecana w przypadku korzystania z dystrybucji Anaconda, ponieważ wymaga dodatkowych pakietów. Aby uzyskać więcej informacji, zobacz [Używanie IPython w oknie Interaktywna](interactive-repl-ipython.md). |
| **Otwórz w programie PowerShell** | Uruchamia interpreter w oknie polecenia programu PowerShell. |
| (Łącza do folderów i programów) | Zapewnia szybki dostęp do folderu instalacyjnego środowiska, interpretera *python.exe* i interpretera *pythonw.exe.* Pierwszy otwiera się w Eksploratorze Windows, dwa ostatnie otwierają okno konsoli. |

### <a name="startup-scripts"></a>Skrypty startowe

Podczas korzystania z interaktywnych okien w codziennym przepływie pracy prawdopodobnie opracowywane są funkcje pomocnicze, których regularnie używasz. Na przykład można utworzyć funkcję, która otwiera DataFrame w programie Excel, a następnie zapisać ten kod jako skrypt startowy, tak aby był zawsze dostępny w oknie **Interaktywna.**

Skrypty startowe zawierają kod, który **okno Interaktywne** ładuje i uruchamia automatycznie, w tym import, definicje funkcji i dosłownie wszystko inne. Takie skrypty są odwoływane na dwa sposoby:

1. Po zainstalowaniu środowiska program Visual Studio tworzy folder *Dokumenty\Wersja programu Visual Studio \<>\Środowisko skryptów\\\<Języka Python>,* w którym&gt; &lt;wersja&gt; jest wersją &lt;programu Visual Studio (na przykład 2017 lub 2019) i środowisko pasuje do nazwy środowiska. Za pomocą polecenia **Eksploruj skrypty interaktywne** można łatwo przejść do folderu specyficznego dla środowiska. Po uruchomieniu **interaktywne** okno dla tego środowiska, ładuje i uruchamia cokolwiek *.py* pliki znajdują się tutaj w kolejności alfabetycznej.

1. Formant **Skrypty** w **narzędzia** > **opcje** > **Python** > **interaktywne windows** kartę (zobacz [interaktywne opcje systemu Windows)](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)ma na celu określenie dodatkowego folderu dla skryptów startowych, które są ładowane i uruchamiane we wszystkich środowiskach. Jednak ta funkcja nie działa w chwili obecnej.

## <a name="configure-tab"></a>Karta Konfigurowanie

Jeśli jest dostępna, karta **Konfiguruj** zawiera szczegóły opisane w poniższej tabeli. Jeśli ta karta nie jest obecny, oznacza to, że visual studio zarządza wszystkie szczegóły automatycznie.

::: moniker range="vs-2017"
![Karta Konfigurowanie środowiska języka Python](media/environments/environments-configure-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta Konfigurowanie środowiska języka Python](media/environments/environments-configure-tab-2019.png)
::: moniker-end

| Pole | Opis |
| --- | --- |
| **Opis** | Nazwa, aby nadać środowisko. |
| **Ścieżka prefiksu** | Lokalizacja folderu podstawowego tłumacza. Wypełniając tę wartość i klikając **przycisk Auto Detect**, program Visual Studio próbuje wypełnić inne pola. |
| **Ścieżka interpretera** | Ścieżka do pliku wykonywalnego interpretera, często ścieżka prefiksu, po której następuje **python.exe** |
| **Tłumacz z oknami** | Ścieżka do pliku wykonywalnego bez konsoli, często ścieżka prefiksu, po której następuje **pythonw.exe**. |
| **Ścieżka biblioteki**<br/>(jeśli są dostępne) | Określa katalog główny biblioteki standardowej, ale ta wartość może być ignorowana, jeśli program Visual Studio jest w stanie zażądać dokładniejszej ścieżki od interpretera. |
| **Wersja językowa** | Wybrane z menu rozwijanego. |
| **Architektura** | Normalnie wykrywane i wypełniane automatycznie, w przeciwnym razie określa **32-bitowe** lub **64-bitowe**. |
| **Zmienna środowiska ścieżki** | Zmienna środowiskowa używana przez interpretera do znajdowania ścieżek wyszukiwania. Visual Studio zmienia wartość zmiennej podczas uruchamiania języka Python, tak aby zawierała ścieżki wyszukiwania projektu. Zazwyczaj ta właściwość powinna być ustawiona na **PYTHONPATH**, ale niektóre interpretatory używają innej wartości. |

## <a name="packages-tab"></a>Karta Pakiety

*Również oznaczone jako "pip" we wcześniejszych wersjach.*

Zarządza pakietami zainstalowanymi w środowisku przy użyciu pip **(pakiety (PyPI)** kartę) lub conda **(pakiety (Conda)** kartę, dla środowisk conda w programie Visual Studio 2017 w wersji 15.7 i nowszych). W tej karcie można również wyszukiwać i instalować nowe pakiety, w tym ich zależności.

Pakiety, które są już zainstalowane pojawiają się z formantami, aby zaktualizować (strzałka w górę) i odinstalować (X w kole) pakiet:

![Karta Pakiety środowisk języka Python](media/environments/environments-pip-tab-controls.png)

Wprowadzenie wyszukiwanego terminu filtruje listę zainstalowanych pakietów oraz pakietów, które można zainstalować z pypi.

::: moniker range="vs-2017"
![Python środowiska pakiety kartę z wyszukiwaniem na "num"](media/environments/environments-pip-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python środowiska pakiety kartę z wyszukiwaniem na "num"](media/environments/environments-pip-tab-2019.png)
::: moniker-end

Jak widać na powyższej ilustracji, wyniki wyszukiwania pokazują liczbę pakietów, które pasują do wyszukiwanego hasła; pierwszym wpisem na liście jest jednak polecenie uruchomienia **nazwy instalatora \<pip>** bezpośrednio. Jeśli jesteś na karcie **Pakiety (Conda),** zamiast tego widzisz **nazwę instalacji \<conda>: **

::: moniker range="vs-2017"
![Karta Pakiety Conda z poleceniem instalacji conda](media/environments/environments-conda-tab-install.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta Pakiety Conda z poleceniem instalacji conda](media/environments/environments-conda-tab-install-2019.png)
::: moniker-end

W obu przypadkach można dostosować instalację, dodając argumenty w polu wyszukiwania po nazwie pakietu. Po dodaniu argumentów wyniki wyszukiwania pokazują **instalację pip** lub **conda,** po której następuje zawartość pola wyszukiwania:

::: moniker range="vs-2017"
![Używanie argumentów na poleceniach instalacji pip i conda](media/environments/environments-pip-tab-arguments.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Używanie argumentów na poleceniach instalacji pip i conda](media/environments/environments-pip-tab-arguments-2019.png)
::: moniker-end

Zainstalowanie pakietu tworzy podfoldery w folderze *Lib* środowiska w systemie plików. Na przykład, jeśli masz python 3.6 zainstalowany w *c:\Python36*, pakiety są instalowane w *c:\Python36\Lib*; jeśli anakonda3 jest zainstalowana w *c:\Program Files\Anaconda3,* to pakiety są instalowane w *c:\Program Files\Anaconda3\Lib*. W środowiskach conda pakiety są instalowane w folderze tego środowiska.

### <a name="grant-administrator-privileges-for-package-install"></a>Udzielanie uprawnień administratora do instalowania pakietu

Podczas instalowania pakietów w środowisku, które znajduje się w chronionym obszarze systemu plików, takich jak *c:\Program Files\Anaconda3\Lib*, Visual Studio musi działać `pip install` z podwyższonym poziomem uprawnień, aby umożliwić tworzenie podfolderów pakietów. Gdy wymagane jest podniesienie uprawnień, program Visual Studio wyświetla monit, **może być wymagane uprawnienia administratora do zainstalowania, aktualizacji lub usunięcia pakietów dla tego środowiska:**

![Monit o podniesienie uprawnień do instalacji pakietu](media/environments/environments-pip-elevate.png)

**Elevate teraz** udziela uprawnień administracyjnych do pip dla jednej operacji, z zastrzeżeniem również wszelkie monity systemu operacyjnego o uprawnienia. Wybranie **opcji Kontynuuj bez uprawnień administratora** powoduje próbę zainstalowania pakietu, ale pip kończy się niepowodzeniem podczas próby utworzenia folderów z wyjściem, takich jak **błąd: nie można utworzyć opcji "C:\Program Files\Anaconda3\Lib\site-packages\png.py": Odmowa uprawnień.**

Wybranie **opcji Zawsze podnosić podczas instalowania lub usuwania pakietów** zapobiega pojawianiu się okna dialogowego dla danego środowiska. Aby okno dialogowe było ponownie wyświetlane, przejdź do **pozycji** > **Opcje** > narzędzi**Python** > **Ogólne** i wybierz przycisk **Resetuj wszystkie trwale ukryte okna dialogowe**.

Na tej **samej** karcie Opcje można również wybrać **opcję Zawsze uruchamiaj pip jako administrator,** aby pominąć okno dialogowe dla wszystkich środowisk. Zobacz [opcje — karta Ogólne](python-support-options-and-settings-in-visual-studio.md#general-options).

### <a name="security-restrictions-with-older-versions-of-python"></a>Ograniczenia zabezpieczeń ze starszymi wersjami języka Python

Podczas korzystania z Python 2.6, 3.1 i 3.2, Visual Studio pokazuje ostrzeżenie, **Ze względu na nowe ograniczenia bezpieczeństwa, instalacja z Internetu może nie działać na tej wersji Pythona:**

![Komunikat o ograniczeniach instalacji pip ze starszą wersją języka Python](media/environments/environments-old-version-restriction.png)

Powodem ostrzeżenia jest to, `pip install` że w przypadku tych starszych wersji języka Python nie zawiera obsługi warstwy zabezpieczeń transportu (TLS) 1.2, która jest wymagana do pobierania pakietów ze źródła pakietu, pypi.org. Niestandardowe kompilacje języka Python mogą obsługiwać TLS 1.2, w którym to przypadku `pip install` może działać.

Możliwe jest pobranie odpowiedniego *get-pip.py* dla pakietu z [bootstrap.pypa.io,](https://bootstrap.pypa.io/)ręczne pobranie pakietu z [pypi.org](https://pypi.org/), a następnie zainstalowanie pakietu z tej kopii lokalnej.

Zaleceniem jest jednak po prostu uaktualnienie do języka Python 2.7 lub 3.3+, w którym to przypadku ostrzeżenie nie pojawia się.

::: moniker range="vs-2017"
## <a name="intellisense-tab"></a>Karta IntelliSense

Pokazuje bieżący stan bazy danych ukończenia intellisense:

![Karta IntelliSense środowiska Pythona](media/environments/environments-intellisense-tab.png)

- W programie Visual Studio 2017 w wersji 15.5 i wcześniejszych uzupełnienia IntelliSense zależą od bazy danych, która została skompilowana dla tej biblioteki. Tworzenie bazy danych odbywa się w tle, gdy biblioteka jest zainstalowana, ale może zająć trochę czasu i może nie być kompletna po rozpoczęciu pisania kodu.
- Visual Studio 2017 w wersji 15.6 i nowszych używa szybszej metody, aby zapewnić uzupełnienia, które nie są domyślnie zależne od bazy danych. Z tego powodu karta jest oznaczona jako **IntelliSense [baza danych wyłączona]**. Bazę danych można włączyć, czyszcząc opcję**Opcje** >  **narzędzia** > **Python** > **Experimental** > **Użyj nowego stylu IntelliSense dla środowisk**.

Gdy program Visual Studio wykryje nowe środowisko (lub dodasz jedno), automatycznie rozpoczyna kompilowanie bazy danych przez analizowanie plików źródłowych biblioteki. Ten proces może potrwać od minuty do godziny lub więcej w zależności od tego, co jest zainstalowane. (Anaconda, na przykład, pochodzi z wielu bibliotek i zajmuje trochę czasu, aby skompilować bazę danych.) Po zakończeniu otrzymasz szczegółowy program IntelliSense i nie trzeba ponownie odświeżać bazy danych (za pomocą przycisku **Odśwież bazę danych),** dopóki nie zainstalujesz większej liczby bibliotek.

Biblioteki, dla których dane nie zostały skompilowane, są oznaczone symbolem **!**; jeśli baza danych środowiska nie jest kompletna, a **!** pojawia się obok niego na głównej liście środowiska.

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Zarządzanie środowiskami języka Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Wybieranie interpretera dla projektu](selecting-a-python-environment-for-a-project.md)
- [Używanie pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
