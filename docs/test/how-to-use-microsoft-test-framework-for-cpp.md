---
title: Używanie struktury testów jednostkowych Microsoft dla języka C++
ms.date: 11/15/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 88265c1ac86b5b1c1cd90ef428c9c2c770d9f2a2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068263"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Użyj testów jednostkowych Microsoft Framework dla języka C++ w programie Visual Studio

Framework testów jednostkowych Microsoft dla języka C++ jest domyślnie włączone w **programowanie aplikacji klasycznych w języku C++** obciążenia.

##  <a name="separate_project"></a> Do pisania testów jednostkowych w osobnym projekcie

Zazwyczaj uruchamiasz swój kod testu we własnym projekcie, w tym samym rozwiązaniu, jako kod, który ma zostać przetestowana. Aby skonfigurować i skonfigurować nowy projekt testowy, zobacz [pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md).

##  <a name="same_project"></a> Pisanie testów jednostkowych w tym samym projekcie

W niektórych przypadkach, na przykład podczas testowania — eksportowane funkcje w bibliotece DLL może być konieczne Utwórz testy w tym samym projekcie jako program, które testujesz. Pisanie testów jednostkowych w tym samym projekcie:

1. Zmodyfikuj właściwości projektu, aby uwzględnić pliki nagłówkowe i bibliotek, które są wymagane dla testów jednostkowych.

   1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu dla programu, które testujesz, a następnie wybierz **właściwości** > **właściwości konfiguracji**  >  **Katalogi VC ++**.

   2. Kliknij strzałkę w dół w następujących wierszach i wybierz polecenie **<Edit>** :


      | Katalog | Właściwość |
      |-| - |
      | **Katalogi plików nagłówkowych** | **$(VCInstallDir)UnitTest\include;$(IncludePath)** |
      | **Katalogi bibliotek** | **$(VCInstallDir)UnitTest\lib;$(LibraryPath)** |


2. Dodaj plik testu jednostkowego języka C++:

   -   Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** > **nowy element** > **testu jednostkowego języka C++**.

## <a name="write-the-tests"></a>Pisanie testów

Wszelkie *.cpp* plik z klas testowych musi obejmować "CppUnitTest.h" i mieć za pomocą instrukcji dla `using namespace Microsoft::VisualStudio::CppUnitTestFramework`. Projekt testowy jest już skonfigurowany dla Ciebie. Obejmuje również definicję przestrzeni nazw i TEST_CLASS z TEST_METHOD, aby ułatwić pracę. Możesz zmodyfikować nazwę przestrzeni nazw, a także nazwy w nawiasach w makrach klasy i metody.

Specjalne makra są zdefiniowane dla inicjowanie testu modułów, klas i metod i oczyszczania resoures, po zakończeniu testów. Te makra wygenerować kod, który jest wykonywany przed klasy lub metody najpierw jest dostępny i po wykonaniu ostatniego testu. Aby uzyskać więcej informacji, zobacz [inicjowanie i oczyszczanie](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup).

Użyj metod statycznych w [Asercja](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) klasy w celu zdefiniowania warunków testu. Użyj [rejestratora](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) klasy, aby pisać wiadomości do **okno danych wyjściowych**. Dodawanie atrybutów z metodami testowymi

## <a name="run-the-tests"></a>Uruchom testy

1. Na **testu** menu, wybierz **Windows** > **Eksplorator testów**.
2. Jeśli wszystkie testy nie są widoczne w oknie, tworzenia projektu badania, klikając prawym przyciskiem myszy jego węzła w **Eksploratora rozwiązań** i wybierając pozycję **kompilacji** lub **odbudować**.

3. W **Eksplorator testów**, wybierz **Uruchom wszystkie**, lub wybierz określonych testów, które chcesz uruchomić. Kliknij prawym przyciskiem myszy na test dla innych opcji, w tym uruchamianie w trybie debugowania, z punktami przerwania jest włączony.
4. W **okno danych wyjściowych** wybierz **testy** w rozwijanego wyświetlanie komunikatów o napisanych przez `Logger` klasy:

   ![Okno danych wyjściowych C++ wyświetlanie wiadomości testowe](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Definiowanie cech, aby włączyć grupowanie

Można zdefiniować cech metod testowych, które pozwalają na klasyfikowanie i testy w grupie **Eksploratora testów**. Aby zdefiniować cechę, użyj `TEST_METHOD_ATTRIBUTE` makra. Na przykład aby zdefiniować cechę o nazwie `TEST_MY_TRAIT`:

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

 Aby użyć określonej cechy w testach jednostki:

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
    TEST_OWNER(L"OwnerName")
    TEST_PRIORITY(1)
    TEST_MY_TRAIT(L"thisTraitValue")
END_TEST_METHOD_ATTRIBUTE()

TEST_METHOD(Method1)
{
    Logger::WriteMessage("In Method1");
    Assert::AreEqual(0, 0);
}
```

### <a name="c-trait-attribute-macros"></a>Makra atrybutów cech C++

Następujące cechy wstępnie zdefiniowane, znajdują się w `CppUnitTest.h`. Aby uzyskać więcej informacji, zobacz [Microsoft Framework testów jednostkowych dla odwołania do interfejsu API języka C++](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md).

|Macro|Opis|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Użyj makra test_method_attribute, aby zdefiniować cechę.|
|`TEST_OWNER(ownerAlias)`|Użyj wstępnie zdefiniowana cecha właściciela do określania właściciela metody badania.|
|`TEST_PRIORITY(priority)`|Użyj wstępnie zdefiniowanego cecha priorytetu jest używana do przypisywania względnych priorytetów do metod badania.|

## <a name="see-also"></a>Zobacz także

- [Szybki Start: Testów opartych na tworzenie aplikacji przy użyciu Eksploratora testów](../test/quick-start-test-driven-development-with-test-explorer.md)
