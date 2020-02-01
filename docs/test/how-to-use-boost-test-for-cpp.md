---
title: Jak używać platformy Boost.Test dla języka C++
description: Użyj metody Zwiększ. test, aby utworzyć testy jednostkowe w programie Visual Studio.
ms.date: 01/29/2020
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 0a1a621c7ee7175d86b2cbcf9a6e2c02c0aecbb3
ms.sourcegitcommit: 4be64917e4224fd1fb27ba527465fca422bc7d62
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76922919"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Jak używać platformy Boost.Test dla języka C++ w programie Visual Studio

W programie Visual Studio 2017 i nowszych adaptery zwiększania wydajności test jest zintegrowany z Visual Studio IDE. Jest to składnik **rozwoju pulpitu z C++**  obciążeniem.

![Rozszerzenia test Adapter for Boost.Test](media/cpp-boost-component.png)

Jeśli nie masz zainstalowanego obciążenia dla **komputerów stacjonarnych C++**  , Otwórz **Instalator programu Visual Studio**. Wybierz **programowanie aplikacji klasycznych w języku C++** obciążenia, wybierz **Modyfikuj** przycisku.

## <a name="install-boost"></a>Zainstaluj Boost

Wymaga Boost.Test [Boost](https://www.boost.org/)! Jeśli nie masz zainstalowanej promocji, zalecamy użycie Menedżera pakietów Vcpkg.

1. Postępuj zgodnie z instrukcjami w artykule [Vcpkg: Menedżer pakietów języka C++ dla Windows](/cpp/vcpkg) zainstalował vcpkg (Jeśli nie masz jej jeszcze).

1. Zainstaluj bibliotekę Boost.Test dynamicznej lub statycznej:

    - Uruchom `vcpkg install boost-test`, aby zainstalować bibliotekę dynamiczną Zwiększ. test.

       -LUB-

    - Uruchom `vcpkg install boost-test:x86-windows-static`, aby zainstalować bibliotekę statystyczną Zwiększ. test.

1. Uruchom `vcpkg integrate install`, aby skonfigurować program Visual Studio z biblioteką i dołączyć ścieżki do nagłówków podwyższania poziomu i plików binarnych.

Możesz wybrać sposób konfigurowania testów w ramach rozwiązania w programie Visual Studio: możesz uwzględnić kod testu w badanym projekcie lub można utworzyć oddzielny projekt testowy dla testów. Obie opcje mają zalety i wady.

## <a name="add-tests-inside-your-project"></a>Dodawanie testów wewnątrz projektu

W programie Visual Studio 2017 w wersji 15,6 i nowszych można dodać szablon elementu dla testów do projektu. Zarówno testy, jak i kod na żywo w tym samym projekcie. Musisz utworzyć oddzielną konfigurację kompilacji, aby wygenerować kompilację testową. I należy zachować testy z kompilacji i wydania.

W programie Visual Studio 2017 w wersji 15.5 dostępnych żadnych szablonów projektu lub elementu testowych wstępnie skonfigurowanych dla platformy Boost.Test. Użyj instrukcji, aby utworzyć i skonfigurować oddzielny projekt testowy.

### <a name="create-a-boosttest-item"></a>Utwórz element promocji. test

1. Aby utworzyć plik *. cpp* dla testów, kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodaj nowy element** rozwiń węzeł **zainstalowane** > **Visual C++**  > **test**. Wybierz pozycję **Zwiększ. test**, a następnie wybierz pozycję **Dodaj** , aby dodać *test. cpp* do projektu.

   ![Szablon elementu Boost.Test](media/boost_test_item_template.png)

Nowy plik *. cpp programu testowego* zawiera przykładową metodę testową. Ten plik umożliwia dołączenie własnych plików nagłówkowych i testów zapisu dla aplikacji.

Plik testowy używa także makr do definiowania nowej procedury `main` dla konfiguracji testów. Jeśli kompilujesz projekt teraz, zobaczysz błąd LNK2005, taki jak "_main już zdefiniowany w Main. obj".

### <a name="create-and-update-build-configurations"></a>Tworzenie i aktualizowanie konfiguracji kompilacji

1. Aby utworzyć konfigurację testu, na pasku menu wybierz pozycję **kompilacja** > **Configuration Manager**. W oknie dialogowym **Configuration Manager** Otwórz listę rozwijaną w obszarze **Konfiguracja aktywnego rozwiązania** i wybierz pozycję **Nowy**. W oknie dialogowym **Nowa konfiguracja rozwiązania** wprowadź nazwę, taką jak "Debug UnitTests". W obszarze **Kopiuj ustawienia z** wybierz **Debuguj**, a następnie wybierz **OK**.

1. Wyklucz kod testowy z konfiguracji debugowania i wydania: w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję test. cpp i wybierz pozycję **Właściwości**. W oknie dialogowym **strony właściwości** wybierz pozycję **wszystkie konfiguracje** na liście rozwijanej **Konfiguracja** . Wybierz pozycję **Właściwości konfiguracji** > **Ogólne** i Otwórz listę rozwijaną dla właściwości **wykluczone z kompilacji** . Wybierz pozycję **tak**, a następnie wybierz pozycję **Zastosuj** , aby zapisać zmiany.

1. Aby uwzględnić kod testu w konfiguracji UnitTests debugowania, w oknie dialogowym **strony właściwości** wybierz pozycję **Debuguj UnitTests** na liście rozwijanej **Konfiguracja** . Wybierz pozycję nie w właściwości **nie** **wykluczono z kompilacji** , a następnie wybierz przycisk **OK** , aby zapisać zmiany.

1. Wyklucz główny kod z konfiguracji usługi Debug UnitTests. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik, który zawiera funkcję `main`, a następnie wybierz polecenie **Właściwości**. W oknie dialogowym **strony właściwości** wybierz pozycję **Debuguj UnitTests** na liście rozwijanej **Konfiguracja** . Wybierz pozycję **Właściwości konfiguracji** > **Ogólne** i Otwórz listę rozwijaną dla właściwości **wykluczone z kompilacji** . Wybierz pozycję **tak**, a następnie wybierz przycisk **OK** , aby zapisać zmiany.

1. Ustaw konfigurację rozwiązania na **Debuguj UnitTests**, a następnie Skompiluj projekt, aby umożliwić **Eksploratorowi testów** odnajdywanie metody.

Tak długo, jak utworzona nazwa konfiguracji rozpoczyna się od słów "debug" lub "Release", odpowiadające im podwyższanie poziomu biblioteki testowe są pobierane automatycznie.

Szablon elementu korzysta z wariantu pojedynczego nagłówka Boost.Test, ale można zmodyfikować #include ścieżkę do użycia wariant biblioteki autonomicznych. Aby uzyskać więcej informacji, zobacz [Dodaj dyrektywy #include](#add-include-directives).

## <a name="create-a-separate-test-project"></a>Utwórz oddzielny projekt testowy

W wielu przypadkach łatwiej jest użyć oddzielnego projektu dla testów. Nie trzeba tworzyć specjalnej konfiguracji testu dla projektu. Lub Wyklucz pliki testowe z kompilacji Debug i Release.

### <a name="to-create-a-separate-test-project"></a>Aby utworzyć oddzielny projekt testowy

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł rozwiązania i wybierz **Dodaj** > **nowy projekt**.

1. W oknie dialogowym **Dodawanie nowego projektu** wybierz **C++** pozycję, **okna**i **konsolę** na liście rozwijanej filtr. Wybierz szablon **aplikacja konsoli** , a następnie wybierz przycisk **dalej**.

1. Nadaj projektowi nazwę i wybierz pozycję **Utwórz**.

1. Usuń `main` działa w programach *.cpp* pliku.

1. Jeśli korzystasz z wersji "Promocja" z pojedynczym nagłówkiem lub biblioteką dynamiczną, przejdź do pozycji [Dodaj dyrektywy include](#add-include-directives). Jeśli używasz statycznej wersji biblioteki, musisz wykonać dodatkową konfigurację:

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

   e. Rozwiń **C/C++**  > **generowania kodu**, a następnie wybierz pozycję **biblioteki środowiska uruchomieniowego**. Wybierz **/mtd** dla bibliotek statycznych środowiska uruchomieniowego debugowania lub **/MT** biblioteki statycznej środowiska uruchomieniowego wersji.

   f. Rozwiń **konsolidatora** > **systemu**. Sprawdź, czy **podsystem** jest ustawiony na **konsolę**.

   g. Wybierz **OK** zamknąć na stronach właściwości.

## <a name="add-include-directives"></a>Dodaj dyrektywy #include

1. W teście *.cpp* Dodaj dowolne wymagane `#include` dyrektywy, aby uwidocznić typy i funkcje programu kod testu. Jeśli używasz oddzielnego projektu testowego, zazwyczaj program znajduje się na poziomie elementu równorzędnego w hierarchii folderów. Jeśli wpiszesz `#include "../"`, pojawi się okno technologii IntelliSense i umożliwia wybranie pełną ścieżkę do pliku nagłówka.

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

Teraz możesz przystąpić do pisania i uruchamiania testów Boost. Zobacz [dokumentację biblioteki testów Boost](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html) uzyskać informacji na temat makra testu. Zobacz [Uruchamianie testów jednostkowych w Eksploratorze testów](run-unit-tests-with-test-explorer.md) informacje odnajdywania i uruchamiania i grupowanie testów przy użyciu **Eksplorator testów**.

## <a name="see-also"></a>Zobacz także

- [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)
