---
title: Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest
ms.date: 10/05/2015
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateIntelliTest
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 1d3a86d9ef5823b5935ad99facd6a82bf3af9789
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018929"
---
# <a name="how-to-generate-unit-tests-by-using-intellitest"></a>Instrukcje: Generuj testy jednostkowe za pomocą IntelliTest

Funkcja IntelliTest analizuje kod .NET w celu wygenerowania danych testu i pakietów testów jednostkowych. Dla każdej instrukcji w kodzie są generowane dane wejściowe testu, którymi instrukcja zostanie wykonana. W przypadku każdego rozgałęzienia warunkowego w kodzie jest wykonywana analiza przypadku. Na przykład `if` instrukcje, asercje i wszystkie operacje, które mogą zgłaszać wyjątki są analizowane. Ta analiza jest używana na potrzeby generowania danych testu sparametryzowanego testu jednostkowego dla wszystkich metod użytkownika, tworzenie testów jednostkowych zapewniające wysokie pokrycie kodu.

Po uruchomieniu testów funkcji IntelliTest, można łatwo zobaczyć, testy, które kończą się niepowodzeniem i Dodaj wszelkie niezbędne kod, aby je rozwiązać. Możesz wybrać, które wygenerowanych testów, aby zapisać do projektu testowego, aby zapewnić mechanizm regresji. W przypadku zmiany kodu, należy ponownie uruchomić program IntelliTest w celu synchronizowania wygenerowanych testów wprowadzania zmian w kodzie.

## <a name="availability-and-extensions"></a>Dostępność i rozszerzenia

**Tworzenie testów funkcji IntelliTest** i **Uruchom test IntelliTest** polecenia menu:

* Są dostępne tylko w wersji Enterprise programu Visual Studio.

* Obsługuje tylko C# kod, który jest przeznaczony dla .NET Framework.

* Są [rozszerzalne](#extend-framework) i obsługują emitowanie testów w formacie MSTest, MSTest v2, nunit i xUnit.

* Nie obsługują x64 konfiguracji.

## <a name="explore-use-intellitest-to-explore-your-code-and-generate-unit-tests"></a>Przeglądać Użyj IntelliTest, aby eksplorować kod i generować testy jednostkowe

Do generowania testów jednostkowych, typów muszą być publiczne.

1. Otwórz rozwiązanie w programie Visual Studio, a następnie otwórz plik klasy z metodami, które chcesz przetestować.

2. Kliknij prawym przyciskiem myszy metodę i wybierz polecenie **Uruchom IntelliTest** , aby wygenerować testy jednostkowe dla kodu w metodzie.

   ![Po prawej stronie&#45;kliknij w metodzie do generowania testów jednostkowych](../test/media/runpex.png)

   Funkcja IntelliTest uruchamia kod wiele razy z różnych danych wejściowych. Każde uruchomienie jest reprezentowana w Tabela zawierająca dane wejściowe testu i wynikowy wyjściowych lub wyjątku.

   ![Zostanie wyświetlone okno wyników badań, za pomocą testów](../test/media/pexexplorationresults.png)

Aby wygenerować testy jednostkowe dla wszystkich metod publicznych w klasie, po prostu kliknij prawym przyciskiem myszy w klasie, a nie konkretną metodę, a następnie wybierz polecenie **Uruchom IntelliTest**. Użyj listy rozwijanej w **wyniki eksploracji** okno, aby wyświetlić testy jednostkowe i dane wejściowe dla każdej metody w klasie.

![Wybierz wyniki testów, aby wyświetlić z listy](../test/media/selectpextest.png)

Dla testów, które są zaliczone, sprawdź, czy zgłoszonych wyników w kolumnie wyników odpowiadają Twoim oczekiwaniom, w kodzie. W przypadku testów, które nie spełniają naprawiaj kod zgodnie z potrzebami. Następnie ponownie uruchom program IntelliTest, aby sprawdzić poprawność poprawki.

## <a name="persist-save-the-unit-tests-as-a-regression-suite"></a>Utrzyma Zapisz testy jednostkowe jako pakiet regresji

1. Wybierz wiersze danych, które chcesz zapisać za pomocą sparametryzowanego testu jednostkowego do projektu testowego.

     ![Wybierz testy; prawy&#45;kliknij przycisk, a następnie wybierz opcję Zapisz](../test/media/savepextests.png)

     Możesz wyświetlić projekt testowy i sparametryzowanego testu jednostkowego, który został utworzony — poszczególnych testów, odpowiadający wszystkich wierszy, są zapisywane w *. g.cs* zapisanie pliku w projekcie testowym i sparametryzowanego testu jednostkowego w odpowiadającymi mu dostawcami *.cs* pliku. Można uruchomić testy jednostkowe i wyświetlić wyniki z Eksploratora testów, tak samo jak w przypadku dowolnego testów jednostkowych, które zostały utworzone ręcznie.

     ![Plik klasy otwarte w metodzie testowej, aby wyświetlić testy jednostkowe](../test/media/testmethodpex.png)

     Wszystkie niezbędne odwołania są również dodawane do projektu testowego.

     Jeśli zmieni się kod metody, należy ponownie uruchomić program IntelliTest, aby zachować synchronizację ze zmianami, testy jednostkowe.

## <a name="assist-use-intellitest-to-focus-code-exploration"></a>Wspierany Użyj IntelliTest, aby skoncentrować się na eksplorowaniu kodu

1. W przypadku bardziej złożonego kodu funkcji IntelliTest pomaga z poziomu Eksploracja kodu. Na przykład jeśli masz metodę, która ma interfejs jako parametr, a istnieje więcej niż jedną klasę, która implementuje ten interfejs, IntelliTest umożliwia odnalezienie tych klas i zgłosi ostrzeżenie.

     Wyświetl ostrzeżenia zdecydować, co chcesz zrobić.

     ![Wyświetl ostrzeżenia](../test/media/pexviewwarning.png)

2. Po badanie kodu i zrozumieć, co chcesz przetestować, możesz rozwiązać je, aby wybrać klas, które można używać do testowania interfejsu.

     ![Po prawej stronie&#45;kliknij ostrzeżenie, a następnie wybierz poprawkę](../test/media/pexfixwarning.png)

     Ten wybór jest dodawany do *PexAssemblyInfo.cs* pliku.

     `[assembly: PexUseType(typeof(Camera))]`

3. Teraz można uruchomić program IntelliTest do generowania sparametryzowanego testu jednostkowego i po prostu przy użyciu klasy, która Naprawiono dane testowe.

     ![Ponownie uruchom program IntelliTest w celu wygenerowania danych testowych](../test/media/pexwarningsfixed.png)

## <a name="specify-use-intellitest-to-validate-correctness-properties-that-you-specify-in-code"></a>Podawać Użyj IntelliTest, aby sprawdzić poprawność właściwości, które są określone w kodzie

Określ ogólne relacji między dane wejściowe i wyjściowe, które mają wygenerowane testy jednostkowe do sprawdzania poprawności. Ta specyfikacja jest hermetyzowany w metodzie, która wygląda jak metody testowej, ale ogólnie jest obliczana. Jest to metoda testowa sparametryzowanej jednostki i potwierdzenia, wszystkie wprowadzone muszą spełniać wszystkie możliwe wartości wejściowych, które mogą generować IntelliTest.

## <a name="q--a"></a>Pytania i odpowiedzi

### <a name="q-can-you-use-intellitest-for-unmanaged-code"></a>PYTANIA Czy można używać IntelliTest do niezarządzanego kodu?

**Z** Nie, IntelliTest działa tylko z kodem zarządzanym.

### <a name="q-when-does-a-generated-test-pass-or-fail"></a>PYTANIA Kiedy wygenerowany test zakończy się pomyślnie lub niepowodzeniem?

**Z** Jest ona przekazywana jak każdy inny test jednostkowy, jeśli nie wystąpią żadne wyjątki. Go nie powiedzie się, jeśli wszystkie potwierdzenie nie powiedzie się lub jeśli testowany kod zawiera nieobsługiwany wyjątek.

Jeśli masz test, który można przekazać, jeśli istnieją pewne wyjątki zgłaszane, możesz ustawić jedną z następujących atrybutów, w zależności od wymagań na metody testowej, w klasie testu lub zestawu poziomu:

- **PexAllowedExceptionAttribute**

- **PexAllowedExceptionFromTypeAttribute**

- **PexAllowedExceptionFromTypeUnderTestAttribute**

- **PexAllowedExceptionFromAssemblyAttribute**

### <a name="q-can-i-add-assumptions-to-the-parameterized-unit-test"></a>PYTANIA Czy można dodać założenia do sparametryzowanych testów jednostkowych?

**Z** Tak, użyj założeń, aby określić, które dane testowe nie są wymagane do testów jednostkowych dla określonej metody. Użyj <xref:Microsoft.Pex.Framework.PexAssume> klasy do dodania założeń. Na przykład można dodać założenie, że zmienna `lengths` nie ma wartości null podobnej do:

`PexAssume.IsNotNull(lengths);`

Jeśli dodasz założeń, a następnie ponownie uruchom program IntelliTest, zostaną usunięte dane z badań, które nie są już odpowiednie.

### <a name="q-can-i-add-assertions-to-the-parameterized-unit-test"></a>PYTANIA Czy mogę dodać potwierdzenia do sparametryzowanego testu jednostkowego?

**Z** Tak, IntelliTest sprawdzi, czy co jest prawdziwe w instrukcji, gdy uruchamia testy jednostkowe. Użyj <xref:Microsoft.Pex.Framework.PexAssert> klasy lub potwierdzenia interfejsu API, który jest dostarczany z struktury testowej, można dodać potwierdzenia. Na przykład można dodać potwierdzenia, że dwie zmienne są równe.

`PexAssert.AreEqual(a, b);`

Po dodaniu potwierdzenia i ponownym uruchomieniu IntelliTest sprawdzimy, czy potwierdzenie jest prawidłowe i że test zakończy się niepowodzeniem, jeśli nie jest.

### <a name="NoRun"></a>PYTANIA Czy można generować sparametryzowane testy jednostkowe bez wcześniejszego uruchamiania IntelliTest?

**Z** Tak, kliknij prawym przyciskiem myszy w klasie lub metodzie, a następnie wybierz polecenie **Utwórz IntelliTest**.

![Po prawej stronie&#45;kliknij przycisk edytora, wybierz tworzenie testów funkcji IntelliTest](../test/media/pexcreateintellitest.png)

Zaakceptuj domyślny format generowania testów lub zmienić sposób o nazwie projektu i testów. Można utworzyć nowy projekt testowy, lub Zapisz testów do istniejącego projektu.

![Tworzenie testów funkcji IntelliTest przy użyciu domyślnego MSTest](../test/media/pexcreateintellitestmstest.png)

<a name="extend-framework"></a>
### <a name="q-can-i-use-other-unit-test-frameworks-with-intellitest"></a>PYTANIA Czy mogę używać innych platform testów jednostkowych z IntelliTest?

**Z** Tak, wykonaj następujące kroki, aby [znaleźć i zainstalować inne platformy](../test/install-third-party-unit-test-frameworks.md).
Rozszerzenia struktury testów są również dostępne w Visual Studio Marketplace, na przykład [Generator testu nunit](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371).

Po ponownym uruchomieniu programu Visual Studio i otwórz ponownie rozwiązanie, kliknij prawym przyciskiem myszy klasy lub metody, a następnie wybierz **tworzenie testów funkcji IntelliTest**. Wybierz swoją zainstalowanych strukturę:

![Wybierz inne środowiska testów jednostkowych dla funkcji IntelliTest](../test/media/pexcreateintellitestextensions.png)

Następnie uruchom test IntelliTest do generowania testów jednostkowych poszczególnych w odpowiadające im *. g.cs* plików.

### <a name="q-can-i-learn-more-about-how-the-tests-are-generated"></a>PYTANIA Czy mogę dowiedzieć się więcej o tym, jak są generowane testy?

**Z** Tak, aby uzyskać ogólne omówienie, przeczytaj ten [wpis w blogu](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/).
