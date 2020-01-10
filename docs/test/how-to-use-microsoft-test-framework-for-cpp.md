---
title: Używanie struktury testów jednostkowych Microsoft dla języka C++
description: Użyj struktury testów jednostkowych firmy Microsoft C++ dla programu, aby utworzyć testy C++ jednostkowe dla kodu.
ms.date: 01/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 5c8cb794ce7891e74610f1a73164ce403d294925
ms.sourcegitcommit: 789430e18dfe8e5f7db19273e7298af2f078c0dc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75755566"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Użyj testów jednostkowych Microsoft Framework dla języka C++ w programie Visual Studio

Framework testów jednostkowych Microsoft dla języka C++ jest domyślnie włączone w **programowanie aplikacji klasycznych w języku C++** obciążenia.

## <a name="separate_project"></a> Do pisania testów jednostkowych w osobnym projekcie

Zazwyczaj uruchamiasz swój kod testu we własnym projekcie, w tym samym rozwiązaniu, jako kod, który ma zostać przetestowana. Aby skonfigurować i skonfigurować nowy projekt testowy, zobacz [pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="same_project"></a> Pisanie testów jednostkowych w tym samym projekcie

W niektórych przypadkach, na przykład podczas testowania niewyeksportowanych funkcji w bibliotece DLL, może być konieczne utworzenie testów w tym samym projekcie co program, który jest testowany. Pisanie testów jednostkowych w tym samym projekcie:

1. Zmodyfikuj właściwości projektu, aby uwzględnić pliki nagłówkowe i bibliotek, które są wymagane dla testów jednostkowych.

   1. W Eksplorator rozwiązań w menu skrótów testowanego projektu wybierz polecenie **Właściwości**. Zostanie otwarte okno właściwości projektu.

   1. W oknie dialogowym strony właściwości wybierz pozycję **Właściwości konfiguracji** > **Katalogi VC + +** .

   1. Kliknij strzałkę w dół w poniższych wierszach i wybierz polecenie **\<edytuj >** . Dodaj następujące ścieżki:

      | Katalog | Właściwość |
      |-| - |
      | **Katalogi plików nagłówkowych** | **$(VCInstallDir)Auxiliary\VS\UnitTest\include** |
      | **Katalogi bibliotek** | **$(VCInstallDir)Auxiliary\VS\UnitTest\lib** |

1. Dodaj plik testu jednostkowego języka C++:

   - Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj** > **nowy element** >  **C++ plik (. cpp)** .

## <a name="object_files"></a> Aby powiązać testy z plikami obiektu lub biblioteki

Jeśli testowy kod nie eksportuje funkcji, które mają zostać przetestowane, można dodać plik Output **. obj** lub **. lib** do zależności projektu testowego. Zmodyfikuj właściwości projektu testowego, aby uwzględnić nagłówki i pliki bibliotek lub obiektów, które są wymagane do testowania jednostkowego.

1. W Eksplorator rozwiązań, w menu skrótów projektu testowego, wybierz **Właściwości**. Zostanie otwarte okno właściwości projektu.

1. Wybierz **Właściwości konfiguracji** > **konsolidator** > strona **wejściowa** , a następnie wybierz pozycję **dodatkowe zależności**.

   Wybierz **Edytuj**i Dodaj nazwy **.obj** lub **.lib** plików. Nie używaj pełnych nazw ścieżek.

1. Wybierz **Właściwości konfiguracji** > **konsolidator** > strona **ogólna** , a następnie wybierz pozycję **Dodatkowe katalogi biblioteki**.

   Wybierz **Edytuj**i Dodaj ścieżkę katalogu **.obj** lub **.lib** plików. Ścieżka zazwyczaj mieści się w folderze kompilacji testowanego projektu.

1. Wybierz **Właściwości konfiguracji** > stronie **katalogów VC + +** , a następnie wybierz pozycję **Dołącz katalogi**.

   Wybierz **Edytuj**, a następnie Dodaj nagłówek katalogu testowanego projektu.

## <a name="write-the-tests"></a>Pisanie testów

Wszelkie *.cpp* plik z klas testowych musi obejmować "CppUnitTest.h" i mieć za pomocą instrukcji dla `using namespace Microsoft::VisualStudio::CppUnitTestFramework`. Projekt testowy jest już skonfigurowany dla Ciebie. Obejmuje również definicję przestrzeni nazw i TEST_CLASS z TEST_METHOD, aby ułatwić pracę. Możesz zmodyfikować nazwę przestrzeni nazw i nazwy w nawiasach w makrach klasy i metod.

Struktura testowa definiuje specjalne makra do inicjowania modułów testowych, klas i metod, a następnie czyszczenie zasobów po zakończeniu testów. Te makra generują kod do wykonania przed pierwszym uzyskaniem dostępu do klasy lub metody, a po ostatnim uruchomieniu testu. Aby uzyskać więcej informacji, zobacz [inicjowanie i oczyszczanie](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup).

Użyj metod statycznych w [Asercja](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) klasy w celu zdefiniowania warunków testu. Użyj [rejestratora](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) klasy, aby pisać wiadomości do **okno danych wyjściowych**. Dodawanie atrybutów z metodami testowymi

## <a name="run-the-tests"></a>Uruchom testy

1. Na **testu** menu, wybierz **Windows** > **Eksplorator testów**.

1. Jeśli nie wszystkie testy są widoczne w oknie, Skompiluj projekt testowy, klikając prawym przyciskiem myszy jego węzeł w **Eksplorator rozwiązań** i wybierając opcję **Kompiluj** lub **Kompiluj ponownie**.

1. W **Eksplorator testów**, wybierz **Uruchom wszystkie**, lub wybierz określonych testów, które chcesz uruchomić. Kliknij prawym przyciskiem myszy na test dla innych opcji, w tym uruchamianie w trybie debugowania, z punktami przerwania jest włączony.

1. W **okno dane wyjściowe** wybierz **testy** z listy rozwijanej, aby wyświetlić komunikaty napisywane przez klasę `Logger`:

   ![Okno danych wyjściowych C++ wyświetlanie wiadomości testowe](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Definiowanie cech, aby włączyć grupowanie

Można zdefiniować cechy metod testowych, które umożliwiają kategoryzowanie i grupowanie testów w **Eksploratorze testów**. Aby zdefiniować cechę, użyj `TEST_METHOD_ATTRIBUTE` makra. Na przykład aby zdefiniować cechę o nazwie `TEST_MY_TRAIT`:

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
