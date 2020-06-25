---
title: Jak używać Google Test dla języka C++
description: Użyj Google Test, aby utworzyć testy jednostkowe języka C++ w programie Visual Studio.
ms.date: 05/06/2017
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: bf4db1c01fc79d32f7e498c265b74dec34f67e48
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287249"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Jak używać Google Test dla języka C++ w programie Visual Studio

W programie Visual Studio 2017 i nowszych Google Test jest zintegrowana z programem Visual Studio IDE jako domyślny składnik **tworzenia aplikacji klasycznej przy użyciu obciążenia C++** . Aby sprawdzić, czy jest zainstalowana na komputerze, Otwórz Instalator programu Visual Studio i Znajdź Google Test na liście składników obciążenia:

![Zainstaluj Google Test](media/cpp-google-component.png)

::: moniker range="vs-2019"

## <a name="add-a-google-test-project-in-visual-studio-2019"></a>Dodawanie projektu Google Test w programie Visual Studio 2019

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł rozwiązanie i wybierz polecenie **Dodaj** > **Nowy projekt**.
2. Ustaw **Język** **C++** i wpisz **test** w polu wyszukiwania. Z listy wyników wybierz pozycję **projekt Google test**.
3. Nadaj projektowi testowemu nazwę i kliknij przycisk **OK**.

![Nowy projekt Google Test](media/vs-2019/cpp-gtest-new-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="add-a-google-test-project-in-visual-studio-2017"></a>Dodawanie projektu Google Test w programie Visual Studio 2017

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł rozwiązanie i wybierz polecenie **Dodaj** > **Nowy projekt**.
2. W lewym okienku wybierz **Visual C++** > **test** , a następnie wybierz **Google test projekt** w środkowym okienku.
3. Nadaj projektowi testowemu nazwę i kliknij przycisk **OK**.

![Nowy projekt Google Test](media/cpp-gtest-new-project.png)

::: moniker-end

## <a name="configure-the-test-project"></a>Konfigurowanie projektu testowego

W wyświetlonym oknie dialogowym **Konfiguracja projektu testowego** można wybrać projekt do przetestowania. Po wybraniu projektu program Visual Studio dodaje odwołanie do wybranego projektu. W przypadku wybrania opcji Brak projektu należy ręcznie dodać odwołania do projektów, które mają zostać przetestowane. W przypadku wybrania między statycznym i dynamicznym łączeniem do Google Test plików binarnych zagadnienia są takie same jak w przypadku każdego programu C++. Aby uzyskać więcej informacji, zobacz [biblioteki DLL w Visual C++](/cpp/build/dlls-in-visual-cpp).

![Konfigurowanie projektu Google Test](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>Ustawianie opcji dodatkowych

Z menu głównego wybierz pozycję **Narzędzia**  >  **Opcje**  >  **test adapter for Google test** , aby ustawić dodatkowe opcje. Więcej informacji o tych ustawieniach można znaleźć w dokumentacji Google Test.

![Ustawienia projektu Google Test](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>Dodaj dyrektywy include

W pliku test *. cpp* Dodaj wszelkie potrzebne dyrektywy, `#include` Aby zapewnić, że typy i funkcje programu mają być widoczne dla kodu testu. Zazwyczaj program znajduje się na poziomie jednego poziomu w hierarchii folderów. Po wpisaniu `#include "../"` okna IntelliSense zostanie wyświetlone okno i umożliwi wybranie pełnej ścieżki do pliku nagłówkowego.

![Dodaj dyrektywy #include](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>Zapisz i uruchom testy

Teraz możesz przystąpić do pisania i uruchamiania testów Google. Zobacz Podręcznik [Google test](https://github.com/google/googletest/blob/master/googletest/docs/primer.md) , aby uzyskać informacje na temat makr testowych. Zobacz [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](run-unit-tests-with-test-explorer.md) , aby uzyskać informacje na temat odnajdywania, uruchamiania i grupowania testów przy użyciu programu **Test Explorer**.

## <a name="see-also"></a>Zobacz też

[Zapisz testy jednostkowe dla C/C++](writing-unit-tests-for-c-cpp.md)
