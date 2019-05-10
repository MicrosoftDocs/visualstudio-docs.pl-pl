---
title: Jak używać platformy Boost.Test dla języka C++
description: Użyj Boost.Test można utworzyć testów jednostkowych w programie Visual Studio.
ms.date: 05/06/2019
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: cf962ec4ecade1bb88d9e301d62eb6ab8a5131cf
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226102"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Jak używać platformy Boost.Test dla języka C++ w programie Visual Studio

W programie Visual Studio 2017 i nowszych adapter testowy Boost.Test jest zintegrowana z programu Visual Studio IDE jako składnik **programowanie aplikacji klasycznych przy użyciu C++**  obciążenia.

![Rozszerzenia test Adapter for Boost.Test](media/cpp-boost-component.png)

Jeśli nie masz **programowanie aplikacji klasycznych przy użyciu C++**  obciążenia zainstalowany, otwórz **Instalatora programu Visual Studio**. Wybierz **programowanie aplikacji klasycznych w języku C++** obciążenia, wybierz **Modyfikuj** przycisku.

## <a name="install-boost"></a>Zainstaluj Boost

Wymaga Boost.Test [Boost](http://www.boost.org/)! Jeśli nie masz zainstalowane zwiększenie wydajności, firma Microsoft zaleca użycie Vcpkg Menedżera pakietów.

1. Postępuj zgodnie z instrukcjami w artykule [Vcpkg: Menedżer pakietów języka C++ dla Windows](/cpp/vcpkg) zainstalował vcpkg (Jeśli nie masz jej jeszcze).

1. Zainstaluj bibliotekę Boost.Test dynamicznej lub statycznej:

    - Uruchom **vcpkg zainstalować boost test** Aby zainstalować bibliotekę dynamicznych Boost.Test.

       -LUB-

    - Uruchom **vcpkg zainstalować boost-test: x 86-windows-static** zainstalować biblioteki statycznej platformy Boost.Test.

1. Uruchom **vcpkg integracji instalacji** do konfigurowania programu Visual Studio za pomocą biblioteki i zawierać ścieżki do nagłówków zwiększenie wydajności i danych binarnych.

## <a name="add-the-item-template-visual-studio-2017-version-156-and-later"></a>Dodaj szablon elementu (Visual Studio 2017 w wersji 15.6 i nowsze)

1. Aby utworzyć *.cpp* pliku dla testów, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj nowy element**.

   ![Szablon elementu Boost.Test](media/boost_test_item_template.png)

1. Nowy plik zawiera przykładowe metody testowej. Tworzenie projektu w celu włączenia **Eksplorator testów** metody odnajdywania.

Szablon elementu korzysta z wariantu pojedynczego nagłówka Boost.Test, ale można zmodyfikować #include ścieżkę do użycia wariant biblioteki autonomicznych. Aby uzyskać więcej informacji, zobacz [Dodaj dyrektywy #include](#add-include-directives).

## <a name="create-a-test-project"></a>Utwórz projekt testu

W programie Visual Studio 2017 w wersji 15.5 dostępnych żadnych szablonów projektu lub elementu testowych wstępnie skonfigurowanych dla platformy Boost.Test. W związku z tym należy utworzyć i skonfigurować projekt aplikacji konsoli w celu przechowywania testów.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł rozwiązania i wybierz **Dodaj** > **nowy projekt**.

1. W okienku po lewej stronie wybierz **Visual C++** > **pulpitu Windows**, a następnie wybierz **aplikacji konsoli Windows** szablonu.

1. Nazwij projekt i wybierz **OK**.

1. Usuń `main` działa w programach *.cpp* pliku.

1. Jeśli używasz wersji pojedynczego nagłówka lub dynamicznej biblioteki Boost.Test, przejdź do strony [Dodaj dyrektywy #include](#add-include-directives). Jeśli używasz wersji biblioteki statycznej, musisz przeprowadzić kilka dodatkowych czynności konfiguracyjnych:

   a. Aby edytować plik projektu, najpierw zwolnienia. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Zwolnij projekt**. Następnie kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Edytuj < nazwa\>.vcxproj**.

   b. Dodaj dwa wiersze do **Globals** grupy właściwości, jak pokazano poniżej:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   c. Zapisz i Zamknij  *\*.vcxproj* pliku, a następnie ponownie Załaduj projekt.

   d. Aby otworzyć **stron właściwości**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **właściwości**.

   d. Rozwiń **C/C++** > **generowania kodu**, a następnie wybierz pozycję **biblioteki środowiska uruchomieniowego**. Wybierz **/mtd** dla bibliotek statycznych środowiska uruchomieniowego debugowania lub **/MT** biblioteki statycznej środowiska uruchomieniowego wersji.

   f. Rozwiń **konsolidatora** > **systemu**. Upewnij się, że **podsystemu** ustawiono **konsoli**.

   g. Wybierz **OK** zamknąć na stronach właściwości.

## <a name="add-include-directives"></a>Dodaj dyrektywy #include

1. W teście *.cpp* Dodaj dowolne wymagane `#include` dyrektywy, aby uwidocznić typy i funkcje programu kod testu. Zazwyczaj program jest góry o jeden poziom w hierarchii folderów. Jeśli wpiszesz `#include "../"`, pojawi się okno technologii IntelliSense i umożliwia wybranie pełną ścieżkę do pliku nagłówka.

   ![Dodaj # dyrektywy include](media/cpp-gtest-includes.png)

   Można użyć biblioteki autonomiczny za pomocą:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Lub użyj wersji pojedynczego nagłówka przy użyciu:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Następnie zdefiniuj `BOOST_TEST_MODULE`.

Poniższy przykład jest wystarczające, aby test zakończył się być wykrywalne w **Eksploratora testów**:

```cpp
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp\> //single-header
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string expected_value = "Bill";

    // assume MyClass is defined in MyClass.h
    // and get_value() has public accessibility
    MyClass mc;
    BOOST_CHECK(expected_value == mc.get_value());
}
```

## <a name="write-and-run-tests"></a>Pisanie i Uruchamianie testów

Teraz możesz przystąpić do pisania i uruchamiania testów Boost. Zobacz [dokumentację biblioteki testów Boost](http://www.boost.org/doc/libs/release/libs/test/doc/html/index.html) uzyskać informacji na temat makra testu. Zobacz [Uruchamianie testów jednostkowych w Eksploratorze testów](run-unit-tests-with-test-explorer.md) informacje odnajdywania i uruchamiania i grupowanie testów przy użyciu **Eksplorator testów**.

## <a name="see-also"></a>Zobacz także

- [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)
