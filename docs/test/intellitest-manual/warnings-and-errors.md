---
title: Ostrzeżenia i błędy | Narzędzie Test Microsoft IntelliTest dla deweloperów
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Warnings and errors
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: e6c58aa23e4b5c3133de2bee8f29b3205cf7aff9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942635"
---
# <a name="warnings-and-errors"></a>Ostrzeżenia i błędy

## <a name="warnings-and-errors-by-category"></a>Ostrzeżenia i błędy według kategorii

* **Granice**
  * [Przekroczono MaxBranches](#maxbranches-exceeded)
  * [Przekroczono MaxConstraintSolverTime](#maxconstraintsolvertime-exceeded)
  * [Przekroczono MaxConditions](#maxconditions-exceeded)
  * [Przekroczono MaxCalls](#maxcalls-exceeded)
  * [Przekroczono MaxStack](#maxstack-exceeded)
  * [Przekroczono MaxRuns](#maxruns-exceeded)
  * [MaxRunsWithoutNewTests exceeded](#maxrunswithoutnewtests-exceeded)<p />

* **Rozwiązywanie ograniczeń**
  * [Cannot Concretize Solution](#cannot-concretize-solution)<p />

* **Domains**
  * [Potrzebna pomoc do konstruowania obiektu](#help-construct)
  * [Potrzebujesz pomocy w celu odnalezienia typów](#help-types)
  * [Można używać typu złamać](#usable-type-guessed)<p />

* **Wykonanie**
  * [Nieoczekiwany błąd podczas eksploracji](#unexpected-exploration)
  * [TargetInvocationException](#targetinvocationexception)<p />

* **Instrumentacja**
  * [Niezinstrumentowanej metody o nazwie](#uninstrumented-method-called)
  * [Zewnętrzne metodę o nazwie](#external-method-called)
  * [Niemożliwy do Instrumentacji metodę o nazwie](#uninstrumentable-method-called)
  * [Problem z testowalnością](#testability-issue)
  * [Ograniczenie](#limitation)<p />

* **Interpreter**
  * [Zaobserwowana niezgodność wywołań](#observed-call-mismatch)
  * [Wartość przechowywana w polu statycznym](#value-static-field)

<a name="maxbranches-exceeded"></a>
## <a name="maxbranches-exceeded"></a>Przekroczono MaxBranches

IntelliTest ogranicza długość dowolną ścieżkę wykonywania, który pokazuje go podczas [wejściowych generowania](input-generation.md). Ta funkcja zapobiega IntelliTest przestanie odpowiadać, gdy program przechodzi w pętli nieskończonej.

Każdego rozgałęzienia warunkowego i bezwarunkowe wykonane i monitorowane kodu jest liczone kierunku ten limit, w tym gałęzi, które nie są zależne od dane wejściowe [sparametryzowanego testu jednostkowego](test-generation.md#parameterized-unit-testing).

Na przykład poniższy kod wykorzystuje gałęzie zgodnie z kolejnością 100:

```csharp
for (int i=0; i<100; i++) { }
```

Możesz edytować **MaxBranches** opcji atrybut pochodną **PexSettingsAttributeBase**, takich jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod) . Poniższy przykład usuwa skutecznie to powiązane:

```csharp
[PexMethod(MaxBranches=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Można również ustawić **TestExcludePathBoundsExceeded** opcję, aby poinformować program IntelliTest jak ogólnie do czynienia z tymi problemami.

W kodzie testu, można użyć [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) ignorowanie generowane przez warunek pętli ograniczenia:

```csharp
for (int i=0;
    PexSymbolicValue.Ignore(i<100); // IntelliTest will 'forget' about this path condition
    i++)
{ }
```

<a name="maxconstraintsolvertime-exceeded"></a>
## <a name="maxconstraintsolvertime-exceeded"></a>Przekroczono MaxConstraintSolverTime

Używa funkcji IntelliTest [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver) do obliczenia nowe dane wejściowe testu. Ograniczenie rozwiązywania może być procesem bardzo dużo czasu, więc IntelliTest umożliwia konfigurowanie granic — w szczególności **MaxConstraintSolverTime**.

W przypadku wielu aplikacji znaczne zwiększenie limitu czasu nie spowoduje lepszego pokrycia. Dzieje się większość przekroczeń limitu czasu są spowodowane ograniczenia systemów, na których brak rozwiązań. Jednak program IntelliTest nie może być możliwe ustalenie, czy jest on niezgodny bez próby wszystkie możliwe rozwiązania, które będą powodować przekroczenie limitu czasu.

<a name="maxconditions-exceeded"></a>
## <a name="maxconditions-exceeded"></a>Przekroczono MaxConditions

IntelliTest ogranicza długość dowolną ścieżkę wykonywania, który pokazuje go podczas [wejściowych generowania](input-generation.md). Ta funkcja zapobiega IntelliTest przestanie odpowiadać, gdy pole jest wypełniane wejścia w nieskończoną pętlę.

Każdej gałęzi warunkowej, który zależy od dane wejściowe [sparametryzowanego testu jednostkowego](test-generation.md#parameterized-unit-testing) jest liczony w kierunku tego limitu.

Na przykład, każda ścieżka w poniższym kodzie zużywa **n + 1** warunków:

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

Możesz edytować **MaxConditions** opcji atrybut pochodną **PexSettingsAttributeBase**, takich jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Na przykład:

```csharp
[PexMethod(MaxConditions=10000)]
void ParameterizedTest(int n) {
    // ...
}
```

Można również ustawić **TestExcludePathBoundsExceeded** opcję, aby poinformować program IntelliTest ogólnie radzenia sobie z tymi problemami.

Możesz użyć [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) ignorowanie generowane przez warunek pętli ograniczenia:

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
## <a name="maxcalls-exceeded"></a>Przekroczono MaxCalls

IntelliTest ogranicza długość dowolną ścieżkę wykonywania, który pokazuje go podczas [wejściowych generowania](input-generation.md). Ta funkcja zapobiega IntelliTest przestanie odpowiadać, gdy program przechodzi w pętli nieskończonej.

Każde wywołanie (bezpośrednie, pośrednie, wirtualnej lub przejść) wykonanych i monitorowane kodu jest liczone wobec tego limitu.

Możesz edytować **MaxCalls** opcji atrybut pochodną **PexSettingsAttributeBase**, takich jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Poniższy przykład usuwa skutecznie to powiązane:

```csharp
[PexMethod(MaxCalls=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Można również ustawić **TestExcludePathBoundsExceeded** opcję, aby poinformować program IntelliTest ogólnie radzenia sobie z tymi problemami.

<a name="maxstack-exceeded"></a>
## <a name="maxstack-exceeded"></a>Przekroczono MaxStack

IntelliTest ogranicza rozmiar stosu wywołań dowolną ścieżkę wykonywania, który pokazuje go podczas [wejściowych generowania](input-generation.md). Ta funkcja zapobiega IntelliTest przerywa, jeśli występuje przepełnienie stosu.

Możesz edytować **MaxStack** opcji atrybut pochodną **PexSettingsAttributeBase**, takich jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Poniższy przykład usuwa skutecznie tej granicy (niezalecane):

```csharp
[PexMethod(MaxStack=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Można również ustawić **TestExcludePathBoundsExceeded** opcję, aby poinformować program IntelliTest ogólnie radzenia sobie z tymi problemami.

<a name="maxruns-exceeded"></a>
## <a name="maxruns-exceeded"></a>Przekroczono MaxRuns

IntelliTest ogranicza liczbę ścieżek wykonywania, które analizuje go podczas [wejściowych generowania](input-generation.md). Ta funkcja pozwala zagwarantować, że IntelliTest kończy działanie, gdy program ma pętli lub rekursji.

Nie może być tak, że w każdym uruchomieniu programu IntelliTest test sparametryzowany określoną w danych wejściowych, emituje nowy przypadek testowy. Zobacz [TestEmissionFilter](exploration-bounds.md#testemissionfilter) Aby uzyskać więcej informacji.

Możesz edytować **MaxRuns** opcji atrybut pochodną **PexSettingsAttributeBase**, takich jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Poniższy przykład usuwa skutecznie tej granicy (niezalecane):

```csharp
[PexMethod(MaxRuns=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="maxrunswithoutnewtests-exceeded"></a>
## <a name="maxrunswithoutnewtests-exceeded"></a>MaxRunsWithoutNewTests exceeded

IntelliTest ogranicza liczbę ścieżek wykonywania, które analizuje go podczas [wejściowych generowania](input-generation.md). Ta funkcja pozwala zagwarantować, że IntelliTest kończy działanie, gdy program ma pętli lub rekursji.

Nie może być tak, że w każdym uruchomieniu programu IntelliTest test sparametryzowany określoną w danych wejściowych, emituje nowy przypadek testowy. Zobacz [TestEmissionFilter](exploration-bounds.md#testemissionfilter) Aby uzyskać więcej informacji.

Podczas testów funkcji IntelliTest znajdzie często wiele interesujące dane wejściowe testu początkowo, jego mogą nie - po chwili - emitować żadnych więcej testów. Ta opcja decyduje o tym, ile testów funkcji IntelliTest mogą próbować można znaleźć innego testu odpowiednie dane wejściowe.

Możesz edytować **MaxRunsWithoutNewTests** opcji atrybut pochodną **PexSettingsAttributeBase**, takich jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Poniższy przykład usuwa skutecznie tej granicy (niezalecane):

```csharp
[PexMethod(MaxRunsWithoutNewTests=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="cannot-concretize-solution"></a>
## <a name="cannot-concretize-solution"></a>Nie można skonkretyzować rozwiązania

Ten błąd jest często jego konsekwencję wcześniejszego błędu. Używa funkcji IntelliTest [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver) ustalenie nowe dane wejściowe testu. Czasami testowanie danych wejściowych proponowanych przez [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver) są nieprawidłowe. Taka sytuacja może wystąpić jeśli:

* Niektóre ograniczenia nie są znane.
* Jeśli wartości są tworzone w sposób zdefiniowany przez użytkownika, powodując błędy w kodzie użytkownika
* Niektóre typy, które są zaangażowane mają logiki inicjowania nie są kontrolowane przez funkcję IntelliTest (na przykład klasy COM)

<a name="help-construct"></a>
## <a name="need-help-to-construct-object"></a>Potrzebna pomoc do konstruowania obiektu

Funkcja IntelliTest [generuje dane wejściowe testu](input-generation.md), a niektóre dane wejściowe mogą być obiekty z polami.
W tym miejscu IntelliTest próbuje generowania wystąpienia klasy, która zawiera pole prywatne i przyjęto założenie, że interesujące zachowanie programu podczas wystąpi to prywatne pole ma określoną wartość.

Jednak gdy jest to możliwe za pomocą odbicia, IntelliTest nie produkcji obiekty z dowolnego pola wartościami.
Zamiast tego w takich przypadkach opiera się na użytkownika dostarczanie wskazówek na temat sposobu używania metody publiczne klasy utworzenia obiektu w celu dostosowania go do stanu, w której jej pola prywatnego ma wymaganą wartość.

Odczyt [wystąpienia istniejących klas](input-generation.md#existing-classes) Aby dowiedzieć się, jak możesz pomóc IntelliTest konstruowania interesujących obiektów.

<a name="help-types"></a>
## <a name="need-help-to-find-types"></a>Potrzebujesz pomocy w celu odnalezienia typów

Funkcja IntelliTest [generuje dane wejściowe testu](input-generation.md) dla dowolnego typu platformy .NET. W tym miejscu IntelliTest próbuje utworzyć wystąpienie, która pochodzi z klasy abstrakcyjnej lub implementuje abstrakcyjny interfejs i funkcji IntelliTest nie zna dowolnego typu, który spełnia ograniczenia.

Możesz pomóc IntelliTest poprzez wskazanie jednego lub więcej typów, które pasują do ograniczeń. Zazwyczaj jedną z następujących atrybutów pomoże:

* **PexUseTypeAttribute**, który wskazuje na określonego typu.

  Na przykład, jeśli program IntelliTest zgłasza, że "nie ma żadnych typów, które można przypisać do **System.Collections.IDictionary**", pomaga, dołączając następujące **PexUseTypeAttribute** do testu (lub do klasy początkowych):

  ```csharp
  [PexMethod]
  [PexUseType(typeof(System.Collections.Hashtable))]
  public void MyTest(IDictionary[] dictionaries) { ... }
  ```

* **Atrybut poziomu zestawu**

  ```csharp
  [assembly: PexUseType(typeof(System.Collections.Hashtable))]
  ```

<a name="usable-type-guessed"></a>
## <a name="usable-type-guessed"></a>Można używać typu złamać

Funkcja IntelliTest [generuje dane wejściowe testu](input-generation.md) dla wszystkich typów .NET. Gdy typ jest abstrakcyjny lub interfejs, IntelliTest musi wybrać określoną implementację tego typu. Aby wybrać, musi wiedzieć, jakie typy istnieje.

Jeśli to ostrzeżenie jest wyświetlane, it indiicates, że program IntelliTest przyglądaliśmy przywoływanych zestawach, a znaleziono typ implementacji, ale nie jest pewności, czy powinna korzystać, wpisz lub w przypadku bardziej odpowiednie typy były dostępe gdzie indziej. IntelliTest po prostu wybrać typu, która wyglądały obietnicy.

Aby uniknąć tego ostrzeżenia, można zaakceptować wybór typu dla funkcji IntelliTest, lub pomocy programu IntelliTest w użycie innych typów, dodając odpowiednią [PexUseType](attribute-glossary.md#pexusetype).

<a name="unexpected-exploration"></a>
## <a name="unexpected-failure-during-exploration"></a>Nieoczekiwany błąd podczas eksploracji

Przechwycono nieoczekiwany wyjątek podczas eksploracji testu.

Proszę [Zgłoś to jako usterkę](#report-bug).

<a name="targetinvocationexception"></a>
## <a name="targetinvocationexception"></a>TargetInvocationException

Wystąpił wyjątek w kodzie użytkownika. Sprawdź ślad stosu i usuwanie błędów w kodzie.

<a name="uninstrumented-method-called"></a>
## <a name="uninstrumented-method-called"></a>Niezinstrumentowanej metody o nazwie

Funkcja IntelliTest [generuje dane wejściowe testu](input-generation.md) dzięki monitorowaniu wykonywania programu. Istotne jest, że odpowiedni kod prawidłowo Instrumentacji tak, aby program IntelliTest można monitorować jego zachowanie.

To ostrzeżenie jest wyświetlane, gdy instrumentowanych kod wywołuje metody w zestawie innym, niezinstrumentowanej.
Chcąc IntelliTest, aby zapoznać się z interakcji zarówno, również muszą instrumentować innych zestawów (lub jej części).

<a name="external-method-called"></a>
## <a name="external-method-called"></a>Zewnętrzne metodę o nazwie

Funkcja IntelliTest [generuje dane wejściowe testu](input-generation.md) dzięki monitorowaniu wykonywania aplikacji .NET.
Funkcja IntelliTest nie można wygenerować dane wejściowe testu istotnych dla kodu, który nie został napisany w języku .NET.

To ostrzeżenie jest wyświetlane, gdy instrumentowanych kod wywołuje metodę niezarządzane, natywnej funkcji IntelliTest nie można przeanalizować. Chcąc IntelliTest, aby zapoznać się z interakcji zarówno musi testowanie metody niezarządzanego.

<a name="uninstrumentable-method-called"></a>
## <a name="uninstrumentable-method-called"></a>Niemożliwy do Instrumentacji metodę o nazwie

Funkcja IntelliTest [generuje dane wejściowe testu](input-generation.md) dzięki monitorowaniu wykonywania aplikacji .NET. Istnieją jednak niektóre metody, z przyczyn technicznych programu IntelliTest nie może monitorować. Na przykład programu IntelliTest nie może monitorować Konstruktor statyczny.

To ostrzeżenie jest wyświetlane, gdy instrumentowanych kod wywołuje metodę, która nie może monitorować IntelliTest.

<a name="testability-issue"></a>
## <a name="testability-issue"></a>Problem z testowalnością

Funkcja IntelliTest [generuje dane wejściowe testu](input-generation.md) dzięki monitorowaniu wykonywania programu. Dane wejściowe testu istotne może generować tylko, gdy program jest deterministyczna, a odpowiednie zachowanie jest kontrolowane przez dane wejściowe testu.

Ostrzeżenie to pojawia się, ponieważ, podczas wykonywania przypadku testowego, metoda została wywołana, działa w sposób niejednoznaczny, albo wchodzi w interakcje ze środowiskiem. Należą do nich metod **System.Random** i **System.IO.File**. Jeśli chcesz, aby program IntelliTest, aby utworzyć dane wejściowe testu znaczący, należy testowanie metody, które program IntelliTest flagi jako problemy z testowalnością.

<a name="limitation"></a>
## <a name="limitation"></a>Ograniczenie

Funkcja IntelliTest [generuje dane wejściowe testu](input-generation.md) przy użyciu [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver).
Istnieją jednak pewne operacje, które wykraczają poza zakres [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver).
Obecnie dotyczy to:

* operacje najczęściej zmiennoprzecinkowe (tylko niektóre liniowej arytmetyczny jest obsługiwany na liczb zmiennoprzecinkowych)
* konwersje między liczb zmiennoprzecinkowych i liczb całkowitych
* wszystkie operacje na **System.Decimal** typu

To ostrzeżenie jest wyświetlane, gdy wykonywany kod wykonuje operację lub wywołuje metodę, która nie może zinterpretować IntelliTest.

<a name="observed-call-mismatch"></a>
## <a name="observed-call-mismatch"></a>Zaobserwowana niezgodność wywołań

Funkcja IntelliTest [generuje dane wejściowe testu](input-generation.md) dzięki monitorowaniu wykonywania programu. Jednak program IntelliTest nie można monitorować wszystkie instrukcje. Na przykład nie można monitorować, kodu natywnego, a nie można monitorować, kod, który nie ma instrumentacji.

Funkcja IntelliTest nie może monitorować kodu, nie może generować dane wejściowe testu, które są istotne dla tego kodu.
Często programu IntelliTest nie są świadomi, że nie można go monitorować metody aż wywołanie tej metody zwraca. Jednak jest przyczyną tego ostrzeżenia:

* Funkcja IntelliTest monitorowane kodu, który zainicjował wywołanie niezinstrumentowanej metody
* Niezinstrumentowanej metody wywoływanej metody, która ma Instrumentacji
* Funkcja IntelliTest monitoruje instrumentowanych metodę, która została wywołana

IntelliTest nie zna co niezinstrumentowanej metody pośrednie zostały, więc może być możliwe wygenerowanie dane wejściowe testu, które są istotne dla zagnieżdżone instrumentowanej wywołania.

<a name="value-static-field"></a>
## <a name="value-stored-in-static-field"></a>Wartość przechowywana w polu statycznym

IntelliTest systematycznie można określić [dane wejściowe testu odpowiednie](input-generation.md) tylko podczas testów jednostkowych jest deterministyczna; innymi słowy, zawsze działa ten sam sposób dla tych samych wejściach testu. W szczególności oznacza to, test należy pozostawić system w stanie, który umożliwia ponowne wykonanie tego testu.
W idealnym przypadku testu jednostkowego nie należy zmieniać dowolny stan globalny, ale wszystkie interakcje z funkcje globalne powinny być w postaci makiet.

To ostrzeżenie wskazuje, że pole statyczne został zmieniony; Dzięki temu może być testu zachowują się w sposób niejednoznaczny.

W niektórych sytuacjach dopuszczalne jest zmienianie statycznego pola:

* gdy dane wejściowe testu powoduje, że Instalator lub oczyścić kod, aby cofnąć zmianę
* gdy pole jest inicjowane tylko raz, i wartość nie zmienia się później

<a name="report-bug"></a>

## <a name="got-feedback"></a>Czy chcesz przesłać opinię?

Opublikuj swoje pomysły i funkcji żądania na [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).