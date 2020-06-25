---
title: Używanie struktury testów jednostkowych Microsoft dla języka C++
description: Użyj struktury testów jednostkowych firmy Microsoft dla języka C++, aby utworzyć testy jednostkowe dla kodu C++.
ms.date: 01/08/2020
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: a9393fd248f4e6520c261d405bc624a75d8cf69f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287119"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Korzystanie z struktury testów jednostkowych firmy Microsoft dla języka C++ w programie Visual Studio

Struktura testów jednostkowych firmy Microsoft dla języka C++ jest domyślnie dołączona do **tworzenia aplikacji klasycznych przy użyciu obciążenia c++** .

## <a name="to-write-unit-tests-in-a-separate-project"></a><a name="separate_project"></a>Aby napisać testy jednostkowe w osobnym projekcie

Zazwyczaj kod testowy jest uruchamiany w osobnym projekcie w tym samym rozwiązaniu co kod, który ma zostać przetestowany. Aby skonfigurować i skonfigurować nowy projekt testowy, zobacz [pisanie testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-write-unit-tests-in-the-same-project"></a><a name="same_project"></a>Aby napisać testy jednostkowe w tym samym projekcie

W niektórych przypadkach, na przykład podczas testowania niewyeksportowanych funkcji w bibliotece DLL, może być konieczne utworzenie testów w tym samym projekcie co program, który jest testowany. Aby zapisać testy jednostkowe w tym samym projekcie:

1. Zmodyfikuj właściwości projektu w celu uwzględnienia nagłówków i plików bibliotek, które są wymagane do testowania jednostkowego.

   1. W Eksplorator rozwiązań w menu skrótów testowanego projektu wybierz polecenie **Właściwości**. Zostanie otwarte okno właściwości projektu.

   1. W oknie dialogowym strony właściwości wybierz pozycję **Właściwości konfiguracji**  >  **Katalogi VC + +**.

   1. Kliknij strzałkę w dół w poniższych wierszach i wybierz polecenie **\<Edit>** . Dodaj następujące ścieżki:

      | Katalog | Właściwość |
      |-| - |
      | **Katalogi dołączania** | **$ (VCInstallDir) Auxiliary\VS\UnitTest\include** |
      | **Katalogi bibliotek** | **$ (VCInstallDir) Auxiliary\VS\UnitTest\lib** |

1. Dodaj plik testu jednostkowego języka C++:

   - Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **nowy element**  >  **plik C++ (. cpp)**.

## <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="object_files"></a>Aby połączyć testy z plikami obiektu lub biblioteki

Jeśli testowy kod nie eksportuje funkcji, które mają zostać przetestowane, można dodać plik Output **. obj** lub **. lib** do zależności projektu testowego. Zmodyfikuj właściwości projektu testowego, aby uwzględnić nagłówki i pliki bibliotek lub obiektów, które są wymagane do testowania jednostkowego.

1. W Eksplorator rozwiązań, w menu skrótów projektu testowego, wybierz **Właściwości**. Zostanie otwarte okno właściwości projektu.

1. Wybierz **Configuration Properties**  >  stronę dane wejściowe**konsolidatora**właściwości konfiguracji  >  **Input** , a następnie wybierz pozycję **dodatkowe zależności**.

   Wybierz pozycję **Edytuj**i Dodaj nazwy plików **obj** lub **lib** . Nie używaj pełnych nazw ścieżek.

1. Wybierz stronę **Ogólne właściwości konfiguracji**  >  **konsolidator**  >  **General** , a następnie wybierz pozycję **Dodatkowe katalogi biblioteki**.

   Wybierz pozycję **Edytuj**, a następnie dodaj ścieżkę katalogu plików **obj** lub **lib** . Ścieżka znajduje się zwykle w folderze Build w badanym projekcie.

1. Wybierz stronę katalogi **Właściwości konfiguracji**  >  **VC + +** , a następnie wybierz pozycję **Dołącz katalogi**.

   Wybierz pozycję **Edytuj**, a następnie Dodaj katalog nagłówka testowanego projektu.

## <a name="write-the-tests"></a>Napisz testy

Każdy plik *. cpp* z klasami testów musi zawierać "CppUnitTest. h" i mieć instrukcję using dla `using namespace Microsoft::VisualStudio::CppUnitTestFramework` . Projekt testowy został już skonfigurowany. Zawiera również definicję przestrzeni nazw oraz TEST_CLASS z TEST_METHOD, aby rozpocząć pracę. Możesz zmodyfikować nazwę przestrzeni nazw i nazwy w nawiasach w makrach klasy i metod.

Struktura testowa definiuje specjalne makra do inicjowania modułów testowych, klas i metod, a następnie czyszczenie zasobów po zakończeniu testów. Te makra generują kod do wykonania przed pierwszym uzyskaniem dostępu do klasy lub metody, a po ostatnim uruchomieniu testu. Aby uzyskać więcej informacji, zobacz [Inicjowanie i oczyszczanie](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup).

Użyj metod statycznych w klasie [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) , aby zdefiniować warunki testu. Użyj klasy [rejestratora](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) , aby pisać komunikaty do **okno dane wyjściowe**. Dodawanie atrybutów do metod testowych

## <a name="run-the-tests"></a>Uruchamianie testów

1. W menu **test** wybierz polecenie **Windows**  >  **Eksplorator testów**systemu Windows.

1. Jeśli nie wszystkie testy są widoczne w oknie, Skompiluj projekt testowy, klikając prawym przyciskiem myszy jego węzeł w **Eksplorator rozwiązań** i wybierając opcję **Kompiluj** lub **Kompiluj ponownie**.

1. W **Eksploratorze testów**wybierz opcję **Uruchom wszystkie**lub wybierz konkretne testy, które chcesz uruchomić. Kliknij prawym przyciskiem myszy Test, aby wyświetlić inne opcje, w tym uruchamianie go w trybie debugowania z włączonymi punktami przerwania.

1. W **okno dane wyjściowe** wybierz **testy** z listy rozwijanej, aby wyświetlić komunikaty wytworzone przez `Logger` klasę:

   ![Okno Dane wyjściowe języka C++ przedstawiające wiadomości testowe](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Zdefiniuj cechy umożliwiające grupowanie

Można zdefiniować cechy metod testowych, które umożliwiają kategoryzowanie i grupowanie testów w **Eksploratorze testów**. Aby zdefiniować cechę, użyj `TEST_METHOD_ATTRIBUTE` makra. Na przykład, aby zdefiniować cechę o nazwie `TEST_MY_TRAIT` :

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

Aby użyć zdefiniowanej cechy w testach jednostkowych:

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

### <a name="c-trait-attribute-macros"></a>Makra atrybutów cech języka C++

Następujące wstępnie zdefiniowane cechy znajdują się w temacie `CppUnitTest.h` . Aby uzyskać więcej informacji, zobacz [Microsoft Unit Test Framework for C++ — dokumentacja interfejsu API](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md).

|Makro|Opis|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Użyj makra TEST_METHOD_ATTRIBUTE, aby zdefiniować cechę.|
|`TEST_OWNER(ownerAlias)`|Użyj wstępnie zdefiniowanej cechy właściciela, aby określić właściciela metody testowej.|
|`TEST_PRIORITY(priority)`|Użyj wstępnie zdefiniowanej cechy priorytetu do przypisywania względnych priorytetów do metod testowych.|

## <a name="see-also"></a>Zobacz też

- [Szybki Start: Programowanie sterowane testami za pomocą Eksploratora testów](../test/quick-start-test-driven-development-with-test-explorer.md)
