---
title: Używanie struktury testów jednostkowych Microsoft dla języka C++
description: Użyj microsoft unit testing framework dla języka C++ do tworzenia testów jednostkowych dla kodu C++.
ms.date: 01/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 5c8cb794ce7891e74610f1a73164ce403d294925
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75755566"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Korzystanie z programu Microsoft Unit Testing Framework dla języka C++ w programie Visual Studio

Struktura testowania jednostek firmy Microsoft dla języka C++ jest domyślnie uwzględniona w programie Rozwoju pulpitu z obciążeniem **języka C++.**

## <a name="to-write-unit-tests-in-a-separate-project"></a><a name="separate_project"></a>Aby napisać testy jednostkowe w oddzielnym projekcie

Zazwyczaj można uruchomić kod testowy w swoim własnym projekcie w tym samym rozwiązaniu jako kod, który chcesz przetestować. Aby skonfigurować i skonfigurować nowy projekt testowy, zobacz [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-write-unit-tests-in-the-same-project"></a><a name="same_project"></a>Aby napisać testy jednostkowe w tym samym projekcie

W niektórych przypadkach, na przykład podczas testowania nieeksportowanych funkcji w dll, może być konieczne utworzenie testów w tym samym projekcie, co program, który testujesz. Aby napisać testy jednostkowe w tym samym projekcie:

1. Zmodyfikuj właściwości projektu, aby uwzględnić nagłówki i pliki biblioteki, które są wymagane do testowania jednostkowego.

   1. W Eksploratorze rozwiązań w menu skrótów testowego projektu wybierz polecenie **Właściwości**. Zostanie otwarte okno właściwości projektu.

   1. W oknie dialogowym Strony właściwości wybierz pozycję **Właściwości** > konfiguracji**VC++ Katalogi**.

   1. Kliknij strzałkę w dół w kolejnych wierszach i wybierz pozycję ** \<Edytuj>**. Dodaj następujące ścieżki:

      | Katalog | Właściwość |
      |-| - |
      | **Uwzględnij katalogi** | **$(VCInstallDir)Pomocniczy\VS\UnitTest\include** |
      | **Katalogi bibliotek** | **$(VCInstallDir)Pomocniczy\VS\UnitTest\lib** |

1. Dodaj plik testu jednostki języka C++:

   - Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań** i wybierz pozycję **Dodaj** > nowy plik**C++ (.cpp)****New Item** > .

## <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="object_files"></a>Aby połączyć testy z plikami obiektu lub biblioteki

Jeśli testowany kod nie eksportuje funkcji, które chcesz przetestować, można dodać wyjściowy plik **obj** lub **lib** do zależności projektu testowego. Zmodyfikuj właściwości projektu testowego, aby uwzględnić nagłówki i pliki biblioteki lub obiektów, które są wymagane do testowania jednostkowego.

1. W Eksploratorze rozwiązań w menu skrótów projektu testowego wybierz polecenie **Właściwości**. Zostanie otwarte okno właściwości projektu.

1. Wybierz stronę**Wprowadzanie** **konsolidatora** >  >  **właściwości konfiguracji,** a następnie wybierz pozycję Dodatkowe **zależności**.

   Wybierz **polecenie Edytuj**i dodaj nazwy plików **obj** lub **lib.** Nie używaj pełnych nazw ścieżek.

1. Wybierz stronę**Ogólne**  > **konsolidatora** >  **właściwości konfiguracji,** a następnie wybierz pozycję **Dodatkowe katalogi bibliotek**.

   Wybierz **polecenie Edytuj**i dodaj ścieżkę katalogu plików **obj** lub **lib.** Ścieżka jest zazwyczaj w folderze kompilacji projektu w ramach testu.

1. Wybierz stronę **Właściwości** > konfiguracji**VC++Katalogi,** a następnie wybierz pozycję **Uwzględnij katalogi**.

   Wybierz **polecenie Edytuj**, a następnie dodaj katalog nagłówka testowego projektu.

## <a name="write-the-tests"></a>Napisz testy

Każdy plik *.cpp* z klasami testowym musi zawierać "CppUnitTest.h" i mieć instrukcję using dla `using namespace Microsoft::VisualStudio::CppUnitTestFramework`. Projekt testowy jest już skonfigurowany dla Ciebie. Zawiera również definicję obszaru nazw i TEST_CLASS z TEST_METHOD, aby rozpocząć. Można zmodyfikować nazwę obszaru nazw i nazwy w nawiasach w makrach klasy i metody.

Struktura testów definiuje specjalne makra do inicjowania modułów testowych, klas i metod oraz do oczyszczania zasobów po zakończeniu testów. Te makra generują kod do wykonania przed pierwszym dostępem do klasy lub metody i po uruchomieniu ostatniego testu. Aby uzyskać więcej informacji, zobacz [Inicjowanie i oczyszczanie](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup).

Użyj metod statycznych w [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) klasy do definiowania warunków testu. Użyj [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) klasy do pisania wiadomości do **okna wyjściowego**. Dodawanie atrybutów do metod testowych

## <a name="run-the-tests"></a>Uruchamianie testów

1. W menu **Test** wybierz polecenie**Eksplorator testów** **systemu Windows** > .

1. Jeśli nie wszystkie testy są widoczne w oknie, skompiluj projekt testowy, klikając prawym przyciskiem myszy jego węzeł w **Eksploratorze rozwiązań** i wybierając polecenie **Buduj** lub **przebudowuj**.

1. W **Eksploratorze testów**wybierz pozycję **Uruchom wszystko**lub wybierz konkretne testy, które chcesz uruchomić. Kliknij prawym przyciskiem myszy test dla innych opcji, w tym uruchamianie go w trybie debugowania z włączonymi punktami przerwania.

1. W **oknie wyjściowym** wybierz **testy** z listy rozwijanej, `Logger` aby wyświetlić komunikaty wypisane przez klasę:

   ![Okno wyjściowe języka C++ z komunikatami testowymi](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Definiowanie cech umożliwiających grupowanie

Można zdefiniować cechy metod testowych, które umożliwiają kategoryzowanie i grupowanie testów w **Eksploratorze testów.** Aby zdefiniować cechę, `TEST_METHOD_ATTRIBUTE` użyj makra. Na przykład, aby zdefiniować `TEST_MY_TRAIT`cechę o nazwie:

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

### <a name="c-trait-attribute-macros"></a>Makra atrybutów cechy języka C++

Następujące wstępnie zdefiniowane cechy znajdują `CppUnitTest.h`się w pliku . Aby uzyskać więcej informacji, zobacz [Microsoft Unit Testing Framework for C++ API reference](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md).

|Makro|Opis|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Użyj makra TEST_METHOD_ATTRIBUTE, aby zdefiniować cechę.|
|`TEST_OWNER(ownerAlias)`|Użyj wstępnie zdefiniowanej cechy Owner, aby określić właściciela metody testowej.|
|`TEST_PRIORITY(priority)`|Użyj wstępnie zdefiniowanej cechy priorytetu, aby przypisać względne priorytety do metod testowych.|

## <a name="see-also"></a>Zobacz też

- [Szybki start: program rozwoju oparty na testach za pomocą Eksploratora testów](../test/quick-start-test-driven-development-with-test-explorer.md)
