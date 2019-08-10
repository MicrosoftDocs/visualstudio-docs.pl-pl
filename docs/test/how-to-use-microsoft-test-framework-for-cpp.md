---
title: Używanie struktury testów jednostkowych Microsoft dla języka C++
ms.date: 06/13/2019
ms.topic: conceptual
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: fd5780479da10da43c270bbf4ffc5a215cb86ad6
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926690"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Użyj testów jednostkowych Microsoft Framework dla języka C++ w programie Visual Studio

Framework testów jednostkowych Microsoft dla języka C++ jest domyślnie włączone w **programowanie aplikacji klasycznych w języku C++** obciążenia.

## <a name="separate_project"></a> Do pisania testów jednostkowych w osobnym projekcie

Zazwyczaj uruchamiasz swój kod testu we własnym projekcie, w tym samym rozwiązaniu, jako kod, który ma zostać przetestowana. Aby skonfigurować i skonfigurować nowy projekt testowy, zobacz [pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="same_project"></a> Pisanie testów jednostkowych w tym samym projekcie

W niektórych przypadkach, na przykład podczas testowania niewyeksportowanych funkcji w bibliotece DLL, może być konieczne utworzenie testów w tym samym projekcie co program, który jest testowany. Pisanie testów jednostkowych w tym samym projekcie:

1. Zmodyfikuj właściwości projektu, aby uwzględnić pliki nagłówkowe i bibliotek, które są wymagane dla testów jednostkowych.

   1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu dla programu, które testujesz, a następnie wybierz **właściwości** > **właściwości konfiguracji**  >  **Katalogi VC ++** .

   2. Kliknij strzałkę w dół w poniższych wierszach i wybierz polecenie  **\<Edytuj >** . Dodaj następujące ścieżki:

      | Katalog | Właściwość |
      |-| - |
      | **Katalogi plików nagłówkowych** | **$(VCInstallDir)Auxiliary\VS\UnitTest\include** |
      | **Katalogi bibliotek** | **$(VCInstallDir)Auxiliary\VS\UnitTest\lib** |

2. Dodaj plik testu jednostkowego języka C++:

   - Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj** > **nowy plik elementu**  >   **C++ (. cpp)** .

## <a name="write-the-tests"></a>Pisanie testów

Wszelkie *.cpp* plik z klas testowych musi obejmować "CppUnitTest.h" i mieć za pomocą instrukcji dla `using namespace Microsoft::VisualStudio::CppUnitTestFramework`. Projekt testowy jest już skonfigurowany dla Ciebie. Obejmuje również definicję przestrzeni nazw i TEST_CLASS z TEST_METHOD, aby ułatwić pracę. Możesz zmodyfikować nazwę przestrzeni nazw, a także nazwy w nawiasach w makrach klasy i metody.

Makra specjalne są definiowane do inicjowania modułów testowych, klas i metod oraz do oczyszczania zasobów po zakończeniu testów. Te makra wygenerować kod, który jest wykonywany przed klasy lub metody najpierw jest dostępny i po wykonaniu ostatniego testu. Aby uzyskać więcej informacji, zobacz [inicjowanie i oczyszczanie](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup).

Użyj metod statycznych w [Asercja](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) klasy w celu zdefiniowania warunków testu. Użyj [rejestratora](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) klasy, aby pisać wiadomości do **okno danych wyjściowych**. Dodawanie atrybutów z metodami testowymi

## <a name="run-the-tests"></a>Uruchom testy

1. Na **testu** menu, wybierz **Windows** > **Eksplorator testów**.

1. Jeśli wszystkie testy nie są widoczne w oknie, tworzenia projektu badania, klikając prawym przyciskiem myszy jego węzła w **Eksploratora rozwiązań** i wybierając pozycję **kompilacji** lub **odbudować**.

1. W **Eksplorator testów**, wybierz **Uruchom wszystkie**, lub wybierz określonych testów, które chcesz uruchomić. Kliknij prawym przyciskiem myszy na test dla innych opcji, w tym uruchamianie w trybie debugowania, z punktami przerwania jest włączony.

1. W **okno danych wyjściowych** wybierz **testy** w rozwijanego wyświetlanie komunikatów o napisanych przez `Logger` klasy:

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

- [Szybki start: Programowanie sterowane testami za pomocą Eksploratora testów](../test/quick-start-test-driven-development-with-test-explorer.md)
