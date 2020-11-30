---
title: Zapisz testy jednostkowe dla bibliotek DLL języka C++
description: Poznaj kilka sposobów testowania kodu DLL, w zależności od tego, czy biblioteka DLL eksportuje funkcje, które chcesz przetestować.
ms.custom: SEO-VS-2020
ms.date: 05/01/2019
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: b7eb7b7be524e20ca87c70c3f1f771f4f8a01141
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328629"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Napisz testy jednostkowe dla bibliotek DLL języka C++ w programie Visual Studio

Istnieje kilka sposobów testowania kodu DLL, w zależności od tego, czy eksportuje funkcje, które chcesz przetestować. Wybierz jedną z następujących metod:

**Testy jednostkowe tylko wywołują funkcje wyeksportowane z biblioteki dll:** Dodaj osobny projekt testowy, zgodnie z opisem w temacie [Napisz testy jednostkowe dla C/C++](writing-unit-tests-for-c-cpp.md). W projekcie testowym Dodaj odwołanie do projektu DLL.

Przejdź do procedury, [Aby odwołać się do funkcji wyeksportowanych z projektu DLL](#projectRef).

**Biblioteka DLL została skompilowana jako plik. exe:** Dodaj osobny projekt testowy. Połącz je z plikiem obiektu wyjściowego.

Przejdź do procedury, [Aby połączyć testy z plikami obiektu lub biblioteki](#objectRef).

**Testy jednostkowe wywołują funkcje nieczłonkowskie, które nie zostały wyeksportowane z biblioteki DLL, a Biblioteka DLL może być skompilowana jako Biblioteka statyczna:** Zmień projekt DLL tak, aby był kompilowany do pliku *. lib* . Dodaj oddzielny projekt testowy odwołujący się do testowanego projektu.

Takie podejście ma na celu umożliwienie testom korzystania z wyeksportowanych elementów członkowskich, ale nadal prowadzi testy w osobnym projekcie.

Przejdź do procedury, [Aby zmienić dll na bibliotekę statyczną](#staticLink).

**Testy jednostkowe muszą wywoływać funkcje nieczłonkowskie, które nie zostały wyeksportowane, a kod musi być skompilowany jako biblioteka dołączana dynamicznie (dll):** Dodaj testy jednostkowe w tym samym projekcie, w którym znajduje się kod produktu.

Przejdź do procedury, [Aby dodać testy jednostkowe w tym samym projekcie](#sameProject).

## <a name="create-the-tests"></a>Tworzenie testów

### <a name="to-change-the-dll-to-a-static-library"></a><a name="staticLink"></a> Aby zmienić DLL na bibliotekę statyczną

- Jeśli testy muszą używać elementów członkowskich, które nie są eksportowane przez projekt DLL, a badany projekt jest skompilowany jako Biblioteka dynamiczna, Rozważ przekonwertowanie go na bibliotekę statyczną.

  1. W **Eksplorator rozwiązań** w menu skrótów testowanego projektu wybierz polecenie **Właściwości**. Zostanie otwarte okno **Właściwości** projektu.

  2. Wybierz pozycję **Właściwości konfiguracji**  >  **Ogólne**.

  3. Ustaw **Typ konfiguracji** na **bibliotekę statyczną (. lib)**.

  Kontynuuj procedurę [łączenia testów z plikami obiektów lub bibliotek](#objectRef).

### <a name="to-reference-exported-dll-functions-from-the-test-project"></a><a name="projectRef"></a> Aby odwołać się do wyeksportowanych funkcji DLL z projektu testowego

- Jeśli projekt DLL eksportuje funkcje, które chcesz przetestować, możesz dodać odwołanie do projektu kodu z projektu testowego.

  1. Utwórz natywny projekt testów jednostkowych.

      ::: moniker range="vs-2019"

      1. W menu **plik** wybierz pozycję **Nowy**  >  **projekt**. W oknie dialogowym **Dodawanie nowego projektu** Ustaw **Język** na C++ i wpisz "test" w polu wyszukiwania. Następnie wybierz **natywny projekt testów jednostkowych**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. W menu **plik** wybierz pozycję **Nowy** > **projekt** > **Visual C++** > **Testuj** > **projekt testu jednostkowego w języku C++**.

      ::: moniker-end

  1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt testowy, a następnie wybierz polecenie **Dodaj**  >  **odwołanie**.

  1. Wybierz pozycję **projekty**, a następnie projekt do przetestowania.

       Wybierz przycisk **Dodaj**.

  1. We właściwościach projektu testowego Dodaj lokalizację testowanego projektu do katalogów include.

       Wybierz kolejno pozycje **Właściwości konfiguracji**  >  **Katalogi VC + +**  >  **Include Directories**.

       Wybierz pozycję **Edytuj**, a następnie Dodaj katalog nagłówka testowanego projektu.

  Przejdź do pozycji [Napisz testy jednostkowe](#addTests).

### <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="objectRef"></a> Aby połączyć testy z plikami obiektu lub biblioteki

- Jeśli biblioteka DLL nie eksportuje funkcji, które mają zostać przetestowane, można dodać plik Output *. obj* lub *. lib* do zależności projektu testowego.

  1. Utwórz natywny projekt testów jednostkowych.

      ::: moniker range="vs-2019"

      1. W menu **plik** wybierz pozycję **Nowy**  >  **projekt**. W oknie dialogowym **Dodawanie nowego projektu** Ustaw **Język** na C++ i wpisz "test" w polu wyszukiwania. Następnie wybierz **natywny projekt testów jednostkowych**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. W menu **plik** wybierz pozycję **Nowy** > **projekt** > **Visual C++** > **Testuj** > **projekt testu jednostkowego w języku C++**.

      ::: moniker-end

  2. W **Eksplorator rozwiązań**, w menu skrótów projektu testowego, wybierz **Właściwości**.

  3. Wybierz **Właściwości konfiguracji**  >  **konsolidator**  >  **wprowadzanie**  >  **dodatkowych zależności**.

       Wybierz pozycję **Edytuj** i Dodaj nazwy plików **obj** lub **lib** . Nie używaj pełnych nazw ścieżek.

  4. Wybierz **Właściwości konfiguracji**  >  **konsolidator**  >  **Ogólne**  >  **Dodatkowe katalogi biblioteki**.

       Wybierz pozycję **Edytuj**, a następnie dodaj ścieżkę katalogu plików **obj** lub **lib** . Ścieżka znajduje się zwykle w folderze Build w badanym projekcie.

  5. Wybierz kolejno pozycje **Właściwości konfiguracji**  >  **Katalogi VC + +**  >  **Include Directories**.

       Wybierz pozycję **Edytuj**, a następnie Dodaj katalog nagłówka testowanego projektu.

  Przejdź do pozycji [Napisz testy jednostkowe](#addTests).

### <a name="to-add-unit-tests-in-the-same-project"></a><a name="sameProject"></a> Aby dodać testy jednostkowe w tym samym projekcie

1. Zmodyfikuj właściwości projektu kodu produktu w celu uwzględnienia nagłówków i plików bibliotek, które są wymagane do testowania jednostkowego.

   1. W **Eksplorator rozwiązań** w menu skrótów testowanego projektu wybierz polecenie **Właściwości**. Zostanie otwarte okno **Właściwości** projektu.

   2. Wybierz pozycję **Właściwości konfiguracji**  >  **Katalogi VC + +**.

   3. Edytuj katalogi dołączania i biblioteki:

       |Katalog|Właściwość|
       |-|-|
       |**Katalogi dołączania** | **$ (VCInstallDir) UnitTest\include; $ (IncludePath)**|
       |**Katalogi bibliotek** | **$ (VCInstallDir) UnitTest\lib; $ (LibraryPath)**|

2. Dodaj plik testu jednostkowego języka C++:

   - W **Eksplorator rozwiązań** w menu skrótów projektu wybierz pozycję **Dodaj**  >  **nowy element**  >  **test jednostkowy C++**.

   Przejdź do pozycji [Napisz testy jednostkowe](#addTests).

## <a name="write-the-unit-tests"></a><a name="addTests"></a> Napisz testy jednostkowe

1. W każdym pliku kodu testu jednostkowego Dodaj `#include` instrukcję do nagłówków w badanym projekcie.

2. Dodaj klasy testowe i metody do plików kodu testu jednostkowego. Przykład:

    ```cpp
    #include "stdafx.h"
    #include "CppUnitTest.h"
    #include "MyProjectUnderTest.h"
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;
    namespace MyTest
    {
      TEST_CLASS(MyTests)
      {
      public:
          TEST_METHOD(MyTestMethod)
          {
              Assert::AreEqual(MyProject::Multiply(2,3), 6);
          }
      };
    }
    ```

## <a name="run-the-tests"></a>Uruchamianie testów

1. W menu **test** wybierz polecenie **Windows**  >  **Eksplorator testów** systemu Windows.

1. Jeśli wszystkie testy nie są widoczne w oknie, Skompiluj projekt testowy, klikając prawym przyciskiem myszy jego węzeł w **Eksplorator rozwiązań** i wybierając opcję **Kompiluj** lub **Kompiluj ponownie**.

1. W **Eksploratorze testów** wybierz opcję **Uruchom wszystkie** lub wybierz konkretne testy, które chcesz uruchomić. Kliknij prawym przyciskiem myszy Test, aby wyświetlić inne opcje, w tym uruchamianie go w trybie debugowania z włączonymi punktami przerwania.

## <a name="see-also"></a>Zobacz też

- [Zapisz testy jednostkowe dla C/C++](writing-unit-tests-for-c-cpp.md)
- [Dokumentacja interfejsu API Microsoft. VisualStudio. TestTools. CppUnitTestFramework](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Przewodnik: Tworzenie i używanie biblioteki dołączanej dynamicznie (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Importowanie i eksportowanie](/cpp/build/importing-and-exporting)
- [Szybki Start: Programowanie sterowane testami za pomocą Eksploratora testów](../test/quick-start-test-driven-development-with-test-explorer.md)
