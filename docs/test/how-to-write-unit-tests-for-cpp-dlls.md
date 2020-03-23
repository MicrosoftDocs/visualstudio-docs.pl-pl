---
title: Zapis testów jednostkowych dla bibliotek DLL języka C++
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 856bc21fdee8945ddcd97e3978f46af0008af616
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279276"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Zapisywanie testów jednostkowych bibliotek DLL języka C++ w programie Visual Studio

Istnieje kilka sposobów testowania kodu DLL, w zależności od tego, czy eksportuje funkcje, które chcesz przetestować. Wybierz jeden z następujących sposobów:

**Testy jednostkowe wywołują tylko funkcje, które są eksportowane z biblioteki DLL:** Dodaj oddzielny projekt testowy, zgodnie z opisem w [write testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md). W projekcie testowym dodaj odwołanie do projektu biblioteki DLL.

Przejdź do procedury [Aby odwołać się do eksportowanych funkcji z projektu biblioteki DLL](#projectRef).

**Biblioteka DLL jest zbudowana jako plik exe:** Dodaj oddzielny projekt testowy. Połącz go z plikiem obiektu wyjściowego.

Przejdź do procedury [Aby połączyć testy z plikami obiektu lub biblioteki](#objectRef).

**Testy jednostkowe wywołanie funkcji niebędących członkami, które nie są eksportowane z biblioteki DLL, a biblioteka DLL może być zbudowana jako biblioteka statyczna:** Zmień projekt biblioteki DLL tak, aby był kompilowany do pliku *lib.* Dodaj oddzielny projekt testowy, który odwołuje się do projektu w ramach testu.

Takie podejście ma tę zaletę, zezwalając testom na używanie nieeksportowanych elementów członkowskich, ale nadal przechowuje testy w osobnym projekcie.

Przejdź do procedury [Aby zmienić bibliotekę DLL na bibliotekę statyczną](#staticLink).

**Testy jednostkowe muszą wywoływać funkcje niebędące elementami członkowskimi, które nie są eksportowane, a kod musi być utworzony jako biblioteka łączy dynamicznych (DLL):** Dodaj testy jednostkowe w tym samym projekcie co kod produktu.

Przejdź do procedury [Aby dodać testy jednostkowe w tym samym projekcie](#sameProject).

## <a name="create-the-tests"></a>Tworzenie testów

### <a name="to-change-the-dll-to-a-static-library"></a><a name="staticLink"></a>Aby zmienić bibliotekę DLL na bibliotekę statyczną

- Jeśli testy muszą używać elementów członkowskich, które nie są eksportowane przez projekt biblioteki DLL, a projekt w fazie testów jest zbudowany jako biblioteka dynamiczna, należy rozważyć przekonwertowanie go do biblioteki statycznej.

  1. W **Eksploratorze rozwiązań**w menu skrótów testowego projektu wybierz polecenie **Właściwości**. Zostanie otwarte okno **Właściwości** projektu.

  2. Wybierz polecenie **Właściwości konfiguracyjne** > **ogólne**.

  3. Ustaw **typ konfiguracji** na **Biblioteka statyczna (lib)**.

  Przejdź do procedury [Aby połączyć testy z plikami obiektu lub biblioteki](#objectRef).

### <a name="to-reference-exported-dll-functions-from-the-test-project"></a><a name="projectRef"></a>Aby odwołać się do eksportowanych funkcji biblioteki DLL z projektu testowego

- Jeśli projekt DLL eksportuje funkcje, które chcesz przetestować, można dodać odwołanie do projektu kodu z projektu testowego.

  1. Utwórz natywny projekt testu jednostkowego.

      ::: moniker range="vs-2019"

      1. W menu **Plik** wybierz polecenie **Nowy** > **projekt**. W oknie **dialogowym Dodaj nowy projekt** ustaw **język** na C++ i wpisz "test" w polu wyszukiwania. Następnie wybierz projekt **testu jednostki macierzystej**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. W menu **Plik** wybierz polecenie **Nowy** > **projekt** > **Visual C++** > **Test** > **C++ Unit Test Project**.

      ::: moniker-end

  1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt testowy, a następnie wybierz polecenie **Dodaj** > **odwołanie**.

  1. Wybierz opcję **Projekty**, a następnie projekt, który ma zostać przetestowany.

       Wybierz przycisk **Dodaj**.

  1. We właściwościach projektu testowego dodaj lokalizację testowego projektu do katalogu dołącz.

       Wybierz polecenie Właściwości konfiguracji > **VC++ Katalogi** > **zawierają katalogi**. **Configuration Properties**

       Wybierz **polecenie Edytuj**, a następnie dodaj katalog nagłówka testowego projektu.

  Przejdź do [strony Napisz testy jednostkowe](#addTests).

### <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="objectRef"></a>Aby połączyć testy z plikami obiektu lub biblioteki

- Jeśli biblioteka DLL nie eksportuje funkcji, które chcesz przetestować, można dodać wyjściowy plik *obj* lub *lib* do zależności projektu testowego.

  1. Utwórz natywny projekt testu jednostkowego.

      ::: moniker range="vs-2019"

      1. W menu **Plik** wybierz polecenie **Nowy** > **projekt**. W oknie **dialogowym Dodaj nowy projekt** ustaw **język** na C++ i wpisz "test" w polu wyszukiwania. Następnie wybierz projekt **testu jednostki macierzystej**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. W menu **Plik** wybierz polecenie **Nowy** > **projekt** > **Visual C++** > **Test** > **C++ Unit Test Project**.

      ::: moniker-end

  2. W **Eksploratorze rozwiązań**w menu skrótów projektu testowego wybierz polecenie **Właściwości**.

  3. Wybierz pozycję **Właściwości konfiguracji Dodatkowe** > zależności**wejściowe konsolidatora** > **Additional Dependencies****Linker** > .

       Wybierz **polecenie Edytuj**i dodaj nazwy plików **obj** lub **lib.** Nie należy używać pełnych nazw ścieżek.

  4. Wybierz pozycję Właściwości**General** > konfiguracji **Dodatkowe katalogi** > **biblioteki****.** > 

       Wybierz **polecenie Edytuj**i dodaj ścieżkę katalogu plików **obj** lub **lib.** Ścieżka jest zazwyczaj w folderze kompilacji projektu w ramach testu.

  5. Wybierz polecenie Właściwości konfiguracji > **VC++ Katalogi** > **zawierają katalogi**. **Configuration Properties**

       Wybierz **polecenie Edytuj**, a następnie dodaj katalog nagłówka testowego projektu.

  Przejdź do [strony Napisz testy jednostkowe](#addTests).

### <a name="to-add-unit-tests-in-the-same-project"></a><a name="sameProject"></a>Aby dodać testy jednostkowe w tym samym projekcie

1. Zmodyfikuj właściwości projektu kodu produktu, aby uwzględnić nagłówki i pliki biblioteki, które są wymagane do testowania jednostkowego.

   1. W **Eksploratorze rozwiązań**w menu skrótów testowego projektu wybierz polecenie **Właściwości**. Zostanie otwarte okno **Właściwości** projektu.

   2. Wybierz **pozycję Właściwości** > konfiguracji**VC++ Katalogi**.

   3. Edytuj katalogi Dołączania i Biblioteki:

       |Katalog|Właściwość|
       |-|-|
       |**Uwzględnij katalogi** | **$(VCInstallDir)UnitTest\include;$(IncludePath)**|
       |**Katalogi bibliotek** | **$(VCInstallDir)UnitTest\lib;$(Ścieżka bibliotek)**|

2. Dodaj plik testu jednostki języka C++:

   - W **Eksploratorze rozwiązań**w menu skrótów projektu wybierz polecenie **Dodaj** > **nowy element** > **C++ Test jednostkowy**.

   Przejdź do [strony Napisz testy jednostkowe](#addTests).

## <a name="write-the-unit-tests"></a><a name="addTests"></a>Napisz testy jednostkowe

1. W każdym pliku kodu testu `#include` jednostkowego dodaj instrukcję dla nagłówków testowego projektu.

2. Dodaj klasy i metody testów do plików kodu testu jednostkowego. Przykład:

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

1. W menu **Test** wybierz polecenie**Eksplorator testów** **systemu Windows** > .

1. Jeśli wszystkie testy nie są widoczne w oknie, skompiluj projekt testowy, klikając prawym przyciskiem myszy jego węzeł w **Eksploratorze rozwiązań** i wybierając polecenie **Buduj** lub **przebudowuj**.

1. W **Eksploratorze testów**wybierz pozycję **Uruchom wszystko**lub wybierz konkretne testy, które chcesz uruchomić. Kliknij prawym przyciskiem myszy test dla innych opcji, w tym uruchamianie go w trybie debugowania z włączonymi punktami przerwania.

## <a name="see-also"></a>Zobacz też

- [Zapis testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)
- [Odwołanie do interfejsu API Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Przewodnik: Tworzenie i używanie biblioteki łączy dynamicznych (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Import i eksport](/cpp/build/importing-and-exporting)
- [Szybki start: program rozwoju oparty na testach za pomocą Eksploratora testów](../test/quick-start-test-driven-development-with-test-explorer.md)
