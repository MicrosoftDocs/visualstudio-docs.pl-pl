---
title: Pisanie testów jednostkowych dla bibliotek DLL języka C++
ms.date: 11/04/2017
ms.topic: conceptual
ms.author: mblome
manager: jillfra
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 7606f9f9b521d4bc752b99ad70237ef4ac6bc30e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103264"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Pisanie testów jednostkowych dla bibliotek DLL C++ w programie Visual Studio

 Istnieje kilka sposobów, aby przetestować kod biblioteki DLL, w zależności od tego, czy eksportuje ona funkcje, które mają zostać przetestowane. Wybierz jedną z następujących sposobów:

 **Testy jednostkowe wywołać tylko funkcje, które są eksportowane z biblioteki DLL:** Dodaj osobny projekt testów, zgodnie z opisem w [pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md). W projekcie testowym Dodaj odwołanie do projektu biblioteki DLL.

 Przejdź do procedury [można odwoływać się do eksportowanych funkcji z projektu DLL](#projectRef).

 **Biblioteka DLL jest kompilowany jako plik .exe:** Dodaj osobny projekt testów. Połącz go z wyjściowym plikiem obiektu.

 Przejdź do procedury [połączyć testy z plikami obiektu lub biblioteki](#objectRef).

 **Funkcje nieczłonkowskie wywołanie testy jednostki, które nie są eksportowane z biblioteki DLL i biblioteką DLL może być kompilowany jako biblioteka statyczna:** Zmień projekt DLL tak, aby był skompilowany do *.lib* pliku. Dodaj osobny projekt testów, który odwołuje się do testowanego projektu.

 Takie podejście ma tę zaletę umożliwia testom używać członkowie wyeksportowane, ale nadal utrzymuje testy w osobnym projekcie.

 Przejdź do procedury [zmienić bibliotekę DLL do biblioteki statycznej](#staticLink).

 **Testy jednostkowe muszą wywoływać funkcje nieczłonkowskie, które nie są eksportowane, a kod musi być kompilowany jako biblioteka dołączana dynamicznie (DLL):** Dodawanie testów jednostkowych w tym samym projekcie, co kod produktu.

 Przejdź do procedury [Aby dodać testy jednostkowe w tym samym projekcie](#sameProject).

## <a name="create-the-tests"></a>Tworzenie testów

### <a name="staticLink"></a> Aby zmienić bibliotekę DLL do biblioteki statycznej

- Jeśli testy muszą użyć elementów członkowskich, które nie są eksportowane przez projekt DLL i projekt testowany jest kompilowany jako biblioteka dynamiczna, należy wziąć pod uwagę podczas konwertowania go do biblioteki statycznej.

  1. W **Eksploratora rozwiązań**, w menu skrótów testowanego projektu, wybierz **właściwości**. Projekt **właściwości** zostanie otwarte okno.

  2. Wybierz **właściwości konfiguracji** > **ogólne**.

  3. Ustaw **typu konfiguracji** do **biblioteka statyczna (.lib)**.

  Przejdź do procedury [połączyć testy z plikami obiektu lub biblioteki](#objectRef).

### <a name="projectRef"></a> Aby odwołać się do eksportowanych funkcji DLL z projektu testowego

- Jeśli projekt DLL eksportuje funkcje, które mają zostać przetestowane, można dodać odwołanie do projektu kodu z projektu testowego.

  1. Utwórz natywny projekt testów jednostkowych.

      1. Na **pliku** menu, wybierz **New** > **projektu** > **Visual C++**  >  **Testu** > **projekt testu jednostkowego w języku C++**.

  2. W **Eksploratora rozwiązań**, w menu skrótów projektu testów wybierz **odwołania**. Projekt **właściwości** zostanie otwarte okno.

  3. Wybierz **wspólne właściwości** > **szablon i odwołania**, a następnie wybierz **Dodaj nowe odwołanie** przycisku.

  4. Wybierz **projektów**, a następnie projekt ma zostać przetestowana.

       Wybierz **Dodaj** przycisku.

  5. W oknie właściwości dla projektu testów Dodaj lokalizację testowanego projektu Dołącz katalogi.

       Wybierz **właściwości konfiguracji** > **katalogi VC ++** > **katalogi plików nagłówkowych**.

       Wybierz **Edytuj**, a następnie Dodaj nagłówek katalogu testowanego projektu.

  Przejdź do [pisanie testów jednostkowych](#addTests).

### <a name="objectRef"></a> Aby powiązać testy z plikami obiektu lub biblioteki

- Jeśli biblioteka DLL nie eksportuje funkcji, które chcesz przetestować, możesz dodać dane wyjściowe *.obj* lub *.lib* pliku do zależności testowanego projektu testowego.

  1. Utwórz natywny projekt testów jednostkowych.

      1. Na **pliku** menu, wybierz **New** > **projektu** > **Visual C++**  >  **Testu** > **natywny projekt testów jednostkowych**.

  2. W **Eksploratora rozwiązań**, w menu skrótów projektu testów wybierz **właściwości**.

  3. Wybierz **właściwości konfiguracji** > **konsolidatora** > **dane wejściowe** > **dodatkowe zależności**.

       Wybierz **Edytuj**i Dodaj nazwy **.obj** lub **.lib** plików. Nie należy używać nazw pełnej ścieżki.

  4. Wybierz **właściwości konfiguracji** > **konsolidatora** > **ogólne** > **dodatkowe katalogi biblioteki** .

       Wybierz **Edytuj**i Dodaj ścieżkę katalogu **.obj** lub **.lib** plików. Ścieżka zazwyczaj mieści się w folderze kompilacji testowanego projektu.

  5. Wybierz **właściwości konfiguracji** > **katalogi VC ++** > **katalogi plików nagłówkowych**.

       Wybierz **Edytuj**, a następnie Dodaj nagłówek katalogu testowanego projektu.

  Przejdź do [pisanie testów jednostkowych](#addTests).

### <a name="sameProject"></a> Aby dodać testy jednostkowe w tym samym projekcie

1. Zmodyfikuj właściwości projektu kodu produktu, aby uwzględnić pliki nagłówkowe i bibliotek, które są wymagane dla testów jednostkowych.

   1. W **Eksploratora rozwiązań**, w menu skrótów testowanego projektu wybierz **właściwości**. Projekt **właściwości** zostanie otwarte okno.

   2. Wybierz **właściwości konfiguracji** > **katalogi VC ++**.

   3. Edytuj katalogi dołączonych i bibliotek:

       |Katalog|Właściwość|
       |-|-|
       |**Katalogi plików nagłówkowych** | **$(VCInstallDir)UnitTest\include;$(IncludePath)**|
       |**Katalogi bibliotek** | **$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|

2. Dodaj plik testu jednostkowego języka C++:

   - W **Eksploratora rozwiązań**, w menu skrótów projektu wybierz **Dodaj** > **nowy element** > **testu jednostkowego języka C++**.

   Przejdź do [pisanie testów jednostkowych](#addTests).

## <a name="addTests"></a> Pisanie testów jednostkowych

1. W każdym pliku testu jednostkowego kodu, Dodaj `#include` instrukcji w nagłówkach testowanego projektu.

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

1. Na **testu** menu, wybierz **Windows** > **Eksplorator testów**.

1. Jeśli wszystkie testy nie są widoczne w oknie, tworzenia projektu badania, klikając prawym przyciskiem myszy jego węzła w **Eksploratora rozwiązań** i wybierając pozycję **kompilacji** lub **odbudować**.

1. W **Eksplorator testów**, wybierz **Uruchom wszystkie**, lub wybierz określonych testów, które chcesz uruchomić. Kliknij prawym przyciskiem myszy na test dla innych opcji, w tym uruchamianie w trybie debugowania, z punktami przerwania jest włączony.

## <a name="see-also"></a>Zobacz także

- [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)
- [Dokumentacja interfejsu API z Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Przewodnik: Tworzenie i używanie biblioteki dołączanej dynamicznie (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Importowanie i eksportowanie](/cpp/build/importing-and-exporting)
- [Szybki start: Programowanie sterowane testami za pomocą narzędzia Eksplorator testów](../test/quick-start-test-driven-development-with-test-explorer.md)
