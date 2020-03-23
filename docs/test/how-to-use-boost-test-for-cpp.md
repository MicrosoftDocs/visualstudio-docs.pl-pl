---
title: Jak korzystać z Boost.Test dla języka C++
description: Użyj Boost.Test do tworzenia testów jednostkowych w programie Visual Studio.
ms.date: 01/29/2020
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 0a1a621c7ee7175d86b2cbcf9a6e2c02c0aecbb3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76922919"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Jak korzystać z Boost.Test dla języka C++ w programie Visual Studio

W programie Visual Studio 2017 i nowszych karta testu Boost.Test jest zintegrowana z ideą programu Visual Studio. Jest to składnik **rozwoju pulpitu z c++** obciążenia.

![Adapter testowy do boost.test](media/cpp-boost-component.png)

Jeśli nie masz zainstalowanego obciążenia pulpitu z zainstalowanym obciążeniem **C++,** otwórz **Instalatora programu Visual Studio**. Wybierz **programowanie pulpitu z obciążeniem języka C++,** a następnie wybierz przycisk **Modyfikuj.**

## <a name="install-boost"></a>Zainstalować rozwiązanie Boost

Boost.Test wymaga [wzmocnienia!](https://www.boost.org/) Jeśli nie masz zainstalowanego boosta, zalecamy użycie menedżera pakietów Vcpkg.

1. Postępuj zgodnie z instrukcjami w [Vcpkg: Menedżer pakietów C++ dla systemu Windows,](/cpp/vcpkg) aby zainstalować vcpkg (jeśli jeszcze go nie masz).

1. Zainstaluj bibliotekę dynamiczną lub statyczną Boost.Test:

    - Uruchom, `vcpkg install boost-test` aby zainstalować bibliotekę dynamiczną Boost.Test.

       — Lub —

    - Uruchom, `vcpkg install boost-test:x86-windows-static` aby zainstalować bibliotekę statyczną Boost.Test.

1. Uruchom, `vcpkg integrate install` aby skonfigurować program Visual Studio z biblioteki i dołączyć ścieżki do boost nagłówki i pliki binarne.

Masz możliwość wyboru w jaki sposób skonfigurować testy w ramach rozwiązania w programie Visual Studio: Można dołączyć kod testu w projekcie w ramach testu lub można utworzyć oddzielny projekt testowy dla testów. Oba wybory mają zalety i wady.

## <a name="add-tests-inside-your-project"></a>Dodawanie testów wewnątrz projektu

W programie Visual Studio 2017 w wersji 15.6 lub nowszej można dodać szablon elementu do testów do projektu. Zarówno testy, jak i kod na żywo w tym samym projekcie. Musisz utworzyć konfigurację kompilacji oddzielne do generowania kompilacji testowej. I musisz zachować testy z debugowania i wydania kompilacji.

W programie Visual Studio 2017 w wersji 15.5 nie są dostępne wstępnie skonfigurowane szablony projektu testowego ani elementów dla programu Boost.Test. Użyj instrukcji, aby utworzyć i skonfigurować oddzielny projekt testowy.

### <a name="create-a-boosttest-item"></a>Tworzenie elementu boost.test

1. Aby utworzyć plik *cpp* dla testów, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań** i wybierz polecenie **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodawanie nowego elementu** rozwiń rozwiń węzeł **Zainstalowany** > **test**języka**Visual C++** > . Wybierz **boost.test**, a następnie **wybierz** dodaj, aby dodać *Test.cpp* do projektu.

   ![Szablon elementu boost.test](media/boost_test_item_template.png)

Nowy plik *Test.cpp* zawiera przykładową metodę badania. Ten plik jest, gdzie można dołączyć własne pliki nagłówka i testy zapisu dla aplikacji.

Plik testowy używa również makr `main` do definiowania nowej procedury dla konfiguracji testowych. Jeśli teraz tworzysz projekt, zobaczysz błąd LNK2005, taki jak "_main już zdefiniowany w pliku main.obj".

### <a name="create-and-update-build-configurations"></a>Tworzenie i aktualizowanie konfiguracji kompilacji

1. Aby utworzyć konfigurację testową, na pasku menu wybierz pozycję **Build** > **Configuration Manager**. W oknie **dialogowym Menedżer konfiguracji** otwórz okno rozwijane w obszarze **Konfiguracja rozwiązania aktywnego** i wybierz pozycję **Nowy**. W oknie dialogowym **Nowa konfiguracja rozwiązania** wprowadź nazwę, taką jak "Debug UnitTests". W obszarze **Kopiowanie ustawień z** wybierz **debugowanie**, a następnie wybierz przycisk **OK**.

1. Wyklucz kod testowy z konfiguracji debugowania i wydania: W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy test.cpp i wybierz **polecenie Właściwości**. W oknie dialogowym **Strony właściwości** wybierz pozycję **Wszystkie konfiguracje** z listy rozwijanej **Konfiguracja.** Wybierz pozycję **Właściwości** > **ogólne** konfiguracji i otwórz listy rozwijanej dla właściwości **Wykluczone z kompilacji.** Wybierz **pozycję Tak**, a następnie wybierz pozycję **Zastosuj,** aby zapisać zmiany.

1. Aby uwzględnić kod testowy w konfiguracji debugowania unittests, w oknie dialogowym **Strony właściwości** wybierz pozycję **Debug UnitTests** w **menu rozwijanym Konfiguracja.** Wybierz **pozycję Nie** we właściwości **Wykluczone z kompilacji,** a następnie wybierz przycisk **OK,** aby zapisać zmiany.

1. Wyklucz kod główny z konfiguracji Debug UnitTests. W **Eksploratorze rozwiązań**kliknij prawym `main` przyciskiem myszy plik zawierający funkcję i wybierz polecenie **Właściwości**. W oknie dialogowym **Strony właściwości** wybierz pozycję **Debug UnitTests** w menu rozwijanym **Konfiguracja.** Wybierz pozycję **Właściwości** > **ogólne** konfiguracji i otwórz listy rozwijanej dla właściwości **Wykluczone z kompilacji.** Wybierz **pozycję Tak**, a następnie wybierz przycisk **OK,** aby zapisać zmiany.

1. Ustaw konfigurację rozwiązania na **Debugowanie UnitTests,** a następnie skompiluj projekt, aby włączyć **Eksploratora testów,** aby odnajdywać metodę.

Tak długo, jak nazwa konfiguracji, który tworzysz zaczyna się od słów "Debug" lub "Release", odpowiednie biblioteki Boost.Test są pobierane automatycznie.

Szablon elementu używa wariantu pojedynczego nagłówka Boost.Test, ale można zmodyfikować ścieżkę #include, aby użyć wariantu biblioteki autonomicznej. Aby uzyskać więcej informacji, zobacz [Dodawanie dyrektyw dołączania](#add-include-directives).

## <a name="create-a-separate-test-project"></a>Tworzenie oddzielnego projektu testowego

W wielu przypadkach łatwiej jest użyć oddzielnego projektu dla testów. Nie trzeba tworzyć specjalnej konfiguracji testowej dla projektu. Lub wykluczyć pliki testowe z kompilacji debugowania i wydania.

### <a name="to-create-a-separate-test-project"></a>Aby utworzyć oddzielny projekt testowy

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł rozwiązania i wybierz pozycję **Dodaj** > **nowy projekt**.

1. W oknie **dialogowym Dodawanie nowego projektu** wybierz pozycję **C++**, **Windows**i **Konsola** w menu rozwijanym filtru. Wybierz szablon **aplikacji konsoli,** a następnie wybierz pozycję **Dalej**.

1. Nadaj projektowi nazwę i wybierz pozycję **Utwórz**.

1. Usuń `main` funkcję w pliku *cpp.*

1. Jeśli używasz wersji boost.Test z biblioteką pojedynczego lub dynamicznego, przejdź do [dodawania dyrektyw dołączania.](#add-include-directives) Jeśli używasz wersji biblioteki statycznej, musisz wykonać dodatkową konfigurację:

   a. Aby edytować plik projektu, należy go najpierw zwolnić. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Zwolnij projekt**. Następnie kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Edytuj <nazwę\>.vcxproj**.

   b. Dodaj dwa wiersze do grupy właściwości **Globals,** jak pokazano poniżej:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   d. Zapisz i zamknij plik * \*.vcxproj,* a następnie załaduj ponownie projekt.

   d. Aby otworzyć **stronę Właściwości,** kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Właściwości**.

   e. Rozwiń pozycję**Generowanie kodu** **C/C++,** > a następnie wybierz pozycję **Biblioteka środowiska uruchomieniowego**. Wybierz **/MTd** dla biblioteki wykonawczej statycznej debugowania lub **/MT** dla biblioteki statycznego środowiska uruchomieniowego wydania.

   f. Rozwiń**system** **linkera** > . Sprawdź, czy **podsystem** jest ustawiony na **Konsola**.

   g. Wybierz **przycisk OK,** aby zamknąć strony właściwości.

## <a name="add-include-directives"></a>Dodaj dyrektywy o dołączania

1. W testowym pliku *.cpp* `#include` dodaj wszystkie potrzebne dyrektywy, aby typy i funkcje programu były widoczne dla kodu testowego. Jeśli używasz oddzielnego projektu testowego, zazwyczaj program znajduje się na poziomie równorzędnym w hierarchii folderów. Jeśli wpiszesz, `#include "../"`pojawi się okno IntelliSense i umożliwia wybranie pełnej ścieżki do pliku nagłówka.

   ![Dodawanie dyrektyw #include](media/cpp-gtest-includes.png)

   Biblioteki autonomicznej można używać z:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Możesz też użyć wersji z jednym nagłówkiem z:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Następnie zdefiniuj `BOOST_TEST_MODULE`.

Poniższy przykład jest wystarczający do wykrycia testu w **Eksploratorze testów:**

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

## <a name="write-and-run-tests"></a>Pisanie i uruchamianie testów

Teraz możesz napisać i uruchomić testy Boost. Zobacz [dokumentację biblioteki testów Boost, aby](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html) uzyskać informacje na temat makr testowych. Aby uzyskać informacje na temat odnajdowania, uruchamiania i grupowania testów przy użyciu **Eksploratora testów,** zobacz [Uruchamianie testów jednostkowych z Eksploratorem testów.](run-unit-tests-with-test-explorer.md)

## <a name="see-also"></a>Zobacz też

- [Zapis testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)
