---
title: Pisanie testów jednostkowych dla bibliotek DLL języka C++
description: Dowiedz się więcej o kilku sposobach testowania kodu biblioteki DLL w zależności od tego, czy biblioteka DLL eksportuje funkcje, które chcesz przetestować.
ms.custom: SEO-VS-2020
ms.date: 02/16/2021
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 6e8df96c6345d84531ef04eae56f7f60dcc3eefe
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042876"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Pisanie testów jednostkowych dla bibliotek DLL języka C++ w Visual Studio

Istnieje kilka sposobów testowania kodu biblioteki DLL, w zależności od tego, czy eksportuje on funkcje, które chcesz przetestować. Wybierz jeden z następujących sposobów:

**Testy jednostkowe wywołują tylko funkcje, które są eksportowane z biblioteki DLL:** Dodaj oddzielny projekt testowy zgodnie z opisem w [teście Write unit tests for C/C++](writing-unit-tests-for-c-cpp.md)(Pisanie testów jednostkowych dla języka C/C++). W projekcie testowym dodaj odwołanie do projektu DLL.

Przejdź do procedury [Aby odwołać się do funkcji wyeksportowanych z projektu DLL](#projectRef).

**Biblioteka DLL jest budowaną .exe pliku:** Dodaj oddzielny projekt testowy. Połącz go z plikiem obiektu wyjściowego.

Przejdź do procedury [Aby połączyć testy z plikami obiektu lub biblioteki](#objectRef).

Testy jednostkowe wywołują funkcje inne niż członkowskie, które nie są eksportowane z biblioteki DLL, a bibliotekę DLL można utworzyć **jako bibliotekę statyczną:** Zmień projekt DLL tak, aby został skompilowany do *pliku lib.* Dodaj oddzielny projekt testowy, który odwołuje się do testowego projektu.

Zaletą tego podejścia jest umożliwienie testom używania nieeksportowanych elementów członkowskich, ale ich zachowanie w oddzielnym projekcie.

Przejdź do procedury [Aby zmienić bibliotekę DLL na bibliotekę statyczną](#staticLink).

Testy jednostkowe muszą wywołać funkcje inne niż funkcje członkowskie, które nie są eksportowane, a kod musi być budowany jako **dynamiczna biblioteka linków (DLL):** Dodaj testy jednostkowe w tym samym projekcie co kod produktu.

Przejdź do procedury [Aby dodać testy jednostkowe w tym samym projekcie.](#sameProject)

## <a name="create-the-tests"></a>Tworzenie testów

### <a name="to-change-the-dll-to-a-static-library"></a><a name="staticLink"></a> Aby zmienić bibliotekę DLL na bibliotekę statyczną

- Jeśli testy muszą używać elementów członkowskich, które nie są eksportowane przez projekt DLL, a testowany projekt jest budowaną biblioteką dynamiczną, rozważ przekonwertowanie go na bibliotekę statyczną.

  1. W **Eksplorator rozwiązań** menu skrótów testowego projektu wybierz pozycję **Właściwości**. Zostanie otwarte **okno** Właściwości projektu.

  2. Wybierz **pozycję Właściwości konfiguracji**  >  **Ogólne.**

  3. Ustaw **typ konfiguracji na** **bibliotekę statyczną (lib).**

  Przejdź do procedury [Aby połączyć testy z plikami obiektu lub biblioteki](#objectRef).

### <a name="to-reference-exported-dll-functions-from-the-test-project"></a><a name="projectRef"></a> Aby odwołać się do funkcji biblioteki DLL wyeksportowanych z projektu testowego

- Jeśli projekt DLL eksportuje funkcje, które chcesz przetestować, możesz dodać odwołanie do projektu kodu z projektu testowego.

  1. Tworzenie natywnego projektu testu jednostkowego.

      ::: moniker range=">=vs-2019"

      1. W menu **File (Plik)** wybierz pozycję New Project   >  **(Nowy projekt).** W **oknie dialogowym Dodawanie nowego projektu** ustaw pozycję **Język** na C++ i wpisz "test" w polu wyszukiwania. Następnie wybierz **natywny projekt testu jednostkowego**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. W menu **File (Plik)** wybierz pozycję **New** Project Visual C++ Test C++ Unit Test Project (Projekt testu jednostkowego >  >  >  > **języka C++).**

      ::: moniker-end

  1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt testowy, a następnie wybierz polecenie **Dodaj**  >  **odwołanie**.

  1. Wybierz **pozycję Projekty**, a następnie projekt do przetestowania.

       Wybierz przycisk **Dodaj**.

  1. We właściwościach projektu testowego dodaj lokalizację testowego projektu do pozycji Dołącz katalogi.

       Wybierz **pozycję Właściwości konfiguracji**  >  **Katalogi dołączane VC++**  >  .

       Wybierz **pozycję Edytuj**, a następnie dodaj katalog nagłówkowy testowego projektu.

  Przejdź do [tematu Pisanie testów jednostkowych](#addTests).

### <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="objectRef"></a> Aby połączyć testy z plikami obiektu lub biblioteki

- Jeśli biblioteka DLL nie eksportuje funkcji, które chcesz przetestować, możesz dodać wyjściowy plik *.obj* lub *.lib* do zależności projektu testowego.

  1. Tworzenie natywnego projektu testu jednostkowego.

      ::: moniker range=">=vs-2019"

      1. W menu **File (Plik)** wybierz pozycję New Project   >  **(Nowy projekt).** W **oknie dialogowym Dodawanie nowego projektu** ustaw pozycję **Język** na C++ i wpisz "test" w polu wyszukiwania. Następnie wybierz **natywny projekt testu jednostkowego**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. W menu **File (Plik)** wybierz pozycję **New** Project Visual C++ Test C++ Unit Test Project (Projekt testu jednostkowego >  >  >  > **języka C++).**

      ::: moniker-end

  1. W **Eksplorator rozwiązań** menu skrótów projektu testowego wybierz pozycję **Właściwości**.

  1. Wybierz **pozycję Właściwości konfiguracji**  >  **Linker**  >  **Input**  >  **Additional Dependencies (Dodatkowe zależności wejściowe w programie Linker właściwości konfiguracji).**

       Wybierz **pozycję** Edytuj i dodaj nazwy plików **.obj** **lub .lib.** Nie używaj pełnych nazw ścieżek.

  1. Wybierz **pozycję Właściwości konfiguracji**  >  **Linker**  >  **Ogólne** dodatkowe  >  **katalogi biblioteki.**

       Wybierz **pozycję** Edytuj i dodaj ścieżkę katalogu **plików .obj** lub **.lib.** Ścieżka zazwyczaj znajduje się w folderze kompilacji testowanego projektu.

  1. Wybierz **pozycję Właściwości konfiguracji**  >  **Katalogi dołączane VC++**  >  .

       Wybierz **pozycję Edytuj**, a następnie dodaj katalog nagłówkowy testowego projektu.

  Przejdź do [tematu Pisanie testów jednostkowych](#addTests).

### <a name="to-add-unit-tests-in-the-same-project"></a><a name="sameProject"></a> Aby dodać testy jednostkowe w tym samym projekcie

1. Zmodyfikuj właściwości projektu kodu produktu, aby uwzględnić nagłówki i pliki biblioteki, które są wymagane do testowania jednostkowego.

   1. W **Eksplorator rozwiązań** menu skrótów testowego projektu wybierz pozycję **Właściwości**. Zostanie otwarte **okno** Właściwości projektu.

   1. Wybierz **pozycję Właściwości konfiguracji**  >  **Katalogi VC++.**

   1. Edytuj katalogi Include i Library:

       |Katalog|Właściwość|
       |-|-|
       |**Dołączanie katalogów** | **$(VCInstallDir)Auxiliary\VS\UnitTest\include** |
       |**Katalogi bibliotek** | **$(VCInstallDir)Auxiliary\VS\UnitTest\lib** |

1. Dodaj plik testu jednostkowego języka C++:

   1. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz **polecenie Dodaj**  >  **nowy element**.

   1. W **oknie dialogowym Dodawanie nowego** elementu wybierz pozycję  **Plik C++ (cpp),** nadaj mu odpowiednią nazwę, a następnie wybierz pozycję **Dodaj**.

   Przejdź do [tematu Pisanie testów jednostkowych](#addTests).

## <a name="write-the-unit-tests"></a><a name="addTests"></a> Pisanie testów jednostkowych

1. W każdym pliku kodu testu jednostkowego dodaj `#include` instrukcje dla nagłówków testowego projektu.

1. Dodawanie klas i metod testów do plików kodu testu jednostkowego. Na przykład:

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

1. W menu **Test** wybierz pozycję **Eksplorator testów**  >  **systemu** Windows.

1. Jeśli nie wszystkie testy są widoczne w oknie, skonstruuj projekt testowy: kliknij prawym przyciskiem myszy jego węzeł w oknie **Eksplorator rozwiązań** a następnie wybierz polecenie Build or Rebuild **(Skompilowanie** lub **skompilowanie).**

1. W **Eksploratorze testów** wybierz **pozycję Uruchom wszystko** lub wybierz konkretne testy, które chcesz uruchomić. Kliknij prawym przyciskiem myszy test dla innych opcji, na przykład aby uruchomić go w trybie debugowania z włączonymi punktami przerwania.

## <a name="see-also"></a>Zobacz też

- [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)
- [Dokumentacja interfejsu API Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Przewodnik: Tworzenie i używanie biblioteki dołączanej dynamicznie (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Importowanie i eksportowanie](/cpp/build/importing-and-exporting)
- [Szybki start: tworzenie aplikacji opartych na testach za pomocą Eksploratora testów](../test/quick-start-test-driven-development-with-test-explorer.md)
