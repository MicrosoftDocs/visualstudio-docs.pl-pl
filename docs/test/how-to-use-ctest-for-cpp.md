---
title: Jak używać narzędzia ctest dla języka C++
description: Dowiedz się, jak tworzyć i uruchamiać testy z narzędzia ctest, które są domyślnie zintegrowane z programem Visual Studio IDE.
ms.custom: SEO-VS-2020
ms.date: 01/23/2020
ms.topic: how-to
ms.author: corob
manager: jmartens
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 23d235d4b18c9909868cf890e31d835b3f7ea948
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969285"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio-2017-and-later"></a>Jak używać narzędzia ctest for C++ w programie Visual Studio 2017 i nowszych

CMake (który obejmuje narzędzia ctest) jest domyślnie zintegrowany z programem Visual Studio IDE jako składnik **tworzenia aplikacji klasycznych w** ramach obciążenia C++. Jeśli musisz zainstalować ją na maszynie, Otwórz program Instalator programu Visual Studio, kliknij przycisk **Programowanie aplikacji klasycznych w języku C++** , a następnie kliknij przycisk **Modyfikuj**. Wybierz pozycję **C++ CMAKE Tools for Windows** , na liście składników obciążenia.

## <a name="to-write-tests"></a>Aby napisać testy

Obsługa CMake w programie Visual Studio nie obejmuje systemu projektów programu Visual Studio. W związku z tym należy napisać i skonfigurować testy narzędzia ctest tak samo jak w każdym środowisku CMake. Użyj `enable_testing()` polecenia, aby włączyć testowanie, i `add_test()` polecenie, `gtest_discover_tests()` Aby dodać nowy test. Aby dowiedzieć się więcej na temat narzędzia ctest, zobacz [dokumentację dotyczącą CMAKE](https://gitlab.kitware.com/cmake/community/wikis/doc/ctest/Testing-With-CTest). 

Aby uzyskać więcej informacji o korzystaniu z CMake w programie Visual Studio, zobacz [CMAKE projects in Visual Studio](/cpp/build/cmake-projects-in-visual-studio).

## <a name="to-run-tests"></a>Aby uruchomić testy

Narzędzia ctest jest w pełni zintegrowana z **Eksploratorem testów** i obsługuje zarówno platformy do testowania jednostkowego Google, jak i usprawnienia. Te struktury są uwzględniane domyślnie jako składniki do **tworzenia aplikacji klasycznych przy użyciu obciążenia C++** . Jeśli jednak uaktualniasz projekt ze starszej wersji programu Visual Studio, może być konieczne zainstalowanie tych platform przy użyciu programu Instalator programu Visual Studio.

Na poniższej ilustracji przedstawiono wyniki przebiegu narzędzia ctest przy użyciu platformy Google Test Framework:

![Narzędzia ctest z platformą Google Test w programie Visual Studio](media/ctest-test-explorer.png)

Jeśli używasz narzędzia ctest, ale nie do kart Google i wzbudzenia, zobaczysz wyniki na poziomie narzędzia ctest, a nie na poziomie poszczególnych metod testowych. Możliwe jest debugowanie i przechodzenie krok po kroku do narzędzia ctest plików wykonywalnych, ale ślady stosu dla poszczególnych testów nie są obsługiwane.

## <a name="see-also"></a>Zobacz też

- [Zapisz testy jednostkowe dla C/C++](writing-unit-tests-for-c-cpp.md)
