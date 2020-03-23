---
title: Symbole debugowania w trybie mieszanym Python/C++
description: Jak Visual Studio zapewnia możliwość ładowania symboli dla pełnego trybu mieszanego C++ i Python debugowania.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 77dc73b0be050e5108f73d38dfbbaa763d236995
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62957620"
---
# <a name="install-debugging-symbols-for-python-interpreters"></a>Instalowanie symboli debugowania dla interpreterów języka Python

Aby zapewnić pełne środowisko debugowania, [debuger języka Python w trybie mieszanym](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) w programie Visual Studio wymaga symboli debugowania dla interpretera języka Python używanego do analizowania wielu wewnętrznych struktur danych. Dla *python27.dll*, na przykład, odpowiedni plik symbolu jest *python27.pdb*; dla *python36.dll*, plik symbolu jest *python36.pdb*. Każda wersja tłumacza dostarcza również pliki symboli dla różnych modułów.

W programie Visual Studio 2017 i nowszych interpretatorzy języka Python 3 i Anaconda 3 automatycznie instalują odpowiednie symbole, a program Visual Studio automatycznie odnajduje te symbole. W programie Visual Studio 2015 i wcześniejszych lub podczas korzystania z innych interpreterów, należy **Tools** > pobrać symbole oddzielnie, a następnie wskazać visual studio do nich za pośrednictwem**narzędzia opcje** okna dialogowego na karcie**Symbole** **debugowania.** >  Te kroki są szczegółowo opisane w poniższych sekcjach.

Visual Studio może monitować, gdy potrzebuje symboli, zazwyczaj podczas uruchamiania sesji debugowania w trybie mieszanym. W takim przypadku wyświetla okno dialogowe z dwoma możliwościami:

- **Okno dialogowe Otwieranie ustawień symboli** powoduje otwarcie okna dialogowego **Opcje** na karcie**Symbole** **debugowania.** > 
- **Pobierz symbole dla mojego tłumacza** otwiera tę obecną stronę dokumentacji, w którym to przypadku wybierz**opcje** **narzędzi** > i przejdź do karty**Symbole** **debugowania,** > aby kontynuować.

    ![Monit o symbole debugera trybu mieszanego](media/mixed-mode-debugging-symbols-required.png)

## <a name="download-symbols"></a>Pobierz symbole

- Python 3.5 i nowsze: uzyskiwanie symboli debugowania za pośrednictwem instalatora Języka Python. Wybierz **pozycję Instalacja niestandardowa**, wybierz **pozycję Dalej,** aby przejść do pozycji Opcje **zaawansowane,** a następnie zaznacz pola **wyboru Pobierz symbole debugowania** i **Pobierz pliki binarne debugowania:**

    ![Instalator Języka Python 3.x z symbolami debugowania](media/mixed-mode-debugging-symbols-installer35.png)

    Pliki symboli (*pdb*) znajdują się następnie w głównym folderze instalacyjnym (pliki symboli dla poszczególnych modułów znajdują się również w folderze *bibliotek DLL).* Z tego powodu visual studio znajdzie je automatycznie i nie są potrzebne dalsze kroki.

- Python 3.4.x i wcześniej: symbole są dostępne do pobrania *.zip* plików z [oficjalnych dystrybucji](#official-distributions) lub [Enthought Canopy](#enthought-canopy). Po pobraniu wyodrębnij pliki do folderu lokalnego, aby kontynuować, na przykład folder *Symbole* w folderze Python.

    > [!Important]
    > Symbole różnią się między kompilacjami pomocniczych języka Python i między kompilacjami 32-bitowymi i 64-bitowymi, więc chcesz dokładnie dopasować wersje. Aby sprawdzić używany interpreter, rozwiń *węzeł* **Środowiska języka Python** w ramach projektu w **Eksploratorze rozwiązań** i zanotuj nazwę środowiska. Następnie przełącz się do *okna* **Środowiska języka Python** i zanotuj lokalizację instalacji. Następnie otwórz okno polecenia w tej lokalizacji i uruchom *program python.exe*, który wyświetla dokładną wersję i czy jest to 32-bitowe czy 64-bitowe.

- W przypadku innych dystrybucji języka Python innych firm, takich jak ActiveState Python: skontaktuj się z autorami tej dystrybucji i poproś o podanie symboli. WinPython, ze swojej strony, zawiera standardowy interpreter Python bez zmian, więc użyj symboli z oficjalnej dystrybucji dla odpowiedniego numeru wersji.

## <a name="point-visual-studio-to-the-symbols"></a>Punkt Visual Studio do symboli

Jeśli pobrano symbole oddzielnie, wykonaj poniższe czynności, aby uświadomić programowi Visual Studio o nich. Jeśli symbole zostały zainstalowane za pośrednictwem instalatora języka Python 3.5 lub nowszego, program Visual Studio znajdzie je automatycznie.

1. Wybierz menu**Opcje** **narzędzi** > i przejdź do pozycji **Debugowanie** > **symboli**.

1. Wybierz przycisk **Dodaj** na pasku narzędzi (opisany poniżej), wejdź do folderu, w którym rozwinięto pobrane symbole (czyli miejsce, w którym znajduje się *python.pdb,* na przykład *c:\python34\Symbole*, pokazane poniżej), a następnie wybierz **przycisk OK**.

    ![Opcje symboli debugera trybu mieszanego](media/mixed-mode-debugging-symbols.png)

1. Podczas sesji debugowania program Visual Studio może również monitować o lokalizację pliku źródłowego dla interpretera języka Python. Jeśli pobrałeś pliki źródłowe (na przykład z [python.org/downloads/),](https://www.python.org/downloads/)to oczywiście możesz również je wskazać.

> [!Note]
> Funkcje buforowania symboli wyświetlane w oknie dialogowym służą do tworzenia lokalnej pamięci podręcznej symboli uzyskanych ze źródła online. Te funkcje nie są potrzebne z symbolami interpretera Języka Python, ponieważ symbole są już obecne lokalnie. W każdym przypadku szczegółowe informacje można znaleźć [w polu Określ symbole i pliki źródłowe w debugerze programu Visual Studio.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="official-distributions"></a>Dystrybucje urzędowe

| Wersja języka Python | Pliki do pobrania |
| --- | --- |
| 3.5 i nowsze | Zainstaluj symbole za pomocą instalatora języka Python. |
| 3.4.4 | [32-bitowy](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32-bitowy](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32-bitowy](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32-bitowy](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32-bitowy](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32-bitowy](https://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32-bitowy](https://www.python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32-bitowy](https://www.python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32-bitowy](https://www.python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32-bitowy](https://www.python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32-bitowy](https://www.python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.15 | [32-bitowy](https://www.python.org/ftp/python/2.7.15/python-2.7.15-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/2.7.15/python-2.7.15.amd64-pdb.zip) |
| 2.7.14 | [32-bitowy](https://www.python.org/ftp/python/2.7.14/python-2.7.14-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/2.7.14/python-2.7.14.amd64-pdb.zip) |
| 2.7.13 | [32-bitowy](https://www.python.org/ftp/python/2.7.13/python-2.7.13-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/2.7.13/python-2.7.13.amd64-pdb.zip) |
| 2.7.12 | [32-bitowy](https://www.python.org/ftp/python/2.7.12/python-2.7.12-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/2.7.12/python-2.7.12.amd64-pdb.zip) |
| 2.7.11 | [32-bitowy](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32-bitowy](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32-bitowy](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32-bitowy](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32-bitowy](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32-bitowy](https://www.python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32-bitowy](https://www.python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32-bitowy](https://www.python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32-bitowy](https://www.python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32-bitowy](https://www.python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32-bitowy](https://www.python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64-bitowy](https://www.python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |

## <a name="enthought-canopy"></a>Enthought Baldachim

Enthought Canopy zapewnia symbole dla swoich plików binarnych, począwszy od wersji 1.2. Są one automatycznie instalowane wraz z dystrybucją, ale nadal trzeba ręcznie dodać folder zawierający je do ścieżki symbolu, jak opisano wcześniej. W przypadku typowej instalacji canopy dla użytkownika symbole znajdują się w *%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts* dla wersji 64-bitowej i *%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts* dla wersji 32-bitowej.

Enthought Canopy 1.1 i wcześniej, a także Enthought Python Distribution (EPD), nie dostarczają symboli interpretera i dlatego nie są zgodne z debugowaniem w trybie mieszanym.
