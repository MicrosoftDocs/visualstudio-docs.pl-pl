---
title: Pisanie testów jednostkowych dla bibliotek DLL języka C++
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 856bc21fdee8945ddcd97e3978f46af0008af616
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77279276"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Pisanie testów jednostkowych dla bibliotek DLL C++ w programie Visual Studio

Istnieje kilka sposobów, aby przetestować kod biblioteki DLL, w zależności od tego, czy eksportuje ona funkcje, które mają zostać przetestowane. Wybierz jedną z następujących sposobów:

**Testy jednostkowe tylko wywołują funkcje wyeksportowane z biblioteki dll:** Dodaj oddzielny projekt testowy, zgodnie z opisem w temacie [Napisz testyC++jednostkowe dla C/](writing-unit-tests-for-c-cpp.md). W projekcie testowym Dodaj odwołanie do projektu biblioteki DLL.

Przejdź do procedury, [Aby odwołać się do funkcji wyeksportowanych z projektu DLL](#projectRef).

**Biblioteka DLL została skompilowana jako plik. exe:** Dodaj osobny projekt testowy. Połącz go z wyjściowym plikiem obiektu.

Przejdź do procedury, [Aby połączyć testy z plikami obiektu lub biblioteki](#objectRef).

**Testy jednostkowe wywołują funkcje nieczłonkowskie, które nie zostały wyeksportowane z biblioteki DLL, a Biblioteka DLL może być skompilowana jako Biblioteka statyczna:** Zmień projekt DLL tak, aby był kompilowany do pliku *. lib* . Dodaj osobny projekt testów, który odwołuje się do testowanego projektu.

Takie podejście ma tę zaletę umożliwia testom używać członkowie wyeksportowane, ale nadal utrzymuje testy w osobnym projekcie.

Przejdź do procedury, [Aby zmienić dll na bibliotekę statyczną](#staticLink).

**Testy jednostkowe muszą wywoływać funkcje nieczłonkowskie, które nie zostały wyeksportowane, a kod musi być skompilowany jako biblioteka dołączana dynamicznie (dll):** Dodaj testy jednostkowe w tym samym projekcie, w którym znajduje się kod produktu.

Przejdź do procedury, [Aby dodać testy jednostkowe w tym samym projekcie](#sameProject).

## <a name="create-the-tests"></a>Tworzenie testów

### <a name="staticLink"></a>Aby zmienić DLL na bibliotekę statyczną

- Jeśli testy muszą użyć elementów członkowskich, które nie są eksportowane przez projekt DLL i projekt testowany jest kompilowany jako biblioteka dynamiczna, należy wziąć pod uwagę podczas konwertowania go do biblioteki statycznej.

  1. W **Eksplorator rozwiązań**w menu skrótów testowanego projektu wybierz polecenie **Właściwości**. Zostanie otwarte okno **Właściwości** projektu.

  2. Wybierz **Właściwości konfiguracji** > **Ogólne**.

  3. Ustaw **Typ konfiguracji** na **bibliotekę statyczną (. lib)** .

  Kontynuuj procedurę [łączenia testów z plikami obiektów lub bibliotek](#objectRef).

### <a name="projectRef"></a>Aby odwołać się do wyeksportowanych funkcji DLL z projektu testowego

- Jeśli projekt DLL eksportuje funkcje, które mają zostać przetestowane, można dodać odwołanie do projektu kodu z projektu testowego.

  1. Utwórz natywny projekt testów jednostkowych.

      ::: moniker range="vs-2019"

      1. W menu **plik** wybierz **Nowy** **projekt** > . W oknie dialogowym **Dodawanie nowego projektu** Ustaw **Język** na C++ i wpisz "test" w polu wyszukiwania. Następnie wybierz **natywny projekt testów jednostkowych**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. W menu **plik** wybierz kolejno pozycje nowy **projekt > Project** >  **C++ Visual** > **test** >  **C++ jednostki test jednostkowy**.

      ::: moniker-end

  1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt testowy, a następnie wybierz polecenie **Dodaj** > **odwołanie**.

  1. Wybierz pozycję **projekty**, a następnie projekt do przetestowania.

       Wybierz przycisk **Dodaj** .

  1. W oknie właściwości dla projektu testów Dodaj lokalizację testowanego projektu Dołącz katalogi.

       Wybierz pozycję **Właściwości konfiguracji** > **Katalogi VC + +**  > **Uwzględnij katalogi**.

       Wybierz pozycję **Edytuj**, a następnie Dodaj katalog nagłówka testowanego projektu.

  Przejdź do pozycji [Napisz testy jednostkowe](#addTests).

### <a name="objectRef"></a>Aby połączyć testy z plikami obiektu lub biblioteki

- Jeśli biblioteka DLL nie eksportuje funkcji, które mają zostać przetestowane, można dodać plik Output *. obj* lub *. lib* do zależności projektu testowego.

  1. Utwórz natywny projekt testów jednostkowych.

      ::: moniker range="vs-2019"

      1. W menu **plik** wybierz **Nowy** **projekt** > . W oknie dialogowym **Dodawanie nowego projektu** Ustaw **Język** na C++ i wpisz "test" w polu wyszukiwania. Następnie wybierz **natywny projekt testów jednostkowych**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. W menu **plik** wybierz kolejno pozycje nowy **projekt > Project** >  **C++ Visual** > **test** >  **C++ jednostki test jednostkowy**.

      ::: moniker-end

  2. W **Eksplorator rozwiązań**, w menu skrótów projektu testowego, wybierz **Właściwości**.

  3. Wybierz **Właściwości konfiguracji** > **konsolidator** > **dane wejściowe** > **dodatkowe zależności**.

       Wybierz pozycję **Edytuj**i Dodaj nazwy plików **obj** lub **lib** . Nie należy używać nazw pełnej ścieżki.

  4. Wybierz **Właściwości konfiguracji** > **konsolidator** > **Ogólne** > **Dodatkowe katalogi biblioteki**.

       Wybierz pozycję **Edytuj**, a następnie dodaj ścieżkę katalogu plików **obj** lub **lib** . Ścieżka zazwyczaj mieści się w folderze kompilacji testowanego projektu.

  5. Wybierz pozycję **Właściwości konfiguracji** > **Katalogi VC + +**  > **Uwzględnij katalogi**.

       Wybierz pozycję **Edytuj**, a następnie Dodaj katalog nagłówka testowanego projektu.

  Przejdź do pozycji [Napisz testy jednostkowe](#addTests).

### <a name="sameProject"></a>Aby dodać testy jednostkowe w tym samym projekcie

1. Zmodyfikuj właściwości projektu kodu produktu, aby uwzględnić pliki nagłówkowe i bibliotek, które są wymagane dla testów jednostkowych.

   1. W **Eksplorator rozwiązań**w menu skrótów testowanego projektu wybierz polecenie **Właściwości**. Zostanie otwarte okno **Właściwości** projektu.

   2. Wybierz **Właściwości konfiguracji** > **katalogów VC + +** .

   3. Edytuj katalogi dołączonych i bibliotek:

       |Katalog|Właściwość|
       |-|-|
       |**Katalogi dołączania** | **$ (VCInstallDir) UnitTest\include; $ (IncludePath)**|
       |**Katalogi bibliotek** | **$ (VCInstallDir) UnitTest\lib; $ (LibraryPath)**|

2. Dodaj plik testu jednostkowego języka C++:

   - W **Eksplorator rozwiązań**, w menu skrótów projektu, wybierz **Dodaj** > **nowy element** >  **C++ test jednostkowy**.

   Przejdź do pozycji [Napisz testy jednostkowe](#addTests).

## <a name="addTests"></a>Napisz testy jednostkowe

1. W każdym pliku kodu testu jednostkowego Dodaj instrukcję `#include` dla nagłówków testowanego projektu.

2. Dodaj klasy testów i metody do plików testów jednostkowych kodu. Na przykład:

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

## <a name="run-the-tests"></a>Uruchom testy

1. W menu **test** wybierz pozycję **Windows** > **Test Explorer**.

1. Jeśli wszystkie testy nie są widoczne w oknie, Skompiluj projekt testowy, klikając prawym przyciskiem myszy jego węzeł w **Eksplorator rozwiązań** i wybierając opcję **Kompiluj** lub **Kompiluj ponownie**.

1. W **Eksploratorze testów**wybierz opcję **Uruchom wszystkie**lub wybierz konkretne testy, które chcesz uruchomić. Kliknij prawym przyciskiem myszy na test dla innych opcji, w tym uruchamianie w trybie debugowania, z punktami przerwania jest włączony.

## <a name="see-also"></a>Zobacz też

- [Zapisz testy jednostkowe dla C/C++](writing-unit-tests-for-c-cpp.md)
- [Dokumentacja interfejsu API Microsoft. VisualStudio. TestTools. CppUnitTestFramework](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Przewodnik: Tworzenie i używanie biblioteki dołączanej dynamicznieC++()](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Importowanie i eksportowanie](/cpp/build/importing-and-exporting)
- [Szybki Start: Programowanie sterowane testami za pomocą Eksploratora testów](../test/quick-start-test-driven-development-with-test-explorer.md)
