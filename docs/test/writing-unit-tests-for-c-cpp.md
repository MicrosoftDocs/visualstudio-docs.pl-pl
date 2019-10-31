---
title: Zapisz testy jednostkowe dla C/C++
description: Zapisuj C++ testy jednostkowe w programie Visual Studio przy użyciu różnych platform testowych, w tym narzędzia ctest, zwiększanie. testowanie i Google test.
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 824b928c9f89b98f9026059b824fce84969bf69a
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189103"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Zapisz testy jednostkowe dla CC++ /w Visual Studio

Testy C++ jednostkowe można pisać i uruchamiać przy użyciu okna **Eksploratora testów** , podobnie jak w przypadku innych języków. Aby uzyskać więcej informacji o korzystaniu z programu **Test Explorer**, zobacz [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Niektóre funkcje, takie jak Live Unit Testing, kodowane testy interfejsu użytkownika i IntelliTest nie są C++obsługiwane w programie.

Program Visual Studio zawiera C++ te platformy testowe bez dodatkowych wymaganych plików do pobrania:

- Struktura testów jednostkowych firmy Microsoft dla programuC++
- Google Test
- Zwiększ. test
- Narzędzia ctest

Oprócz zainstalowanych struktur można napisać własną kartę testową dla każdej platformy, która ma być używana w programie Visual Studio. Adapter testowy może zintegrować testy jednostkowe z oknem **Eksplorator testów** . Na [Visual Studio Marketplace](https://marketplace.visualstudio.com)są dostępne kilka kart innych firm. Aby uzyskać więcej informacji, zobacz [Instalowanie platform testów jednostkowych](install-third-party-unit-test-frameworks.md)innych firm.

**Visual Studio 2017 i nowsze (wersje Professional i Enterprise)**

C++projekty testów jednostkowych obsługują [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).

**Visual Studio 2017 i nowsze (wszystkie wersje)**

- **Karta Google test** jest dołączana jako domyślny składnik **tworzenia pulpitu z C++**  obciążeniami. Ma szablon projektu, który można dodać do rozwiązania za pomocą menu **Dodaj nowy projekt** w prawym przyciskiem myszy w węźle rozwiązanie w **Eksplorator rozwiązań**i opcje, które można skonfigurować za pomocą **narzędzi** > **Opcje**. Aby uzyskać więcej informacji, zobacz [How to: Use Google test in Visual Studio](how-to-use-google-test-for-cpp.md).

- **Zwiększenie wydajności. test** jest uwzględniany jako domyślny składnik **tworzenia aplikacji klasycznych C++ z** obciążeniem. Jest ona zintegrowana z **Eksploratorem testów** , ale obecnie nie ma szablonu projektu, dlatego należy ją skonfigurować ręcznie. Aby uzyskać więcej informacji, zobacz [jak: użyć Zwiększ. test w programie Visual Studio](how-to-use-boost-test-for-cpp.md).

- Obsługa **Narzędzia ctest** jest dołączana ze składnikiem  **C++ narzędzia CMAKE** , który jest częścią **tworzenia aplikacji C++ klasycznych** . Jednak narzędzia ctest nie jest jeszcze w pełni zintegrowana z **Eksploratorem testów**. Aby uzyskać więcej informacji, zobacz [How to: use narzędzia ctest in Visual Studio](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 i starsze**

Możesz pobrać adapter Google Test i poprawić rozszerzenia adaptera testowego na Visual Studio Marketplace na [karcie testowej w celu zwiększenia wydajności. Przetestuj](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) i [przetestuj adapter dla Google test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Podstawowy przepływ pracy testu

W poniższych sekcjach przedstawiono podstawowe kroki umożliwiające rozpoczęcie pracy z C++ testami jednostkowymi. Konfiguracja podstawowa jest bardzo podobna dla struktur firmy Microsoft i Google Test. Podwyższanie poziomu. test wymaga ręcznego utworzenia projektu testowego.

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Tworzenie projektu testowego w programie Visual Studio 2019

Można definiować i uruchamiać testy wewnątrz co najmniej jednego projektu testowego, który znajduje się w tym samym rozwiązaniu co kod, który ma zostać przetestowany. Aby dodać nowy projekt testowy do istniejącego rozwiązania, kliknij prawym przyciskiem myszy węzeł rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj** > **Nowy projekt**. Ustaw **Język** na C++ i wpisz "test" w polu wyszukiwania. Na poniższej ilustracji przedstawiono projekty testowe, które są dostępne po zainstalowaniu programu **Desktop Development C++**  i **platformy UWP Development** :

![C++Testowanie projektów w programie VIsual Studio 2019](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Tworzenie projektu testowego w programie Visual Studio 2017

Można definiować i uruchamiać testy wewnątrz co najmniej jednego projektu testowego, który znajduje się w tym samym rozwiązaniu co kod, który ma zostać przetestowany. Aby dodać nowy projekt testowy do istniejącego rozwiązania, kliknij prawym przyciskiem myszy węzeł rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj** > **Nowy projekt**. Następnie w okienku po lewej stronie wybierz pozycję **test wizualny C++**  , a następnie wybierz jeden z typów projektu w środkowym okienku. Na poniższej ilustracji przedstawiono projekty testowe, które są dostępne po zainstalowaniu programu **Desktop Development C++ with** obciążeń:

![C++Projekty testowe](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Tworzenie odwołań do innych projektów w rozwiązaniu

Aby umożliwić testowanie kodu w celu uzyskania dostępu do funkcji w projekcie w celu przetestowania, Dodaj odwołanie do projektu w projekcie testowym. Kliknij prawym przyciskiem myszy węzeł projektu testowego w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj** > **odwołanie**. Następnie w oknie dialogowym Wybierz projekty, które chcesz przetestować.

![Dodaj odwołanie](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Połącz z obiektem lub plikami biblioteki

Jeśli kod testu nie eksportuje funkcji, które mają zostać przetestowane, można dodać pliki Output. obj lub. lib do zależności projektu testowego. Zobacz, [Aby połączyć testy z plikami obiektu lub biblioteki](how-to-use-microsoft-test-framework-for-cpp.md).

### <a name="add-include-directives-for-header-files"></a>Dodaj dyrektywy #include dla plików nagłówkowych

Następnie w pliku *. cpp* testu jednostkowego dodaj dyrektywę `#include` dla wszystkich plików nagłówkowych, które deklarują typy i funkcje, które chcesz przetestować. Typ `#include "`, a następnie technologia IntelliSense zostanie aktywowana, aby ułatwić wybór. Powtórz te czynności dla wszystkich dodatkowych nagłówków.

![Dodaj dyrektywy include](media/cpp-add-includes-test-project.png)

Aby uniknąć konieczności wpisywania pełnej ścieżki w każdej instrukcji include w pliku źródłowym, można dodać wymagane foldery we **właściwościach** > **projektu** > **CC++ /**  > **Ogólne** > **dodatkowe Katalogi**.

### <a name="write-test-methods"></a>Pisanie metod testowych

> [!NOTE]
> W tej sekcji przedstawiono składnię dla struktury testowania jednostkowego firmy MicrosoftC++dla języka C/. Jest on udokumentowany w tym miejscu: [Microsoft. VisualStudio. TestTools. CPPUNITTESTFRAMEWORK API Reference](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Aby uzyskać dokumentację Google Test, zobacz [Google test](https://github.com/google/googletest/blob/master/googletest/docs/primer.md). Aby zwiększyć. test, zobacz [biblioteka Boost test: Struktura testów jednostkowych](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

Plik *. cpp* w projekcie testowym ma klasę zastępczą i metodę zdefiniowaną dla Ciebie jako przykład sposobu pisania kodu testu. Zwróć uwagę, że podpisy używają makr TEST_CLASS i TEST_METHOD, które umożliwiają odnajdywanie metod z okna **Eksplorator testów** .

![Dodaj dyrektywy include](media/cpp-write-test-methods.png)

TEST_CLASS i TEST_METHOD są częścią [natywnego środowiska testowego firmy Microsoft](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). **Eksplorator testów** odnajduje metody testowe w innych obsługiwanych platformach w podobny sposób.

Element TEST_METHOD zwraca wartość void. Aby utworzyć wynik testu, użyj metod statycznych w klasie `Assert`, aby przetestować rzeczywiste wyniki względem tego, co jest oczekiwane. W poniższym przykładzie Załóżmy, że `MyClass` ma konstruktora, który przyjmuje `std::string`. Możemy sprawdzić, czy Konstruktor inicjuje klasę zgodnie z oczekiwaniami, tak jak to zrobić:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

W poprzednim przykładzie wynik wywołania `Assert::AreEqual` określa, czy test kończy się powodzeniem, czy nie. Klasa Assert zawiera wiele innych metod porównujących wyniki oczekiwane i rzeczywiste.

Można dodać *cechy* do metod testowych, aby określić właścicieli testów, priorytet i inne informacje. Następnie można użyć tych wartości do sortowania i grupowania testów w **Eksploratorze testów**. Aby uzyskać więcej informacji, zobacz [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Uruchom testy

1. W menu **test** wybierz pozycję **Windows** > **Test Explorer**. Na poniższej ilustracji przedstawiono projekt testowy, którego testy nie zostały jeszcze uruchomione.

   ![Eksplorator testów przed uruchomieniem testów](media/cpp-test-explorer.png)

   > [!NOTE]
   > Integracja narzędzia ctest z **Eksploratorem testów** nie jest jeszcze dostępna. Uruchom testy narzędzia ctest z głównego menu CMake.

1. Jeśli wszystkie testy nie są widoczne w oknie, Skompiluj projekt testowy, klikając prawym przyciskiem myszy jego węzeł w **Eksplorator rozwiązań** i wybierając opcję **Kompiluj** lub **Kompiluj ponownie**.

1. W **Eksploratorze testów**wybierz opcję **Uruchom wszystkie**lub wybierz konkretne testy, które chcesz uruchomić. Kliknij prawym przyciskiem myszy Test, aby wyświetlić inne opcje, w tym uruchamianie go w trybie debugowania z włączonymi punktami przerwania. Po uruchomieniu wszystkich testów okno pokazuje, które testy zakończyły się powodzeniem, a które nie powiodły się:

![Eksplorator testów po uruchomieniu testów](media/cpp-test-explorer-passed.png)

W przypadku testów zakończonych niepowodzeniem komunikat zawiera szczegółowe informacje ułatwiające zdiagnozowanie przyczyny. Możesz kliknąć prawym przyciskiem myszy Test zakończony niepowodzeniem i wybrać **Debuguj wybrane testy** , aby przejść przez funkcję, w której wystąpił błąd.

Aby uzyskać więcej informacji o korzystaniu z programu **Test Explorer**, zobacz [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](run-unit-tests-with-test-explorer.md).

Aby uzyskać najlepsze rozwiązania dotyczące testów jednostkowych, zobacz [podstawowe informacje o teście jednostkowym](unit-test-basics.md)

## <a name="use-codelens"></a>Użyj CodeLens

**Visual Studio 2017 i nowsze (wersje Professional i Enterprise)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) umożliwia szybkie sprawdzenie stanu testu jednostkowego bez opuszczania edytora kodu. Można inicjować CodeLens dla projektu testów C++ jednostkowych w dowolny z następujących sposobów:

- Edytuj i skompiluj projekt testowy lub rozwiązanie.
- Odbuduj projekt lub rozwiązanie.
- Uruchom testy z okna **Eksplorator testów** .

Po zainicjowaniu **CodeLens** można zobaczyć ikony stanu testu powyżej poszczególnych testów jednostkowych.

![C++Ikony CodeLens](media/cpp-test-codelens-icons.png)

Kliknij ikonę, aby uzyskać więcej informacji, lub Uruchom lub Debuguj test jednostkowy:

![C++CodeLens i debugowanie](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Zobacz także

- [Testowanie jednostkowe kodu](unit-test-your-code.md)
