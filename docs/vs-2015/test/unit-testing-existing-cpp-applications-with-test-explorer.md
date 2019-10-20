---
title: Testowanie jednostkowe C++ istniejących aplikacji za pomocą Eksploratora testów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7d08de69-c32e-4f0b-89aa-75347b15fb82
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 34d1918522711f3070cf6988a83ebdbd1e80b2f4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659583"
---
# <a name="unit-testing-existing-c-applications-with-test-explorer"></a>Testy jednostkowe istniejących aplikacji C++ za pomocą narzędzia Eksplorator testów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zalecamy, aby przed zmianą istniejącej aplikacji upewnić się, że ma ona dobre pokrycie w testach jednostkowych. Daje to pewność, że zmiany nie wprowadziły błędów. Jeśli aplikacja nie ma jeszcze testów jednostkowych, można je dodać przy użyciu technik opisanych w tym temacie. W tym temacie opisano, jak dodać testy jednostkowe dla C++ istniejącego kodu wizualizacji, rozpoczynając od decydowania o sposobie testowania kodu, a następnie tworzenia, pisania i wreszcie uruchamiania testów.

## <a name="deciding-how-to-test-your-code"></a>Decydowanie o sposobie testowania kodu
 Otwórz istniejący C++ projekt i Zbadaj go, aby zdecydować, jak chcesz dodać testy jednostkowe. Możesz chcieć użyć niektórych narzędzi do modelowania, które ułatwiają Wyświetlanie zależności w kodzie i zrozumienie, jak współdziałają części. Aby uzyskać więcej informacji, zobacz [Wizualizacja kodu](../modeling/visualize-code.md).

 Zalecamy oddzielenie zmian na małe zadania. Przed każdą małą zmianą należy napisać testy jednostkowe dla aspektów zachowania, które pozostaną takie same. Te testy będą nadal przekazywane po dokonaniu zmiany. Na przykład jeśli planujesz zmianę funkcji sortowania tak, aby posortować listę osób według nazwiska, a nie według imienia, można napisać test jednostkowy, który sprawdza, czy wszystkie nazwy wejściowe pojawiają się w danych wyjściowych. Po wprowadzeniu zmiany możesz chcieć dodać nowe testy jednostkowe dla nowego zachowania.

 Jeśli jest to praktyczne, wiele lub wszystkie testy jednostkowe powinny używać tylko eksportowanych funkcji. Ale jeśli zmieniasz tylko niewielką część całej aplikacji, możesz chcieć użyć funkcji, które nie zostały wyeksportowane. Na przykład możesz potrzebować testów, które wywołują funkcje wewnętrzne, lub testów, które ustawiają i pobierają wartości zmiennych wewnętrznych.

 Istnieje kilka sposobów testowania kodu produktu, w zależności od tego, czy uwidacznia on interfejsy, które chcesz przetestować. Wybierz jedną z następujących metod:

 **Testy jednostkowe będą korzystać tylko z funkcji wyeksportowanych z testowanego kodu:** Dodaj osobny projekt testowy. W projekcie testowym Dodaj odwołanie do testowanego projektu.

 Przejdź do procedury, [Aby odwołać się do funkcji wyeksportowanych z projektu testowego](#projectRef).

 **Testowy kod jest skompilowany jako plik. exe:** Dodaj osobny projekt testowy. Połącz je z plikiem obiektu wyjściowego.

 Przejdź do procedury, [Aby połączyć testy z plikami obiektu lub biblioteki](#objectRef).

 **Testy jednostkowe muszą używać prywatnych funkcji i danych, a badany kod może być skompilowany jako Biblioteka statyczna:** Zmień badany projekt, tak aby został skompilowany do pliku. lib. Dodaj oddzielny projekt testowy odwołujący się do testowanego projektu.

 Takie podejście ma na celu umożliwienie testom używania prywatnych elementów członkowskich, ale nadal prowadzi testy w osobnym projekcie. Jednak może nie być odpowiednie dla niektórych aplikacji, w których wymagana jest biblioteka dołączana dynamicznie (dll).

 Przejdź do procedury, [Aby zmienić testowy kod na bibliotekę statyczną](#staticLink).

 **Testy jednostkowe muszą używać prywatnych funkcji i danych, a kod musi być skompilowany jako biblioteka dołączana dynamicznie (dll):** Dodaj testy jednostkowe w tym samym projekcie, w którym znajduje się kod produktu.

 Przejdź do procedury, [Aby dodać testy jednostkowe w tym samym projekcie](#sameProject).

## <a name="creating-the-tests"></a>Tworzenie testów

### <a name="staticLink"></a>Aby zmienić testowany kod na bibliotekę statyczną

- Jeśli testy muszą używać elementów członkowskich, które nie są eksportowane przez badany projekt, a badany projekt jest skompilowany jako Biblioteka dynamiczna, Rozważ przekonwertowanie go na bibliotekę statyczną.

  1. W Eksplorator rozwiązań w menu skrótów testowanego projektu wybierz polecenie **Właściwości**. Zostanie otwarte okno właściwości projektu.

  2. Wybierz **Właściwości konfiguracji**, **Ogólne**.

  3. Ustaw **Typ konfiguracji** na **bibliotekę statyczną (. lib)** .

  Kontynuuj procedurę [łączenia testów z plikami obiektów lub bibliotek](#objectRef).

### <a name="projectRef"></a>Aby odwołać się do funkcji wyeksportowanych z projektu testowego

- Jeśli badany projekt eksportuje funkcje, które chcesz przetestować, możesz dodać odwołanie do projektu kodu z projektu testowego.

  1. Utwórz projekt C++ testowy.

      1. W menu **plik** wybierz polecenie **Nowy**, **projekt**, **Wizualizacja C++, test**,  **C++ projekt testu jednostkowego**.

  2. W Eksplorator rozwiązań, w menu skrótów projektu testowego, wybierz **odwołania**. Zostanie otwarte okno właściwości projektu.

  3. Wybierz pozycję **typowe właściwości**, **Struktura i odwołania**, a następnie wybierz przycisk **Dodaj nowe odwołanie** .

  4. Wybierz pozycję **projekty**, a następnie projekt do przetestowania.

       Wybierz przycisk **Dodaj** .

  5. We właściwościach projektu testowego Dodaj lokalizację testowanego projektu do katalogów include.

       Wybierz **Właściwości konfiguracji**, **Katalogi VC + +** , **Dołącz katalogi**.

       Wybierz pozycję **Edytuj**, a następnie Dodaj katalog nagłówka testowanego projektu.

  Przejdź do pozycji [pisanie testów jednostkowych](#addTests).

### <a name="objectRef"></a>Aby połączyć testy z plikami obiektu lub biblioteki

- Jeśli testowy kod nie eksportuje funkcji, które mają zostać przetestowane, można dodać plik Output **. obj** lub **. lib** do zależności projektu testowego.

  1. Utwórz projekt C++ testowy.

      1. W menu **plik** wybierz polecenie **Nowy**, **projekt**, **Wizualizacja C++, test**,  **C++ projekt testu jednostkowego**.

  2. W Eksplorator rozwiązań, w menu skrótów projektu testowego, wybierz **Właściwości**. Zostanie otwarte okno właściwości projektu.

  3. Wybierz **Właściwości konfiguracji**, **konsolidator**, **dane wejściowe**, **dodatkowe zależności**.

       Wybierz pozycję **Edytuj**i Dodaj nazwy plików **obj** lub **lib** . Nie używaj pełnych nazw ścieżek.

  4. Wybierz **Właściwości konfiguracji**, **konsolidator**, **Ogólne**, **Dodatkowe katalogi biblioteki**.

       Wybierz pozycję **Edytuj**, a następnie dodaj ścieżkę katalogu plików **obj** lub **lib** . Ścieżka znajduje się zwykle w folderze Build w badanym projekcie.

  5. Wybierz **Właściwości konfiguracji**, **Katalogi VC + +** , **Dołącz katalogi**.

       Wybierz pozycję **Edytuj**, a następnie Dodaj katalog nagłówka testowanego projektu.

  Przejdź do pozycji [pisanie testów jednostkowych](#addTests).

### <a name="sameProject"></a>Aby dodać testy jednostkowe w tym samym projekcie

1. Zmodyfikuj właściwości projektu kodu produktu w celu uwzględnienia nagłówków i plików bibliotek, które są wymagane do testowania jednostkowego.

   1. W Eksplorator rozwiązań w menu skrótów testowanego projektu wybierz polecenie Właściwości. Zostanie otwarte okno właściwości projektu.

   2. Wybierz **Właściwości konfiguracji**, **Katalogi VC + +** .

   3. Edytuj katalogi dołączania i biblioteki:

       |||
       |-|-|
       |**Katalogi dołączania**|**$ (VCInstallDir) UnitTest\include; $ (IncludePath)**|
       |**Katalogi bibliotek**|**$ (VCInstallDir) UnitTest\lib; $ (LibraryPath)**|

2. Dodaj plik C++ testu jednostkowego:

   - W Eksplorator rozwiązań, w menu skrótów projektu, wybierz **Dodaj**, **nowy element**, a następnie wybierz  **C++ test jednostkowy**.

   Przejdź do pozycji [pisanie testów jednostkowych](#addTests).

## <a name="addTests"></a>Pisanie testów jednostkowych

1. W każdym pliku kodu testu jednostkowego Dodaj instrukcję `#include` dla nagłówków testowanego projektu.

2. Dodaj klasy testowe i metody do plików kodu testu jednostkowego. Na przykład:

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

   Aby uzyskać więcej informacji, zobacz [kod natywny testowania jednostek w Eksploratorze testów](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c).

## <a name="run-the-tests"></a>Uruchom testy

1. W menu **Widok** wybierz **inne okna**, **Eksplorator testów**.

2. W Eksploratorze testów wybierz opcję **Uruchom wszystkie**.

   Aby uzyskać więcej informacji, zobacz [Szybki Start: Programowanie sterowane testami za pomocą Eksploratora testów](../test/quick-start-test-driven-development-with-test-explorer.md).
