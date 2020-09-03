---
title: Generuj testy jednostkowe dla kodu za pomocą IntelliTest | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateIntelliTest
ms.assetid: cd9ff940-e948-4d28-a72c-b291ef5c1e90
caps.latest.revision: 35
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f03490fc7ea3513a006254e3931cc1113f3bc159
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74302594"
---
# <a name="generate-unit-tests-for-your-code-with-intellitest"></a>Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliTest Eksplorowanie kodu platformy .NET do generowania danych testowych i zestawu testów jednostkowych. Dla każdej instrukcji w kodzie są generowane dane wejściowe testu, które spowodują wykonanie tej instrukcji. Analiza przypadku jest wykonywana dla każdego rozgałęzienia warunkowego w kodzie. Na przykład, jeśli są analizowane instrukcje, potwierdzenia i wszystkie operacje, które mogą zgłaszać wyjątki. Ta analiza służy do generowania danych testowych dla sparametryzowanych testów jednostkowych dla każdej z metod, co pozwala tworzyć testy jednostkowe z dużym pokryciem kodu.

 Po uruchomieniu programu IntelliTest można łatwo sprawdzić, które testy kończą się niepowodzeniem i dodać kod, aby rozwiązać ten problem. Możesz wybrać, które z wygenerowanych testów mają być zapisane w projekcie testowym w celu udostępnienia pakietu regresji. Zmieniając kod, należy ponownie uruchomić program IntelliTest w celu zachowania synchronizacji generowanych testów z kodem.

 IntelliTest jest dostępna tylko dla języka C# i nie obsługuje konfiguracji x64.

## <a name="get-started-with-intellitest"></a>Wprowadzenie do funkcji IntelliTest
 Będziesz potrzebować Visual Studio Enterprise.

### <a name="explore-use-intellitest-to-explore-your-code-and-generate-unit-tests"></a>Eksplorowanie: Użyj IntelliTest, aby eksplorować kod i generować testy jednostkowe
 Aby wygenerować testy jednostkowe, typy muszą być publiczne. W przeciwnym razie przed jego wygenerowaniem [Utwórz testy jednostkowe](#NoRun) .

1. Otwórz rozwiązanie w programie Visual Studio. Następnie otwórz plik klasy, który ma metody, które chcesz przetestować.

2. Kliknij prawym przyciskiem myszy metodę w kodzie i wybierz polecenie **Uruchom IntelliTest** , aby wygenerować testy jednostkowe dla kodu w metodzie.

     ![Prawy&#45;kliknij metodę, aby wygenerować testy jednostkowe](../test/media/runpex.png "RunPEX")

     IntelliTest uruchamia kod wiele razy z różnymi danymi wejściowymi. Każde uruchomienie jest reprezentowane w tabeli zawierającej dane wejściowe testów oraz wynikowe wyniki lub wyjątek.

     ![Wyświetlane jest okno wyników eksploracji z testami](../test/media/pexexplorationresults.png "PEXExplorationResults")

     Aby wygenerować testy jednostkowe dla wszystkich metod publicznych w klasie, po prostu kliknij prawym przyciskiem myszy w klasie, a nie konkretną metodę. Następnie wybierz pozycję **Uruchom IntelliTest**. Użyj listy rozwijanej w oknie wyników eksploracji, aby wyświetlić testy jednostkowe i dane wejściowe dla każdej metody w klasie.

     ![Wybierz z listy wyniki testów do wyświetlenia](../test/media/selectpextest.png "SelectPEXTest")

     W przypadku testów, które zakończyły się powodzeniem, sprawdź, czy raportowane wyniki w kolumnie wynik są zgodne z oczekiwaniami dla kodu. W przypadku testów, które kończą się niepowodzeniem, Popraw kod w odpowiedni sposób. Następnie uruchom ponownie program IntelliTest, aby sprawdzić poprawność poprawek.

### <a name="persist-save-the-unit-tests-as-a-regression-suite"></a>Utrwalanie: Zapisz testy jednostkowe jako pakiet regresji

1. Wybierz wiersze danych, które chcesz zapisać z sparametryzowanym testem jednostkowym w projekcie testowym.

     ![Wybierz testy; prawy&#45;kliknij i wybierz pozycję Zapisz.](../test/media/savepextests.png "SavePEXTests")

     Można wyświetlić projekt testowy i sparametryzowany test jednostkowy, który został utworzony — poszczególne testy jednostkowe, odpowiadające poszczególnym wierszom, są zapisywane w pliku. g.cs w projekcie testowym, a sparametryzowany test jednostkowy jest zapisywany w odpowiadającym mu pliku CS. Można uruchomić testy jednostkowe i wyświetlić wyniki z Eksploratora testów tak samo jak w przypadku testów jednostkowych, które zostały utworzone ręcznie.

     ![Otwórz plik klasy w metodzie testowej, aby wyświetlić test jednostkowy](../test/media/testmethodpex.png "TestMethodPEX")

     Wszystkie niezbędne odwołania są również dodawane do projektu testowego.

     Jeśli kod metody ulegnie zmianie, należy ponownie uruchomić program IntelliTest w celu zachowania synchronizacji testów jednostkowych ze zmianami.

### <a name="assist-use-intellitest-to-focus-code-exploration"></a>Asysta: Użyj IntelliTest, aby skoncentrować eksplorację kodu

1. Jeśli masz bardziej skomplikowany kod, IntelliTest pomaga w skoncentrowaniu się na eksploracji kodu. Na przykład jeśli masz metodę, która ma interfejs jako parametr i istnieje więcej niż jedna klasa, która implementuje ten interfejs, IntelliTest odnajduje te klasy i raportuje ostrzeżenie.

     Wyświetl ostrzeżenia, aby zdecydować, co chcesz zrobić.

     ![Wyświetl ostrzeżenia](../test/media/pexviewwarning.png "PEXViewWarning")

2. Po zbadaniu kodu i zrozumieniu, co chcesz przetestować, możesz naprawić ostrzeżenie, aby wybrać klasy do użycia w celu przetestowania interfejsu.

     ![Prawo&#45;kliknij ostrzeżenie i wybierz pozycję Napraw.](../test/media/pexfixwarning.png "PEXFixWarning")

     Ten wybór jest dodawany do pliku PexAssemblyInfo.cs.

     `[assembly: PexUseType(typeof(Camera))]`

3. Teraz można ponownie uruchomić program IntelliTest w celu wygenerowania sparametryzowanych testów jednostkowych i danych testowych przy użyciu ustalonej klasy.

     ![Uruchom ponownie program IntelliTest w celu wygenerowania danych testowych](../test/media/pexwarningsfixed.png "PEXWarningsFixed")

### <a name="specify-use-intellitest-to-validate-correctness-properties-that-you-specify-in-code"></a>Określ: Użyj IntelliTest, aby sprawdzić poprawność właściwości poprawnych określonych w kodzie
 Określ ogólną relację między danymi wejściowymi i wyjściowymi, które mają być weryfikowane przez wygenerowane testy jednostkowe. Ta specyfikacja jest hermetyzowana w metodzie, która wygląda jak metoda testowa, ale jest określana uniwersalnie. Jest to sparametryzowane metody testów jednostkowych, a wszystkie pożądane potwierdzenia muszą być przechowywane dla wszystkich możliwych wartości wejściowych, które IntelliTest mogą generować.

## <a name="q--a"></a><a name="QandALink"></a> P & A

### <a name="q-can-you-use-intellitest-for-unmanaged-code"></a>P: Czy można używać IntelliTest do niezarządzanego kodu?
 Odp **.:** Nie, IntelliTest działa tylko z kodem zarządzanym.

### <a name="q-when-does-a-generated-test-pass-or-fail"></a>P: Kiedy wygenerowany test zakończy się pomyślnie lub niepowodzeniem?
 Odp **.:** Jest ona przekazywana jak każdy inny test jednostkowy, jeśli nie wystąpią żadne wyjątki. Nie powiedzie się, jeśli jakiekolwiek potwierdzenie nie powiedzie się lub jeśli testowy kod zgłosi nieobsłużony wyjątek.

 Jeśli istnieje test, który może zostać przekazany w przypadku zgłoszenia pewnych wyjątków, można ustawić jeden z następujących atrybutów na podstawie wymagań w metodzie testowej, klasy testowej lub na poziomie zestawu:

- **PexAllowedExceptionAttribute**

- **PexAllowedExceptionFromTypeAttribute**

- **PexAllowedExceptionFromTypeUnderTestAttribute**

- **PexAllowedExceptionFromAssemblyAttribute**

### <a name="q-can-i-add-assumptions-to-the-parameterized-unit-test"></a>P: Czy można dodać założenia do sparametryzowany test jednostkowy?
 Odp **.:** Tak, użyj założeń, aby określić, które dane testowe nie są wymagane do testów jednostkowych dla określonej metody. Użyj <xref:Microsoft.Pex.Framework.PexAssume> klasy, aby dodać założenia. Na przykład można dodać założenie, że zmienna długości nie ma wartości null podobnej do tej.

 `PexAssume.IsNotNull(lengths);`

 W przypadku dodania założeń i ponownego uruchomienia IntelliTest dane testowe, które nie są już potrzebne, zostaną usunięte.

### <a name="q-can-i-add-assertions-to-the-parameterized-unit-test"></a>P: Czy można dodać potwierdzenia do sparametryzowanego testu jednostkowego?
 Odp **.:** Tak, IntelliTest sprawdzi, czy co jest prawdziwe w instrukcji, gdy uruchamia testy jednostkowe. Użyj <xref:Microsoft.Pex.Framework.PexAssert> klasy lub interfejsu API potwierdzenia, który jest dostarczany z platformą testową w celu dodania potwierdzeń. Na przykład można dodać potwierdzenie, że dwie zmienne są równe.

 `PexAssert.AreEqual(a, b);`

 Po dodaniu potwierdzenia i ponownym uruchomieniu IntelliTest sprawdzimy, czy potwierdzenie jest prawidłowe i że test zakończy się niepowodzeniem, jeśli nie jest.

### <a name="q-can-i-generate-parameterized-unit-tests-without-running-intellitest-first"></a><a name="NoRun"></a> P: Czy można generować sparametryzowane testy jednostkowe bez wcześniejszego uruchamiania IntelliTest?
 Odp **.:** Tak, kliknij prawym przyciskiem myszy w klasie lub metodzie, a następnie wybierz polecenie **Utwórz IntelliTest**.

 ![Prawy&#45;kliknij pozycję Edytor, wybierz polecenie Utwórz IntelliTest](../test/media/pexcreateintellitest.png "PEXCreateIntelliTest")

 Zaakceptuj domyślny format, aby wygenerować testy, lub Zmień sposób nazywania projektu i testów. Można utworzyć nowy projekt testowy lub zapisać testy w istniejącym projekcie.

 ![Utwórz IntelliTest z wartością domyślną MSTest](../test/media/pexcreateintellitestmstest.png "PEXCreateIntelliTestMSTest")

### <a name="q-can-i-use-other-unit-test-frameworks-with-intellitest"></a>P: Czy można używać innych platform testów jednostkowych z IntelliTest?
 Odp **.:** Tak, wykonaj następujące kroki, aby [znaleźć i zainstalować inne platformy](../test/install-third-party-unit-test-frameworks.md). Po ponownym uruchomieniu programu Visual Studio i ponownym otwarciu rozwiązania kliknij prawym przyciskiem myszy w klasie lub metodzie, a następnie wybierz pozycję **Utwórz IntelliTest**. Wybierz zainstalowaną strukturę tutaj:

 ![Wybierz inną strukturę testów jednostkowych dla IntelliTest](../test/media/pexcreateintellitestextensions.png "PEXCreateIntelliTestExtensions")

 Następnie uruchom program IntelliTest, aby wygenerować poszczególne testy jednostkowe w odpowiadających im plikach g.cs.

### <a name="q-can-i-learn-more-about-how-the-tests-are-generated"></a>P: Czy można dowiedzieć się więcej o tym, jak są generowane testy?
 Odp **.:** Tak, aby uzyskać ogólne omówienie, przeczytaj ten [wpis w blogu](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/).
