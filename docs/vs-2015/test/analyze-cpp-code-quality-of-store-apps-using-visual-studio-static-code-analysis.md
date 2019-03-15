---
title: Aplikacje Store analizy kodu statycznego C++
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native.express
ms.assetid: c5355e43-a37c-4686-a969-18e3dfc59a9c
caps.latest.revision: 15
author: alexhomer1
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9194da6803f04f3bf4cc56696d01a68a3e27d67d
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873246"
---
# <a name="analyze-c-code-quality-of-store-apps-using-visual-studio-static-code-analysis"></a>Analizowanie jakości kodu C++ w aplikacjach Store przy użyciu programu Visual Studio statycznej analizy kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ma to zastosowanie, Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Narzędzie do analizy kodu w wersjach express programu Visual Studio analizuje kod do zestaw typowych problemów i naruszeń dobrą praktykę programistyczną. Ostrzeżenia analizy kodu różnią się od błędów i ostrzeżeń, ponieważ analiza kodu szuka wzorców konkretnego kodu, które są prawidłowe, ale nadal można tworzyć problemy dla Ciebie lub innych osób używających Twojego kodu. Analiza kodu, można także znaleźć defektów w kodzie, które są trudne do odnajdywania za pomocą testowania. Podczas procesu opracowywania uruchomione narzędzie do analizy kodu w regularnych odstępach czasu może zwiększyć jakość ukończonej aplikacji.

> [!NOTE]
> W programie Visual Studio Ultimate, Visual Studio Premium i Visual Studio Professional można użyć pełnej funkcjonalności narzędzi analizy kodu. Zobacz [analiza jakości aplikacji za pomocą narzędzi analizy kodu](http://msdn.microsoft.com/library/dd264897.aspx) w bibliotece MSDN.

##  <a name="BKMK_Run"></a> Trwa uruchamianie analizy kodu
 Aby uruchomić analizę kodu w rozwiązaniu programu Visual Studio:

- Na **kompilacji** menu, wybierz **Uruchom analizę kodu dla rozwiązania**.

  Do automatycznego uruchamiania analizy kodu za każdym razem, tworzysz projekt:

1. Wybierz nazwę projektu w Eksploratorze rozwiązań, a następnie wybierz **właściwości**.

2. Na stronie właściwości projektu, wybierz opcję **analizy kodu** , a następnie wybierz **Włącz analizę kodu C/c++ podczas kompilacji**.

   Rozwiązania jest kompilowana i uruchomieniu analizy kodu. Wyniki są wyświetlane w oknie analizy kodu.

   ![Okno analizy kodu](../test/media/ca-cpp-collapsed.png "CA_CPP_Collapsed")

##  <a name="BKMK_Analyze"></a> Analizowanie i rozwiązywanie ostrzeżenia analizy kodu
 Aby analizować szczególne ostrzeżenie, wybierz tytuł ostrzeżenia w oknie analizy kodu. Ostrzeżenie rozwija, aby wyświetlić szczegółowe informacje o problemie. Jeśli to możliwe, analizy kodu wyświetla wiersza numer i analizy logikę, która doprowadziła do ostrzeżenia.

 ![Rozwinięte ostrzeżenie analizy kodu](../test/media/ca-cpp-expanded-callout.png "CA_CPP_Expanded_Callout")

 Po rozwinięciu ostrzeżenie wierszy kodu, który spowodował ostrzeżenie zostaną wyróżnione w edytorze kodu programu Visual Studio.

 ![Wyróżniony kod źródłowy](../test/media/ca-cpp-sourceline.png "CA_CPP_SourceLine")

 Po zrozumieniu problem można rozwiązać, w kodzie. Następnie uruchom ponownie analizę kodu, aby upewnić się, że ostrzeżenie nie jest już wyświetlany w oknie analizy kodu i rozwiązanie problemu nie został zgłoszony nowe ostrzeżenia.

> [!TIP]
>  Możesz ponownie uruchomić analizę kodu w oknie analizy kodu. Wybierz **analizy** przycisk, a następnie wybierz zakres analizy. Możesz ponownie uruchomić analizy na całego rozwiązania lub wybranego projektu.

##  <a name="BKMK_Suppress"></a> Pomijanie ostrzeżeń analizy kodu
 Istnieją terminy, gdy można zdecydować, Rezygnacja z naprawiania ostrzeżenie analizy kodu. Można zdecydować, rozpoznawanie ostrzeżenia wymaga zbyt dużo nagrywanie względem prawdopodobieństwo wystąpienia problemu w implementacji rzeczywistych swój kod. Lub może być uważa, że analizy, który jest używany w ostrzeżenia jest nieodpowiedni dla określonego kontekstu. Poszczególne ostrzeżenia można pominąć, tak aby nie były widoczne w oknie analizy kodu.

 Aby pominąć Ostrzeżenie:

1. Jeśli nie są wyświetlane szczegółowe informacje, należy rozwinąć tytuł ostrzeżenia.

2. Wybierz **akcje** widocznego u dołu ostrzeżenia.

3. Możliwość **Pomiń komunikat** , a następnie wybierz **w źródłowej**.

   Pomijanie wiadomości wstawia `#pragma(warning:` *WarningId* `)` który umożliwia pominięcie ostrzeżenia dla wiersza kodu.

##  <a name="BKMK_Search"></a> Wyszukiwanie i filtrowanie wyników analizy kodu
 Możesz wyszukiwać długim spisem komunikaty ostrzegawcze i filtrować ostrzeżeń w rozwiązaniach dotyczących wielu projektów.

 ![Wyszukiwanie i filtrowanie oknie analizy kodu](../test/media/ca-searchfilter.png "CA_SearchFilter")

##  <a name="Warnings"></a> Ostrzeżenia analizy kodu w języku C++
 Analiza kodu generuje następujące ostrzeżenia dla kodu C++:


|                                      Reguła                                      |                                                  Opis                                                  |
|--------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|
|                       [C6001](../code-quality/c6001.md)                        |                                          Używanie niezainicjowanej pamięci                                           |
|                       [C6011](../code-quality/c6011.md)                        |                                          Wyłuskanie wskaźnika o wartości Null                                           |
|                       [C6029](../code-quality/c6029.md)                        |                                            Użycie wartości typu Unchecked                                             |
|                       [C6053](../code-quality/c6053.md)                        |                                          Zakończenie zerem z wywołania                                           |
|                       [C6059](../code-quality/c6059.md)                        |                                               Złe łączenie                                               |
|                       [C6063](../code-quality/c6063.md)                        |                                  Brak argumentu ciągu w funkcji formatującej                                   |
|                       [C6064](../code-quality/c6064.md)                        |                                  Brak argumentu całkowitego dla funkcji formatującej                                  |
|                       [C6066](../code-quality/c6066.md)                        |                                  Brak argumentu będącego wskaźnikiem w funkcji formatującej                                  |
|                       [C6067](../code-quality/c6067.md)                        |                              Brak argumentu będącego wskaźnikiem ciągu w funkcji formatującej                               |
|                       [C6101](../code-quality/c6101.md)                        |                                        Zwracanie niezainicjowanej pamięci                                         |
|                       [C6200](../code-quality/c6200.md)                        |                                         Indeks przekracza maksimum dla bufora                                          |
|                       [C6201](../code-quality/c6201.md)                        |                                      Indeks przekracza maksimum dla bufora stosu                                       |
|                       [C6270](../code-quality/c6270.md)                        |                                   Brak argumentu typu Float w funkcji formatującej                                   |
|                       [C6271](../code-quality/c6271.md)                        |                                       Dodatkowy Argument w funkcji formatującej                                       |
|                       [C6272](../code-quality/c6272.md)                        |                                     Argument niż typu Float w funkcji formatującej                                     |
|                       [C6273](../code-quality/c6273.md)                        |                                    Argument nie jest liczbą całkowitą w funkcji formatującej                                     |
|                       [C6274](../code-quality/c6274.md)                        |                                   -Znakowy argumentu funkcji formatującej                                   |
|                       [C6276](../code-quality/c6276.md)                        |                                              Nieprawidłowe rzutowanie ciągu                                              |
|                       [C6277](../code-quality/c6277.md)                        |                                          Nieprawidłowe wywołanie funkcji CreateProcess                                           |
|                       [C6284](../code-quality/c6284.md)                        |                                  Nieprawidłowy Argument obiektu dla funkcji formatującej                                   |
|                       [C6290](../code-quality/c6290.md)                        |                                      Bitowe or logiczne Not- i pierwszeństwo                                       |
|                       [C6291](../code-quality/c6291.md)                        |                                       Bitowe or logiczne Not- lub priorytetu                                       |
|                       [C6302](../code-quality/c6302.md)                        |                             Nieprawidłowy argument będący ciągiem znaków funkcji formatującej                              |
|                       [C6303](../code-quality/c6303.md)                        |                           Argument ciągu nieprawidłowych znaków dwubajtowych w funkcji formatującej                           |
|                       [C6305](../code-quality/c6305.md)                        |                                         Niezgodny rozmiaru i korzystania z liczby                                         |
|                       [C6306](../code-quality/c6306.md)                        |                                   Nieprawidłowy Argument zmiennej, wywołanie funkcji                                   |
|                       [C6328](../code-quality/c6328.md)                        |                                       Potencjalna niezgodność typu argumentu                                        |
|                       [C6385](../code-quality/c6385.md)                        |                                                 Przepełnienie podczas odczytu                                                  |
|                       [C6386](../code-quality/c6386.md)                        |                                                 Przepełnienie podczas zapisu                                                 |
|                       [C6387](../code-quality/c6387.md)                        |                                            Nieprawidłowa wartość parametru                                            |
|                       [C6500](../code-quality/c6500.md)                        |                                          Nieprawidłowa właściwość atrybutu                                           |
|                       [C6501](../code-quality/c6501.md)                        |                                     Wartości właściwości atrybutów powodujące konflikt                                     |
|                       [C6503](../code-quality/c6503.md)                        |                                           Odwołania nie może mieć wartości Null                                           |
|                       [C6504](../code-quality/c6504.md)                        |                                              Wartość null na nie będącego wskaźnikiem                                              |
|                       [C6505](../code-quality/c6505.md)                        |                                               MustCheck dla typu Void                                               |
|                       [C6506](../code-quality/c6506.md)                        |                                      Rozmiar buforu dla elementu nie będącego wskaźnikiem lub tablicy                                      |
| [C6507](http://msdn.microsoft.com/18f88cd1-d035-4403-a6a4-12dd0affcf21)        |                                       Wartość null niezgodności w Wyłuskania Zero                                       |
|                       [C6508](../code-quality/c6508.md)                        |                                           Dostęp do zapisu dla stałej                                            |
|                       [C6509](../code-quality/c6509.md)                        |                                          Użyto Return w warunku wstępnym                                          |
|                       [C6510](../code-quality/c6510.md)                        |                                        Zakończenie wartością null dla nie będącego wskaźnikiem                                         |
|                       [C6511](../code-quality/c6511.md)                        |                                          MustCheck musi być tak lub nie                                          |
|                       [C6513](../code-quality/c6513.md)                        |                                       Rozmiar elementu bez rozmiar bufora                                        |
|                       [C6514](../code-quality/c6514.md)                        |                                        Rozmiar buforu przekracza rozmiar tablicy                                         |
|                       [C6515](../code-quality/c6515.md)                        |                                          Rozmiar buforu dla elementu nie będącego wskaźnikiem                                           |
|                       [C6516](../code-quality/c6516.md)                        |                                          Brak właściwości dla atrybutu                                           |
|                       [C6517](../code-quality/c6517.md)                        |                                       Nieprawidłowy rozmiar dla bufora bez możliwości odczytu                                       |
|                       [C6518](../code-quality/c6518.md)                        |                                     Rozmiar obszaru do zapisu dla bufora bez możliwości zapisu                                      |
| [C6521](http://msdn.microsoft.com/e98d0ae3-6f13-47b2-9a15-15d4055af9ef)  |                                        Nieprawidłowy rozmiar ciągu Wyłuskania                                        |
|                       [C6522](../code-quality/c6522.md)                        |                                           Nieprawidłowy typ ciągu rozmiaru                                            |
| [C6523](http://msdn.microsoft.com/11397a31-b224-46b0-afb7-d49ca576a3bb)  |                                         Nieprawidłowy rozmiar parametru ciągu                                         |
|                       [C6525](../code-quality/c6525.md)                        |                                   Nieosiągalna lokalizacja ciągu nieprawidłowy rozmiar                                    |
| [C6526](http://msdn.microsoft.com/59c590c7-0098-4166-a1ac-87f324596002)  |                                        Nieprawidłowy typ ciągu rozmiaru buforu                                        |
|                       [C6527](../code-quality/c6527.md)                        |              Nieprawidłowa adnotacja: Właściwość "NeedsRelease" nie może być używana dla wartości typu void               |
|                       [C6530](../code-quality/c6530.md)                        |                                       Nierozpoznany styl ciągu formatu                                        |
|                       [C6540](../code-quality/c6540.md)                        | Użycie adnotacji atrybutów dla tej funkcji spowoduje unieważnienie wszystkich istniejących adnotacji __declspec  |
|                       [C6551](../code-quality/c6551.md)                        |                              Nieprawidłowa specyfikacja rozmiaru: nie można przeanalizować wyrażenia                              |
|                       [C6552](../code-quality/c6552.md)                        |                              Nieprawidłowe wyrażenie Deref = lub Notref =: nie można przeanalizować wyrażenia                               |
|                       [C6701](../code-quality/c6701.md)                        |                                  Wartość nie jest prawidłową wartością Yes/No/Maybe                                  |
|                       [C6702](../code-quality/c6702.md)                        |                                        Wartość nie jest wartością ciągu                                        |
|                       [C6703](../code-quality/c6703.md)                        |                                           Wartość nie jest liczbą                                           |
|                       [C6704](../code-quality/c6704.md)                        |                                    Nieoczekiwany błąd adnotacji wyrażenia                                     |
|                       [C6705](../code-quality/c6705.md)                        |     Oczekiwana liczba argumentów dla adnotacji nie jest zgodna z rzeczywistą liczbę argumentów dla adnotacji      |
|                       [C6706](../code-quality/c6706.md)                        |                                  Nieoczekiwany błąd adnotacji dla adnotacji                                   |
|                      [C28021](../code-quality/c28021.md)                       |                                Parametr, którego dodawana jest adnotacja, musi być wskaźnikiem                                |
|                      [C28182](../code-quality/c28182.md)                       |         Wyłuskanie wskaźnika o wartości NULL. Wskaźnik zawiera tę samą wartość NULL, tak jak innego wskaźnika.          |
|                      [C28202](../code-quality/c28202.md)                       |                                    Niedozwolone odwołanie do niestatycznego elementu członkowskiego                                     |
|                      [C28203](../code-quality/c28203.md)                       |                                     Niejednoznaczne odwołanie do składowej klasy.                                      |
|                      [C28205](../code-quality/c28205.md)                       |                           \_Powodzenie\_ lub \_On_failure\_ używane w niedozwolonym kontekście                            |
|                      [C28206](../code-quality/c28206.md)                       |                                   Lewy argument operacji wskazuje na strukturę, użyj opcji "->"                                   |
|                      [C28207](../code-quality/c28207.md)                       |                                       Lewy operand jest strukturą, użyj "."                                       |
|                      [C28210](../code-quality/c28210.md)                       |                 Adnotacje dla kontekstu __on_failure nie może być w jawnym kontekście pre                  |
|                      [C28211](../code-quality/c28211.md)                       |                                 Oczekiwano nazwy kontekstu statycznego dla SAL_context                                  |
|                      [C28212](../code-quality/c28212.md)                       |                                  Oczekiwano wyrażenia wskaźnikowego dla adnotacji                                   |
|                      [C28213](../code-quality/c28213.md)                       | \_Use_decl_annotations\_ adnotacja musi być używana do odwołania, bez żadnych modyfikacji, wcześniejszej deklaracji. |
|                      [C28214](../code-quality/c28214.md)                       |                                   Nazwy parametrów atrybutów muszą być p1... p9                                   |
|                      [C28215](../code-quality/c28215.md)                       |                    Nie można zastosować elementu typefix parametr, który ma już typefix                    |
|                      [C28216](../code-quality/c28216.md)                       |        Adnotacja checkReturn dotyczy tylko warunków końcowych dla określonego parametru funkcji.         |
|                      [C28217](../code-quality/c28217.md)                       |            Dla funkcji liczba parametrów dla adnotacji odpowiada znalezionej w pliku             |
|                      [C28218](../code-quality/c28218.md)                       |             Dla parametru funkcji adnotacji nie odpowiada znalezionej w pliku              |
|                      [C28219](../code-quality/c28219.md)                       |                 Element członkowski wyliczenia oczekiwał na adnotację parametru w adnotacji                 |
|                      [C28220](../code-quality/c28220.md)                       |                  Wyrażenia typu całkowitego oczekiwana dla adnotacji parametru w adnotacji                   |
|                      [C28221](../code-quality/c28221.md)                       |                        Oczekiwano wyrażenia ciągu dla parametru w adnotacji                         |
|                      [C28222](../code-quality/c28222.md)                       |                               Oczekiwano __yes \__NIE, lub \__maybe oczekiwana dla adnotacji                               |
|                      [C28223](../code-quality/c28223.md)                       |                       Nie odnaleziono oczekiwanego tokenu/identyfikatora dla adnotacji, parametr                        |
|                      [C28224](../code-quality/c28224.md)                       |                                        Adnotacja wymaga parametrów                                         |
|                      [C28225](../code-quality/c28225.md)                       |                     Nie znaleziono prawidłowej liczby wymaganych parametrów w adnotacji                      |
|                      [C28226](../code-quality/c28226.md)                       |                          Adnotacja nie może być PrimOp (w bieżącej deklaracji)                          |
|                      [C28227](../code-quality/c28227.md)                       |                          Adnotacja nie może być PrimOp (patrz Poprzednia deklaracja)                           |
|                      [C28228](../code-quality/c28228.md)                       |                             Parametr adnotacji: nie można użyć typu w adnotacjach                              |
|                      [C28229](../code-quality/c28229.md)                       |                                    Adnotacja nie obsługuje parametrów                                     |
|                      [C28230](../code-quality/c28230.md)                       |                                     Typ parametru nie ma składowej.                                      |
|                      [C28231](../code-quality/c28231.md)                       |                                       Adnotacja jest prawidłowa tylko na tablicy                                       |
|                      [C28232](../code-quality/c28232.md)                       |                               Operatory pre, post i deref nie są stosowane do żadnej adnotacji                               |
|                      [C28233](../code-quality/c28233.md)                       |                                    Operatory pre, post i deref zostały zastosowane do bloku                                     |
|                      [C28234](../code-quality/c28234.md)                       |                              __at wyrażenie nie ma zastosowania do bieżącej funkcji                               |
|                      [C28235](../code-quality/c28235.md)                       |                               Funkcja nie może występować samodzielnie jako adnotacja                                |
|                      [C28236](../code-quality/c28236.md)                       |                                Nie można użyć adnotacji w wyrażeniu                                 |
|                      [C28237](../code-quality/c28237.md)                       |                              Adnotacja dla parametru nie jest już obsługiwana                               |
|                      [C28238](../code-quality/c28238.md)                       |      Adnotacja dla parametru ma więcej niż jedną wartość, stringValue i longValue. Użyj paramn = xxx       |
|                      [C28239](../code-quality/c28239.md)                       |  Adnotacja dla parametru ma zarówno wartość, stringValue lub longValue; i paramn = xxx. Użyj tylko paramn = xxx   |
|                      [C28240](../code-quality/c28240.md)                       |                             Adnotacja dla parametru ma param2, ale nie ma param1                              |
|                      [C28241](../code-quality/c28241.md)                       |                          Adnotacja dla funkcji na parametrze nie została rozpoznana.                           |
|                      [C28243](../code-quality/c28243.md)                       |   Adnotacja dla funkcji na parametrze, wymaga więcej wyłuskań niż pozwala właściwy adnotowany typ   |
|                      [C28245](../code-quality/c28245.md)                       |                     Adnotacja dla funkcji oznacza stosowanym "this" w innych — funkcji składowej                     |
|                      [C28246](../code-quality/c28246.md)                       |                Adnotacja parametru dla funkcji jest niezgodna z typem parametru                 |
|                      [C28250](../code-quality/c28250.md)                       |                    Niespójna adnotacja dla funkcji: poprzednie wystąpienie zawiera błąd.                     |
|                      [C28251](../code-quality/c28251.md)                       |                       Niespójna adnotacja dla funkcji: to wystąpienie posiada błąd.                       |
|                      [C28252](../code-quality/c28252.md)                       |           Niespójna adnotacja dla funkcji: parametr ma inne adnotacje, w tym wystąpieniu.           |
|                      [C28253](../code-quality/c28253.md)                       |           Niespójna adnotacja dla funkcji: parametr ma inne adnotacje, w tym wystąpieniu.           |
|                      [C28254](../code-quality/c28254.md)                       |                               (dynamic_cast <>) nie jest obsługiwane w adnotacjach                                |
|                      [C28262](../code-quality/c28262.md)                       |                    Znaleziono błąd składni w adnotacji w funkcji dla adnotacji                     |
|                      [C28263](../code-quality/c28263.md)                       |                 Znaleziono błąd składni w warunkowej adnotacji dla wewnętrznych adnotacji                 |
|                      [C28267](../code-quality/c28267.md)                       |                    Znaleziono błąd składni w adnotacjach adnotacji w funkcji.                    |
|                      [C28272](../code-quality/c28272.md)                       |      Adnotacja dla funkcji, parametr podczas badania jest niespójny z deklaracją funkcji      |
|                      [C28273](../code-quality/c28273.md)                       |                    W przypadku funkcji są niespójne z deklaracją funkcji                     |
|                      [C28275](../code-quality/c28275.md)                       |                                   Parametr \_Macro_value\_ ma wartość null                                    |
|                      [C28279](../code-quality/c28279.md)                       |                           Dla symbolu znaleziono "begin" bez pasującego "end"                            |
|                      [C28280](../code-quality/c28280.md)                       |                           Dla symbolu element "end" znaleziono bez pasującego "begin"                           |
|                      [C28282](../code-quality/c28282.md)                       |                                    Ciągi formatu muszą znajdować się w warunkach wstępnych                                    |
|                      [C28285](../code-quality/c28285.md)                       |                                    Dla funkcji, błąd składni w parametrze                                    |
|                      [C28286](../code-quality/c28286.md)                       |                                    Dla funkcji, błąd składni w pobliżu końca                                    |
|                      [C28287](../code-quality/c28287.md)                       |                Dla funkcji, błąd składni w \_na\_adnotacji () (Nierozpoznana nazwa parametru)                |
|                      [C28288](../code-quality/c28288.md)                       |                  Dla funkcji, błąd składni w \_na\_adnotacji () (Nieprawidłowa nazwa parametru)                   |
|                      [C28289](../code-quality/c28289.md)                       |                Dla funkcji: Elementy ReadableTo lub WritableTo nie miał elementu limit-spec jako parametru                |
|                      [C28290](../code-quality/c28290.md)                       |           Adnotacja dla funkcji zawierających więcej obiektów zewnętrznych niż rzeczywista liczba parametrów            |
|                      [C28291](../code-quality/c28291.md)                       |                        Post null/notnull na poziomie deref 0 jest bez znaczenia dla funkcji.                        |
|                      [C28300](../code-quality/c28300.md)                       |                            Argumenty operacji wyrażenia o niezgodnych typach dla operatora                             |
|                      [C28301](../code-quality/c28301.md)                       |                               Brak adnotacji dla pierwszej deklaracji funkcji.                               |
|                      [C28302](../code-quality/c28302.md)                       |                             Dodatkowy \_Deref\_ operator znaleziono w adnotacji.                              |
|                      [C28303](../code-quality/c28303.md)                       |                           Niejednoznaczny \_Deref\_ operator znaleziono w adnotacji.                            |
|                      [C28304](../code-quality/c28304.md)                       |                     Nieprawidłowo umieszczony \_Notref\_ znaleziono operator zastosowany do tokenu.                      |
|                      [C28305](../code-quality/c28305.md)                       |                                Wykryto błąd podczas analizowania tokenu.                                 |
|                      [C28350](../code-quality/c28350.md)                       |                  Adnotacja opisuje sytuację, która nie jest warunkowo stosowana.                   |
|                      [C28351](../code-quality/c28351.md)                       |         Adnotacja zawiera opis, gdy wartość dynamiczna (zmienna) nie można użyć w warunku.          |
