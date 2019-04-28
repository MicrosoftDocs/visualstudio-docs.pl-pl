---
title: Jak używać narzędzia CTest dla języka C++
ms.date: 11/07/2017
ms.topic: conceptual
ms.author: mblome
manager: jillfra
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 6be079a5adfe52a7ac750f6713672dad50c7d2a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945385"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Jak używać narzędzia CTest dla języka C++ w programie Visual Studio

CMake (co obejmuje narzędzia CTest) jest zintegrowana w środowisku IDE programu Visual Studio domyślnie jako część **programowanie aplikacji klasycznych w języku C++** obciążenia. Jeśli musisz zainstalować go na komputerze, Otwórz program Instalator programu Visual Studio, kliknij pozycję **Modyfikuj** przycisk, a następnie sprawdź [narzędzia CMake w języku Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) pod listą składników obciążenia.

## <a name="to-write-tests"></a>Do pisania testów

Obsługa CMake w programie Visual Studio nie obejmują systemu projektu programu Visual Studio. W związku z tym zapisu i Konfigurowanie narzędzia CTest testów, tak samo jak w każdym środowisku CMake. Aby uzyskać więcej informacji na temat używania narzędzia CMake w programie Visual Studio, zobacz [narzędzia CMake w języku Visual C++](/cpp/ide/cmake-tools-for-visual-cpp).

## <a name="to-run-tests"></a>Aby uruchomić testy

::: moniker range="vs-2017"

### <a name="visual-studio-2017-version-156-and-later"></a>Visual Studio 2017 w wersji 15.6 i nowsze

W programie Visual Studio 2017 w wersji 15.6 i nowszych narzędzia CTest jest w pełni zintegrowana z **Eksplorator testów** i obsługuje także jednostki Google i zwiększenie wydajności, testowanie struktur. Te struktury są domyślnie dołączone jako składników w **programowanie aplikacji klasycznych w języku C++** obciążenia. Jednak w przypadku uaktualniania projektu ze starszej wersji programu Visual Studio, może być konieczne zainstalowanie tych środowisk przy użyciu programu Instalatora programu Visual Studio.

Na poniższej ilustracji przedstawiono wyniki narzędzia CTest uruchamiane przy użyciu framework platformy Google Test:

![Narzędzia CTest przy użyciu Framework platformy Google Test w programie Visual Studio 2017](media/ctest-test-explorer.png)

Jeśli używasz narzędzia CTest, ale nie Google lub Boost kart, zobaczysz wyniki na poziomie narzędzia CTest zamiast poszczególnych testów poziom metody. Można debugować i krokowym tylko do narzędzia CTest pliki wykonywalne, ale ślady stosu na poszczególne testy nie są obsługiwane.

### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15.5

W programie Visual Studio 2017 w wersji 15.5 narzędzia CTest nie jest zintegrowany z **Eksplorator testów**. Możesz uruchomić testy z menu głównego narzędzia CMake lub w menu kliknij prawym przyciskiem myszy *CMakeLists.txt* w pliku **Eksploratora rozwiązań**. Wyniki testów są kierowane do programu Visual Studio **okno danych wyjściowych**.

![Uruchamianie narzędzia CTest testów w programie Visual Studio 2017 w wersji 15.5](media/cpp-cmake-run-tests.png)

::: moniker-end

::: moniker range=">=vs-2019"

Narzędzia CTest jest w pełni zintegrowana z **Eksplorator testów** i obsługuje także jednostki Google i zwiększenie wydajności, testowanie struktur. Te struktury są domyślnie dołączone jako składników w **programowanie aplikacji klasycznych w języku C++** obciążenia. Jednak w przypadku uaktualniania projektu ze starszej wersji programu Visual Studio, może być konieczne zainstalowanie tych środowisk przy użyciu programu Instalatora programu Visual Studio.

Na poniższej ilustracji przedstawiono wyniki narzędzia CTest uruchamiane przy użyciu framework platformy Google Test:

![Narzędzia CTest przy użyciu Framework platformy Google Test w programie Visual Studio](media/ctest-test-explorer.png)

Jeśli używasz narzędzia CTest, ale nie Google lub Boost kart, zobaczysz wyniki na poziomie narzędzia CTest zamiast poszczególnych testów poziom metody. Można debugować i krokowym tylko do narzędzia CTest pliki wykonywalne, ale ślady stosu na poszczególne testy nie są obsługiwane.

::: moniker-end

## <a name="see-also"></a>Zobacz także

- [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)