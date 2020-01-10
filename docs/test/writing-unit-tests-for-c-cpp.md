---
title: Pisanie testów jednostkowych dla języka C/C++
description: Zapisuj C++ testy jednostkowe w programie Visual Studio przy użyciu różnych platform testowych, w tym narzędzia ctest, zwiększanie. testowanie i Google test.
ms.date: 01/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: bcddce98470bc4d1b68eb7c2a6e3936f3abbb930
ms.sourcegitcommit: 789430e18dfe8e5f7db19273e7298af2f078c0dc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75755590"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Pisanie testów jednostkowych dla języka C/C++ w programie Visual Studio

Testy C++ jednostkowe można pisać i uruchamiać przy użyciu okna **Eksplorator testów** . Działa tak samo jak w przypadku innych języków. Aby uzyskać więcej informacji o korzystaniu z **Eksplorator testów**, zobacz [Uruchamianie testów jednostkowych w Eksploratorze testów](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Niektóre funkcje, takie jak Live Unit Testing, kodowanych testów interfejsu użytkownika i funkcji IntelliTest nie są obsługiwane dla języka C++.

Program Visual Studio zawiera następujące struktury testów języka C++ z żadnych dodatkowych plików do pobrania wymagane:

- Microsoft testowania jednostkowego dla języka C++
- Google Test
- Boost.Test
- Narzędzia CTest

Wraz z użyciem zainstalowanych platform można napisać własną kartę testową dla każdej platformy, która ma być używana w programie Visual Studio. Adapter testowy można zintegrować testów jednostkowych za pomocą **Eksploratora testów** okna. Kilka kart sieciowych innych firm są dostępne na [Visual Studio Marketplace](https://marketplace.visualstudio.com). Aby uzyskać więcej informacji, zobacz [instalowanie platform testów jednostkowych innych firm](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 i nowsze (wersje Professional i Enterprise)**

Test jednostkowy C++ projektów pomocy technicznej [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).

**Visual Studio 2017 i nowsze (wszystkie wersje)**

- **Google Test Adapter** jest dołączony jako część domyślnego **programowanie aplikacji klasycznych w języku C++** obciążenia. Ma szablon projektu, który można dodać do rozwiązania. Użyj menu **Dodaj nowy projekt** prawym przyciskiem myszy w węźle rozwiązanie w **Eksplorator rozwiązań** , aby go dodać. Dostępne są również opcje, które można skonfigurować za pomocą **narzędzi** > **Opcje**. Aby uzyskać więcej informacji, zobacz [How to: Use Google test in Visual Studio](how-to-use-google-test-for-cpp.md).

- **Boost.Test** jest dołączony jako część domyślnego **programowanie aplikacji klasycznych w języku C++** obciążenia. Jest ona zintegrowana z **Eksploratorem testów**, ale obecnie nie ma szablonu projektu. Należy ją skonfigurować ręcznie. Aby uzyskać więcej informacji, zobacz [jak: użyć Zwiększ. test w programie Visual Studio](how-to-use-boost-test-for-cpp.md).

- Obsługa **Narzędzia ctest** jest dołączana ze składnikiem  **C++ narzędzia CMAKE** , który jest częścią **tworzenia aplikacji C++ klasycznych** . Jednak narzędzia ctest nie jest jeszcze w pełni zintegrowany z **Eksploratorem testów** . Aby uzyskać więcej informacji, zobacz [How to: use narzędzia ctest in Visual Studio](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 i starsze**

Możesz pobrać adapter Google Test i poprawić rozszerzenia adaptera testowego na Visual Studio Marketplace. Znajdź je na [adapterze testowym w celu zwiększenia wydajności. test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) i [adapter testowy dla Google test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Podstawowy test przepływu pracy

W poniższych sekcjach przedstawiono podstawowe kroki ułatwiające rozpoczęcie pracy z testowania jednostkowego w języku C++. Podstawowa konfiguracja jest podobna do obu struktur firmy Microsoft i Google Test. Boost.Test wymaga ręcznie utworzyć projekt testów.

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Tworzenie projektu testowego w programie Visual Studio 2019

Można definiować i uruchamiać testy w jednym lub wielu projektach testowych. Projekty są tworzone w tym samym rozwiązaniu co kod, który ma zostać przetestowany. Aby dodać nowy projekt testowy do istniejącego rozwiązania, kliknij prawym przyciskiem myszy węzeł rozwiązanie w **Eksplorator rozwiązań**. W menu podręcznym wybierz pozycję **dodaj** > **Nowy projekt**. Ustaw **Język** na C++ i wpisz "test" w polu wyszukiwania. Na poniższej ilustracji przedstawiono projekty testowe, które są dostępne po zainstalowaniu programu **Desktop Development C++**  i **platformy UWP Development** :

![C++Testowanie projektów w programie VIsual Studio 2019](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Tworzenie projektu testowego w programie Visual Studio 2017

Można definiować i uruchamiać testy w jednym lub wielu projektach testowych. Projekty są tworzone w tym samym rozwiązaniu co kod, który ma zostać przetestowany. Aby dodać nowy projekt testowy, kliknij prawym przyciskiem myszy węzeł rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj** > **Nowy projekt**. W lewym okienku wybierz pozycję **test wizualny C++** . Następnie wybierz jeden z typów projektu w środkowym okienku. Na poniższej ilustracji przedstawiono projekty testowe, które są dostępne, kiedy **programowanie aplikacji klasycznych w języku C++** obciążenie jest zainstalowany:

![Projekty testowe w języku C++](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Tworzenie odwołania do innych projektów w rozwiązaniu

Aby włączyć dostęp do funkcji w badanym projekcie, Dodaj odwołanie do projektu w projekcie testowym. Kliknij prawym przyciskiem myszy węzeł projektu testowego w **Eksplorator rozwiązań** dla menu podręcznego. Wybierz pozycję dodaj **odwołanie** > . W oknie dialogowym Dodawanie odwołania wybierz projekty, które chcesz przetestować.

![Dodawanie odwołania](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Połącz z obiektem lub plikami biblioteki

Jeśli kod testu nie eksportuje funkcji, które mają zostać przetestowane, można dodać pliki Output. obj lub. lib do zależności projektu testowego. Aby uzyskać więcej informacji, zobacz [Aby połączyć testy z plikami obiektów lub bibliotek](/visualstudio/test/how-to-use-microsoft-test-framework-for-cpp#object_files).

### <a name="add-include-directives-for-header-files"></a>Dodaj #include dyrektywy dla plików nagłówkowych

Następnie w testu jednostkowego *.cpp* Dodaj `#include` dyrektywy dla wszelkich plików nagłówkowych, które deklarują typy i funkcje, którą chcesz przetestować. Typ `#include "` , a następnie IntelliSense będzie aktywować ułatwiające wybór. Powtórz dla dowolnych dodatkowych nagłówków.

![Dodaj dyrektywy #include](media/cpp-add-includes-test-project.png)

Aby uniknąć konieczności wpisywania pełnej ścieżki w każdej instrukcji include w pliku źródłowym, można dodać wymagane foldery we **właściwościach** > **projektu** > **CC++ /**  > **Ogólne** > **Dodatkowe katalogi dołączane**.

### <a name="write-test-methods"></a>Pisanie metod testowych

> [!NOTE]
> W tej sekcji przedstawiono składnię dla Frameworka testów jednostkowych firmy Microsoft dla języka C/C++. Jest opisane tutaj: [dokumentacja interfejsu API z Microsoft.VisualStudio.TestTools.CppUnitTestFramework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Aby uzyskać dokumentację platformy Google Test, zobacz [podstawy platformy Google Test](https://github.com/google/googletest/blob/master/googletest/docs/primer.md). Dla platformy Boost.Test, zobacz [biblioteki Boost Test: platformy testów jednostkowych](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

Plik *. cpp* w projekcie testowym ma klasę zastępczą i metodę zdefiniowaną dla Ciebie. Przedstawiają przykład sposobu pisania kodu testu. Podpisy używają makr TEST_CLASS i TEST_METHOD, które umożliwiają odnajdywanie metod z okna **Eksplorator testów** .

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

Można dodać *cechy* do metod testowych, aby określić właścicieli testów, priorytet i inne informacje. Następnie można te wartości sortowanie i grupowanie testów w **Eksplorator testów**. Aby uzyskać więcej informacji, zobacz [Uruchamianie testów jednostkowych w Eksploratorze testów](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Uruchom testy

1. Na **testu** menu, wybierz **Windows** > **Eksplorator testów**. Poniższa ilustracja przedstawia projekt testowy, w których testy nie zostały jeszcze uruchomione.

   ![Eksplorator testów przed uruchomieniem testów](media/cpp-test-explorer.png)

   > [!NOTE]
   > Integracja narzędzia CTest z **Eksplorator testów** nie jest jeszcze dostępna. Uruchom testy narzędzia CTest z menu głównego narzędzia CMake.

1. Jeśli nie wszystkie testy są widoczne w oknie, Skompiluj projekt testowy, klikając prawym przyciskiem myszy jego węzeł w **Eksplorator rozwiązań** i wybierając opcję **Kompiluj** lub **Kompiluj ponownie**.

1. W **Eksplorator testów**, wybierz **Uruchom wszystkie**, lub wybierz określonych testów, które chcesz uruchomić. Kliknij prawym przyciskiem myszy na test dla innych opcji, w tym uruchamianie w trybie debugowania, z punktami przerwania jest włączony. Po uruchomieniu wszystkich testów, okno pokazuje, które testów zakończonych powodzeniem i te, które nie powiodła się:

![Eksplorator testów, po uruchomieniu testów](media/cpp-test-explorer-passed.png)

Dla testów zakończonych niepowodzeniem komunikat oferuje szczegółowe informacje, które pomagają przyczynę. Kliknij prawym przyciskiem myszy Test zakończony niepowodzeniem dla menu podręcznego. Wybierz **Debuguj wybrane testy** , aby przejść przez funkcję, w której wystąpił błąd.

Aby uzyskać więcej informacji o korzystaniu z **Eksplorator testów**, zobacz [Uruchamianie testów jednostkowych w Eksploratorze testów](run-unit-tests-with-test-explorer.md).

Aby uzyskać więcej informacji dotyczących testów jednostkowych, zobacz temat podstawowe informacje o [teście jednostkowym](unit-test-basics.md)

## <a name="use-codelens"></a>Używanie funkcji CodeLens

**Visual Studio 2017 i nowsze (wersje Professional i Enterprise)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) umożliwia szybkie sprawdzenie stanu testu jednostkowego bez opuszczania edytora kodu.

Można zainicjować wskaźników CodeLens dla projektu testu jednostkowego języka C++ w jeden z następujących sposobów:

- Edytowanie i tworzenie projektu testu lub rozwiązania.
- Ponownie skompiluj swój projekt lub rozwiązanie.
- Uruchom testy z okna **Eksplorator testów** .

Po jego zainicjowaniu można zobaczyć ikony stanu testu powyżej poszczególnych testów jednostkowych.

![Ikony CodeLens języka C++](media/cpp-test-codelens-icons.png)

Kliknij ikonę, aby uzyskać więcej informacji, lub do uruchamiania lub debugowania test jednostkowy:

![C++ CodeLens, uruchamianie i debugowanie](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Zobacz także

- [Kod testu jednostkowego](unit-test-your-code.md)
