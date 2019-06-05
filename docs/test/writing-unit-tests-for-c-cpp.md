---
title: Pisanie testów jednostkowych dla języka C/C++
description: Zapis C++ testów jednostkowych w programie Visual Studio przy użyciu różnych środowisk testowych, w tym narzędzia CTest, Boost.Test i platformy Google Test.
ms.date: 05/06/2019
ms.topic: conceptual
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: f27e2585d082f61021fbc736b394612095f56684
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66715248"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Pisanie testów jednostkowych dla języka C/C++ w programie Visual Studio

Można napisać i Uruchamianie testów jednostkowych C++ za pomocą **Eksplorator testów** okna, podobnie jak w przypadku innych języków. Aby uzyskać więcej informacji o korzystaniu z **Eksplorator testów**, zobacz [Uruchamianie testów jednostkowych w Eksploratorze testów](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Niektóre funkcje, takie jak Live Unit Testing, kodowanych testów interfejsu użytkownika i funkcji IntelliTest nie są obsługiwane dla języka C++.

Program Visual Studio zawiera następujące struktury testów języka C++ z żadnych dodatkowych plików do pobrania wymagane:

- Microsoft testowania jednostkowego dla języka C++
- Google Test
- Boost.Test
- Narzędzia CTest

Oprócz zainstalowanych platform można napisać własne rozszerzenia test adapter for niezależnie od framework, które chcesz użyć w programie Visual Studio. Adapter testowy można zintegrować testów jednostkowych za pomocą **Eksploratora testów** okna. Kilka kart sieciowych innych firm są dostępne na [Visual Studio Marketplace](https://marketplace.visualstudio.com). Aby uzyskać więcej informacji, zobacz [instalowanie platform testów jednostkowych innych firm](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 i nowsze (Professional i Enterprise)**

Test jednostkowy C++ projektów pomocy technicznej [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).

**Visual Studio 2017 i nowsze (wszystkie wersje)**

- **Google Test Adapter** jest dołączony jako część domyślnego **programowanie aplikacji klasycznych w języku C++** obciążenia. Ma ona szablon projektu, można dodać do rozwiązania za pośrednictwem **Dodaj nowy projekt** menu kliknij prawym przyciskiem myszy węzeł rozwiązania w **Eksploratora rozwiązań**i opcje, które można skonfigurować za pomocą **narzędzia**  >  **Opcje**. Aby uzyskać więcej informacji, zobacz [porady: Użyj platformy Google Test w programie Visual Studio](how-to-use-google-test-for-cpp.md).

- **Boost.Test** jest dołączony jako część domyślnego **programowanie aplikacji klasycznych w języku C++** obciążenia. Jest zintegrowana z usługą **Eksplorator testów** , ale obecnie nie ma szablonu projektu, w związku z tym musi być ręcznie skonfigurowany. Aby uzyskać więcej informacji, zobacz [porady: Używanie narzędzia Boost.Test w programie Visual Studio](how-to-use-boost-test-for-cpp.md).

- **Narzędzia CTest** pomoc techniczna jest uwzględniona w [narzędzia CMake dla programu Visual Studio](/cpp/build/cmake-tools-for-visual-cpp) składnika, który jest częścią programu **programowanie aplikacji klasycznych w języku C++** obciążenia. Jednak narzędzia CTest nie jest jeszcze w pełni zintegrowana z **Eksplorator testów**. Aby uzyskać więcej informacji, zobacz [porady: Używanie narzędzia CTest w programie Visual Studio](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 i starsze**

Możesz pobrać karty platformy Google Test i Boost.Test karty rozszerzeń w Visual Studio Marketplace na [rozszerzenia Test adapter for Boost.Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) i [rozszerzenia Test adapter for Google Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Podstawowy test przepływu pracy

W poniższych sekcjach przedstawiono podstawowe kroki ułatwiające rozpoczęcie pracy z testowania jednostkowego w języku C++. Podstawowa konfiguracja jest bardzo podobne do struktury firmy Microsoft i platformy Google Test. Boost.Test wymaga ręcznie utworzyć projekt testów.

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Tworzenie projektu testu w programie Visual Studio 2019 r.

Zdefiniować i uruchomić testy wewnątrz projekty testowe, które znajdują się w tym samym rozwiązaniu, jako kod, który ma zostać przetestowana. Aby dodać nowy projekt testowy do istniejącego rozwiązania, kliknij prawym przyciskiem myszy węzeł rozwiązania w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** > **nowy projekt**. Ustaw **języka** do C++ i wpisz "test", w polu wyszukiwania. Na poniższej ilustracji przedstawiono projekty testowe, które są dostępne, kiedy **programowanie aplikacji klasycznych przy użyciu C++**  i **programowania platformy uniwersalnej systemu Windows** obciążenia są zainstalowane:

![C++Projekty testowe w programie VIsual Studio 2019 r.](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Tworzenie projektu testu w programie Visual Studio 2017

Zdefiniować i uruchomić testy wewnątrz projekty testowe, które znajdują się w tym samym rozwiązaniu, jako kod, który ma zostać przetestowana. Aby dodać nowy projekt testowy do istniejącego rozwiązania, kliknij prawym przyciskiem myszy węzeł rozwiązania w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** > **nowy projekt**. Następnie w okienku po lewej stronie wybierz **Test programu Visual C++** i wybierz jeden z typów projektów w środkowym okienku. Na poniższej ilustracji przedstawiono projekty testowe, które są dostępne, kiedy **programowanie aplikacji klasycznych w języku C++** obciążenie jest zainstalowany:

![Projekty testowe w języku C++](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Tworzenie odwołania do innych projektów w rozwiązaniu

Aby włączyć swój kod testu, aby uzyskać dostęp do funkcji w projekcie, który ma zostać przetestowana, należy dodać odwołanie do projektu w projekcie testu. Kliknij prawym przyciskiem myszy węzeł projektu testu w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** > **odwołania**. Następnie w oknie dialogowym Wybierz projekty, które mają zostać przetestowane.

![Dodawanie odwołania](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Połącz z plikami obiektu lub biblioteki

Jeśli kod testu nie eksportuje funkcji, które chcesz przetestować, możesz dodać dane wyjściowe pliki obj i lib, do zależności testowanego projektu testowego. Zobacz [połączyć testy z plikami obiektu lub biblioteki](https://docs.microsoft.com/visualstudio/test/unit-testing-existing-cpp-applications-with-test-explorer?view=vs-2015#objectRef).

### <a name="add-include-directives-for-header-files"></a>Dodaj #include dyrektywy dla plików nagłówkowych

Następnie w testu jednostkowego *.cpp* Dodaj `#include` dyrektywy dla wszelkich plików nagłówkowych, które deklarują typy i funkcje, którą chcesz przetestować. Typ `#include "` , a następnie IntelliSense będzie aktywować ułatwiające wybór. Powtórz dla dowolnych dodatkowych nagłówków.

![Dodaj dyrektywy #include](media/cpp-add-includes-test-project.png)

### <a name="write-test-methods"></a>Pisanie metod testowych

> [!NOTE]
> W tej sekcji przedstawiono składnię dla Frameworka testów jednostkowych firmy Microsoft dla języka C/C++. Jest opisane tutaj: [Dokumentacja interfejsu API z Microsoft.VisualStudio.TestTools.CppUnitTestFramework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Aby uzyskać dokumentację platformy Google Test, zobacz [podstawy platformy Google Test](https://github.com/google/googletest/blob/master/googletest/docs/primer.md). Dla platformy Boost.Test, zobacz [biblioteki Boost Test: Framework testów jednostkowych](http://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

*.Cpp* plik w projekcie testu ma klasy wycinka i metody zdefiniowane jako przykład sposobu pisania testować kod. Pamiętaj, że sygnatury użyć makra TEST_CLASS i TEST_METHOD, które metody stał się wykrywalny z **Eksplorator testów** okna.

![Dodaj dyrektywy #include](media/cpp-write-test-methods.png)

TEST_CLASS i TEST_METHOD są częścią [natywne środowisko testów Microsoft](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). **Eksplorator testów** wykrywa metody testowe w innych obsługiwanych platform w podobny sposób.

TEST_METHOD zwraca wartość void. Do uzyskania wyniku testu, użyj metod statycznych w `Assert` klasy do przetestowania rzeczywiste wyniki niż oczekiwana. W poniższym przykładzie przyjęto założenie, `MyClass` zawiera konstruktora przyjmującego `std::string`. Można przetestować, Konstruktor inicjuje klasy zgodnie z oczekiwaniami w następujący sposób:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

W poprzednim przykładzie, wynik `Assert::AreEqual` wywołanie określa, czy test przekazuje lub nie powiedzie się. Klasa Asercja zawiera wiele innych metod do porównywania, oczekiwany, a rzeczywiste wyniki.

Możesz dodać *cech* do testowania metod do określenia testów właścicieli, priorytetu i innych informacji. Następnie można te wartości sortowanie i grupowanie testów w **Eksplorator testów**. Aby uzyskać więcej informacji, zobacz [Uruchamianie testów jednostkowych w Eksploratorze testów](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Uruchom testy

1. Na **testu** menu, wybierz **Windows** > **Eksplorator testów**. Poniższa ilustracja przedstawia projekt testowy, w których testy nie zostały jeszcze uruchomione.

   ![Eksplorator testów przed uruchomieniem testów](media/cpp-test-explorer.png)

   > [!NOTE]
   > Integracja narzędzia CTest z **Eksplorator testów** nie jest jeszcze dostępna. Uruchom testy narzędzia CTest z menu głównego narzędzia CMake.

1. Jeśli wszystkie testy nie są widoczne w oknie, tworzenia projektu badania, klikając prawym przyciskiem myszy jego węzła w **Eksploratora rozwiązań** i wybierając pozycję **kompilacji** lub **odbudować**.

1. W **Eksplorator testów**, wybierz **Uruchom wszystkie**, lub wybierz określonych testów, które chcesz uruchomić. Kliknij prawym przyciskiem myszy na test dla innych opcji, w tym uruchamianie w trybie debugowania, z punktami przerwania jest włączony. Po uruchomieniu wszystkich testów, okno pokazuje, które testów zakończonych powodzeniem i te, które nie powiodła się:

![Eksplorator testów, po uruchomieniu testów](media/cpp-test-explorer-passed.png)

Dla testów zakończonych niepowodzeniem komunikat oferuje szczegółowe informacje, które pomagają przyczynę. Możesz kliknąć prawym przyciskiem myszy na test niepowodzeniem i wybrać **Debuguj wybrane testy** przechodzić przez funkcję, w którym wystąpił błąd.

Aby uzyskać więcej informacji o korzystaniu z **Eksplorator testów**, zobacz [Uruchamianie testów jednostkowych w Eksploratorze testów](run-unit-tests-with-test-explorer.md).

Aby uzyskać najlepsze rozwiązania związane z testów jednostkowych, zobacz [podstawy testów jednostkowych](unit-test-basics.md)

## <a name="use-codelens"></a>Używanie funkcji CodeLens

**Visual Studio 2017 i nowsze (wersje Professional i Enterprise)**

[Funkcja CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) pozwala szybko sprawdzić stan jednostki testowania bez opuszczania edytora kodu. Można zainicjować wskaźników CodeLens dla projektu testu jednostkowego języka C++ w jeden z następujących sposobów:

- Edytowanie i tworzenie projektu testu lub rozwiązania.
- Ponownie skompiluj swój projekt lub rozwiązanie.
- Uruchom testy z **Eksploratora testów** okna.

Po **CodeLens** jest inicjowany, możesz zobaczyć testowanie ikony stanu powyżej każdy test jednostkowy.

![Ikony CodeLens języka C++](media/cpp-test-codelens-icons.png)

Kliknij ikonę, aby uzyskać więcej informacji, lub do uruchamiania lub debugowania test jednostkowy:

![C++ CodeLens, uruchamianie i debugowanie](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Zobacz także

- [Kod testu jednostkowego](unit-test-your-code.md)
