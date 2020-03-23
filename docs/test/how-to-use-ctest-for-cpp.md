---
title: Jak używać CTest dla języka C++
ms.date: 01/23/2020
ms.topic: conceptual
ms.author: corob
manager: jillfra
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 78759a017575916bce3b3fff643cbce8ff303fd6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76826526"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio-2017-and-later"></a>Jak używać CTest dla języka C++ w programie Visual Studio 2017 i nowszych

CMake (który zawiera CTest) jest domyślnie zintegrowany z ide programu Visual Studio jako składnik **pulpitu rozwoju z c++** obciążenia. Jeśli chcesz zainstalować go na komputerze, otwórz program Visual Studio Installer program, kliknij przycisk **Desktop Development z c++,** a następnie kliknij przycisk **Modyfikuj**. Wybierz **C++ CMake narzędzia dla systemu Windows** na liście składników obciążenia.

## <a name="to-write-tests"></a>Aby napisać testy

CMake pomocy technicznej w programie Visual Studio nie obejmuje systemu projektu visual studio. W związku z tym można napisać i skonfigurować CTest testy tak samo jak w dowolnym środowisku CMake. Użyj `enable_testing()` polecenia, aby włączyć `add_test()` testowanie, a lub `gtest_discover_tests()` polecenia, aby dodać nowy test. Aby dowiedzieć się więcej o CTest, zobacz [CMake dokumentacji](https://gitlab.kitware.com/cmake/community/wikis/doc/ctest/Testing-With-CTest). 

Aby uzyskać więcej informacji na temat korzystania z CMake w programie Visual Studio, zobacz [CMake projektów w programie Visual Studio](/cpp/build/cmake-projects-in-visual-studio).

## <a name="to-run-tests"></a>Aby uruchomić testy

CTest jest w pełni zintegrowany z **Eksploratorem testów,** a także obsługuje zarówno platformy testowania jednostek Google, jak i Boost. Te struktury są domyślnie uwzględniane jako składniki w programie Rozwoju pulpitu z obciążeniem **C++.** Jednak w przypadku uaktualniania projektu ze starszej wersji programu Visual Studio może być konieczne zainstalowanie tych struktur przy użyciu programu Visual Studio Installer.

Na poniższej ilustracji przedstawiono wyniki ctest uruchomić przy użyciu struktury Google Test:

![CTest z Google Test Framework w programie Visual Studio](media/ctest-test-explorer.png)

Jeśli używasz CTest, ale nie google lub boost karty, zobaczysz wyniki na poziomie CTest zamiast na poziomie metody indywidualnej. Można debugować i krok po kroku CTest tylko pliki wykonywalne, ale ślady stosu na poszczególnych testów nie są obsługiwane.

## <a name="see-also"></a>Zobacz też

- [Zapis testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)
