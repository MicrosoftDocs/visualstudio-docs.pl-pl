---
title: Jak używać narzędzia CTest dla języka C++
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: mblome
manager: jillfra
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 0b6c4eb391014342a18ec3fe56a03a651463105c
ms.sourcegitcommit: d4920babfc3d24a3fe1d4bf446ed3fe73b344467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2019
ms.locfileid: "67160089"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio-2017-and-later"></a>Jak używać narzędzia CTest dla C++ w programie Visual Studio 2017 i nowsze

CMake (co obejmuje narzędzia CTest) jest zintegrowana w środowisku IDE programu Visual Studio domyślnie jako część **programowanie aplikacji klasycznych w języku C++** obciążenia. Jeśli musisz zainstalować go na komputerze, Otwórz program Instalator programu Visual Studio, kliknij pozycję **programowanie aplikacji klasycznych przy użyciu C++**  przycisk, a następnie kliknij przycisk **Modyfikuj**. Wybierz  **C++ narzędzia CMake dla Windows** pod listą składników obciążenia.

## <a name="to-write-tests"></a>Do pisania testów

Obsługa CMake w programie Visual Studio nie obejmują systemu projektu programu Visual Studio. W związku z tym zapisu i Konfigurowanie narzędzia CTest testów, tak samo jak w każdym środowisku CMake. Aby uzyskać więcej informacji na temat używania narzędzia CMake w programie Visual Studio, zobacz [projektów CMake w programie Visual Studio](/cpp/build/cmake-projects-in-visual-studio).

## <a name="to-run-tests"></a>Aby uruchomić testy

Narzędzia CTest jest w pełni zintegrowana z **Eksplorator testów** i obsługuje także jednostki Google i zwiększenie wydajności, testowanie struktur. Te struktury są domyślnie dołączone jako składników w **programowanie aplikacji klasycznych w języku C++** obciążenia. Jednak w przypadku uaktualniania projektu ze starszej wersji programu Visual Studio, może być konieczne zainstalowanie tych środowisk przy użyciu programu Instalatora programu Visual Studio.

Na poniższej ilustracji przedstawiono wyniki narzędzia CTest uruchamiane przy użyciu framework platformy Google Test:

![Narzędzia CTest przy użyciu Framework platformy Google Test w programie Visual Studio](media/ctest-test-explorer.png)

Jeśli używasz narzędzia CTest, ale nie Google lub Boost kart, zobaczysz wyniki na poziomie narzędzia CTest zamiast poszczególnych testów poziom metody. Można debugować i krokowym tylko do narzędzia CTest pliki wykonywalne, ale ślady stosu na poszczególne testy nie są obsługiwane.

Na poniższej ilustracji przedstawiono wyniki narzędzia CTest uruchamiane przy użyciu framework platformy Google Test:

![Narzędzia CTest przy użyciu Framework platformy Google Test w programie Visual Studio 2017](media/ctest-test-explorer.png)

Jeśli używasz narzędzia CTest, ale nie Google lub Boost kart, zobaczysz wyniki na poziomie narzędzia CTest zamiast poszczególnych testów poziom metody. Można debugować i krokowym tylko do narzędzia CTest pliki wykonywalne, ale ślady stosu na poszczególne testy nie są obsługiwane.

## <a name="see-also"></a>Zobacz także

- [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)
