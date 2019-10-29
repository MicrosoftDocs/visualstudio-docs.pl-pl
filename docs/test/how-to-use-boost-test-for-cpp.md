---
title: Jak używać metody Zwiększ. test dlaC++
description: Użyj metody Zwiększ. test, aby utworzyć testy jednostkowe w programie Visual Studio.
ms.date: 05/06/2019
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 966983fa15b60db33f11645b25561a74ad5fadbe
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983445"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Jak używać metody Zwiększ. test dla C++ programu Visual Studio

W programie Visual Studio 2017 i nowszych adaptery zwiększania wydajności test jest zintegrowany ze środowiskiem IDE programu Visual Studio jako składnikem **tworzenia aplikacji C++ klasycznych** .

![Adapter testowy do zwiększenia. test](media/cpp-boost-component.png)

Jeśli nie masz zainstalowanego obciążenia dla **komputerów stacjonarnych C++**  , Otwórz **Instalator programu Visual Studio**. Wybierz pozycję **programowanie C++ dla komputerów stacjonarnych** , a następnie wybierz przycisk **Modyfikuj** .

## <a name="install-boost"></a>Zwiększ zwiększenie wydajności

Zwiększenie wydajności. test wymaga [zwiększenia wydajności](https://www.boost.org/). Jeśli nie masz zainstalowanej promocji, zalecamy użycie Menedżera pakietów Vcpkg.

1. Postępuj zgodnie z instrukcjami w [Vcpkg C++ : Menedżer pakietów dla systemu Windows](/cpp/vcpkg) do zainstalowania Vcpkg (jeśli go jeszcze nie masz).

1. Zainstaluj bibliotekę "Zwiększ. test" dynamicznej lub statycznej:

    - Uruchom **podwyższenie poziomu instalacji vcpkg — test** , aby zainstalować bibliotekę dynamiczną Zwiększ. test.

       Oraz

    - Uruchom podwyższenie poziomu **instalacji vcpkg-test: x86-Windows-static** , aby zainstalować statyczną bibliotekę.

1. Uruchom **vcpkg integrację instalacji** , aby skonfigurować program Visual Studio z biblioteką i dołączyć ścieżki do nagłówków i plików binarnych podwyższania poziomu.

## <a name="add-the-item-template-visual-studio-2017-version-156-and-later"></a>Dodaj szablon elementu (Visual Studio 2017 w wersji 15,6 lub nowszej)

1. Aby utworzyć plik *. cpp* dla testów, kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj nowy element**.

   ![Zwiększ. szablon elementu testowego](media/boost_test_item_template.png)

1. Nowy plik zawiera przykładową metodę testową. Skompiluj projekt, aby umożliwić **Eksploratorowi testów** odnajdywanie metody.

Szablon elementu używa wariantu o pojedynczym nagłówku podwyższania poziomu. test, ale można zmodyfikować ścieżkę #include, aby użyć wariantu biblioteki autonomicznej. Aby uzyskać więcej informacji, zobacz [Dodawanie dyrektyw include](#add-include-directives).

## <a name="create-a-test-project"></a>Tworzenie projektu testowego

W programie Visual Studio 2017 w wersji 15,5 nie ma wstępnie skonfigurowanego projektu testowego ani szablonów elementów dostępnych do zwiększenia. test. W związku z tym należy utworzyć i skonfigurować projekt aplikacji konsolowej do przechowywania testów.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł rozwiązania i wybierz polecenie **Dodaj** > **Nowy projekt**.

1. W lewym okienku wybierz pozycję **Visual C++**  > **Windows Desktop**, a następnie wybierz szablon **aplikacja konsoli systemu Windows** .

1. Nadaj projektowi nazwę i wybierz **przycisk OK**.

1. Usuń funkcję `main` w pliku *CPP* .

1. Jeśli używasz wersji "Promocja" z pojedynczym nagłówkiem lub biblioteką dynamiczną, przejdź do pozycji [Dodaj dyrektywy include](#add-include-directives). Jeśli używasz statycznej wersji biblioteki, musisz wykonać kilka dodatkowych konfiguracji:

   a. Aby edytować plik projektu, najpierw go Zwolnij. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Zwolnij projekt**. Następnie kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **edytuj < nazwa\>. vcxproj**.

   b. Dodaj dwa wiersze do grupy właściwości **Globals** , jak pokazano poniżej:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   s. Zapisz i zamknij plik *\*. vcxproj* , a następnie załaduj ponownie projekt.

   Wykres. Aby otworzyć **strony właściwości**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Właściwości**.

   Wykres. Rozwiń pozycję **generowanie kodu**w języku **C/C++**  > , a następnie wybierz pozycję **Biblioteka środowiska uruchomieniowego**. Wybierz pozycję **/MTD** , aby debugować statyczną bibliotekę wykonawczą lub **/MT** dla biblioteki środowiska uruchomieniowego statycznej wersji.

   n. Rozwiń węzeł **konsolidator** > **system**. Sprawdź, czy **podsystem** jest ustawiony na **konsolę**.

   g. Wybierz **przycisk OK** , aby zamknąć strony właściwości.

## <a name="add-include-directives"></a>Dodaj dyrektywy include

1. W pliku test *. cpp* Dodaj wszelkie potrzebne dyrektywy `#include`, aby zapewnić, że typy i funkcje programu mają być widoczne dla kodu testu. Zazwyczaj program znajduje się na poziomie jednego poziomu w hierarchii folderów. Jeśli wpiszesz `#include "../"`, zostanie wyświetlone okno IntelliSense, które umożliwi wybranie pełnej ścieżki do pliku nagłówkowego.

   ![Dodaj dyrektywy #include](media/cpp-gtest-includes.png)

   Możesz użyć autonomicznej biblioteki z:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Lub użyj wersji pojedynczego nagłówka z:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Następnie zdefiniuj `BOOST_TEST_MODULE`.

Poniższy przykład jest wystarczający, aby test mógł zostać wykrywalny w **Eksploratorze testów**:

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

## <a name="write-and-run-tests"></a>Zapisz i uruchom testy

Teraz możesz przystąpić do pisania i uruchamiania testów wzrostu. Więcej informacji na temat makr testowych można znaleźć w [dokumentacji biblioteki testowej o zwiększeniu wydajności](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html) . Zobacz [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](run-unit-tests-with-test-explorer.md) , aby uzyskać informacje na temat odnajdywania, uruchamiania i grupowania testów przy użyciu programu **Test Explorer**.

## <a name="see-also"></a>Zobacz także

- [Zapisz testy jednostkowe dla C/C++](writing-unit-tests-for-c-cpp.md)
