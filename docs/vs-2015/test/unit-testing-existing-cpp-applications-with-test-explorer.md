---
title: Testy jednostkowe istniejących aplikacji C++ za pomocą narzędzia Eksplorator testów | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7d08de69-c32e-4f0b-89aa-75347b15fb82
caps.latest.revision: 13
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3952f73c214c0d7070005f28140e048136279215
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760229"
---
# <a name="unit-testing-existing-c-applications-with-test-explorer"></a>Testy jednostkowe istniejących aplikacji C++ za pomocą narzędzia Eksplorator testów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zaleca się, że zanim będzie można zmienić istniejącą aplikację, należy upewnić się, czy ma ona dobre pokrycie testami jednostkowymi. Daje to pewność, że zmiany nie wprowadzają błędów. Jeśli aplikacja nie ma jeszcze testów jednostkowych, można je dodać przy użyciu technik opisanych w tym temacie. W tym temacie opisano sposób dodawania testów jednostkowych dla istniejącego kodu języka Visual C++, począwszy od wyboru sposobu testowania kodu oraz poprzez tworzenie, pisanie i wreszcie Uruchamianie testów.  
  
## <a name="deciding-how-to-test-your-code"></a>Wybór sposobu testowania kodu  
 Otwórz istniejący projekt C++ i sprawdź go, by zdecydować, jak chcesz dodać testy jednostkowe. Możesz chcieć użyć niektórych narzędzi modelowania, które pomagają zobaczyć zależności w kodzie i pomóc Ci zrozumieć sposób interakcji części. Aby uzyskać więcej informacji, zobacz [tworzenie wizualizacji kodu](../modeling/visualize-code.md).  
  
 Zaleca się wydzielenie zmian w małe zadania. Przed każdą małą zmianą, pisać testy jednostkowe dla aspektów zachowania, które pozostaną takie same. Testy te będą nadal zaliczane pomyślnie po dokonaniu zmiany. Na przykład jeśli zamierzasz zmienić funkcję sortowania, dzięki czemu sortuje listę osób według nazwiska, a nie według imienia, następnie można napisać test jednostkowy, który sprawdza, czy wszystkie nazwy wejściowe są widoczne w danych wyjściowych. Po dokonaniu zmiany, można dodać nowe testy jednostkowe dla nowego zachowania.  
  
 Jeśli jest to praktyczne, wiele lub wszystkie z testów jednostkowych należy używać jedynie eksportowanych funkcji. Ale jeśli zmieniasz tylko niewielką część całej aplikacji, a następnie możesz chcieć użyć funkcji, które nie są eksportowane. Na przykład możesz zechcieć, testy, które wywołują funkcje wewnętrzne lub testów, które ustawiają i pobierają wartości wewnętrznych zmiennych.  
  
 Istnieje kilka sposobów na przetestowanie kodu produktu, w zależności od tego, czy uwidacznia on interfejsy, które mają zostać przetestowane. Wybierz jedną z następujących sposobów:  
  
 **Testy jednostkowe użyją tylko funkcji, które są eksportowane z testowanego kodu:**  
 Dodaj osobny projekt testów. W projekcie testowym Dodaj odwołanie do testowanego projektu.  
  
 Przejdź do procedury [k Odkazu eksportowanych funkcji z projektu testów](#projectRef).  
  
 **Testowany kod jest kompilowany jako plik .exe:**  
 Dodaj osobny projekt testów. Połącz go z wyjściowym plikiem obiektu.  
  
 Przejdź do procedury [połączyć testy z plikami obiektu lub biblioteki](#objectRef).  
  
 **Testy jednostkowe muszą używać prywatnych funkcji i danych, a testowany kod może być kompilowany jako biblioteka statyczna:**  
 Zmiana testowanego projektu tak, by był skompilowany do pliku. lib. Dodaj osobny projekt testów, który odwołuje się do testowanego projektu.  
  
 Takie podejście ma tę zaletę umożliwia testom używane prywatnych elementów członkowskich, ale nadal utrzymuje testy w osobnym projekcie. Jednak może nie być odpowiednie w przypadku niektórych aplikacji gdzie konieczne jest posiadanie biblioteki dołączanej dynamicznie (dll).  
  
 Przejdź do procedury [Aby zmienić testowany kod na bibliotekę statyczną](#staticLink).  
  
 **Testy jednostkowe muszą używać prywatnych funkcji i danych, a kod musi być kompilowany jako biblioteka dołączana dynamicznie (DLL):**  
 Dodawanie testów jednostkowych w tym samym projekcie, co kod produktu.  
  
 Przejdź do procedury [Aby dodać testy jednostkowe w tym samym projekcie](#sameProject).  
  
## <a name="creating-the-tests"></a>Tworzenie testów  
  
###  <a name="staticLink"></a> Aby zmienić testowany kod na bibliotekę statyczną  
  
- Jeśli testy muszą użyć elementów członkowskich, które nie są eksportowane przez testowany projekt i projekt testowany jest kompilowany jako biblioteka dynamiczna, należy wziąć pod uwagę podczas konwertowania go do biblioteki statycznej.  
  
  1.  W Eksploratorze rozwiązań w menu skrótów testowanego projektu testu, wybierz **właściwości**. Zostanie otwarte okno właściwości projektu.  
  
  2.  Wybierz **właściwości konfiguracji**, **ogólne**.  
  
  3.  Ustaw **typu konfiguracji** do **biblioteka statyczna (.lib)**.  
  
  Przejdź do procedury [połączyć testy z plikami obiektu lub biblioteki](#objectRef).  
  
###  <a name="projectRef"></a> Aby odwołać się do eksportowanych funkcji z projektu testowego  
  
- Jeśli testowany projekt eksportuje funkcje, które mają zostać przetestowane, można dodać odwołanie do projektu kodu z projektu testowego.  
  
  1.  Utwórz projekt testów języka C++.  
  
      1.  Na **pliku** menu, wybierz **New**, **projektu**, **Visual C++, testowanie**, **projekt testów jednostkowych C++**.  
  
  2.  W Eksploratorze rozwiązań w menu skrótów projektu testów wybierz **odwołania**. Zostanie otwarte okno właściwości projektu.  
  
  3.  Wybierz **wspólne właściwości**, **szablon i odwołania**, a następnie wybierz **Dodaj nowe odwołanie** przycisku.  
  
  4.  Wybierz **projektów**, a następnie projekt ma zostać przetestowana.  
  
       Wybierz **Dodaj** przycisku.  
  
  5.  W oknie właściwości dla projektu testów Dodaj lokalizację testowanego projektu Dołącz katalogi.  
  
       Wybierz **właściwości konfiguracji**, **katalogi VC ++**, **katalogi plików nagłówkowych**.  
  
       Wybierz **Edytuj**, a następnie Dodaj nagłówek katalogu testowanego projektu.  
  
  Przejdź do [pisanie testów jednostkowych](#addTests).  
  
###  <a name="objectRef"></a> Aby powiązać testy z plikami obiektu lub biblioteki  
  
- Jeśli testowany kod nie eksportuje funkcji, które chcesz przetestować, możesz dodać dane wyjściowe **.obj** lub **.lib** pliku do zależności testowanego projektu testowego.  
  
  1.  Utwórz projekt testów języka C++.  
  
      1.  Na **pliku** menu, wybierz **New**, **projektu**, **Visual C++, testowanie**, **projekt testów jednostkowych C++**.  
  
  2.  W Eksploratorze rozwiązań w menu skrótów projektu testów wybierz **właściwości**. Zostanie otwarte okno właściwości projektu.  
  
  3.  Wybierz **właściwości konfiguracji**, **konsolidatora**, **dane wejściowe**, **dodatkowe zależności**.  
  
       Wybierz **Edytuj**i Dodaj nazwy **.obj** lub **.lib** plików. Nie należy używać nazw pełnej ścieżki.  
  
  4.  Wybierz **właściwości konfiguracji**, **konsolidatora**, **ogólne**, **dodatkowe katalogi biblioteki**.  
  
       Wybierz **Edytuj**i Dodaj ścieżkę katalogu **.obj** lub **.lib** plików. Ścieżka zazwyczaj mieści się w folderze kompilacji testowanego projektu.  
  
  5.  Wybierz **właściwości konfiguracji**, **katalogi VC ++**, **katalogi plików nagłówkowych**.  
  
       Wybierz **Edytuj**, a następnie Dodaj nagłówek katalogu testowanego projektu.  
  
  Przejdź do [pisanie testów jednostkowych](#addTests).  
  
###  <a name="sameProject"></a> Aby dodać testy jednostkowe w tym samym projekcie  
  
1. Zmodyfikuj właściwości projektu kodu produktu, aby uwzględnić pliki nagłówkowe i bibliotek, które są wymagane dla testów jednostkowych.  
  
   1.  W Eksploratorze rozwiązań w menu skrótów testowanego projektu testu, wybierz polecenie Właściwości. Zostanie otwarte okno właściwości projektu.  
  
   2.  Wybierz **właściwości konfiguracji**, **katalogi VC ++**.  
  
   3.  Edytuj katalogi dołączonych i bibliotek:  
  
       |||  
       |-|-|  
       |**Katalogi plików nagłówkowych**|**$(VCInstallDir)UnitTest\include;$(IncludePath)**|  
       |**Katalogi bibliotek**|**$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|  
  
2. Dodaj plik testu jednostkowego języka C++:  
  
   -   W Eksploratorze rozwiązań w menu skrótów projektu, wybierz **Dodaj**, **nowy element**, a następnie wybierz **testu jednostkowego języka C++**.  
  
   Przejdź do [pisanie testów jednostkowych](#addTests).  
  
##  <a name="addTests"></a> Pisanie testów jednostkowych  
  
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
  
   Aby uzyskać więcej informacji, zobacz [testy jednostkowe kodu natywnego za pomocą narzędzia Eksplorator testów](http://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c).  
  
## <a name="run-the-tests"></a>Uruchom testy  
  
1. Na **widoku** menu, wybierz **Windows inne**, **Eksplorator testów**.  
  
2. W Eksploratorze testów wybierz **Uruchom wszystkie**.  
  
   Aby uzyskać więcej informacji, zobacz [Szybki Start: Testów opartych na tworzenie aplikacji przy użyciu Eksploratora testów](../test/quick-start-test-driven-development-with-test-explorer.md).
