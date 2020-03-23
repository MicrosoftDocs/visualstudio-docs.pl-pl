---
title: Ostrzeżenia i błędy | Narzędzie testowe Microsoft IntelliTest Developer
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Warnings and errors
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c3f5fe55a4e1afb1a9551d43d0d61ae9f76b81e4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77275436"
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

* **Domeny lub środowisko wykonawcze**
  * [Potrzebujesz pomocy w konstruowaniu obiektu](#help-construct)
  * [Potrzebujesz pomocy w znajdowaniu typów](#help-types)
  * [Typ użytkowy Odgadnięty](#usable-type-guessed)

* **Wykonanie**
  * [Nieoczekiwany błąd podczas eksploracji](#unexpected-exploration)
  * [TargetInvocationException](#targetinvocationexception)

* **Instrumentacji**
  * [Nieinstrumentowana metoda wywoływana](#uninstrumented-method-called)
  * [Metoda zewnętrzna wywoływana](#external-method-called)
  * [Metoda nierozerwalna wywoływana](#uninstrumentable-method-called)
  * [Problem z testowalnością](#testability-issue)
  * [Ograniczenia](#limitation)

* **Interpreter**
  * [Obserwowana niezgodność połączeń](#observed-call-mismatch)
  * [Wartość przechowywana w polu statycznym](#value-static-field)

<a name="maxbranches-exceeded"></a>
## <a name="maxbranches-exceeded"></a>Przekroczono wartość MaxBranches

IntelliTest ogranicza długość każdej ścieżki wykonywania, która eksploruje podczas [generowania danych wejściowych.](input-generation.md) Ta funkcja zapobiega IntelliTest staje się nie odpowiada, gdy program przechodzi w nieskończoną pętlę.

Każda warunkowa i bezwarunkowa gałąź wykonanego i monitorowanego kodu jest wliczona do tego limitu, w tym gałęzi, które nie zależą od danych wejściowych [sparametryzowanego testu jednostkowego](test-generation.md#parameterized-unit-testing).

Na przykład następujący kod zużywa gałęzie w kolejności 100:

```csharp
for (int i=0; i<100; i++) { }
```

Można edytować opcję **MaxBranches** atrybutu uzyskanego z **PexSettingsAttributeBase**, takiego jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Poniższy przykład skutecznie usuwa ten związany:

```csharp
[PexMethod(MaxBranches=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Można również ustawić **TestExcludePathBoundsExceeded** opcja poinformować IntelliTest, jak ogólnie radzić sobie z tymi problemami.

W kodzie testowym można użyć [PexSymbolicValue,](static-helper-classes.md#pexsymbolicvalue) aby zignorować ograniczenia generowane przez warunek pętli:

```csharp
for (int i=0;
    PexSymbolicValue.Ignore(i<100); // IntelliTest will 'forget' about this path condition
    i++)
{ }
```

<a name="maxconstraintsolvertime-exceeded"></a>
## <a name="maxconstraintsolvertime-exceeded"></a>Przekroczono wartość MaxConstraintSolverTime

IntelliTest używa [solver ograniczenia](input-generation.md#constraint-solver) do obliczania nowych danych wejściowych testu. Rozwiązywanie ograniczeń może być bardzo czasochłonnym procesem, więc IntelliTest pozwala na skonfigurowanie granic - w szczególności **MaxConstraintSolverTime**.

W przypadku wielu aplikacji znaczne zwiększenie limitu czasu nie spowoduje lepszego zasięgu. Powodem tego jest to, że większość limitów czasu są spowodowane przez systemy ograniczeń, które nie mają rozwiązań. Jednak IntelliTest może nie być w stanie ustalić, że jest niespójne bez wypróbowania wszystkich możliwych rozwiązań, co spowoduje limit czasu.

<a name="maxconditions-exceeded"></a>
## <a name="maxconditions-exceeded"></a>Przekroczono wartość MaxConditions

IntelliTest ogranicza długość każdej ścieżki wykonywania, która eksploruje podczas [generowania danych wejściowych.](input-generation.md) Ta funkcja zapobiega, aby intellitest przestał odpowiadać, gdy program wejdzie w nieskończoną pętlę.

Każda gałąź warunkowa, która zależy od danych wejściowych [sparametryzowanego testu jednostkowego,](test-generation.md#parameterized-unit-testing) jest wliczona do tego limitu.

Na przykład każda ścieżka w poniższym kodzie zużywa **n +1** warunki:

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

Można edytować opcję **MaxConditions** atrybutu uzyskanego z **PexSettingsAttributeBase**, takiego jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Przykład:

```csharp
[PexMethod(MaxConditions=10000)]
void ParameterizedTest(int n) {
    // ...
}
```

Można również ustawić **TestExcludePathBoundsExceeded** opcja poinformować IntelliTest jak ogólnie radzić sobie z tymi problemami.

Za pomocą [funkcji PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) można zignorować ograniczenia generowane przez warunek pętli:

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

IntelliTest ogranicza długość każdej ścieżki wykonywania, która eksploruje podczas [generowania danych wejściowych.](input-generation.md) Ta funkcja zapobiega intellitest staje się nie odpowiada, gdy program przechodzi wchodzi nieskończoną pętlę.

Każde wywołanie (bezpośrednie, pośrednie, wirtualne lub skok) wykonanego i monitorowanego kodu jest wliczane do tego limitu.

Można edytować opcję **MaxCalls** atrybutu uzyskanego z **PexSettingsAttributeBase**, takiego jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Poniższy przykład skutecznie usuwa ten związany:

```csharp
[PexMethod(MaxCalls=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Można również ustawić **TestExcludePathBoundsExceeded** opcja poinformować IntelliTest jak ogólnie radzić sobie z tymi problemami.

<a name="maxstack-exceeded"></a>
## <a name="maxstack-exceeded"></a>Przekroczono wartość MaxStack

IntelliTest ogranicza rozmiar stosu wywołań dowolnej ścieżki wykonywania, która eksploruje podczas [generowania danych wejściowych.](input-generation.md) Ta funkcja zapobiega IntelliTest z zakończenia, gdy występuje przepełnienie stosu.

Można edytować opcję **MaxStack** atrybutu uzyskanego z **PexSettingsAttributeBase**, takiego jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Poniższy przykład skutecznie usuwa ten związany (nie zalecane):

```csharp
[PexMethod(MaxStack=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Można również ustawić **TestExcludePathBoundsExceeded** opcja poinformować IntelliTest jak ogólnie radzić sobie z tymi problemami.

<a name="maxruns-exceeded"></a>
## <a name="maxruns-exceeded"></a>Przekroczono wartość MaxRuns

IntelliTest ogranicza liczbę ścieżek wykonywania, które eksploruje podczas [generowania danych wejściowych.](input-generation.md) Ta funkcja zapewnia, że IntelliTest kończy się, gdy program ma pętle lub rekursji.

Nie może być tak, że za każdym razem IntelliTest uruchamia test sparametryzowany z określonymi wejściami, emituje nowy przypadek testowy. Zobacz [TestEmissionFilter aby](exploration-bounds.md#testemissionfilter) uzyskać więcej informacji.

Można edytować opcję **MaxRuns** atrybutu uzyskanego z **PexSettingsAttributeBase**, takiego jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Poniższy przykład skutecznie usuwa ten związany (nie zalecane):

```csharp
[PexMethod(MaxRuns=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="maxrunswithoutnewtests-exceeded"></a>
## <a name="maxrunswithoutnewtests-exceeded"></a>Przekroczono wartość MaxRunsWithoutNewTests

IntelliTest ogranicza liczbę ścieżek wykonywania, które eksploruje podczas [generowania danych wejściowych.](input-generation.md) Ta funkcja zapewnia, że IntelliTest kończy się, gdy program ma pętle lub rekursji.

Nie może być tak, że za każdym razem IntelliTest uruchamia test sparametryzowany z określonymi wejściami, emituje nowy przypadek testowy. Zobacz [TestEmissionFilter aby](exploration-bounds.md#testemissionfilter) uzyskać więcej informacji.

Chociaż IntelliTest często znajduje wiele interesujących danych wejściowych testowych początkowo, może nie - po pewnym czasie - emitować więcej testów. Ta opcja określa, jak długo IntelliTest może próbować znaleźć inny odpowiedni test danych wejściowych.

Można edytować opcję **MaxRunsWithoutNewTests** atrybutu uzyskanego z **PexSettingsAttributeBase**, takiego jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Poniższy przykład skutecznie usuwa ten związany (nie zalecane):

```csharp
[PexMethod(MaxRunsWithoutNewTests=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="cannot-concretize-solution"></a>
## <a name="cannot-concretize-solution"></a>Nie można skonkretyzować rozwiązania

Ten błąd jest często konsekwencją wcześniejszego błędu. IntelliTest używa [solver ograniczenia](input-generation.md#constraint-solver) do określenia nowych danych wejściowych testu. Czasami dane wejściowe testowe proponowane przez [solver ograniczeń](input-generation.md#constraint-solver) są nieprawidłowe. Może się tak zdarzyć, gdy:

* pewne ograniczenia nie są znane
* jeśli wartości są tworzone w sposób zdefiniowany przez użytkownika, co powoduje wystąpienie błędów w kodzie użytkownika
* niektóre z zaangażowanych typów mają logikę inicjowania nie kontrolowaną przez IntelliTest (na przykład klasy COM)

<a name="help-construct"></a>
## <a name="need-help-to-construct-object"></a>Potrzebna jest pomoc przy konstruowaniu obiektu

IntelliTest [generuje dane wejściowe testowe,](input-generation.md)a niektóre dane wejściowe mogą być obiektami z polami.
W tym miejscu IntelliTest próbuje wygenerować wystąpienie klasy, która ma pole prywatne i zakłada, że ciekawe zachowanie programu wystąpi, gdy to pole prywatne ma określoną wartość.

Jednak chociaż jest to możliwe w za pomocą reflection, IntelliTest nie produkuje obiektów z dowolnej wartości pola.
Zamiast tego w takich przypadkach opiera się na użytkownika, aby zapewnić wskazówki dotyczące sposobu używania publicznych metod klasy do tworzenia obiektu i doprowadzić go do stanu, w którym jego pole prywatne ma żądaną wartość.

Przeczytaj [tworzenie wystąpienia istniejących klas,](input-generation.md#existing-classes) aby dowiedzieć się, jak możesz pomóc IntelliTest konstruować ciekawe obiekty.

<a name="help-types"></a>
## <a name="need-help-to-find-types"></a>Potrzebna jest pomoc przy znajdowaniu typów

IntelliTest [generuje dane wejściowe testowe](input-generation.md) dla dowolnego typu .NET. W tym miejscu IntelliTest próbuje utworzyć wystąpienie, które pochodzi z klasy abstrakcyjnej lub implementuje interfejs abstrakcyjny, a IntelliTest nie wie o dowolnym typie, który spełnia ograniczenia.

IntelliTest można pomóc, wskazując jeden lub więcej typów, które pasują do ograniczeń. Zwykle jeden z następujących atrybutów pomoże:

* **PexUseTypeAttribute**, który wskazuje na określony typ.

  Na przykład jeśli IntelliTest zgłasza, że "nie zna żadnych typów przypisanych do **System.Collections.IDictionary**", można pomóc, dołączając następujący **atrybut PexUseTypeAttribute** do testu (lub do klasy urządzenia):

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

IntelliTest [generuje dane wejściowe testowe](input-generation.md) dla wszystkich typów .NET. Gdy typ jest abstrakcyjny lub interfejs, IntelliTest musi wybrać określoną implementację tego typu. Aby dokonać tego wyboru, musi wiedzieć, które typy istnieją.

Gdy to ostrzeżenie jest wyświetlane, wskazuje, że IntelliTest spojrzał na niektóre zestawy, do których istnieją odwołania i znaleźć typ implementacji, ale nie jest pewien, czy należy użyć tego typu lub jeśli istnieją bardziej odpowiednie typy dostępne gdzie indziej. IntelliTest po prostu wybrał typ, który wyglądał obiecująco.

Aby uniknąć tego ostrzeżenia, można zaakceptować wybór typu IntelliTest lub pomóc IntelliTest w użyciu innych typów, dodając odpowiedni [PexUseType](attribute-glossary.md#pexusetype).

<a name="unexpected-exploration"></a>
## <a name="unexpected-failure-during-exploration"></a>Nieoczekiwany błąd podczas eksploracji

Nieoczekiwany wyjątek został przechwycony podczas eksplorowania testu.

[Zgłoś to jako błąd](#report-bug).

<a name="targetinvocationexception"></a>
## <a name="targetinvocationexception"></a>TargetInvocationException

Wystąpił wyjątek w kodzie użytkownika. Sprawdź ślad stosu i usuń błąd w kodzie.

<a name="uninstrumented-method-called"></a>
## <a name="uninstrumented-method-called"></a>Wywołano niezinstrumentowaną metodę

IntelliTest [generuje dane wejściowe testowe](input-generation.md) przez monitorowanie wykonywania programu. Istotne jest, że odpowiedni kod jest prawidłowo instrumentowane, dzięki czemu IntelliTest można monitorować jego zachowanie.

To ostrzeżenie pojawia się, gdy instrumentowany kod wywołuje metody w innym, nieinstrumentowanym zestawie.
Jeśli chcesz IntelliTest do eksplorowania interakcji obu, należy również instrument innego zestawu (lub jego części).

<a name="external-method-called"></a>
## <a name="external-method-called"></a>Wywołano metodę zewnętrzną

IntelliTest [generuje dane wejściowe testowe](input-generation.md) przez monitorowanie wykonywania aplikacji .NET.
IntelliTest nie może generować znaczących danych wejściowych testowych dla kodu, który nie jest napisany w języku .NET.

To ostrzeżenie pojawia się, gdy instrumentowany kod wywołuje niezarządzaną, natywną metodę, którą IntelliTest nie może analizować. Jeśli chcesz IntelliTest do eksplorowania interakcji obu, należy mock metody niezarządzane.

<a name="uninstrumentable-method-called"></a>
## <a name="uninstrumentable-method-called"></a>Wywołano metodę bez możliwości instrumentacji

IntelliTest [generuje dane wejściowe testowe](input-generation.md) przez monitorowanie wykonywania aplikacji .NET. Istnieją jednak pewne metody, które ze względów technicznych IntelliTest nie może monitorować . Na przykład IntelliTest nie może monitorować konstruktora statycznego.

To ostrzeżenie pojawia się, gdy instrumentowany kod wywołuje metodę, która IntelliTest nie może monitorować.

<a name="testability-issue"></a>
## <a name="testability-issue"></a>Problem z testowalnością

IntelliTest [generuje dane wejściowe testowe,](input-generation.md) monitorując wykonanie programu. Może generować odpowiednie dane wejściowe testu tylko wtedy, gdy program jest deterministyczny i gdy odpowiednie zachowanie jest kontrolowane przez dane wejściowe testu.

To ostrzeżenie pojawia się, ponieważ podczas wykonywania przypadku testowego została wywołana metoda, która zachowuje się niedeterministycznie lub współdziała ze środowiskiem. Przykładami są metody **System.Random** i **System.IO.File**. Jeśli chcesz IntelliTest do tworzenia znaczących danych wejściowych testowych, należy mock metody, które IntelliTest flagi jako problemy z testowaniem.

<a name="limitation"></a>
## <a name="limitation"></a>Ograniczenia

IntelliTest [generuje dane wejściowe testowe](input-generation.md) przy użyciu [solvera ograniczeń](input-generation.md#constraint-solver).
Istnieją jednak pewne operacje, które wykraczają poza zakres [solvera ograniczeń](input-generation.md#constraint-solver).
Obecnie obejmuje to:

* większość operacji zmiennoprzecinkowych (tylko niektóre arytmetyczne liniowe są obsługiwane w liczbach zmiennoprzecinkowych)
* konwersje między liczbami zmiennoprzecinkowymi a liczbami całkowitymi
* wszystkie operacje typu **System.Decimal**

To ostrzeżenie pojawia się, gdy wykonany kod wykonuje operację lub wywołuje metodę, która IntelliTest nie może zinterpretować.

<a name="observed-call-mismatch"></a>
## <a name="observed-call-mismatch"></a>Zaobserwowano niezgodność wywołań

IntelliTest [generuje dane wejściowe testowe](input-generation.md) przez monitorowanie wykonywania programu. Jednak IntelliTest może nie być w stanie monitorować wszystkie instrukcje. Na przykład nie może monitorować kodu macierzystego i nie może monitorować kodu, który nie jest instrumentowany.

Gdy IntelliTest nie może monitorować kodu, nie może generować danych wejściowych testowych, które są istotne dla tego kodu.
Często IntelliTest nie jest świadomy faktu, że nie można monitorować metody, dopóki wywołanie tej metody zwraca. Jednak przyczyną tego ostrzeżenia jest:

* IntelliTest monitorował niektóre kody, które zainicjowały wywołanie metody nieinstrumentacji
* Nieinstrumentowana metoda zwana metodą, która jest instrumentowana
* IntelliTest monitoruje metodę instrumentamencie, która została wywołana

IntelliTest nie wie, co nieinstrumentowane metody pośredniej nie, więc może nie być w stanie wygenerować danych wejściowych testowych, które są istotne dla zagnieżdżonych wywoływania instrumentowane.

<a name="value-static-field"></a>
## <a name="value-stored-in-static-field"></a>Wartość przechowywana w polu statycznym

IntelliTest może systematycznie określać [odpowiednie dane wejściowe testu](input-generation.md) tylko wtedy, gdy test jednostkowy jest deterministyczny; innymi słowy, zawsze zachowuje się w ten sam sposób dla tych samych danych wejściowych testu. W szczególności oznacza to, że test powinien pozostawić system w stanie, który pozwala na ponowne wykonanie tego testu.
W idealnym przypadku test jednostkowy nie powinien zmieniać żadnego stanu globalnego, ale wszystkie interakcje z globals powinny być wyśmiewane.

To ostrzeżenie wskazuje, że pole statyczne zostało zmienione; może to sprawić, że test będzie zachowywał się niedeterministycznie.

W niektórych sytuacjach zmiana pola statycznego jest dopuszczalna:

* gdy dane wejściowe testu powodują, że kod ustawień lub oczyszczania cofa zmianę
* gdy pole jest inicjowane tylko raz, a wartość nie zmienia się później

<a name="report-bug"></a>

## <a name="got-feedback"></a>Chcesz przesłać opinię?

Opublikuj swoje pomysły i sugestie funkcji w [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
