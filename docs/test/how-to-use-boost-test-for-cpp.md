---
title: Jak używać metody Zwiększ. test dla języka C++
description: Użyj metody Zwiększ. test, aby utworzyć testy jednostkowe w programie Visual Studio.
ms.date: 01/29/2020
ms.topic: how-to
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 34c593469a586d1314c7ee52f3aeb3ab6faf334c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287275"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Jak używać usprawnienia. test dla języka C++ w programie Visual Studio

W programie Visual Studio 2017 i nowszych adaptery zwiększania wydajności test jest zintegrowany z Visual Studio IDE. Jest to składnik **tworzenia aplikacji klasycznych z obciążeniem języka C++** .

![Adapter testowy do zwiększenia. test](media/cpp-boost-component.png)

Jeśli nie masz zainstalowanego obciążenia **pulpitu z** zainstalowanym obciążeniem języka C++, Otwórz **Instalator programu Visual Studio**. Wybierz pozycję **Programowanie aplikacji klasycznych w języku C++** , a następnie wybierz przycisk **Modyfikuj** .

## <a name="install-boost"></a>Zainstalować rozwiązanie Boost

Zwiększenie wydajności. test wymaga [zwiększenia wydajności](https://www.boost.org/). Jeśli nie masz zainstalowanej promocji, zalecamy użycie Menedżera pakietów Vcpkg.

1. Postępuj zgodnie z instrukcjami w [Vcpkg: Menedżer pakietów C++ dla systemu Windows](/cpp/vcpkg) do zainstalowania Vcpkg (jeśli go jeszcze nie masz).

1. Zainstaluj bibliotekę "Zwiększ. test" dynamicznej lub statycznej:

    - Uruchom `vcpkg install boost-test` , aby zainstalować bibliotekę dynamiczną Zwiększ. test.

       — Lub —

    - Uruchom `vcpkg install boost-test:x86-windows-static` , aby zainstalować bibliotekę statyczną Zwiększ. test.

1. Uruchom, `vcpkg integrate install` Aby skonfigurować program Visual Studio z biblioteką i dołączyć ścieżki do nagłówków podwyższania poziomu i plików binarnych.

Możesz wybrać sposób konfigurowania testów w ramach rozwiązania w programie Visual Studio: możesz uwzględnić kod testu w badanym projekcie lub można utworzyć oddzielny projekt testowy dla testów. Obie opcje mają zalety i wady.

## <a name="add-tests-inside-your-project"></a>Dodawanie testów wewnątrz projektu

W programie Visual Studio 2017 w wersji 15,6 i nowszych można dodać szablon elementu dla testów do projektu. Zarówno testy, jak i kod na żywo w tym samym projekcie. Musisz utworzyć oddzielną konfigurację kompilacji, aby wygenerować kompilację testową. I należy zachować testy z kompilacji i wydania.

W programie Visual Studio 2017 w wersji 15,5 nie ma wstępnie skonfigurowanego projektu testowego ani szablonów elementów dostępnych do zwiększenia. test. Użyj instrukcji, aby utworzyć i skonfigurować oddzielny projekt testowy.

### <a name="create-a-boosttest-item"></a>Utwórz element promocji. test

1. Aby utworzyć plik *. cpp* dla testów, kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **nowy element**.

1. W oknie dialogowym **Dodaj nowy element** rozwiń węzeł **zainstalowane**  >  **Visual C++**  >  **test**. Wybierz pozycję **Zwiększ. test**, a następnie wybierz pozycję **Dodaj** , aby dodać *test. cpp* do projektu.

   ![Zwiększ. szablon elementu testowego](media/boost_test_item_template.png)

Nowy plik *. cpp programu testowego* zawiera przykładową metodę testową. Ten plik umożliwia dołączenie własnych plików nagłówkowych i testów zapisu dla aplikacji.

Plik testowy używa także makr do definiowania nowej `main` procedury dla konfiguracji testów. Jeśli kompilujesz projekt teraz, zobaczysz błąd LNK2005, taki jak "_main już zdefiniowany w Main. obj".

### <a name="create-and-update-build-configurations"></a>Tworzenie i aktualizowanie konfiguracji kompilacji

1. Aby utworzyć konfigurację testu, na pasku menu wybierz opcję **Kompiluj**  >  **Configuration Manager**. W oknie dialogowym **Configuration Manager** Otwórz listę rozwijaną w obszarze **Konfiguracja aktywnego rozwiązania** i wybierz pozycję **Nowy**. W oknie dialogowym **Nowa konfiguracja rozwiązania** wprowadź nazwę, taką jak "Debug UnitTests". W obszarze **Kopiuj ustawienia z** wybierz **Debuguj**, a następnie wybierz **OK**.

1. Wyklucz kod testowy z konfiguracji debugowania i wydania: w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję test. cpp i wybierz pozycję **Właściwości**. W oknie dialogowym **strony właściwości** wybierz pozycję **wszystkie konfiguracje** na liście rozwijanej **Konfiguracja** . Wybierz pozycję **Właściwości konfiguracji**  >  **Ogólne** i Otwórz listę rozwijaną dla właściwości **wykluczone z kompilacji** . Wybierz pozycję **tak**, a następnie wybierz pozycję **Zastosuj** , aby zapisać zmiany.

1. Aby uwzględnić kod testu w konfiguracji UnitTests debugowania, w oknie dialogowym **strony właściwości** wybierz pozycję **Debuguj UnitTests** na liście rozwijanej **Konfiguracja** . Wybierz pozycję nie w właściwości **nie** **wykluczono z kompilacji** , a następnie wybierz przycisk **OK** , aby zapisać zmiany.

1. Wyklucz główny kod z konfiguracji usługi Debug UnitTests. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik, który zawiera `main` funkcję, a następnie wybierz polecenie **Właściwości**. W oknie dialogowym **strony właściwości** wybierz pozycję **Debuguj UnitTests** na liście rozwijanej **Konfiguracja** . Wybierz pozycję **Właściwości konfiguracji**  >  **Ogólne** i Otwórz listę rozwijaną dla właściwości **wykluczone z kompilacji** . Wybierz pozycję **tak**, a następnie wybierz przycisk **OK** , aby zapisać zmiany.

1. Ustaw konfigurację rozwiązania na **Debuguj UnitTests**, a następnie Skompiluj projekt, aby umożliwić **Eksploratorowi testów** odnajdywanie metody.

Tak długo, jak utworzona nazwa konfiguracji rozpoczyna się od słów "debug" lub "Release", odpowiadające im podwyższanie poziomu biblioteki testowe są pobierane automatycznie.

Szablon elementu używa wariantu o pojedynczym nagłówku podwyższania poziomu. test, ale można zmodyfikować ścieżkę #include, aby użyć wariantu biblioteki autonomicznej. Aby uzyskać więcej informacji, zobacz [Dodawanie dyrektyw include](#add-include-directives).

## <a name="create-a-separate-test-project"></a>Utwórz oddzielny projekt testowy

W wielu przypadkach łatwiej jest użyć oddzielnego projektu dla testów. Nie trzeba tworzyć specjalnej konfiguracji testu dla projektu. Lub Wyklucz pliki testowe z kompilacji Debug i Release.

### <a name="to-create-a-separate-test-project"></a>Aby utworzyć oddzielny projekt testowy

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł rozwiązania i wybierz polecenie **Dodaj**  >  **Nowy projekt**.

1. W oknie dialogowym **Dodawanie nowego projektu** wybierz pozycję **C++**, **okna**i **konsolę** na liście rozwijanej filtr. Wybierz szablon **aplikacja konsoli** , a następnie wybierz przycisk **dalej**.

1. Nadaj projektowi nazwę i wybierz pozycję **Utwórz**.

1. Usuń `main` funkcję z pliku *. cpp* .

1. Jeśli korzystasz z wersji "Promocja" z pojedynczym nagłówkiem lub biblioteką dynamiczną, przejdź do pozycji [Dodaj dyrektywy include](#add-include-directives). Jeśli używasz statycznej wersji biblioteki, musisz wykonać dodatkową konfigurację:

   a. Aby edytować plik projektu, najpierw go Zwolnij. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Zwolnij projekt**. Następnie kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **edytuj <Name \> . vcxproj**.

   b. Dodaj dwa wiersze do grupy właściwości **Globals** , jak pokazano poniżej:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   c. Zapisz i zamknij plik * \* . vcxproj* , a następnie załaduj ponownie projekt.

   d. Aby otworzyć **strony właściwości**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Właściwości**.

   e. Rozwiń pozycję generowanie kodu **C/C++**  >  **Code Generation**, a następnie wybierz pozycję **Biblioteka środowiska uruchomieniowego**. Wybierz pozycję **/MTD** , aby debugować statyczną bibliotekę wykonawczą lub **/MT** dla biblioteki środowiska uruchomieniowego statycznej wersji.

   f. Rozwiń węzeł System **konsolidatora**  >  **System**. Sprawdź, czy **podsystem** jest ustawiony na **konsolę**.

   przykład Wybierz **przycisk OK** , aby zamknąć strony właściwości.

## <a name="add-include-directives"></a>Dodaj dyrektywy include

1. W pliku test *. cpp* Dodaj wszelkie potrzebne dyrektywy, `#include` Aby zapewnić, że typy i funkcje programu mają być widoczne dla kodu testu. Jeśli używasz oddzielnego projektu testowego, zazwyczaj program znajduje się na poziomie elementu równorzędnego w hierarchii folderów. Jeśli wpiszesz `#include "../"` , zostanie wyświetlone okno IntelliSense, które umożliwi wybranie pełnej ścieżki do pliku nagłówkowego.

   ![Dodaj dyrektywy #include](media/cpp-gtest-includes.png)

   Możesz użyć autonomicznej biblioteki z:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Lub użyj wersji pojedynczego nagłówka z:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Następnie zdefiniuj `BOOST_TEST_MODULE` .

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

## <a name="see-also"></a>Zobacz też

- [Zapisz testy jednostkowe dla C/C++](writing-unit-tests-for-c-cpp.md)
