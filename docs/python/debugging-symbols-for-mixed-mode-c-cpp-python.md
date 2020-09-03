---
title: Symbole dla debugowania w trybie mieszanym (Python/C++)
description: Jak program Visual Studio umożliwia ładowanie symboli w celu pełnego debugowania C++ i języka Python.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 4a735c374216b1810b3abd99ffab89000cec8b8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540923"
---
# <a name="install-debugging-symbols-for-python-interpreters"></a>Instalowanie symboli debugowania dla interpreterów języka Python

Aby zapewnić pełne środowisko debugowania, [debuger Python w trybie mieszanym](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) w programie Visual Studio potrzebuje symboli debugowania dla interpretera języka Python używanego do analizowania wielu wewnętrznych struktur danych. Na przykład, odpowiedni plik symboli to *python27. pdb*; *python27.dll* w przypadku *python36.dll*plik symboli to *python36. pdb*. Każda wersja interpretera udostępnia również pliki symboli dla różnych modułów.

W przypadku programu Visual Studio 2017 i nowszych interpretery języka Python 3 i Anaconda 3 automatycznie instalują odpowiednie symbole i program Visual Studio automatycznie odnajdzie te symbole. W przypadku programu Visual Studio 2015 lub starszej wersji lub w przypadku korzystania z innych interpreterów należy pobrać symbole oddzielnie, a następnie wskazać je w programie **Tools**Visual Studio za pomocą  >  okna dialogowego**Opcje** narzędzi na **Debugging**  >  karcie**symbole** debugowania. Te kroki opisano szczegółowo w poniższych sekcjach.

Program Visual Studio może monitować, gdy potrzebuje symboli, zazwyczaj podczas uruchamiania sesji debugowania w trybie mieszanym. W takim przypadku wyświetlane jest okno dialogowe z dwoma opcjami:

- **Otwarte okno dialogowe Ustawienia symboli** otwiera okno dialogowe **Opcje** na **Debugging**  >  karcie**symbole** debugowania.
- **Symbole pobierania dla mojego interpretera** otwierają tę obecną stronę dokumentacji, w takim przypadku **Tools**wybierz  >  **Opcje** narzędzia i przejdź do **Debugging**  >  karty**symbole** debugowania, aby kontynuować.

    ![Monit symboli debugera w trybie mieszanym](media/mixed-mode-debugging-symbols-required.png)

## <a name="download-symbols"></a>Pobierz symbole

- Python 3,5 i nowsze: uzyskiwanie symboli debugowania za pomocą Instalatora języka Python. Wybierz pozycję **Instalacja niestandardowa**, wybierz pozycję **dalej** , aby przejść do **opcji Zaawansowane**, a następnie wybierz pola do **pobrania symbole debugowania** i **Pobierz pliki binarne debugowania**:

    ![Instalator języka Python 3. x z uwzględnieniem symboli debugowania](media/mixed-mode-debugging-symbols-installer35.png)

    Pliki symboli (*. pdb*) są następnie znajdowane w głównym folderze instalacyjnym (pliki symboli dla poszczególnych modułów znajdują się również w folderze *dll* ). W związku z tym program Visual Studio znajdzie je automatycznie i nie trzeba wykonywać żadnych dalszych kroków.

- Python 3.4. x i wcześniejszych: symbole są dostępne jako pliki *zip* do pobrania z [oficjalnych dystrybucji](#official-distributions) lub [Enthought korony](#enthought-canopy). Po pobraniu programu Wyodrębnij pliki do folderu lokalnego, aby kontynuować, takie jak folder *symboli* w folderze języka Python.

    > [!Important]
    > Symbole różnią się między niewielkimi kompilacjami w języku Python i między 32-bitowymi i 64-bitowymi kompilacjami, aby dokładnie dopasować wersje. Aby sprawdzić używany interpreter, rozwiń *węzeł* **środowiska Python** w obszarze projektu w **Eksplorator rozwiązań** i zanotuj nazwę środowiska. Następnie przejdź do okna **środowiska Python** *window* i zanotuj lokalizację instalacji. Następnie otwórz okno polecenia w tej lokalizacji i Rozpocznij *python.exe*, w którym wyświetlana jest dokładna wersja i czy jest to 32-bitowa czy 64-bit.

- W przypadku innych dystrybucji języka Python innych firm, takich jak ActiveState Python: skontaktuj się z autorami tej dystrybucji i poproś ich o podanie symboli. WinPython, w związku z tym, zawiera standardowe interpreter języka Python bez zmian, dlatego należy użyć symboli z oficjalnej dystrybucji dla odpowiadającego im numeru wersji.

## <a name="point-visual-studio-to-the-symbols"></a>Wskaż Visual Studio symbole

Jeśli pobrano symbole oddzielnie, wykonaj poniższe kroki, aby poznać ich informacje. Jeśli zainstalowano symbole za pomocą Instalatora Python 3,5 lub nowszego, program Visual Studio znajdzie je automatycznie.

1. Wybierz menu **Tools**  >  **Opcje** narzędzi i przejdź do opcji **debugowanie**  >  **symboli**.

1. Wybierz przycisk **Dodaj** na pasku narzędzi (przedstawionym poniżej), wprowadź folder, w którym rozszerzono pobrane symbole (w którym znajduje się plik *Python. pdb* , taki jak *c:\python34\Symbols*, pokazany poniżej), a następnie wybierz **przycisk OK**.

    ![Opcje symboli debugera w trybie mieszanym](media/mixed-mode-debugging-symbols.png)

1. Podczas sesji debugowania program Visual Studio może również wyświetlać monit o podanie lokalizacji pliku źródłowego interpretera języka Python. Jeśli pliki źródłowe zostały pobrane (na przykład z [Python.org/downloads/](https://www.python.org/downloads/)), można je również wskazać.

> [!Note]
> Funkcja buforowania symboli pokazana w oknie dialogowym służy do tworzenia lokalnej pamięci podręcznej symboli uzyskanych ze źródła online. Te funkcje nie są potrzebne w przypadku symboli interpretera języka Python, ponieważ symbole są już obecne lokalnie. W każdym przypadku zapoznaj się z tematem [Określanie symboli i plików źródłowych w debugerze programu Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) , aby uzyskać szczegółowe informacje.

## <a name="official-distributions"></a>Oficjalne dystrybucje

| Wersja języka Python | Pobieranie |
| --- | --- |
| 3,5 i nowsze | Instalowanie symboli za pomocą Instalatora języka Python. |
| 3.4.4 | [32 — bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32 — bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32 — bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32 — bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32 — bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32 — bit](https://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32 — bit](https://www.python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32 — bit](https://www.python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32 — bit](https://www.python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32 — bit](https://www.python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32 — bit](https://www.python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.15 | [32 — bit](https://www.python.org/ftp/python/2.7.15/python-2.7.15-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/2.7.15/python-2.7.15.amd64-pdb.zip) |
| 2.7.14 | [32 — bit](https://www.python.org/ftp/python/2.7.14/python-2.7.14-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/2.7.14/python-2.7.14.amd64-pdb.zip) |
| 2.7.13 | [32 — bit](https://www.python.org/ftp/python/2.7.13/python-2.7.13-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/2.7.13/python-2.7.13.amd64-pdb.zip) |
| 2.7.12 | [32 — bit](https://www.python.org/ftp/python/2.7.12/python-2.7.12-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/2.7.12/python-2.7.12.amd64-pdb.zip) |
| 2.7.11 | [32 — bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32 — bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32 — bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32 — bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32 — bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32 — bit](https://www.python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32 — bit](https://www.python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32 — bit](https://www.python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32 — bit](https://www.python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32 — bit](https://www.python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32 — bit](https://www.python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip)  -  [64 — bit](https://www.python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |

## <a name="enthought-canopy"></a>Enthought koronki

Enthought koroner zawiera symbole plików binarnych, począwszy od wersji 1,2. Są one instalowane automatycznie wraz z dystrybucją, ale nadal trzeba ręcznie dodać folder zawierający je do ścieżki symboli zgodnie z wcześniejszym opisem. W przypadku typowej instalacji z poziomu korony dla poszczególnych użytkowników symbole znajdują się w *%USERPROFILE%\AppData\Local\Enthought\Canopy\User\Scripts* dla wersji 64-bitowej i *%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts* dla wersji 32-bitowej.

Enthought koroner 1,1 i starsze, a także Enthought (EPD) w języku Python, nie zapewniają symboli interpretera i dlatego nie są zgodne z debugowaniem w trybie mieszanym.
