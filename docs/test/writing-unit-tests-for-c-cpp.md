---
title: Zapis testów jednostkowych dla języka C/C++
description: Napisz c++ testy jednostkowe w programie Visual Studio przy użyciu różnych struktur testowych, w tym CTest, Boost.Test i Google Test.
ms.date: 02/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 354ccad121884c99541057a2e0e0a47d9d2a4341
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78937555"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Zapisywanie testów jednostkowych dla języka C/C++ w programie Visual Studio

Można napisać i uruchomić testy jednostkowe języka C++ przy użyciu okna **Eksploratora testów.** Działa tak samo jak w przypadku innych języków. Aby uzyskać więcej informacji na temat korzystania z **Eksploratora testów,** zobacz [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Niektóre funkcje, takie jak live unit testing, kodowane testy interfejsu użytkownika i IntelliTest nie są obsługiwane dla języka C++.

Visual Studio zawiera te struktury testów języka C++ bez dodatkowych pobierania wymagane:

- Struktura testowania jednostek firmy Microsoft dla języka C++
- Google Test
- Boost.Test
- CTest (polski)

Wraz z przy użyciu zainstalowanych struktur, można napisać własną kartę testową dla dowolnej struktury, które chcesz użyć w programie Visual Studio. Karta testowa może integrować testy jednostkowe z oknem **Eksploratora testów.** W programie [Visual Studio Marketplace](https://marketplace.visualstudio.com)dostępnych jest kilka kart innych firm. Aby uzyskać więcej informacji, zobacz [Instalowanie struktur testów jednostkowych innych firm](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 i nowsze (Professional i Enterprise)**

Projekty testów jednostkowych języka C++ obsługują [kod CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).

**Visual Studio 2017 i nowsze (wszystkie wersje)**

- **Karta testowa Google** jest dołączona jako domyślny składnik programu Desktop development z obciążeniem **w języku C++.** Ma szablon projektu, który można dodać do rozwiązania. Użyj menu **Dodaj nowy projekt** prawym przyciskiem myszy w węźle rozwiązania w **Eksploratorze rozwiązań,** aby go dodać. Posiada również opcje, które można skonfigurować za pomocą**opcji** **narzędzi** > . Aby uzyskać więcej informacji, zobacz [Jak: Korzystanie z testu Google w programie Visual Studio](how-to-use-google-test-for-cpp.md).

- **Boost.Test** jest dołączony jako domyślny składnik rozwoju pulpitu z obciążeniem **C++.** Jest zintegrowany z **Eksploratorem testów,** ale obecnie nie ma szablonu projektu. Musi być skonfigurowany ręcznie. Aby uzyskać więcej informacji, zobacz [Jak: Użyj Boost.Test w programie Visual Studio](how-to-use-boost-test-for-cpp.md).

- **Obsługa CTest** jest dołączona do składnika **narzędzi C++ CMake,** który jest częścią rozwoju pulpitu z obciążeniem **C++.** Aby uzyskać więcej informacji, zobacz [Jak: Użyj CTest w programie Visual Studio](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 i starsze**

Możesz pobrać karty testowej Google i rozszerzenia karty Boost.Test adaptera w portalu Visual Studio Marketplace. Znajdź je w [adapterze testowym do boost.test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) i [adaptera testowego do google test .](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest)

## <a name="basic-test-workflow"></a>Podstawowy przepływ pracy testu

W poniższych sekcjach przedstawiono podstawowe kroki, aby rozpocząć testowanie jednostek języka C++. Podstawowa konfiguracja jest podobna zarówno dla platform Microsoft, jak i Google Test. Boost.Test wymaga ręcznego utworzenia projektu testowego.

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Tworzenie projektu testowego w programie Visual Studio 2019

Definiujesz i uruchamiasz testy wewnątrz jednego lub więcej projektów testowych. Tworzenie projektów w tym samym rozwiązaniu jako kod, który chcesz przetestować. Aby dodać nowy projekt testowy do istniejącego rozwiązania, kliknij prawym przyciskiem myszy węzeł Rozwiązanie w **Eksploratorze rozwiązań**. W wyskakującym menu wybierz polecenie **Dodaj** > **nowy projekt**. Ustaw **język** na C++ i wpisz "test" w polu wyszukiwania. Na poniższej ilustracji przedstawiono projekty testowe, które są dostępne po **zainstalowaniu programu Rozwoju pulpitu z c++** i obciążenie **programistycznego systemu Windows:**

![Projekty testowe C++ w VIsual Studio 2019](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Tworzenie projektu testowego w programie Visual Studio 2017

Definiujesz i uruchamiasz testy wewnątrz jednego lub więcej projektów testowych. Tworzenie projektów w tym samym rozwiązaniu jako kod, który chcesz przetestować. Aby dodać nowy projekt testowy, kliknij prawym przyciskiem myszy węzeł Rozwiązanie w **Eksploratorze rozwiązań** i wybierz pozycję **Dodaj** > **nowy projekt**. W lewym okienku wybierz polecenie **Test języka Visual C++**. Następnie wybierz jeden z typów projektu z centralnego okienka. Na poniższej ilustracji przedstawiono projekty testowe, które są dostępne po zainstalowaniu programu Desktop Development z obciążeniem **języka C++:**

![Projekty testowe języka C++](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Tworzenie odwołań do innych projektów w rozwiązaniu

Aby włączyć dostęp do funkcji w projekcie w ramach testu, dodaj odwołanie do projektu w projekcie testowym. Kliknij prawym przyciskiem myszy węzeł projektu testowego w **Eksploratorze rozwiązań,** aby uzyskać menu podręczne. Wybierz **pozycję Dodaj** > **odwołanie**. W oknie dialogowym Dodawanie odwołań wybierz projekt, który chcesz przetestować.

![Dodawanie odwołania](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Łącze do plików obiektów lub bibliotek

Jeśli kod testowy nie eksportuje funkcji, które chcesz przetestować, można dodać pliki wyjściowe obj lub lib do zależności projektu testowego. Aby uzyskać więcej informacji, zobacz [Aby połączyć testy z plikami obiektu lub biblioteki](/visualstudio/test/how-to-use-microsoft-test-framework-for-cpp#object_files).

### <a name="add-include-directives-for-header-files"></a>Dodawanie #include dyrektyw dla plików nagłówkowych

Następnie w pliku *.cpp* testu jednostkowego dodaj dyrektywę `#include` dla wszystkich plików nagłówkowych, które deklarują typy i funkcje, które chcesz przetestować. Wpisz, `#include "` a następnie IntelliSense aktywuje się, aby pomóc Ci wybrać. Powtórz tę czynność dla wszystkich dodatkowych nagłówków.

![Dodaj dyrektywy o dołączania](media/cpp-add-includes-test-project.png)

Aby uniknąć konieczności wpisywać pełną ścieżkę w każdej instrukcji dołączania w pliku źródłowym, można dodać wymagane foldery we**właściwościach** >  **projektu** > **C/C++** > **Ogólne** > **dodatkowe katalogi dołączania**.

### <a name="write-test-methods"></a>Napisz metody testowe

> [!NOTE]
> W tej sekcji przedstawiono składnię programu Microsoft Unit Testing Framework for C/C++. Jest to udokumentowane tutaj: [Microsoft.VisualStudio.TestTools.CppUnitTestFramework odwołania interfejsu API](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Aby uzyskać dokumentację testu Google, zobacz [Google Test primer](https://github.com/google/googletest/blob/master/googletest/docs/primer.md). Aby uzyskać boost.test, zobacz [Boost Biblioteka testu: Struktura testu jednostkowego](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

Plik *.cpp* w projekcie testowym ma klasę skrótową i metodę zdefiniowaną dla Ciebie. Pokazują one przykład jak napisać kod testowy. Podpisy używają makr TEST_CLASS i TEST_METHOD, które sprawiają, że metody są wykrywalne w oknie **Eksploratora testów.**

![Dodaj dyrektywy o dołączania](media/cpp-write-test-methods.png)

TEST_CLASS i TEST_METHOD są częścią programu [Microsoft Native Test Framework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). **Eksplorator testów** odnajduje metody testów w innych obsługiwanych ramach w podobny sposób.

TEST_METHOD zwraca pustkę. Aby uzyskać wynik testu, należy użyć `Assert` metod statycznych w klasie, aby przetestować rzeczywiste wyniki względem oczekiwanych. W poniższym przykładzie załóżmy, `MyClass` `std::string`że ma konstruktora, który przyjmuje . Możemy sprawdzić, czy konstruktor inicjuje klasę zgodnie z oczekiwaniami, tak jak:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

W poprzednim przykładzie wynik `Assert::AreEqual` wywołania określa, czy test kończy się niepowodzeniem lub niepowodzeniem. Assert Klasa zawiera wiele innych metod porównywania oczekiwanych vs rzeczywiste wyniki.

Można dodać cechy do metod *testowych,* aby określić właścicieli testów, priorytet i inne informacje. Następnie można użyć tych wartości do sortowania i grupowania testów w **Eksploratorze testów**. Aby uzyskać więcej informacji, zobacz [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Uruchamianie testów

1. W menu **Test** wybierz polecenie**Eksplorator testów** **systemu Windows** > . Na poniższej ilustracji przedstawiono projekt testowy, którego testy nie zostały jeszcze uruchomione.

   ![Eksplorator testów przed uruchomieniem testów](media/cpp-test-explorer.png)

   > [!NOTE]
   > CTest integracji z **Eksploratorem testów** nie jest jeszcze dostępna. Uruchom testy CTest z menu głównego CMake.

1. Jeśli nie wszystkie testy są widoczne w oknie, skompiluj projekt testowy, klikając prawym przyciskiem myszy jego węzeł w **Eksploratorze rozwiązań** i wybierając polecenie **Buduj** lub **przebudowuj**.

1. W **Eksploratorze testów**wybierz pozycję **Uruchom wszystko**lub wybierz konkretne testy, które chcesz uruchomić. Kliknij prawym przyciskiem myszy test dla innych opcji, w tym uruchamianie go w trybie debugowania z włączonymi punktami przerwania. Po uruchomieniu wszystkich testów, okno pokazuje, które testy przeszły, a które nie:

![Eksplorator testów po uruchomieniu testów](media/cpp-test-explorer-passed.png)

W przypadku nieudanych testów komunikat zawiera szczegółowe informacje, które pomagają zdiagnozować przyczynę. Kliknij prawym przyciskiem myszy test niepowodzenia w menu podręcznym. Wybierz **opcję Debugowanie wybranych testów,** aby przejść przez funkcję, w której wystąpił błąd.

Aby uzyskać więcej informacji na temat korzystania z **Eksploratora testów,** zobacz [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](run-unit-tests-with-test-explorer.md).

Aby uzyskać więcej informacji dotyczących testowania jednostkowego, zobacz [Podstawy testu jednostkowego](unit-test-basics.md)

## <a name="use-codelens"></a>Korzystanie z funkcji CodeLens

**Visual Studio 2017 i nowsze wersje (wersje Professional i Enterprise)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) pozwala szybko zobaczyć stan testu jednostkowego bez opuszczania edytora kodu.

Można zainicjować CodeLens dla projektu testu jednostkowego języka C++ w dowolny z następujących sposobów:

- Edytuj i skompiluj projekt testowy lub rozwiązanie.
- Odbuduj swój projekt lub rozwiązanie.
- Uruchom testy z okna **Eksploratora testów.**

Po jego zainicjowaniu, można zobaczyć ikony stanu testu powyżej każdego testu jednostkowego.

![Ikony kodu Języka C++](media/cpp-test-codelens-icons.png)

Kliknij ikonę, aby uzyskać więcej informacji lub uruchomić lub debugować test jednostkowy:

![Uruchamianie i debugowanie kodu języka C++](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Zobacz też

- [Jednostka przetestować swój kod](unit-test-your-code.md)
