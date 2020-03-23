---
title: Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest
ms.date: 10/05/2015
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateIntelliTest
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 65b1de58f195b957d080bd21144c22479b1aafed
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589594"
---
# <a name="how-to-generate-unit-tests-by-using-intellitest"></a>Jak: Generowanie testów jednostkowych przy użyciu testu IntelliTest

IntelliTest eksploruje kod platformy .NET do generowania danych testowych i zestawu testów jednostkowych. Dla każdej instrukcji w kodzie jest generowany test danych wejściowych, który wykona tę instrukcję. Analiza przypadków jest wykonywana dla każdej gałęzi warunkowej w kodzie. Na przykład `if` instrukcje, potwierdzenia i wszystkie operacje, które mogą zgłaszać wyjątki są analizowane. Ta analiza jest używana do generowania danych testowych dla sparametryzowanego testu jednostkowego dla każdej z metod, tworząc testy jednostkowe o wysokim pokryciu kodu.

Po uruchomieniu IntelliTest, można łatwo zobaczyć, które testy są niepowodzeniem i dodać dowolny kod niezbędne, aby je naprawić. Można wybrać, które z wygenerowanych testów, aby zapisać w projekcie testowym, aby zapewnić pakiet regresji. Po zmianie kodu uruchom ponownie IntelliTest, aby zachować wygenerowane testy w synchronizacji ze zmianami kodu.

## <a name="availability-and-extensions"></a>Dostępność i rozszerzenia

Polecenia menu **Utwórz intellitest** i **uruchom intellitest:**

* Są dostępne tylko w wersji Enterprise Edition programu Visual Studio.

* Obsługa tylko kod języka C#, który jest przeznaczony dla programu .NET Framework.

* Są [rozszerzalne](#extend-framework) i obsługują testy emitujące w formacie MSTest, MSTest V2, NUnit i xUnit.

* Nie obsługuje konfiguracji x64.

## <a name="explore-use-intellitest-to-explore-your-code-and-generate-unit-tests"></a>Eksploruj: użyj intellitestu, aby eksplorować kod i generować testy jednostkowe

Aby wygenerować testy jednostkowe, typy muszą być publiczne.

1. Otwórz rozwiązanie w programie Visual Studio, a następnie otwórz plik klasy, który zawiera metody, które chcesz przetestować.

2. Kliknij prawym przyciskiem myszy metodę i wybierz **polecenie Uruchom intellitest,** aby wygenerować testy jednostkowe dla kodu w metodzie.

   ![Prawym&#45;kliknij metodę generowania testów jednostkowych](../test/media/runpex.png)

   IntelliTest uruchamia kod wiele razy z różnych danych wejściowych. Każde uruchomienie jest reprezentowana w tabeli przedstawiającej dane testu wejściowego i wynikowe dane wyjściowe lub wyjątku.

   ![Okno Wyniki eksploracji jest wyświetlane z testami](../test/media/pexexplorationresults.png)

Aby wygenerować testy jednostkowe dla wszystkich metod publicznych w klasie, wystarczy kliknąć prawym przyciskiem myszy w klasie, a nie w określonej metodzie, a następnie wybrać **polecenie Uruchom intellitest**. Użyj listy rozwijanej w oknie **Wyniki eksploracji,** aby wyświetlić testy jednostkowe i dane wejściowe dla każdej metody w klasie.

![Wybierz wyniki testów do wyświetlenia z listy](../test/media/selectpextest.png)

W przypadku testów, które przechodzą, sprawdź, czy zgłoszone wyniki w kolumnie wyników są zgodne z oczekiwaniami dotyczącymi kodu. W przypadku testów, które nie powiodą się, należy odpowiednio naprawić kod. Następnie uruchom ponownie IntelliTest, aby sprawdzić poprawność poprawek.

## <a name="persist-save-the-unit-tests-as-a-regression-suite"></a>Persist: Zapisz testy jednostkowe jako pakiet regresji

1. Wybierz wiersze danych, które chcesz zapisać za pomocą sparametryzowanego testu jednostkowego w projekcie testowym.

     ![Wybierz testy; prawym&#45;kliknij i wybierz pozycję Zapisz](../test/media/savepextests.png)

     Można wyświetlić projekt testowy i sparametryzowany test jednostkowy, który został utworzony - poszczególne testy jednostkowe, odpowiadające każdemu z wierszy, są zapisywane w pliku *.g.cs* w projekcie testowym, a sparametryzowany test jednostkowy jest zapisywany w odpowiednim pliku *cs.* Można uruchomić testy jednostkowe i wyświetlić wyniki z Eksploratora testów, tak samo jak w przypadku testów jednostkowych utworzonych ręcznie.

     ![Otwórz plik klasy w metodzie testowej, aby wyświetlić test jednostkowy](../test/media/testmethodpex.png)

     Wszelkie niezbędne odwołania są również dodawane do projektu testowego.

     Jeśli kod metody ulegnie zmianie, uruchom ponownie IntelliTest, aby zachować synchronizację testów jednostkowych ze zmianami.

## <a name="assist-use-intellitest-to-focus-code-exploration"></a>Asysta: Użyj intellitestu, aby skupić się na eksploracji kodu

1. Jeśli masz bardziej złożony kod, IntelliTest pomaga w skupieniu eksploracji kodu. Na przykład jeśli masz metodę, która ma interfejs jako parametr i istnieje więcej niż jedna klasa, która implementuje tego interfejsu, IntelliTest odnajduje te klasy i zgłasza ostrzeżenie.

     Wyświetl ostrzeżenia, aby zdecydować, co chcesz zrobić.

     ![Wyświetlanie ostrzeżeń](../test/media/pexviewwarning.png)

2. Po zbadaniu kodu i zrozumieć, co chcesz przetestować, można rozwiązać ostrzeżenie, aby wybrać klasy, które mają być używane do testowania interfejsu.

     ![Prawym&#45;kliknij ostrzeżenie i wybierz pozycję Napraw](../test/media/pexfixwarning.png)

     Ten wybór zostanie dodany do pliku *PexAssemblyInfo.cs.*

     `[assembly: PexUseType(typeof(Camera))]`

3. Teraz można ponownie uruchomić IntelliTest do generowania sparametryzowany test jednostki i dane testowe tylko przy użyciu klasy, które zostały ustalone.

     ![Uruchom ponownie test IntelliTest w celu wygenerowania danych testowych](../test/media/pexwarningsfixed.png)

## <a name="specify-use-intellitest-to-validate-correctness-properties-that-you-specify-in-code"></a>Określ: Użyj testu IntelliTest, aby sprawdzić poprawność właściwości poprawności, które określisz w kodzie

Określ ogólną relację między wejściami i wyjściami, które mają zostać sprawdzone przez wygenerowane testy jednostkowe. Ta specyfikacja jest hermetyzowana w metodzie, która wygląda jak metoda testowa, ale jest powszechnie określana ilościowo. Jest to sparametryzowana metoda testu jednostkowego i wszelkie potwierdzenia, które należy przechowywać dla wszystkich możliwych wartości wejściowych, które IntelliTest może generować.

## <a name="q--a"></a>Pytania i odpowiedzi

### <a name="q-can-you-use-intellitest-for-unmanaged-code"></a>Pyt.: Czy można użyć IntelliTest dla niezarządzanego kodu?

**Odp.:** Nie, IntelliTest działa tylko z kodem zarządzanym.

### <a name="q-when-does-a-generated-test-pass-or-fail"></a>Pyt.: Kiedy wygenerowany test zakończy się niepowodzeniem lub niepowodzeniem?

**Odp.:** Przechodzi jak każdy inny test jednostkowy, jeśli nie występują żadne wyjątki. Kończy się niepowodzeniem, jeśli asercja nie powiedzie się lub jeśli kod w ramach testu zgłasza nieobsługiwał wyjątek.

Jeśli masz test, który może przejść, jeśli są generowane pewne wyjątki, można ustawić jeden z następujących atrybutów na podstawie wymagań na poziomie metody testowej, klasy testu lub zestawu:

- **PexAllowedExceptionAttribute (Atrybut PexAllowedExceptionAttribute)**

- **PexAllowedExceptionFromTypeAttribute**

- **PexAllowedExceptionFromTypeUnderTestAttribute**

- **PexAllowedExceptionFromAssemblyAttribute**

### <a name="q-can-i-add-assumptions-to-the-parameterized-unit-test"></a>Pyt.: Czy mogę dodać założenia do sparametryzowanego testu jednostkowego?

**Odp.:** Tak, należy użyć założeń, aby określić, które dane testowe nie są wymagane dla testu jednostkowego dla określonej metody. Użyj <xref:Microsoft.Pex.Framework.PexAssume> klasy, aby dodać założenia. Na przykład można dodać założenie, `lengths` że zmienna nie jest null tak:

`PexAssume.IsNotNull(lengths);`

Jeśli dodasz założenie i ponownie uruchom IntelliTest, dane testowe, które nie są już istotne zostaną usunięte.

### <a name="q-can-i-add-assertions-to-the-parameterized-unit-test"></a>Pyt.: Czy mogę dodać potwierdzenia do sparametryzowanego testu jednostkowego?

**Odp.:** Tak, IntelliTest sprawdzi, że to, co potwierdzasz w instrukcji jest w rzeczywistości poprawne, gdy uruchamia testy jednostkowe. Użyj <xref:Microsoft.Pex.Framework.PexAssert> klasy lub interfejsu API potwierdzenia, który jest dostarczany z platformą testów, aby dodać potwierdzenia. Na przykład można dodać twierdzenie, że dwie zmienne są równe.

`PexAssert.AreEqual(a, b);`

Jeśli dodasz asercja i ponownie uruchom IntelliTest, sprawdzi, czy twierdzenie jest prawidłowe, a test zakończy się niepowodzeniem, jeśli nie jest.

### <a name="q-can-i-generate-parameterized-unit-tests-without-running-intellitest-first"></a><a name="NoRun"></a>Pyt.: Czy można wygenerować sparametryzowane testy jednostkowe bez uruchamiania IntelliTest pierwszy?

**Odp.:** Tak, kliknij prawym przyciskiem myszy w klasie lub metodzie, a następnie wybierz polecenie **Utwórz intellitest**.

![Prawym&#45;kliknięcie edytora, wybierz pozycję Utwórz test IntelliTest](../test/media/pexcreateintellitest.png)

Zaakceptuj domyślny format, aby wygenerować testy lub zmienić sposób, w jaki projekt i testy są nazwane. Można utworzyć nowy projekt testowy lub zapisać testy w istniejącym projekcie.

![Tworzenie intellitestu przy domyślnym mstestze](../test/media/pexcreateintellitestmstest.png)

<a name="extend-framework"></a>
### <a name="q-can-i-use-other-unit-test-frameworks-with-intellitest"></a>Pyt.: Czy można użyć innych jednostek testowych z IntelliTest?

**Odp.:** Tak, wykonaj następujące kroki, aby [znaleźć i zainstalować inne struktury](../test/install-third-party-unit-test-frameworks.md).
Rozszerzenia struktury testów są również dostępne w programie Visual Studio Marketplace, na przykład [NUnit Test Generator](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371).

Po ponownym uruchomieniu programu Visual Studio i ponownym otwarciu rozwiązania kliknij prawym przyciskiem myszy klasę lub metodę, a następnie wybierz polecenie **Utwórz intellitest**. Wybierz zainstalowaną strukturę tutaj:

![Wybierz inną strukturę testów jednostkowych dla IntelliTest](../test/media/pexcreateintellitestextensions.png)

Następnie uruchom IntelliTest do generowania poszczególnych testów jednostkowych w odpowiednich plikach *.g.cs.*

### <a name="q-can-i-learn-more-about-how-the-tests-are-generated"></a>Pyt.: Czy mogę dowiedzieć się więcej o tym, jak testy są generowane?

**Odp.:** Tak, aby uzyskać ogólny przegląd, przeczytaj ten [wpis na blogu](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/).
