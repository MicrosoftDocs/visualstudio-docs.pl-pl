---
title: Jak używać platformy Google Test dla języka C++
ms.date: 11/04/2017
ms.topic: conceptual
ms.author: mblome
manager: jillfra
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 90761092f3e3be9aad57ab2b47e4648676871f9d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55957367"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Jak używać platformy Google Test dla języka C++ w programie Visual Studio
W **programu Visual Studio 2017 w wersji 15.5** i później platformy Google Test jest zintegrowana w środowisku IDE programu Visual Studio jako część domyślnego **programowanie aplikacji klasycznych w języku C++** obciążenia. Aby sprawdzić, czy jest zainstalowany na komputerze, otwórz Instalator programu Visual Studio i Znajdź platformy Google Test pod listą składników obciążenia:

![Instalowanie platformy Google Test](media/cpp-google-component.png)

## <a name="add-a-google-test-project-to-the-solution"></a>Dodaj projekt Google Test do rozwiązania
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł rozwiązania i wybierz **Dodaj** > **nowy projekt**.
2. W okienku po lewej stronie wybierz **Visual C++** > **testu** , a następnie wybierz **projekt testowy Google** w środkowym okienku.
3. Nazwij projekt testowy, a następnie kliknij przycisk **OK**.

![Nowy projekt Google Test](media/cpp-gtest-new-project.png)

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
