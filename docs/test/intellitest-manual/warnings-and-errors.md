---
title: Ostrzeżenia i błędy | Narzędzie testowe dla deweloperów Microsoft IntelliTest
description: Ten artykuł zawiera IntelliTest ostrzeżenia i błędy, podzielone na kategorie z opisami poszczególnych ostrzeżeń i błędów.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Warnings and errors
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d72ee803389c692233478d742dadbcf514a3a036
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668069"
---
# <a name="warnings-and-errors"></a>Ostrzeżenia i błędy

## <a name="warnings-and-errors-by-category"></a>Ostrzeżenia i błędy według kategorii

* **Granice**
  * [Przekroczono wartość MaxBranches](#maxbranches-exceeded)
  * [Przekroczono wartość MaxConstraintSolverTime](#maxconstraintsolvertime-exceeded)
  * [Przekroczono wartość MaxConditions](#maxconditions-exceeded)
  * [Przekroczono wartość MaxCalls](#maxcalls-exceeded)
  * [Przekroczono wartość MaxStack](#maxstack-exceeded)
  * [Przekroczono wartość MaxRuns](#maxruns-exceeded)
  * [Przekroczono wartość MaxRunsWithoutNewTests](#maxrunswithoutnewtests-exceeded)

* **Rozwiązywanie ograniczeń**
  * [Nie można skonkretyzować rozwiązania](#cannot-concretize-solution)

* **Domeny lub środowisko uruchomieniowe**
  * [Potrzebna pomoc dla konstruowania obiektu](#help-construct)
  * [Potrzebujesz pomocy w znalezieniu typów](#help-types)
  * [Typ możliwych do użycia](#usable-type-guessed)

* **Wykonanie**
  * [Nieoczekiwany błąd podczas eksploracji](#unexpected-exploration)
  * [TargetInvocationException](#targetinvocationexception)

* **WMI**
  * [Wywołana metoda bez Instrumentacji](#uninstrumented-method-called)
  * [Wywołana metoda zewnętrzna](#external-method-called)
  * [Wywołana metoda bezinstrumentowa](#uninstrumentable-method-called)
  * [Problem z testowaniem](#testability-issue)
  * [Ograniczenie](#limitation)

* **Interpretera**
  * [Obserwowana niezgodność wywołań](#observed-call-mismatch)
  * [Wartość przechowywana w polu statycznym](#value-static-field)

<a name="maxbranches-exceeded"></a>
## <a name="maxbranches-exceeded"></a>Przekroczono wartość MaxBranches

IntelliTest ogranicza długość dowolnej ścieżki wykonywania badanej podczas [generowania danych wejściowych](input-generation.md). Ta funkcja zapobiega niereagowaniu IntelliTest, gdy program przejdzie w nieskończoną pętlę.

Wszystkie warunkowe i bezwarunkowe rozgałęzienia wykonanego i monitorowanego kodu są zliczane do tego limitu, w tym gałęzie, które nie zależą od danych wejściowych [testów jednostkowych sparametryzowane](test-generation.md#parameterized-unit-testing).

Na przykład poniższy kod zużywa gałęzie w kolejności od 100:

```csharp
for (int i=0; i<100; i++) { }
```

Można edytować opcję **MaxBranches** atrybutu pochodnego od **PexSettingsAttributeBase**, takich jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Poniższy przykład skutecznie usuwa ten zakres:

```csharp
[PexMethod(MaxBranches=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Możesz również ustawić opcję **TestExcludePathBoundsExceeded** , aby informować IntelliTest o tym, jak ogólnie rozwiązać te problemy.

W kodzie testowym można użyć [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) do ignorowania ograniczeń generowanych przez warunek pętli:

```csharp
for (int i=0;
    PexSymbolicValue.Ignore(i<100); // IntelliTest will 'forget' about this path condition
    i++)
{ }
```

<a name="maxconstraintsolvertime-exceeded"></a>
## <a name="maxconstraintsolvertime-exceeded"></a>Przekroczono wartość MaxConstraintSolverTime

IntelliTest używa [funkcji ograniczającej ograniczenia](input-generation.md#constraint-solver) , aby obliczyć nowe dane wejściowe testu. Rozwiązywanie ograniczeń może być bardzo czasochłonne, więc IntelliTest umożliwia skonfigurowanie granic — w szczególności **MaxConstraintSolverTime**.

W przypadku wielu aplikacji znacznie zwiększenie limitu czasu nie spowoduje lepszego pokrycia. Przyczyną tego jest to, że większość limitów czasu jest spowodowana przez systemy ograniczeń, które nie mają rozwiązań. Niemniej jednak IntelliTest może nie być w stanie ustalić, że jest niespójna, bez konieczności ponawiania wszystkich możliwych rozwiązań, co spowoduje przekroczenie limitu czasu.

<a name="maxconditions-exceeded"></a>
## <a name="maxconditions-exceeded"></a>Przekroczono wartość MaxConditions

IntelliTest ogranicza długość dowolnej ścieżki wykonywania badanej podczas [generowania danych wejściowych](input-generation.md). Ta funkcja zapobiega niereagowaniu IntelliTest, gdy program wejdzie w nieskończoną pętlę.

Wszystkie gałęzie warunkowe, które są zależne od danych wejściowych [testu jednostkowego](test-generation.md#parameterized-unit-testing) , są zliczane do tego limitu.

Na przykład każda ścieżka w poniższym kodzie zużywa **n + 1** warunek:

```csharp
[PexMethod]
void ParameterizedTest(int n) {
    // conditions are "0<n", "1<n", ..., "!(n<n)"
    for (int i=0; i<n; i++)
    { ... }

    // irrelevant for MaxConditions, since conditions do not depend on input
    for (int i=0; i<100; i++)
    { ... }
}
```

Można edytować opcję **MaxConditions** atrybutu pochodnego od **PexSettingsAttributeBase**, takich jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Na przykład:

```csharp
[PexMethod(MaxConditions=10000)]
void ParameterizedTest(int n) {
    // ...
}
```

Możesz również ustawić opcję **TestExcludePathBoundsExceeded** , aby poinformować IntelliTest o tym, jak ogólnie rozwiązać te problemy.

Można użyć [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) do ignorowania ograniczeń generowanych przez warunek pętli:

```csharp
[PexMethod]
void ParameterizedTest(int n) {
    int nshadow = PexSymbolicValue.Ignore(n); // IntelliTest looses track of 'n'

    // irrevelant for MaxConditions, since nshadow is not related to input
    for (int i=0; i<nshadow; i++)
    {...}
}
```

<a name="maxcalls-exceeded"></a>
## <a name="maxcalls-exceeded"></a>Przekroczono wartość MaxCalls

IntelliTest ogranicza długość dowolnej ścieżki wykonywania badanej podczas [generowania danych wejściowych](input-generation.md). Ta funkcja zapobiega niereagowaniu IntelliTest, gdy program przejdzie w nieskończoną pętlę.

Każde wywołanie (bezpośrednie, pośrednie, wirtualne lub skok) wykonanego i monitorowanego kodu jest zliczane do tego limitu.

Można edytować opcję **MaxCalls** atrybutu pochodnego od **PexSettingsAttributeBase**, takich jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Poniższy przykład skutecznie usuwa ten zakres:

```csharp
[PexMethod(MaxCalls=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Możesz również ustawić opcję **TestExcludePathBoundsExceeded** , aby poinformować IntelliTest o tym, jak ogólnie rozwiązać te problemy.

<a name="maxstack-exceeded"></a>
## <a name="maxstack-exceeded"></a>Przekroczono wartość MaxStack

IntelliTest ogranicza rozmiar stosu wywołań dowolnej ścieżki wykonywania, którą bada podczas [generowania danych wejściowych](input-generation.md). Ta funkcja uniemożliwia zakończenie działania usługi IntelliTest w przypadku przepełnienia stosu.

Można edytować opcję **MaxStack** atrybutu pochodnego od **PexSettingsAttributeBase**, takich jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Poniższy przykład skutecznie usuwa to powiązanie (niezalecane):

```csharp
[PexMethod(MaxStack=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Możesz również ustawić opcję **TestExcludePathBoundsExceeded** , aby poinformować IntelliTest o tym, jak ogólnie rozwiązać te problemy.

<a name="maxruns-exceeded"></a>
## <a name="maxruns-exceeded"></a>Przekroczono wartość MaxRuns

IntelliTest ogranicza liczbę ścieżek wykonywania, które bada podczas [generowania danych wejściowych](input-generation.md). Ta funkcja zapewnia, że IntelliTest kończy się, gdy program ma pętle lub rekursję.

Może to nie być przypadek, który, za każdym razem, gdy IntelliTest uruchamia test sparametryzowany z konkretnymi danymi wejściowymi, emituje nowy przypadek testowy. Aby uzyskać więcej informacji, zobacz [TestEmissionFilter](exploration-bounds.md#testemissionfilter) .

Można edytować opcję **MaxRuns** atrybutu pochodnego od **PexSettingsAttributeBase**, takich jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Poniższy przykład skutecznie usuwa to powiązanie (niezalecane):

```csharp
[PexMethod(MaxRuns=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="maxrunswithoutnewtests-exceeded"></a>
## <a name="maxrunswithoutnewtests-exceeded"></a>Przekroczono wartość MaxRunsWithoutNewTests

IntelliTest ogranicza liczbę ścieżek wykonywania, które bada podczas [generowania danych wejściowych](input-generation.md). Ta funkcja zapewnia, że IntelliTest kończy się, gdy program ma pętle lub rekursję.

Może to nie być przypadek, który, za każdym razem, gdy IntelliTest uruchamia test sparametryzowany z konkretnymi danymi wejściowymi, emituje nowy przypadek testowy. Aby uzyskać więcej informacji, zobacz [TestEmissionFilter](exploration-bounds.md#testemissionfilter) .

Mimo że IntelliTest często znajduje wiele interesujących danych wejściowych testów, może nie być za chwilą i emitować więcej testów. Ta opcja określa, jak długo IntelliTest może próbować znaleźć inne odpowiednie dane wejściowe testu.

Można edytować opcję **MaxRunsWithoutNewTests** atrybutu pochodnego od **PexSettingsAttributeBase**, takich jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Poniższy przykład skutecznie usuwa to powiązanie (niezalecane):

```csharp
[PexMethod(MaxRunsWithoutNewTests=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="cannot-concretize-solution"></a>
## <a name="cannot-concretize-solution"></a>Nie można skonkretyzować rozwiązania

Ten błąd jest często wynikiem wcześniejszego błędu. IntelliTest używa [funkcji ograniczającej ograniczenia](input-generation.md#constraint-solver) , aby określić nowe dane wejściowe testu. Czasami dane wejściowe testów proponowane przez program do [rozwiązywania ograniczeń](input-generation.md#constraint-solver) są nieprawidłowe. Może się tak zdarzyć, gdy:

* Niektóre ograniczenia są nieznane
* Jeśli wartości są tworzone w sposób zdefiniowany przez użytkownika, powodując błędy występujące w kodzie użytkownika
* Niektóre z typów, których dotyczy logika inicjalizacji, nie są kontrolowane przez IntelliTest (na przykład klasy COM)

<a name="help-construct"></a>
## <a name="need-help-to-construct-object"></a>Potrzebna jest pomoc przy konstruowaniu obiektu

IntelliTest [generuje dane wejściowe testu](input-generation.md), a niektóre dane wejściowe mogą być obiektami z polami.
W tym miejscu IntelliTest próbuje wygenerować wystąpienie klasy zawierającej pole prywatne i założono, że w przypadku tego pola prywatnego zostanie wykonane ciekawe zachowanie programu.

Jednak chociaż jest to możliwe przy odbiciu, IntelliTest nie produkuje obiektów z dowolnymi wartościami pól.
Zamiast tego w takich przypadkach zależy od użytkownika, aby przedstawić wskazówki dotyczące sposobu używania metod publicznych klasy w celu utworzenia obiektu i przełączenia go do stanu, w którym jego pole prywatne ma wymaganą wartość.

Przeczytaj [Tworzenie wystąpienia istniejących klas](input-generation.md#existing-classes) , aby dowiedzieć się, jak można ułatwić IntelliTest konstruowanie interesujących obiektów.

<a name="help-types"></a>
## <a name="need-help-to-find-types"></a>Potrzebna jest pomoc przy znajdowaniu typów

IntelliTest [generuje dane wejściowe testów](input-generation.md) dla dowolnego typu .NET. W tym miejscu IntelliTest próbuje utworzyć wystąpienie pochodzące z klasy abstrakcyjnej lub implementuje interfejs abstrakcyjny, a IntelliTest nie wie o żadnym typie, który spełnia ograniczenia.

Możesz pomóc IntelliTest, wskazując jeden lub więcej typów, które pasują do ograniczeń. Zazwyczaj jeden z następujących atrybutów pomoże:

* **PexUseTypeAttribute**, który wskazuje na konkretny typ.

  Na przykład jeśli IntelliTest zgłasza, że "nie wie o żadnych typach, które można przypisać do **System. Collections. IDictionary**", można to pomóc poprzez dołączenie następującego **PexUseTypeAttribute** do testu (lub klasy osprzętu):

  ```csharp
  [PexMethod]
  [PexUseType(typeof(System.Collections.Hashtable))]
  public void MyTest(IDictionary[] dictionaries) { ... }
  ```

* **Atrybut na poziomie zestawu**

  ```csharp
  [assembly: PexUseType(typeof(System.Collections.Hashtable))]
  ```

<a name="usable-type-guessed"></a>
## <a name="usable-type-guessed"></a>Odgadnięto typ, którego można użyć

IntelliTest [generuje dane wejściowe testów](input-generation.md) dla dowolnego typu .NET. Gdy typ jest abstrakcyjny lub interfejs, IntelliTest musi wybrać określoną implementację tego typu. Aby to umożliwić, należy wiedzieć, które typy istnieją.

Gdy to ostrzeżenie jest wyświetlane, wskazuje, że IntelliTest wyglądało na niektórych przywoływanych zestawach i znalazł typ implementacji, ale nie ma pewności, czy powinien on korzystać z tego typu, czy też w innym miejscu dostępne są inne typy. IntelliTest po prostu wybierz typ, który ma wyszukiwane obietnice.

Aby uniknąć tego ostrzeżenia, można zaakceptować wybór typu IntelliTest lub pomóc IntelliTest w użyciu innych typów przez dodanie odpowiedniego [PexUseType](attribute-glossary.md#pexusetype).

<a name="unexpected-exploration"></a>
## <a name="unexpected-failure-during-exploration"></a>Nieoczekiwany błąd podczas eksploracji

Podczas eksplorowania testu przechwycono nieoczekiwany wyjątek.

[Zgłoś ten błąd jako usterkę](#report-bug).

<a name="targetinvocationexception"></a>
## <a name="targetinvocationexception"></a>TargetInvocationException

Wystąpił wyjątek w kodzie użytkownika. Zbadaj ślad stosu i Usuń usterkę w kodzie.

<a name="uninstrumented-method-called"></a>
## <a name="uninstrumented-method-called"></a>Wywołano niezinstrumentowaną metodę

IntelliTest [generuje dane wejściowe testów](input-generation.md) przez wykonanie programu monitorowania. Istotne jest, aby odpowiedni kod był prawidłowo instrumentem, dzięki czemu IntelliTest może monitorować jego zachowanie.

To ostrzeżenie jest wyświetlane, gdy kod Instrumentacji wywołuje metody z innego, nieinstrumentacja zestawu.
Jeśli chcesz, aby IntelliTest interakcje obu tych elementów, należy również instrumentować inne zestawy (lub ich części).

<a name="external-method-called"></a>
## <a name="external-method-called"></a>Wywołano metodę zewnętrzną

IntelliTest [generuje dane wejściowe testów](input-generation.md) przez monitorowanie wykonywania aplikacji .NET.
IntelliTest nie może wygenerować znaczących danych wejściowych testu dla kodu, który nie jest pisany w języku .NET.

To ostrzeżenie jest wyświetlane, gdy kod Instrumentacji wywołuje niezarządzaną metodę natywną, którą IntelliTest nie może przeanalizować. Jeśli chcesz, aby IntelliTest interakcje obu tych elementów, musisz zasymulować niezarządzaną metodę.

<a name="uninstrumentable-method-called"></a>
## <a name="uninstrumentable-method-called"></a>Wywołano metodę bez możliwości instrumentacji

IntelliTest [generuje dane wejściowe testów](input-generation.md) przez monitorowanie wykonywania aplikacji .NET. Istnieją jednak pewne metody, które ze względów technicznych nie mogą monitorować IntelliTest. Na przykład IntelliTest nie może monitorować statycznego konstruktora.

To ostrzeżenie jest wyświetlane, gdy kod Instrumentacji wywołuje metodę, którą nie może monitorować IntelliTest.

<a name="testability-issue"></a>
## <a name="testability-issue"></a>Problem z testowalnością

IntelliTest [generuje dane wejściowe testów](input-generation.md) przez monitorowanie wykonywania programu. Może generować tylko istotne dane wejściowe testu, gdy program jest deterministyczny i gdy odpowiednie zachowanie jest kontrolowane przez dane wejściowe testu.

To ostrzeżenie jest wyświetlane, ponieważ podczas wykonywania przypadku testowego wywołana została metoda, która zachowuje się niedeterministycznie lub współdziała ze środowiskiem. Przykłady to metody **System. Random** i **System. IO. File**. Jeśli chcesz, aby IntelliTest tworzyć znaczące dane wejściowe testów, musisz zasymulować metody, które IntelliTest flagi jako problemy z testowaniem.

<a name="limitation"></a>
## <a name="limitation"></a>Ograniczenie

IntelliTest [generuje dane wejściowe testów](input-generation.md) przy użyciu [funkcji ograniczenia Solver](input-generation.md#constraint-solver).
Istnieją jednak pewne operacje, które wykraczają poza zakres [funkcji ograniczenia](input-generation.md#constraint-solver).
Obecnie obejmuje to:

* Większość operacji zmiennoprzecinkowych (w liczbie zmiennoprzecinkowej jest obsługiwana tylko część arytmetyczna)
* Konwersje między liczbami zmiennoprzecinkowymi a liczbami całkowitymi
* wszystkie operacje na typie **System. Decimal**

To ostrzeżenie jest wyświetlane, gdy wykonany kod wykonuje operację lub wywołuje metodę, którą nie można zinterpretować IntelliTest.

<a name="observed-call-mismatch"></a>
## <a name="observed-call-mismatch"></a>Zaobserwowano niezgodność wywołań

IntelliTest [generuje dane wejściowe testów](input-generation.md) przez wykonanie programu monitorowania. Jednak IntelliTest może nie być w stanie monitorować wszystkich instrukcji. Na przykład nie może monitorować kodu natywnego i nie może monitorować kodu, który nie jest Instrumentacją.

Gdy IntelliTest nie może monitorować kodu, nie może wygenerować danych wejściowych testów, które są istotne dla tego kodu.
Często IntelliTest nie wie, że nie może monitorować metody do momentu, gdy wywołanie tej metody nie zwraca. Przyczyną tego ostrzeżenia jest jednak:

* IntelliTest monitorować jakiś kod, który zainicjował wywołanie metody bez instrumentu
* Metoda bez Instrumentacji nazywana metodą, która jest Instrumentacją
* IntelliTest monitoruje metodę instrumentową, która została wywołana

IntelliTest nie wie, jak Metoda pośrednia bezinstrumentacja zakończyła działanie, dlatego może nie być w stanie wygenerować danych wejściowych testów, które są istotne dla zagnieżdżonego wywołania Instrumentacji.

<a name="value-static-field"></a>
## <a name="value-stored-in-static-field"></a>Wartość przechowywana w polu statycznym

IntelliTest może systematycznie określić [istotne dane wejściowe testu](input-generation.md) tylko wtedy, gdy test jednostkowy jest deterministyczny; Innymi słowy, zawsze zachowuje ten sam sposób dla tych samych testów danych wejściowych. W szczególności oznacza to, że test powinien opuścić system w stanie, który umożliwia ponowne uruchomienie tego testu.
W idealnym przypadku test jednostkowy nie powinien zmieniać żadnego stanu globalnego, ale należy zasymulować wszystkie interakcje z Globals.

To ostrzeżenie wskazuje, że pole statyczne zostało zmienione; może to spowodować, że test zadziała niedeterministycznie.

W niektórych sytuacjach dopuszczalna jest zmiana pola statycznego:

* gdy dane wejściowe testu powodują, że Instalator lub kod czyszczący cofa zmiany
* gdy pole jest inicjowane tylko raz, a wartość nie zmienia się później

<a name="report-bug"></a>

## <a name="got-feedback"></a>Chcesz przesłać opinię?

Opublikuj swoje pomysły i sugestie funkcji w [społeczności deweloperów](https://aka.ms/feedback/suggest?space=8).
