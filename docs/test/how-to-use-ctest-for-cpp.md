---
title: Jak używać narzędzia CTest dla języka C++
ms.date: 01/23/2020
ms.topic: conceptual
ms.author: corob
manager: jillfra
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 78759a017575916bce3b3fff643cbce8ff303fd6
ms.sourcegitcommit: 8cbced0fb46959a3a2494852df1e41db1177a26c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76826526"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio-2017-and-later"></a>Jak używać narzędzia ctest dla C++ programu Visual Studio 2017 i nowszych

CMAKE (który obejmuje narzędzia ctest) jest domyślnie zintegrowany z programem Visual Studio IDE jako składnik **tworzenia pulpitu z C++**  obciążeniem. Jeśli musisz zainstalować ją na maszynie, Otwórz program Instalator programu Visual Studio, kliknij przycisk **Programowanie aplikacji C++ klasycznych** , a następnie kliknij przycisk **Modyfikuj**. Wybierz pozycję  **C++ narzędzia CMAKE dla systemu Windows** poniżej listy składników obciążenia.

## <a name="to-write-tests"></a>Do pisania testów

Obsługa CMake w programie Visual Studio nie obejmują systemu projektu programu Visual Studio. W związku z tym zapisu i Konfigurowanie narzędzia CTest testów, tak samo jak w każdym środowisku CMake. Użyj `enable_testing()` polecenia, aby włączyć testowanie, i `add_test()` lub `gtest_discover_tests()` polecenie, aby dodać nowy test. Aby dowiedzieć się więcej na temat narzędzia ctest, zobacz [dokumentację dotyczącą CMAKE](https://gitlab.kitware.com/cmake/community/wikis/doc/ctest/Testing-With-CTest). 

Aby uzyskać więcej informacji o korzystaniu z CMake w programie Visual Studio, zobacz [CMAKE projects in Visual Studio](/cpp/build/cmake-projects-in-visual-studio).

## <a name="to-run-tests"></a>Aby uruchomić testy

Narzędzia ctest jest w pełni zintegrowana z **Eksploratorem testów** i obsługuje zarówno platformy do testowania jednostkowego Google, jak i usprawnienia. Te struktury są domyślnie uwzględniane jako składniki do **tworzenia aplikacji C++ klasycznych** . Jednak w przypadku uaktualniania projektu ze starszej wersji programu Visual Studio, może być konieczne zainstalowanie tych środowisk przy użyciu programu Instalatora programu Visual Studio.

Na poniższej ilustracji przedstawiono wyniki narzędzia CTest uruchamiane przy użyciu framework platformy Google Test:

![Narzędzia ctest z platformą Google Test w programie Visual Studio](media/ctest-test-explorer.png)

Jeśli używasz narzędzia CTest, ale nie Google lub Boost kart, zobaczysz wyniki na poziomie narzędzia CTest zamiast poszczególnych testów poziom metody. Można debugować i krokowym tylko do narzędzia CTest pliki wykonywalne, ale ślady stosu na poszczególne testy nie są obsługiwane.

## <a name="see-also"></a>Zobacz także

- [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)
