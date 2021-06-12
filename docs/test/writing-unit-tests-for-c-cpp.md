---
title: Pisanie testów jednostkowych dla języka C/C++
description: Pisanie testów jednostkowych języka C++ w Visual Studio różnych platform testowych, takich jak CTest, Boost.Test i Google Test.
ms.date: 04/01/2021
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 877c9163d05f458ce45a46d6b3e6d14e354df591
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042890"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Pisanie testów jednostkowych dla języka C/C++ w Visual Studio

Testy jednostkowe języka C++ można pisać i uruchamiać przy użyciu okna **Eksplorator testów.** Działa ona tak samo jak w przypadku innych języków. Aby uzyskać więcej informacji na temat korzystania z **Eksploratora testów,** zobacz [Run unit tests with Test Explorer (Uruchamianie testów jednostkowych za pomocą Eksploratora testów).](run-unit-tests-with-test-explorer.md)

> [!NOTE]
> Niektóre funkcje, takie jak Live Unit Testing, kodowane testy interfejsu użytkownika i IntelliTest, nie są obsługiwane w języku C++.

Visual Studio te struktury testowe języka C++ bez dodatkowych plików do pobrania:

- Microsoft Unit Testing Framework for C++
- Google Test
- Boost.Test
- CTest

Oprócz korzystania z zainstalowanych platform można napisać własny adapter testowy dla dowolnej struktury, która ma być Visual Studio. Adapter testowy może integrować testy jednostkowe z **oknem Eksplorator testów.** Na Visual Studio Marketplace dostępnych jest [kilka kart innych Visual Studio Marketplace](https://marketplace.visualstudio.com). Aby uzyskać więcej informacji, zobacz Instalowanie platform testów [jednostkowych innych firm.](install-third-party-unit-test-frameworks.md)

**Visual Studio 2017 i nowsze (Professional i Enterprise)**

Projekty testów jednostkowych języka C++ obsługują [funkcje CodeLens.](../ide/find-code-changes-and-other-history-with-codelens.md)

**Visual Studio 2017 i nowsze (wszystkie wersje)**

- **Google Test adapter jest** dołączony jako domyślny składnik pakietu roboczego Tworzenie aplikacji klasycznych **w języku C++.** Zawiera szablon projektu, który można dodać do rozwiązania. Użyj menu **dodaj nowy projekt** prawym przyciskiem myszy w węźle rozwiązania w **Eksplorator rozwiązań,** aby go dodać. Dostępne są również opcje, które można skonfigurować za pomocą **opcji**  >  **narzędzia**. Aby uzyskać więcej informacji, [zobacz How to: Use Google Test in Visual Studio](how-to-use-google-test-for-cpp.md)(Jak używać Google Test w Visual Studio ).

- **Zestaw Boost.Test** jest dołączony jako domyślny składnik programowania aplikacji klasycznych **w obciążeniu języka C++.** Jest on zintegrowany z **Eksploratorem testów,** ale obecnie nie ma szablonu projektu. Musi być ręcznie skonfigurowany. Aby uzyskać więcej informacji, [zobacz How to: Use Boost.Test in Visual Studio (Jak używać metody Boost.Test w Visual Studio).](how-to-use-boost-test-for-cpp.md)

- **Obsługa CTest** jest dołączona do składnika narzędzi **CMake języka C++,** który jest częścią programowania aplikacji klasycznych **przy użyciu obciążenia C++.** Aby uzyskać więcej informacji, [zobacz How to: Use CTest in Visual Studio](how-to-use-ctest-for-cpp.md)( Jak używać CTest w Visual Studio .

**Visual Studio 2015 r. i starsze**

Możesz pobrać adapter Google Test i rozszerzenia Boost.Test Adapter na Visual Studio Marketplace. Można je znaleźć na [stronie Test adapter for Boost.Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) and Test adapter for [Google Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Podstawowy przepływ pracy testu

W poniższych sekcjach przedstawiono podstawowe kroki, które należy wykonać, aby rozpocząć pracę z testowaniem jednostkowym języka C++. Podstawowa konfiguracja jest podobna zarówno w przypadku platform firmy Microsoft, jak Google Test platformy. Projekt Boost.Test wymaga ręcznego utworzenia projektu testowego.

::: moniker range=">=vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Tworzenie projektu testowego w Visual Studio 2019 r.

Testy można definiować i uruchamiać wewnątrz jednego lub większej liczby projektów testowych. Projekty tworzy się w tym samym rozwiązaniu co kod, który chcesz przetestować. Aby dodać nowy projekt testowy do istniejącego rozwiązania, kliknij prawym przyciskiem myszy węzeł Rozwiązanie w **Eksplorator rozwiązań**. W menu podręcznym wybierz pozycję **Dodaj**  >  **nowy projekt.** Ustaw **pole Language** na C++ i wpisz "test" w polu wyszukiwania. Na poniższej ilustracji przedstawiono projekty testowe, które są dostępne po zainstalowaniu pakietu roboczego Tworzenie aplikacji klasycznych w języku **C++** i programowania dla platformy **uniwersalnej** systemu Windows:

![Projekty testowe języka C++ w programie VIsual Studio 2019](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Tworzenie projektu testowego w programie Visual Studio 2017

Testy można definiować i uruchamiać wewnątrz jednego lub większej liczby projektów testowych. Projekty tworzy się w tym samym rozwiązaniu co kod, który chcesz przetestować. Aby dodać nowy projekt testowy, kliknij prawym przyciskiem myszy węzeł Rozwiązanie w Eksplorator rozwiązań **wybierz** **polecenie Dodaj**  >  **nowy projekt.** W okienku po lewej stronie wybierz **pozycję Visual C++ Test.** Następnie wybierz jeden z typów projektów w środkowym okienku. Na poniższej ilustracji przedstawiono projekty testowe, które są dostępne po zainstalowaniu pakietu roboczego Tworzenie aplikacji klasycznych w języku **C++:**

![Projekty testowe języka C++](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Tworzenie odwołań do innych projektów w rozwiązaniu

Aby włączyć dostęp do funkcji w testowym projekcie, dodaj odwołanie do projektu w projekcie testowym. Kliknij prawym przyciskiem myszy węzeł projektu testowego w **Eksplorator rozwiązań** menu podręcznego. Wybierz **pozycję Dodaj**  >  **odwołanie.** W oknie dialogowym Dodawanie odwołania wybierz projekt,który chcesz przetestować.

![Dodawanie odwołania](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Link do plików obiektu lub biblioteki

Jeśli kod testowy nie eksportuje funkcji, które chcesz przetestować, możesz dodać pliki wyjściowe .obj lub .lib do zależności projektu testowego. Aby uzyskać więcej informacji, zobacz [Aby połączyć testy z plikami obiektu lub biblioteki](how-to-use-microsoft-test-framework-for-cpp.md#object_files).

### <a name="add-include-directives-for-header-files"></a>Dodawanie #include dla plików nagłówkowych

Następnie w pliku *cpp* testu jednostkowego dodaj dyrektywę dla wszystkich plików nagłówkowych, które deklarują typy i funkcje, `#include` które chcesz przetestować. Wpisz `#include "` polecenie , a następnie funkcja IntelliSense zostanie aktywowana, aby ułatwić wybór. Powtórz te czynności, aby uzyskać dodatkowe nagłówki.

![Zrzut ekranu przedstawiający Eksplorator rozwiązań dodano #include, a funkcja IntelliSense wyróżniła plik nagłówkowy do uwzględnienia.](media/cpp-add-includes-test-project.png)

Aby uniknąć konieczności wpisywania pełnej ścieżki w każdej instrukcji include w pliku źródłowym, możesz dodać wymagane foldery we właściwościach projektu  >    >  **C/C++** Ogólne dodatkowe  >    >  **katalogi dołączania.**

### <a name="write-test-methods"></a>Pisanie metod testowych

> [!NOTE]
> W tej sekcji przedstawiono składnię struktury testowania jednostkowego firmy Microsoft dla języka C/C++. Jest on udokumentowany tutaj: [Dokumentacja interfejsu API Microsoft.VisualStudio.TestTools.CppUnitTestFramework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Aby uzyskać Google Test dokumentacji, zobacz [Google Test primer](https://github.com/google/googletest/blob/master/docs/primer.md)( Aby uzyskać informacje na temat biblioteki Boost.Test, zobacz Boost Test library: The unit test framework (Biblioteka [testów jednostkowych: ).](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html)

Plik *cpp w* projekcie testowym ma zdefiniowaną klasę wycinki i metodę . Pokazują one przykład pisania kodu testowego. Podpisy używają TEST_CLASS i TEST_METHOD, dzięki którym metody są wykrywalne w **oknie Eksplorator testów.**

![Zrzut ekranu okna Eksplorator testów przedstawiający plik kodu unittest1.cpp zawierający klasę wycinki i metodę przy użyciu TEST_CLASS i TEST_METHOD kodu.](media/cpp-write-test-methods.png)

TEST_CLASS i TEST_METHOD są częścią programu [Microsoft Native Test Framework.](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md) **Eksplorator testów** odnajduje metody testowe w innych obsługiwanych platformach w podobny sposób.

Wartość TEST_METHOD zwraca wartość void. Aby uzyskać wynik testu, użyj metod statycznych w klasie , aby `Assert` przetestować rzeczywiste wyniki względem oczekiwanych wyników. W poniższym przykładzie przyjmijmy, `MyClass` że ma konstruktor, który przyjmuje `std::string` . Możemy przetestować, czy konstruktor inicjuje klasę zgodnie z oczekiwaniami w następujący sposób:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

W poprzednim przykładzie wynik wywołania określa, czy test zakończył się `Assert::AreEqual` pomyślnie, czy nie. Klasa Assert zawiera wiele innych metod porównywania oczekiwanych i rzeczywistych wyników.

Możesz dodać cechy *do metod* testowych, aby określić właścicieli testów, priorytet i inne informacje. Następnie można użyć tych wartości do sortowania i grupowania testów w **Eksploratorze testów.** Aby uzyskać więcej informacji, zobacz [Run unit tests with Test Explorer (Uruchamianie testów jednostkowych za pomocą Eksploratora testów).](run-unit-tests-with-test-explorer.md)

### <a name="run-the-tests"></a>Uruchamianie testów

1. W menu **Test** wybierz pozycję **Eksplorator testów**  >  **systemu** Windows. Na poniższej ilustracji przedstawiono projekt testowy, którego testy nie zostały jeszcze uruchomione.

   ![Eksplorator testów przed uruchomieniem testów](media/cpp-test-explorer.png)

   > [!NOTE]
   > Integracja testów CTest z **Eksploratorem testów** nie jest jeszcze dostępna. Uruchom testy CTest z menu głównego narzędzia CMake.

1. Jeśli nie wszystkie testy są widoczne w oknie, skonstruuj projekt testowy, klikając prawym przyciskiem myszy jego węzeł w oknie Eksplorator rozwiązań i wybierając polecenie Build or Rebuild **(Skompilowanie** **lub Skompilowanie).** 

1. W **Eksploratorze testów** wybierz **pozycję Uruchom wszystko** lub wybierz konkretne testy, które chcesz uruchomić. Kliknij prawym przyciskiem myszy test dla innych opcji, w tym uruchamianie go w trybie debugowania z włączonymi punktami przerwania. Po uruchomieniu wszystkich testów w oknie widać testy, które zakończyły się pomyślnie, a które zakończyły się niepowodzeniem:

![Eksplorator testów po uruchomieniu testów](media/cpp-test-explorer-passed.png)

W przypadku testów nieudanych komunikat zawiera szczegółowe informacje, które pomagają zdiagnozować przyczynę. Kliknij prawym przyciskiem myszy test po awarii dla menu podręcznego. Wybierz **pozycję Debuguj wybrane testy,** aby przejść przez funkcję, w której wystąpił błąd.

Aby uzyskać więcej informacji na temat korzystania **z Eksploratora testów,** zobacz [Run unit tests with Test Explorer (Uruchamianie testów jednostkowych za pomocą Eksploratora testów).](run-unit-tests-with-test-explorer.md)

Aby uzyskać więcej informacji dotyczących testowania jednostkowego, zobacz [Podstawowe informacje o testach jednostkowych](unit-test-basics.md)

## <a name="use-codelens"></a>Korzystanie z funkcji CodeLens

**Visual Studio 2017 i nowsze (wersje Professional i Enterprise)**

[Funkcja CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) umożliwia szybkie wyświetlanie stanu testu jednostkowego bez opuszczania edytora kodu.

Funkcje CodeLens dla projektu testu jednostkowego języka C++ można zainicjować na jeden z tych sposobów:

- Edytuj i skompilowaj projekt testowy lub rozwiązanie.
- Ponownie skompilować projekt lub rozwiązanie.
- Uruchom testy w **oknie Eksplorator testów.**

Po zainicjowaniu ikony stanu testu są widoczne nad każdym testem jednostkowym.

![Ikony CodeLens języka C++](media/cpp-test-codelens-icons.png)

Kliknij ikonę, aby uzyskać więcej informacji, lub aby uruchomić lub debugować test jednostkowy:

![Uruchamianie i debugowanie codeLens języka C++](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Zobacz też

- [Testowanie jednostkowe kodu](unit-test-your-code.md)
