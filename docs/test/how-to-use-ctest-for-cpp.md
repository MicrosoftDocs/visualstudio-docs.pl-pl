---
title: Jak używać narzędzia CTest dla języka C++
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: mblome
manager: jillfra
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: a97aa7dfcc1cc46d64813ea7714629cb8557055d
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714891"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio-2017-and-later"></a>Jak używać narzędzia CTest dla C++ w programie Visual Studio 2017 i nowsze

CMake (co obejmuje narzędzia CTest) jest zintegrowana w środowisku IDE programu Visual Studio domyślnie jako część **programowanie aplikacji klasycznych w języku C++** obciążenia. Jeśli musisz zainstalować go na komputerze, Otwórz program Instalator programu Visual Studio, kliknij pozycję **programowanie aplikacji klasycznych przy użyciu C++**  przycisk, a następnie kliknij przycisk **Modyfikuj**. Sprawdź [narzędzia CMake dla elementu wizualnego C++ ](/cpp/build/cmake-tools-for-visual-cpp) pod listą składników obciążenia.

## <a name="to-write-tests"></a>Do pisania testów

Obsługa CMake w programie Visual Studio nie obejmują systemu projektu programu Visual Studio. W związku z tym zapisu i Konfigurowanie narzędzia CTest testów, tak samo jak w każdym środowisku CMake. Aby uzyskać więcej informacji na temat używania narzędzia CMake w programie Visual Studio, zobacz [narzędzia CMake w języku Visual C++](/cpp/ide/cmake-tools-for-visual-cpp).

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