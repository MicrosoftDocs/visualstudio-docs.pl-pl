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
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302594"
---
# <a name="generate-unit-tests-for-your-code-with-intellitest"></a>Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkcja IntelliTest analizuje kod .NET w celu wygenerowania danych testu i pakietów testów jednostkowych. Dla każdej instrukcji w kodzie są generowane dane wejściowe testu, którymi instrukcja zostanie wykonana. W przypadku każdego rozgałęzienia warunkowego w kodzie jest wykonywana analiza przypadku. Na przykład, jeśli są analizowane instrukcje, potwierdzenia i wszystkie operacje, które mogą zgłaszać wyjątki. Ta analiza jest używana na potrzeby generowania danych testu sparametryzowanego testu jednostkowego dla wszystkich metod użytkownika, tworzenie testów jednostkowych zapewniające wysokie pokrycie kodu.

 Po uruchomieniu testów funkcji IntelliTest, można łatwo zobaczyć, testy, które kończą się niepowodzeniem i Dodaj wszelkie niezbędne kod, aby je rozwiązać. Możesz wybrać, które wygenerowanych testów, aby zapisać do projektu testowego, aby zapewnić mechanizm regresji. W przypadku zmiany kodu, należy ponownie uruchomić program IntelliTest w celu synchronizowania wygenerowanych testów wprowadzania zmian w kodzie.

 IntelliTest jest dostępny tylko C# dla i nie obsługuje konfiguracji x64.

## <a name="get-started-with-intellitest"></a>Wprowadzenie do IntelliTest
 Będziesz potrzebować Visual Studio Enterprise.

### <a name="explore-use-intellitest-to-explore-your-code-and-generate-unit-tests"></a>Poznaj: Użycie funkcji IntelliTest eksplorować kod i generowania testów jednostkowych
 Do generowania testów jednostkowych, typów muszą być publiczne. W przeciwnym razie przed jego wygenerowaniem [Utwórz testy jednostkowe](#NoRun) .

1. Otwórz swoje rozwiązanie w programie Visual Studio. Następnie otwórz plik klasy, który zawiera metody, które mają zostać przetestowane.

2. Kliknij prawym przyciskiem myszy metodę w kodzie i wybierz polecenie **Uruchom IntelliTest** , aby wygenerować testy jednostkowe dla kodu w metodzie.

     ![Kliknij&#45;prawym przyciskiem myszy metodę, aby wygenerować testy jednostkowe](../test/media/runpex.png "RunPEX")

     Funkcja IntelliTest uruchamia kod wiele razy z różnych danych wejściowych. Każde uruchomienie jest reprezentowana w Tabela zawierająca dane wejściowe testu i wynikowy wyjściowych lub wyjątku.

     ![Wyświetlane jest okno wyników eksploracji z testami](../test/media/pexexplorationresults.png "PEXExplorationResults")

     Do generowania testów jednostkowych dla wszystkich metod publicznych w klasie, po prostu kliknij prawym przyciskiem myszy w klasie zamiast określonej metody. Następnie wybierz pozycję **Uruchom IntelliTest**. Użyj listy rozwijanej w oknie wyników eksploracji, aby wyświetlić testy jednostkowe i dane wejściowe dla każdej metody w klasie.

     ![Wybierz z listy wyniki testów do wyświetlenia](../test/media/selectpextest.png "SelectPEXTest")

     Dla testów, które są zaliczone, sprawdź, czy zgłoszonych wyników w kolumnie wyników odpowiadają Twoim oczekiwaniom, w kodzie. W przypadku testów, które nie spełniają naprawiaj kod zgodnie z potrzebami. Następnie ponownie uruchom program IntelliTest, aby sprawdzić poprawność poprawki.

### <a name="persist-save-the-unit-tests-as-a-regression-suite"></a>Utrwalanie: Zapisz testów jednostkowych jako mechanizm regresji

1. Wybierz wiersze danych, które chcesz zapisać za pomocą sparametryzowanego testu jednostkowego do projektu testowego.

     ![Wybierz testy; Kliknij&#45;prawym przyciskiem myszy i wybierz pozycję Zapisz.](../test/media/savepextests.png "SavePEXTests")

     Można wyświetlić projekt testowy i sparametryzowany test jednostkowy, który został utworzony — poszczególne testy jednostkowe, odpowiadające poszczególnym wierszom, są zapisywane w pliku. g.cs w projekcie testowym, a sparametryzowany test jednostkowy jest zapisywany w odpowiadającym mu pliku CS. Można uruchomić testy jednostkowe i wyświetlić wyniki z Eksploratora testów, tak samo jak w przypadku dowolnego testów jednostkowych, które zostały utworzone ręcznie.

     ![Otwórz plik klasy w metodzie testowej, aby wyświetlić test jednostkowy](../test/media/testmethodpex.png "TestMethodPEX")

     Wszystkie niezbędne odwołania są również dodawane do projektu testowego.

     Jeśli zmieni się kod metody, należy ponownie uruchomić program IntelliTest, aby zachować synchronizację ze zmianami, testy jednostkowe.

### <a name="assist-use-intellitest-to-focus-code-exploration"></a>Pomoc telefoniczną: Użyj IntelliTest eksplorację kodu zespołu

1. W przypadku bardziej złożonego kodu funkcji IntelliTest pomaga z poziomu Eksploracja kodu. Na przykład jeśli masz metodę, która ma interfejs jako parametr, a istnieje więcej niż jedną klasę, która implementuje ten interfejs, IntelliTest umożliwia odnalezienie tych klas i zgłosi ostrzeżenie.

     Wyświetl ostrzeżenia zdecydować, co chcesz zrobić.

     ![Wyświetl ostrzeżenia](../test/media/pexviewwarning.png "PEXViewWarning")

2. Po badanie kodu i zrozumieć, co chcesz przetestować, możesz rozwiązać je, aby wybrać klas, które można używać do testowania interfejsu.

     ![Kliknij&#45;prawym przyciskiem myszy ostrzeżenie i wybierz polecenie Napraw.](../test/media/pexfixwarning.png "PEXFixWarning")

     Ten wybór jest dodawany do pliku PexAssemblyInfo.cs.

     `[assembly: PexUseType(typeof(Camera))]`

3. Teraz można uruchomić program IntelliTest do generowania sparametryzowanego testu jednostkowego i po prostu przy użyciu klasy, która Naprawiono dane testowe.

     ![Uruchom ponownie program IntelliTest w celu wygenerowania danych testowych](../test/media/pexwarningsfixed.png "PEXWarningsFixed")

### <a name="specify-use-intellitest-to-validate-correctness-properties-that-you-specify-in-code"></a>Określ: Użycie funkcji IntelliTest do sprawdzania poprawności właściwości określone w kodzie
 Określ ogólne relacji między dane wejściowe i wyjściowe, które mają wygenerowane testy jednostkowe do sprawdzania poprawności. Ta specyfikacja jest hermetyzowany w metodzie, która wygląda jak metody testowej, ale ogólnie jest obliczana. Jest to metoda testowa sparametryzowanej jednostki i potwierdzenia, wszystkie wprowadzone muszą spełniać wszystkie możliwe wartości wejściowych, które mogą generować IntelliTest.

## <a name="QandALink"></a>p & A

### <a name="q-can-you-use-intellitest-for-unmanaged-code"></a>P: czy można używać funkcji IntelliTest dla niezarządzanego kodu?
 Odp **.:** Nie, IntelliTest działa tylko z kodem zarządzanym.

### <a name="q-when-does-a-generated-test-pass-or-fail"></a>P: kiedy wygenerowany test powodzeniem lub niepowodzeniem?
 Odp **.:** Jest ona przekazywana jak każdy inny test jednostkowy, jeśli nie wystąpią żadne wyjątki. Go nie powiedzie się, jeśli wszystkie potwierdzenie nie powiedzie się lub jeśli testowany kod zawiera nieobsługiwany wyjątek.

 Jeśli masz test, który można przekazać, jeśli istnieją pewne wyjątki zgłaszane, możesz ustawić jedną z następujących atrybutów, w zależności od wymagań na metody testowej, w klasie testu lub zestawu poziomu:

- **PexAllowedExceptionAttribute**

- **PexAllowedExceptionFromTypeAttribute**

- **PexAllowedExceptionFromTypeUnderTestAttribute**

- **PexAllowedExceptionFromAssemblyAttribute**

### <a name="q-can-i-add-assumptions-to-the-parameterized-unit-test"></a>P: czy mogę dodać założenia co do sparametryzowanego testu jednostkowego?
 Odp **.:** Tak, użyj założeń, aby określić, które dane testowe nie są wymagane do testów jednostkowych dla określonej metody. Użyj klasy <xref:Microsoft.Pex.Framework.PexAssume>, aby dodać założenia. Na przykład można dodać założenie zmiennej długości nie jest null następująco.

 `PexAssume.IsNotNull(lengths);`

 Jeśli dodasz założeń, a następnie ponownie uruchom program IntelliTest, zostaną usunięte dane z badań, które nie są już odpowiednie.

### <a name="q-can-i-add-assertions-to-the-parameterized-unit-test"></a>P: czy można dodać potwierdzenia do sparametryzowanego testu jednostkowego?
 Odp **.:** Tak, IntelliTest sprawdzi, czy co jest prawdziwe w instrukcji, gdy uruchamia testy jednostkowe. Użyj klasy <xref:Microsoft.Pex.Framework.PexAssert> lub interfejsu API potwierdzenia, który jest dostarczany z platformą testową w celu dodania potwierdzeń. Na przykład można dodać potwierdzenia, że dwie zmienne są równe.

 `PexAssert.AreEqual(a, b);`

 Jeśli dodasz potwierdzenie, a następnie ponownie uruchom program IntelliTest, będzie sprawdzał, czy Twoje potwierdzenie jest prawidłowa, i test zakończy się niepowodzeniem, jeśli nie jest.

### <a name="NoRun"></a>P: Czy można generować sparametryzowane testy jednostkowe bez wcześniejszego uruchamiania IntelliTest?
 Odp **.:** Tak, kliknij prawym przyciskiem myszy w klasie lub metodzie, a następnie wybierz polecenie **Utwórz IntelliTest**.

 ![Kliknij&#45;prawym przyciskiem myszy edytor, wybierz polecenie Utwórz IntelliTest](../test/media/pexcreateintellitest.png "PEXCreateIntelliTest")

 Zaakceptuj domyślny format generowania testów lub zmienić sposób o nazwie projektu i testów. Można utworzyć nowy projekt testowy, lub Zapisz testów do istniejącego projektu.

 ![Utwórz IntelliTest z wartością domyślną MSTest](../test/media/pexcreateintellitestmstest.png "PEXCreateIntelliTestMSTest")

### <a name="q-can-i-use-other-unit-test-frameworks-with-intellitest"></a>P: czy mogę używać innych struktur testów jednostek pochodzących z funkcją IntelliTest?
 Odp **.:** Tak, wykonaj następujące kroki, aby [znaleźć i zainstalować inne platformy](../test/install-third-party-unit-test-frameworks.md). Po ponownym uruchomieniu programu Visual Studio i ponownym otwarciu rozwiązania kliknij prawym przyciskiem myszy w klasie lub metodzie, a następnie wybierz pozycję **Utwórz IntelliTest**. Wybierz swoją zainstalowanych strukturę:

 ![Wybierz inną strukturę testów jednostkowych dla IntelliTest](../test/media/pexcreateintellitestextensions.png "PEXCreateIntelliTestExtensions")

 Następnie uruchom program IntelliTest, aby wygenerować poszczególne testy jednostkowe w odpowiadających im plikach g.cs.

### <a name="q-can-i-learn-more-about-how-the-tests-are-generated"></a>P: czy można dowiedzieć się więcej na temat sposobu generowania testów?
 Odp **.:** Tak, aby uzyskać ogólne omówienie, przeczytaj ten [wpis w blogu](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/).
