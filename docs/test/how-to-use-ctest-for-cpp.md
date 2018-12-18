---
title: Jak używać narzędzia CTest dla języka C++
ms.date: 11/07/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 7a4475cba023f792c2ff96895eb4dd7e0b4ebcf5
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53050217"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Jak używać narzędzia CTest dla języka C++ w programie Visual Studio

CMake (co obejmuje narzędzia CTest) jest zintegrowana w środowisku IDE programu Visual Studio domyślnie jako część **Develoment pulpitu za pomocą języka C++** obciążenia. Jeśli musisz zainstalować go na komputerze, Otwórz program Instalator programu Visual Studio, kliknij pozycję **Modyfikuj** przycisk, a następnie sprawdź [narzędzia CMake w języku Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) pod listą składników obciążenia.

## <a name="to-write-tests"></a>Do pisania testów

Obsługa CMake w programie Visual Studio nie obejmują systemu projektu programu Visual Studio. W związku z tym zapisu i Konfigurowanie narzędzia CTest testów, tak samo jak w każdym środowisku CMake. Aby uzyskać więcej informacji na temat używania narzędzia CMake w programie Visual Studio, zobacz [narzędzia CMake w języku Visual C++](/cpp/ide/cmake-tools-for-visual-cpp).

## <a name="to-run-tests-visual-studio-2017-version-156"></a>Aby uruchomić testy (Visual Studio 2017 w wersji 15.6)

W programie Visual Studio 2017 w wersji 15.6 narzędzia CTest jest w pełni zintegrowana z **Eksplorator testów** i obsługuje także jednostki Google i zwiększenie wydajności, testowanie struktur. Te struktury są domyślnie dołączone jako składników w **Develoment pulpitu za pomocą języka C++** obciążenia. Jednak w przypadku uaktualniania projektu ze starszej wersji programu Visual Studio, może być konieczne zainstalowanie tych środowisk przy użyciu programu Instalatora programu Visual Studio.

Na poniższej ilustracji przedstawiono wyniki narzędzia CTest uruchamiane przy użyciu framework platformy Google Test:

![Narzędzia CTest przy użyciu Framework platformy Google Test w programie VS2017 wersji 15.6](media/ctest-test-explorer.png)

Jeśli używasz narzędzia CTest, ale nie Google lub Boost kart, zobaczysz wyniki na poziomie narzędzia CTest zamiast poszczególnych testów poziom metody. Można debugować i krokowym tylko do narzędzia CTest pliki wykonywalne, ale ślady stosu na poszczególne testy nie są obsługiwane.

## <a name="to-run-tests-visual-studio-2017-version-155"></a>Aby uruchomić testy (Visual Studio 2017 w wersji 15.5)

W **programu Visual Studio 2017 w wersji 15.5**, narzędzia CTest nie jest zintegrowany z **Eksplorator testów**. Można uruchomić testy z menu głównego narzędzia CMake lub z menu kontekstowego *CMakeLists.txt* w pliku **Eksploratora rozwiązań**. Wyniki testów są kierowane do programu Visual Studio **okno danych wyjściowych**.

![Uruchom testy narzędzia CTest w wersji 15.5 programu VS 2017](media/cpp-cmake-run-tests.png)

## <a name="see-also"></a>Zobacz także

[Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)