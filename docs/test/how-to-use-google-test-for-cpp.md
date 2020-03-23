---
title: Jak korzystać z Google Test dla Języka C++
description: Użyj Testu Google, aby utworzyć testy jednostkowe języka C++ w programie Visual Studio.
ms.date: 05/06/2017
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 31078b060c94f3253232d22681a1a5dae47e03b6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279295"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Jak korzystać z Google Test dla języka C++ w programie Visual Studio

W programie Visual Studio 2017 i nowszych test Google jest zintegrowany z ideą programu Visual Studio jako domyślny składnik **środowiska deweloperskie dla komputerów stacjonarnych z obciążeniem języka C++.** Aby sprawdzić, czy jest zainstalowany na komputerze, otwórz Instalator programu Visual Studio i znajdź Test Google na liście składników obciążenia:

![Zainstaluj test Google](media/cpp-google-component.png)

::: moniker range="vs-2019"

## <a name="add-a-google-test-project-in-visual-studio-2019"></a>Dodawanie projektu testu Google w programie Visual Studio 2019

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł rozwiązania i wybierz polecenie **Dodaj** > **nowy projekt**.
2. Ustaw **język** na **C++** i wpisz **test** w polu wyszukiwania. Z listy wyników wybierz pozycję **Google Test Project**.
3. Nadaj projektowi testowi nazwę i kliknij przycisk **OK**.

![Nowy projekt testowy Google](media/vs-2019/cpp-gtest-new-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="add-a-google-test-project-in-visual-studio-2017"></a>Dodawanie projektu testu Google w programie Visual Studio 2017

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł rozwiązania i wybierz polecenie **Dodaj** > **nowy projekt**.
2. W lewym okienku wybierz pozycję **Test języka Visual C++,** > **a** następnie wybierz pozycję Google Test **Project** w środkowym okienku.
3. Nadaj projektowi testowi nazwę i kliknij przycisk **OK**.

![Nowy projekt testowy Google](media/cpp-gtest-new-project.png)

::: moniker-end

## <a name="configure-the-test-project"></a>Konfigurowanie projektu testowego

W wyświetlonym oknie dialogowym **Konfiguracja projektu testowego** można wybrać projekt, który chcesz przetestować. Po wybraniu projektu visual studio dodaje odwołanie do wybranego projektu. Jeśli wybierzesz żaden projekt, musisz ręcznie dodać odwołania do projektów, które chcesz przetestować. Wybierając między statycznym i dynamicznym łączem do plików binarnych testu Google, zagadnienia są takie same jak w przypadku każdego programu C++. Aby uzyskać więcej informacji, zobacz [biblioteki DLL w języku Visual C++](/cpp/build/dlls-in-visual-cpp).

![Konfigurowanie projektu testowego Google](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>Ustawianie dodatkowych opcji

Z menu głównego wybierz opcję **Adapter** > testu**opcji** > narzędzi**dla testu Google,** aby ustawić dodatkowe opcje. Więcej informacji na temat tych ustawień można znaleźć w dokumentacji testu Google.

![Ustawienia projektu testu Google](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>Dodaj dyrektywy o dołączania

W testowym pliku *.cpp* `#include` dodaj wszystkie potrzebne dyrektywy, aby typy i funkcje programu były widoczne dla kodu testowego. Zazwyczaj program jest o jeden poziom w hierarchii folderów. Jeśli wpiszesz `#include "../"` okno IntelliSense pojawi się i umożliwi wybranie pełnej ścieżki do pliku nagłówka.

![Dodawanie dyrektyw #include](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>Pisanie i uruchamianie testów

Teraz możesz pisać i uruchamiać testy Google. Informacje na temat makr testowych można znaleźć w [podkładie testowym Google](https://github.com/google/googletest/blob/master/googletest/docs/primer.md) Test. Aby uzyskać informacje na temat odnajdowania, uruchamiania i grupowania testów przy użyciu **Eksploratora testów,** zobacz [Uruchamianie testów jednostkowych z Eksploratorem testów.](run-unit-tests-with-test-explorer.md)

## <a name="see-also"></a>Zobacz też

[Zapis testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)
