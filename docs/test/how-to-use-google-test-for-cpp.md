---
title: Jak używać Google Test dla języka C++
description: Użyj Google Test, aby utworzyć testy jednostkowe języka C++ w Visual Studio.
ms.date: 05/06/2017
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: a338b6f62aee6ec342ef6a16abec71cb6a833bc0
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042967"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Jak używać Google Test dla języka C++ w programie Visual Studio

W Visual Studio 2017 r. i nowszych Google Test zintegrowane ze środowiskami IDE programu Visual Studio jako domyślny składnik obciążenia Tworzenie aplikacji klasycznych w języku **C++.** Aby sprawdzić, czy jest on zainstalowany na maszynie, otwórz Instalator programu Visual Studio i znajdź Google Test na liście składników obciążenia:

![Instalowanie Google Test](media/cpp-google-component.png)

::: moniker range=">=vs-2019"

## <a name="add-a-google-test-project-in-visual-studio-2019"></a>Dodawanie Google Test projektu w Visual Studio 2019 r.

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł rozwiązania i wybierz polecenie **Dodaj** > **nowy projekt.**
2. Ustaw **wartość Language** na **C++** i **wpisz test** w polu wyszukiwania. Z listy wyników wybierz pozycję **Google Test Project**.
3. Nadaj projektowi testoweowi nazwę i kliknij przycisk **OK.**

![Nowy Google Test projekt](media/vs-2019/cpp-gtest-new-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="add-a-google-test-project-in-visual-studio-2017"></a>Dodawanie projektu Google Test w programie Visual Studio 2017

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł rozwiązania i wybierz polecenie **Dodaj** > **nowy projekt.**
2. W okienku po lewej stronie wybierz **pozycję Visual C++** Test, a następnie wybierz pozycję >  Google Test **Project** (Projekt) w środkowym okienku.
3. Nadaj projektowi testoweowi nazwę i kliknij przycisk **OK.**

![Nowy Google Test projekt](media/cpp-gtest-new-project.png)

::: moniker-end

## <a name="configure-the-test-project"></a>Konfigurowanie projektu testowego

W **wyświetlonym oknie dialogowym** Konfiguracja projektu testowego możesz wybrać projekt, który chcesz przetestować. Po wybraniu projektu program Visual Studio odwołanie do wybranego projektu. Jeśli nie wybierzesz projektu, musisz ręcznie dodać odwołania do projektów, które chcesz przetestować. Podczas wybierania między statycznym i dynamicznym łączeniu z Google Test binarnymi zagadnienia są takie same, jak w przypadku dowolnego programu w języku C++. Aby uzyskać więcej informacji, zobacz [Biblioteki DLL w Visual C++](/cpp/build/dlls-in-visual-cpp).

![Konfigurowanie Google Test projektu](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>Ustawianie dodatkowych opcji

Z menu głównego wybierz pozycję **Opcje**  >  **Test Adapter for Google Test,**  >   aby ustawić dodatkowe opcje. Zobacz dokumentację Google Test, aby uzyskać więcej informacji na temat tych ustawień.

![Google Test projektu](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>Dodawanie dyrektyw include

W *testowym pliku cpp* dodaj wszelkie potrzebne dyrektywy, aby typy i funkcje programu były `#include` widoczne dla kodu testowego. Zazwyczaj program znajduje się o jeden poziom w hierarchii folderów. Jeśli wpiszesz okno Funkcji IntelliSense, zostanie wyświetlone okno umożliwiające wybranie pełnej `#include "../"` ścieżki do pliku nagłówkowego.

![Dodawanie #include dyrektywy](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>Pisanie i uruchamianie testów

Teraz możesz pisać i uruchamiać testy Google. Zobacz [Google Test, aby](https://github.com/google/googletest/blob/master/docs/primer.md) uzyskać informacje o makrach testowych. Zobacz Run unit tests with Test Explorer (Uruchamianie testów jednostkowych za pomocą [Eksploratora](run-unit-tests-with-test-explorer.md) testów), aby uzyskać informacje na temat odnajdywania, uruchamiania i grupowania testów przy użyciu **Eksploratora testów.**

## <a name="see-also"></a>Zobacz też

[Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)
