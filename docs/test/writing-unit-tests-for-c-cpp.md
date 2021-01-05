---
title: Zapisz testy jednostkowe dla C/C++
description: Napisz testy jednostkowe języka C++ w programie Visual Studio przy użyciu różnych platform testowych, takich jak narzędzia ctest, zwiększanie. testowanie i Google Test.
ms.date: 02/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: cf6287ebdb4c2df6145a0e60e22ac1197a517fde
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729369"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Zapisz testy jednostkowe dla C/C++ w programie Visual Studio

Testy jednostkowe języka C++ można pisać i uruchamiać przy użyciu okna **Eksplorator testów** . Działa tak samo jak w przypadku innych języków. Aby uzyskać więcej informacji o korzystaniu z programu **Test Explorer**, zobacz [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Niektóre funkcje, takie jak Live Unit Testing, kodowane testy interfejsu użytkownika i IntelliTest nie są obsługiwane w języku C++.

Program Visual Studio zawiera te platformy testów C++ bez dodatkowych wymaganych plików do pobrania:

- Struktura testów jednostkowych firmy Microsoft dla języka C++
- Google Test
- Zwiększ. test
- Narzędzia ctest

Wraz z użyciem zainstalowanych platform można napisać własną kartę testową dla każdej platformy, która ma być używana w programie Visual Studio. Adapter testowy może zintegrować testy jednostkowe z oknem **Eksplorator testów** . Na [Visual Studio Marketplace](https://marketplace.visualstudio.com)są dostępne kilka kart innych firm. Aby uzyskać więcej informacji, zobacz [Instalowanie platform testów jednostkowych](install-third-party-unit-test-frameworks.md)innych firm.

**Visual Studio 2017 i nowsze (wersje Professional i Enterprise)**

Projekty testów jednostkowych języka C++ obsługują [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).

**Visual Studio 2017 i nowsze (wszystkie wersje)**

- **Karta Google test** jest dołączana jako domyślny składnik **tworzenia aplikacji klasycznych w ramach obciążeń języka C++** . Ma szablon projektu, który można dodać do rozwiązania. Użyj menu **Dodaj nowy projekt** prawym przyciskiem myszy w węźle rozwiązanie w **Eksplorator rozwiązań** , aby go dodać. Dostępne są również opcje, które można skonfigurować za pomocą  >  **opcji** narzędzia. Aby uzyskać więcej informacji, zobacz [How to: Use Google test in Visual Studio](how-to-use-google-test-for-cpp.md).

- **Zwiększenie wydajności. test** jest uwzględniany jako domyślny składnik **tworzenia aplikacji klasycznych w ramach obciążeń języka C++** . Jest ona zintegrowana z **Eksploratorem testów**, ale obecnie nie ma szablonu projektu. Należy ją skonfigurować ręcznie. Aby uzyskać więcej informacji, zobacz [jak: użyć Zwiększ. test w programie Visual Studio](how-to-use-boost-test-for-cpp.md).

- Obsługa **Narzędzia ctest** jest dostępna w składniku **c++ CMAKE Tools** , który jest częścią **tworzenia aplikacji klasycznych przy użyciu obciążenia c++** . Aby uzyskać więcej informacji, zobacz [How to: use narzędzia ctest in Visual Studio](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 i starsze**

Możesz pobrać adapter Google Test i poprawić rozszerzenia adaptera testowego na Visual Studio Marketplace. Znajdź je na [adapterze testowym w celu zwiększenia wydajności. test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) i [adapter testowy dla Google test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Podstawowy przepływ pracy testu

W poniższych sekcjach przedstawiono podstawowe kroki umożliwiające rozpoczęcie pracy z testowaniem jednostkowym języka C++. Podstawowa konfiguracja jest podobna do obu struktur firmy Microsoft i Google Test. Podwyższanie poziomu. test wymaga ręcznego utworzenia projektu testowego.

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Tworzenie projektu testowego w programie Visual Studio 2019

Można definiować i uruchamiać testy w jednym lub wielu projektach testowych. Projekty są tworzone w tym samym rozwiązaniu co kod, który ma zostać przetestowany. Aby dodać nowy projekt testowy do istniejącego rozwiązania, kliknij prawym przyciskiem myszy węzeł rozwiązanie w **Eksplorator rozwiązań**. W menu podręcznym wybierz pozycję **Dodaj**  >  **Nowy projekt**. Ustaw **Język** na C++ i wpisz "test" w polu wyszukiwania. Na poniższej ilustracji przedstawiono projekty testowe, które są dostępne po zainstalowaniu **środowiska tworzenia aplikacji klasycznych w języku C++** i **platformy UWP** :

![Projekty testowe języka C++ w programie VIsual Studio 2019](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Tworzenie projektu testowego w programie Visual Studio 2017

Można definiować i uruchamiać testy w jednym lub wielu projektach testowych. Projekty są tworzone w tym samym rozwiązaniu co kod, który ma zostać przetestowany. Aby dodać nowy projekt testowy, kliknij prawym przyciskiem myszy węzeł rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **Nowy projekt**. W lewym okienku wybierz **Visual C++ test**. Następnie wybierz jeden z typów projektu w środkowym okienku. Na poniższej ilustracji przedstawiono projekty testowe, które są dostępne po zainstalowaniu obciążeń **klasycznych w języku C++** :

![Projekty testowe języka C++](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Tworzenie odwołań do innych projektów w rozwiązaniu

Aby włączyć dostęp do funkcji w badanym projekcie, Dodaj odwołanie do projektu w projekcie testowym. Kliknij prawym przyciskiem myszy węzeł projektu testowego w **Eksplorator rozwiązań** dla menu podręcznego. Wybierz pozycję **Dodaj**  >  **odwołanie**. W oknie dialogowym Dodawanie odwołania wybierz projekty, które chcesz przetestować.

![Dodawanie odwołania](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Połącz z obiektem lub plikami biblioteki

Jeśli kod testu nie eksportuje funkcji, które mają zostać przetestowane, można dodać pliki Output. obj lub. lib do zależności projektu testowego. Aby uzyskać więcej informacji, zobacz [Aby połączyć testy z plikami obiektów lub bibliotek](how-to-use-microsoft-test-framework-for-cpp.md#object_files).

### <a name="add-include-directives-for-header-files"></a>Dodaj dyrektywy #include dla plików nagłówkowych

Następnie w pliku *. cpp* testu jednostkowego Dodaj `#include` dyrektywę dla wszystkich plików nagłówkowych, które deklarują typy i funkcje, które chcesz przetestować. Typ `#include "` , a następnie technologia IntelliSense zostanie aktywowana, aby ułatwić wybór. Powtórz te czynności dla wszystkich dodatkowych nagłówków.

![Zrzut ekranu przedstawiający Eksplorator rozwiązań, w którym jest wyświetlana Dyrektywa #include dodawana przy użyciu funkcji IntelliSense wyróżniania pliku nagłówkowego do uwzględnienia.](media/cpp-add-includes-test-project.png)

Aby uniknąć konieczności wpisywania pełnej ścieżki w każdej instrukcji include w pliku źródłowym, można dodać wymagane foldery we   >  **właściwościach** projektu  >    >  **Ogólne**  >  **Dodatkowe katalogi dołączania**.

### <a name="write-test-methods"></a>Pisanie metod testowych

> [!NOTE]
> W tej sekcji przedstawiono składnię struktury testów jednostkowych firmy Microsoft dla języka C/C++. Jest on udokumentowany w tym miejscu: [Microsoft. VisualStudio. TestTools. CPPUNITTESTFRAMEWORK API Reference](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Aby uzyskać dokumentację Google Test, zobacz [Google test](https://github.com/google/googletest/blob/master/googletest/docs/primer.md). Aby zwiększyć. test, zobacz [biblioteka Boost test: Struktura testów jednostkowych](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

Plik *. cpp* w projekcie testowym ma klasę zastępczą i metodę zdefiniowaną dla Ciebie. Przedstawiają przykład sposobu pisania kodu testu. Podpisy używają makr TEST_CLASS i TEST_METHOD, które umożliwiają odnajdywanie metod z okna **Eksplorator testów** .

![Zrzut ekranu okna Eksplorator testów, który pokazuje plik kodu UnitTest1. cpp zawierający klasę zastępczą i metodę za pomocą makr TEST_CLASS i TEST_METHOD.](media/cpp-write-test-methods.png)

TEST_CLASS i TEST_METHOD są częścią [natywnego środowiska testowego firmy Microsoft](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). **Eksplorator testów** odnajduje metody testowe w innych obsługiwanych platformach w podobny sposób.

TEST_METHOD zwraca wartość void. Aby utworzyć wynik testu, należy użyć metod statycznych w klasie w `Assert` celu przetestowania rzeczywistych wyników względem oczekiwań. W poniższym przykładzie Załóżmy, `MyClass` że ma konstruktora, który przyjmuje `std::string` . Możemy sprawdzić, czy Konstruktor inicjuje klasę zgodnie z oczekiwaniami, tak jak to zrobić:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

W poprzednim przykładzie wynik `Assert::AreEqual` wywołania decyduje o tym, czy test zakończy się powodzeniem, czy nie. Klasa Assert zawiera wiele innych metod porównujących wyniki oczekiwane i rzeczywiste.

Można dodać *cechy* do metod testowych, aby określić właścicieli testów, priorytet i inne informacje. Następnie można użyć tych wartości do sortowania i grupowania testów w **Eksploratorze testów**. Aby uzyskać więcej informacji, zobacz [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Uruchamianie testów

1. W menu **test** wybierz polecenie   >  **Eksplorator testów** systemu Windows. Na poniższej ilustracji przedstawiono projekt testowy, którego testy nie zostały jeszcze uruchomione.

   ![Eksplorator testów przed uruchomieniem testów](media/cpp-test-explorer.png)

   > [!NOTE]
   > Integracja narzędzia ctest z **Eksploratorem testów** nie jest jeszcze dostępna. Uruchom testy narzędzia ctest z głównego menu CMake.

1. Jeśli nie wszystkie testy są widoczne w oknie, Skompiluj projekt testowy, klikając prawym przyciskiem myszy jego węzeł w **Eksplorator rozwiązań** i wybierając opcję **Kompiluj** lub **Kompiluj ponownie**.

1. W **Eksploratorze testów** wybierz opcję **Uruchom wszystkie** lub wybierz konkretne testy, które chcesz uruchomić. Kliknij prawym przyciskiem myszy Test, aby wyświetlić inne opcje, w tym uruchamianie go w trybie debugowania z włączonymi punktami przerwania. Po uruchomieniu wszystkich testów okno pokazuje, które testy zakończyły się powodzeniem, a które nie powiodły się:

![Eksplorator testów po uruchomieniu testów](media/cpp-test-explorer-passed.png)

W przypadku testów zakończonych niepowodzeniem komunikat zawiera szczegółowe informacje ułatwiające zdiagnozowanie przyczyny. Kliknij prawym przyciskiem myszy Test zakończony niepowodzeniem dla menu podręcznego. Wybierz **Debuguj wybrane testy** , aby przejść przez funkcję, w której wystąpił błąd.

Aby uzyskać więcej informacji o korzystaniu z programu **Test Explorer**, zobacz [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](run-unit-tests-with-test-explorer.md).

Aby uzyskać więcej informacji dotyczących testów jednostkowych, zobacz temat podstawowe informacje o [teście jednostkowym](unit-test-basics.md)

## <a name="use-codelens"></a>Użyj CodeLens

**Visual Studio 2017 i nowsze (wersje Professional i Enterprise)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) umożliwia szybkie sprawdzenie stanu testu jednostkowego bez opuszczania edytora kodu.

Możesz zainicjować CodeLens dla projektu testów jednostkowych języka C++ w dowolny z następujących sposobów:

- Edytuj i skompiluj projekt testowy lub rozwiązanie.
- Odbuduj projekt lub rozwiązanie.
- Uruchom testy z okna **Eksplorator testów** .

Po jego zainicjowaniu można zobaczyć ikony stanu testu powyżej poszczególnych testów jednostkowych.

![Ikony C++ CodeLens](media/cpp-test-codelens-icons.png)

Kliknij ikonę, aby uzyskać więcej informacji, lub Uruchom lub Debuguj test jednostkowy:

![Debugowanie i uruchamianie CodeLens w języku C++](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Zobacz też

- [Testowanie jednostkowe kodu](unit-test-your-code.md)
