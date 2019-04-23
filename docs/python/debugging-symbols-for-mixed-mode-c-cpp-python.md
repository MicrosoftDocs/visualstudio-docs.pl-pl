---
title: Symbole dla języków Python/C++ debugowanie w trybie mieszanym
description: Jak program Visual Studio zapewnia możliwość ładowania symboli dla pełną C++ trybu mieszanego i debugowania języka Python.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 77dc73b0be050e5108f73d38dfbbaa763d236995
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60100499"
---
# <a name="install-debugging-symbols-for-python-interpreters"></a>Instalowanie symboli debugowania dla interpreterów języka Python

Zapewnienie pełnego środowiska debugowania [debugera języka Python w trybie mieszanym](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) w programie Visual Studio potrzebuje symbole debugowania dla interpretera języka Python, używane do analizowania wiele wewnętrznych struktur danych. Dla *python27.dll*, na przykład, jest odpowiedni plik symboli *python27.pdb*; *python36.dll*, plik symboli jest *python36.pdb*. Każda wersja interpreter dostarcza również pliki symboli dla różnych modułów.

Za pomocą programu Visual Studio 2017 i nowszych interpreterów języka Python 3 oraz Anaconda 3 automatycznie instalować ich odpowiednich symboli i program Visual Studio automatycznie znajdzie te symbole. Dla programu Visual Studio 2015 i starsze, lub w przypadku używania innych interpreterów, musisz osobno pobierać symbole, a następnie wskazać je za pomocą programu Visual Studio **narzędzia** > **opcje** w okna dialogowego **debugowanie** > **symbole** kartę. Te kroki są szczegółowo opisane w poniższych sekcjach.

Program Visual Studio może zostać wyświetlony komunikat po potrzebny symbole, zazwyczaj podczas uruchamiania sesji debugowania w trybie mieszanym. W tym przypadku wyświetla okno dialogowe z jedną z dwóch opcji:

- **Okno dialogowe Ustawienia symboli Otwórz** otwiera **opcje** okno dialogowe **debugowanie** > **symbole** kartę.
- **Pobrać symbole dla mojego interpreter** otwiera to obecne stronę dokumentacji, w którym to przypadku wybierz **narzędzia** > **opcje** i przejdź do **debugowania**   >  **Symbole** kartę, aby kontynuować.

    ![Tryb mieszany debuger symbole w wierszu polecenia](media/mixed-mode-debugging-symbols-required.png)

## <a name="download-symbols"></a>Pobieranie symboli

- Python 3.5 i nowsze: uzyskiwanie symboli debugowania za pośrednictwem Instalatora języka Python. Wybierz **Instalacja niestandardowa**, wybierz opcję **dalej** do **zaawansowane opcje**, następnie zaznacz pola wyboru odpowiadające **pobrać symbole debugowania** i **pliki binarne debugowania pobierania**:

    ![Instalator środowiska Python 3.x, w tym symbole debugowania](media/mixed-mode-debugging-symbols-installer35.png)

    Pliki symboli (*.pdb*) następnie znajdują się w folderze instalacyjnym głównego (pliki symboli dla poszczególnych modułów znajdują się w *biblioteki dll* również folder). W związku z tym program Visual Studio znajdzie je automatycznie i nie trzeba wykonywać dalszych czynności są wymagane.

- Python 3.4.x i starszych: symbole są dostępne do pobrania *zip* plików z [oficjalne dystrybucje](#official-distributions) lub [korony Enthought](#enthought-canopy). Po pobraniu, Wyodrębnij pliki do folderu lokalnego, aby kontynuować, takich jak *symbole* folder wewnątrz folderu, języka Python.

    > [!Important]
    > Symbole różnią się między kompilacjami pomocniczych języka Python, a między 32-bitowych i 64-bitowych kompilacji, dlatego należy dokładnie zgodne z wersjami. Aby sprawdzić interpreter używany, rozwiń węzeł **środowiska Python** *węzła* pod projektem w **Eksploratora rozwiązań** i określ nazwę środowiska. Następnie przełącz się do **środowiska Python** *okna* i zanotuj lokalizację instalacji. Następnie otwórz okno poleceń w tej lokalizacji i uruchom *python.exe*, powoduje wyświetlenie dokładnie wersji i czy jest 32-bitową lub 64-bitowych.

- Dla żadnych innych firm Python dystrybucji takich jak ActiveState Python: Skontaktuj się z autorzy dystrybucji i zażądać ich do przedstawienia symboli. WinPython, ze swojej strony zawiera standardowe interpreter języka Python, bez konieczności wprowadzania zmian, a więc symbole z oficjalnego dystrybucji dla jej numer wersji.

## <a name="point-visual-studio-to-the-symbols"></a>Polecenie symboli programu Visual Studio

Jeśli symbole zostały pobrane oddzielnie, wykonaj poniższe kroki, aby uświadomić programu Visual Studio z nich. Jeśli zainstalowano symbole za pomocą języka Python 3.5 lub nowszej Instalatora, program Visual Studio znajdzie je automatycznie.

1. Wybierz **narzędzia** > **opcje** menu i przejdź do **debugowanie** > **symbole**.

1. Wybierz **Dodaj** przycisk na pasku narzędzi (opisanych poniżej), wprowadź folder, w którym rozwinięte symbole pobrane (czyli, gdzie *python.pdb* znajduje się przykład *c:\python34\Symbols* , jak pokazano poniżej) i wybierz **OK**.

    ![Tryb mieszany debuger symboli opcje](media/mixed-mode-debugging-symbols.png)

1. Podczas sesji debugowania programu Visual Studio może również monit o lokalizację pliku źródłowego interpreter języka Python. Jeśli pobrano pliki źródłowe (z [python.org/downloads/](https://www.python.org/downloads/), na przykład), a następnie oczywiście można wskazać im także.

> [!Note]
> Funkcje pamięci podręcznej symboli pokazać w oknie dialogowym są używane do tworzenia lokalnej pamięci podręcznej symboli uzyskanych ze źródła online. Jako symbole znajdujące się lokalnie, te funkcje nie są potrzebne przy użyciu symboli interpreter języka Python. W każdym przypadku dotyczą [Określ symboli i źródłowych plików w debugerze programu Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Aby uzyskać szczegółowe informacje.

## <a name="official-distributions"></a>Oficjalna dystrybucji

| Wersja języka Python | Pliki do pobrania |
| --- | --- |
| 3.5 i nowsze | Instalowanie symboli za pośrednictwem Instalatora języka Python. |
| 3.4.4 | [32-bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32-bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32-bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32-bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32-bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32-bit](https://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32-bit](https://www.python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32-bit](https://www.python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32-bit](https://www.python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32-bit](https://www.python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32-bit](https://www.python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.15 | [32-bit](https://www.python.org/ftp/python/2.7.15/python-2.7.15-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.15/python-2.7.15.amd64-pdb.zip) |
| 2.7.14 | [32-bit](https://www.python.org/ftp/python/2.7.14/python-2.7.14-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.14/python-2.7.14.amd64-pdb.zip) |
| 2.7.13 | [32-bit](https://www.python.org/ftp/python/2.7.13/python-2.7.13-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.13/python-2.7.13.amd64-pdb.zip) |
| 2.7.12 | [32-bit](https://www.python.org/ftp/python/2.7.12/python-2.7.12-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.12/python-2.7.12.amd64-pdb.zip) |
| 2.7.11 | [32-bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32-bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32-bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32-bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32-bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32-bit](https://www.python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32-bit](https://www.python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32-bit](https://www.python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32-bit](https://www.python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32-bit](https://www.python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32-bit](https://www.python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |

## <a name="enthought-canopy"></a>Korony Enthought

Korony Enthought zawiera symbole dla swoich danych binarnych, począwszy od wersji 1.2. Są one instalowane automatycznie razem z rozkładem, ale nadal musisz ręcznie dodać do folderu zawierającego je do ścieżki symboli, zgodnie z wcześniejszym opisem. W przypadku użytkownika typowej instalacji korony symbole znajdują się w *%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts* dla wersji 64-bitowych i *%UserProfile%\AppData\Local\Enthought\ Canopy32\User\Scripts* dla 32-bitowej wersji.

Korony Enthought 1.1 i starszych, a także Enthought dystrybucji Python (EPD) są oferowane interpreter symbole, a w związku z tym są niezgodne z debugowanie w trybie mieszanym.
