---
title: Jak używać platformy Google Test dla języka C++
description: Użyj Google Test, aby C++ utworzyć testy jednostkowe w programie Visual Studio.
ms.date: 05/06/2017
ms.topic: conceptual
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 73f62e8b74864af0292a9cc3ab1eb325d679d2ea
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926753"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Jak używać platformy Google Test dla języka C++ w programie Visual Studio

W programie Visual Studio 2017 i nowszych Google test jest zintegrowana z programem Visual Studio IDE jako domyślny składnik **tworzenia pulpitu z C++**  obciążeniem. Aby sprawdzić, czy jest zainstalowany na komputerze, otwórz Instalator programu Visual Studio i Znajdź platformy Google Test pod listą składników obciążenia:

![Instalowanie platformy Google Test](media/cpp-google-component.png)

::: moniker range="vs-2019"

## <a name="add-a-google-test-project-in-visual-studio-2019"></a>Dodawanie projektu Google Test w programie Visual Studio 2019

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł rozwiązanie i wybierz polecenie **Dodaj** > **Nowy projekt**.
2. Ustaw **Język** na **C++** i wpisz **test** w polu wyszukiwania. Z listy wyników wybierz pozycję **projekt Google test**.
3. Nazwij projekt testowy, a następnie kliknij przycisk **OK**.

![Nowy projekt Google Test](media/vs-2019/cpp-gtest-new-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="add-a-google-test-project-in-visual-studio-2017"></a>Dodawanie projektu Google Test w programie Visual Studio 2017

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł rozwiązanie i wybierz polecenie **Dodaj** > **Nowy projekt**.
2. W lewym okienku wybierz pozycję > **test** **wizualny C++**  , a następnie wybierz **Google test projekt** w środkowym okienku.
3. Nazwij projekt testowy, a następnie kliknij przycisk **OK**.

![Nowy projekt Google Test](media/cpp-gtest-new-project.png)

::: moniker-end

## <a name="configure-the-test-project"></a>Konfigurowanie projektu testowego

W **przetestować konfigurację projektu** wyświetlonym oknie dialogowym możesz wybrać projekt, którą chcesz przetestować. Po wybraniu projektu, Visual Studio dodaje odwołanie do wybranego projektu. Jeśli wybierzesz opcję Brak projektu, musisz ręcznie dodać odwołania do projektów, które mają zostać przetestowane. Wybierając między statyczne i dynamiczne łączenie plików binarnych platformy Google Test zagadnienia są takie same jak program w języku C++. Aby uzyskać więcej informacji, zobacz [biblioteki dll w programie Visual C++](/cpp/build/dlls-in-visual-cpp).

![Konfigurowanie projektu platformy Google Test](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>Ustawianie opcji dodatkowych

W menu głównym wybierz **narzędzia** > **opcje** > **rozszerzenia Test Adapter for Google Test** można ustawić dodatkowe opcje. Zobacz dokumentację platformy Google Test, aby uzyskać więcej informacji o tych ustawieniach.

![Ustawienia projektu testowego Google](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>Dodaj dyrektywy #include

W teście *.cpp* Dodaj dowolne wymagane `#include` dyrektywy, aby uwidocznić typy i funkcje programu kod testu. Zazwyczaj program jest góry o jeden poziom w hierarchii folderów. Jeśli wpiszesz `#include "../"` okno technologii IntelliSense będą wyświetlane i umożliwiają wybór pełną ścieżkę do pliku nagłówka.

![Dodaj # dyrektywy include](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>Pisanie i Uruchamianie testów

Teraz można przystąpić do pisania i uruchamiania testów Google. Zobacz [podstawy platformy Google Test](https://github.com/google/googletest/blob/master/googletest/docs/primer.md) uzyskać informacji na temat makra testu. Zobacz [Uruchamianie testów jednostkowych w Eksploratorze testów](run-unit-tests-with-test-explorer.md) informacje odnajdywania i uruchamiania i grupowanie testów przy użyciu **Eksplorator testów**.

## <a name="see-also"></a>Zobacz także

[Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)
