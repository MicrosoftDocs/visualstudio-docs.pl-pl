---
title: Wiązania eksploracji | Narzędzie Test Microsoft IntelliTest dla deweloperów
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Exploration bounds
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9d1ac08a2314119c924417191ca509a4bcd18021
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000659"
---
# <a name="exploration-bounds"></a>Wiązania eksploracji

**PexSettingsAttributeBase** jest abstrakcyjna klasa bazowa dla ustawienia granic jako atrybuty. Zobacz [kaskadowy model ustawień](settings-waterfall.md) omówienie ustawienia programu IntelliTest.

Aby zmodyfikować ustawienia, należy za pomocą nazwanych właściwości tej lokacji i jego atrybuty pochodne:

```csharp
[PexClass(MaxRuns = 10)]
public partial class FooTest {...}
```

* **Ograniczenie rozwiązywania granice**
  * [MaxConstraintSolverTime](#maxconstraintsolvertime) — liczba sekund [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver) ma odnajdywania danych wejściowych, które spowodują wykonanie inną ścieżkę należy postępować zgodnie.
  * [MaxConstraintSolverMemory](#maxconstraintsolvermemory) — rozmiar w megabajtach, [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver) może użyć do odnalezienia danych wejściowych.<p />
* **Eksploracja ścieżką granic**
  * [MaxBranches](#maxbranches) — maksymalna liczba gałęzi, które mogą zostać podjęte w ścieżce pojedyncze wykonanie.
  * [MaxCalls](#maxcalls) — maksymalna liczba wywołań, wprowadzone podczas ścieżką pojedynczego uruchomienia.
  * [MaxStack](#maxstack) — maksymalny rozmiar stosu w dowolnym momencie podczas ścieżką pojedynczego uruchomienia mierzony jako liczba ramek aktywnego połączenia.
  * [MaxConditions](#maxconditions) — maksymalna liczba warunków za pośrednictwem danych wejściowych, które mogą być sprawdzane podczas ścieżką pojedynczego uruchomienia.<p />
* **Wiązania eksploracji**
  * [MaxRuns](#maxruns) — maksymalna liczba uruchomień, które zostanie podjęta podczas eksploracji.
  * [MaxRunsWithoutNewTests](#maxrunswithoutnewtests) -maksymalną liczbę kolejnych uruchomień bez nowego testu jest emitowane.
  * [MaxRunsWithUniquePaths](#maxrunswithuniquepaths) — maksymalna liczba przebiegów ze ścieżkami unikatowy wykonywania, które zostanie podjęta podczas eksploracji.
  * [MaxExceptions](#maxexceptions) — maksymalna liczba wyjątków, które można znaleźć kombinacji wszystkich ścieżek odnalezionych wykonywania.<p />
* **Ustawienia generowania kodu zestawu testów**
  * [TestExcludePathBoundsExceeded](#testexcludepathboundsexceeded) — gdy ma wartość true, ścieżki wykonywania, które przekraczają znajdujących się w granicach ścieżki ([MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), [ MaxConditions](#maxconditions)) są ignorowane.
  * [TestEmissionFilter](#testemissionfilter) — wskazuje, w jakich okolicznościach IntelliTest, powinny wysyłać testów.
  * [TestEmissionBranchHits](#testemissionbranchhits) -Określa, ile testów funkcji IntelliTest emituje.

<a name="maxconstraintsolvertime"></a>
## <a name="maxconstraintsolvertime"></a>MaxConstraintSolverTime

Liczba sekund [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver) należy obliczyć danych wejściowych, które spowoduje, że ścieżki wykonywania nowe i zróżnicowane, podejmowane. Jest to opcja **PexSettingsAttributeBase** i jego typów pochodnych.

Głębiej tej funkcji IntelliTest analizuje ścieżki wykonywania programu, stają się bardziej złożonych systemów ograniczenia, które program IntelliTest kompilacje przepływu sterowania i przepływu danych programu. W zależności od Twojego ograniczenie czasu można ustawić tę wartość, aby umożliwić funkcji IntelliTest móc więcej lub mniej czasu wykrywanie nowych wykonania ścieżki.

Zazwyczaj Przyczyna przekroczenia limitu czasu jest, że IntelliTest próbuje znaleźć rozwiązania dla systemu ograniczenia, który nie ma rozwiązania, ale nie ma informacji o tym fakcie. Ponieważ jest to najbardziej typowe zdarza się w przypadku przekroczenia limitu czasu, może nie mieć sens, aby zwiększyć powiązane z.

<a name="maxconstraintsolvermemory"></a>
## <a name="maxconstraintsolvermemory"></a>MaxConstraintSolverMemory

W megabajtach, [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver) należy obliczyć danych wejściowych, które spowoduje, że ścieżki wykonywania nowe i zróżnicowane, podejmowane. Jest to opcja *PexSettingsAttributeBase** i jego typów pochodnych.

Lepiej IntelliTest odkrywa ścieżki wykonywania programu, tym bardziej złożone, które stają się systemy ograniczenia, które program IntelliTest kompilacje przepływu sterowania i przepływu danych programu. W zależności od dostępnej pamięci na komputerze można ustawić tę wartość, aby umożliwić funkcji IntelliTest do bardziej złożonych systemów ograniczenia.

Zazwyczaj Przyczyna przekroczenia limitu czasu jest, że IntelliTest próbuje znaleźć rozwiązania dla systemu ograniczenia, który nie ma rozwiązania, ale nie ma informacji o tym fakcie. Ponieważ jest to najbardziej typowe przyczyny sytuacji braku pamięci, może nie mieć sens, aby zwiększyć powiązane z.

<a name="maxbranches"></a>
## <a name="maxbranches"></a>MaxBranches

Maksymalna liczba gałęzi, które mogą zostać podjęte w ścieżce pojedyncze wykonanie.

Motywacja za tej prezentacji powiązany jest ograniczenie długości dowolną ścieżkę wykonywania, który program IntelliTest pokazuje podczas [wejściowych generowania](input-generation.md). W szczególności uniemożliwia IntelliTest przestanie odpowiadać, jeśli program przechodzi w pętli nieskończonej.

Każda gałąź warunkowe i bezwarunkowe kod wykonywany i monitorowanie jest liczony kierunku ten limit, w tym gałęzi, które nie są zależne od danych wejściowych test sparametryzowany.

Na przykład poniższy kod wykorzystuje gałęzie w kolejności 100:

```csharp
for (int i=0; i<100; i++) { }
```

<a name="maxcalls"></a>
## <a name="maxcalls"></a>MaxCalls

Maksymalna liczba wywołań, które mogą być nawiązywane podczas ścieżką pojedynczego uruchomienia.

Motywacja za tej prezentacji powiązany jest ograniczenie długości dowolną ścieżkę wykonywania, który program IntelliTest pokazuje podczas [wejściowych generowania](input-generation.md). W szczególności uniemożliwia IntelliTest przestanie odpowiadać, jeśli program wywołuje cyklicznie metoda nieograniczoną liczbę razy, co mogłoby spowodować przepełnienie stosu funkcji IntelliTest nie można odzyskać z.

Każde wywołanie (bezpośrednie, pośrednie, wirtualnej jump) kod wykonywany i monitorowanie jest liczony w kierunku tego limitu.

<a name="maxstack"></a>
## <a name="maxstack"></a>MaxStack

Maksymalny rozmiar stosu w dowolnym momencie podczas ścieżką pojedynczego uruchomienia mierzone przez liczbę klatek aktywnego połączenia.

Motywacją za tej prezentacji powiązany jest limit rozmiaru stosu dowolną ścieżkę wykonywania, który program IntelliTest pokazuje podczas [wejściowych generowania](input-generation.md). W szczególności że uniemożliwia IntelliTest przy użyciu wszystkich dostępnych stosu wolnego miejsca, co mogłoby spowodować przepełnienie stosu funkcji IntelliTest nie można odzyskać z.

<a name="maxconditions"></a>
## <a name="maxconditions"></a>MaxConditions

Liczba emaximum warunki za pośrednictwem danych wejściowych, które mogą być sprawdzane podczas ścieżką pojedynczego uruchomienia.

Motywacją za tej prezentacji powiązany jest ograniczyć złożoność dowolną ścieżkę wykonywania, który program IntelliTest pokazuje podczas [wejściowych generowania](input-generation.md). Każdej gałęzi warunkowej, który zależy od wejść test sparametryzowany, jest liczony wobec tego limitu.

Na przykład każda ścieżka w poniższym kodzie zużywa n + 1 warunków:

```csharp
[PexMethod]
void ParameterizedTest(int n) 
{
     for (int i=0; i<n; i++) { // conditions are "0<n", "1<n", ..., "!(n<n)"
          ...
     }
     for (int i=0; i<100; i++) { // irrelevant for MaxConditions, since conditions do not depend on input
          ...
     }
}
```

<a name="maxruns"></a>
## <a name="maxruns"></a>MaxRuns

TH emaximum Liczba uruchomień, które program IntelliTest zostanie ponowiona podczas eksploracji testu.

Motywacja za tej prezentacji powiązany jest jakiegokolwiek kodu, który zawiera pętli lub rekursji może mieć nieograniczoną liczbę ścieżki wykonywania i dlatego IntelliTest musi być ograniczona podczas [wejściowych generowania](input-generation.md).

Dwa ustawienia **MaxRuns** i **MaxRunsWithUniquePaths** są ze sobą powiązane w następujący sposób:

* Program IntelliTest zostanie do wywołania metody test sparametryzowany **MaxRuns** razy z różnymi elementami wejściowymi.
* Jeśli wykonywany kod jest deterministyczna, IntelliTest potrwa ścieżką wykonywania różnych każdorazowo. Jednak w niektórych warunkach wykonywany kod może wykonać ścieżką wykonywania podjętą już wcześniej, za pomocą różnych danych wejściowych.
* IntelliTest zlicza liczbę ścieżek wykonywania unikatowy znajdzie; Ta liczba jest ograniczona przez **MaxRunsWithUniquePaths** opcji.

<a name="maxrunswithoutnewtests"></a>
## <a name="maxrunswithoutnewtests"></a>MaxRunsWithoutNewTests

Maksymalna liczba kolejnych uruchomień bez nowego testu jest emitowane.

Podczas testów funkcji IntelliTest często można znaleźć wiele interesujące dane wejściowe testu w krótkim czasie, po chwili, nie zostaną znalezione wszystkie bardziej nowe dane wejściowe testu i zostanie wyemitowany przez żadne testy jednostkowe. Ta opcja konfiguracji umieszcza granicę liczby kolejnych prób do wykonania funkcji IntelliTest mogą bez emitowania nowy test. Jeśli osiągnięty, zatrzyma badań.

<a name="maxrunswithuniquepaths"></a>
## <a name="maxrunswithuniquepaths"></a>MaxRunsWithUniquePaths

Maksymalna liczba unikatowych ścieżek, które program IntelliTest zostanie należy wziąć pod uwagę podczas eksploracji.

Motywacja za tej prezentacji powiązany jest jakiegokolwiek kodu zawierające pętli lub rekursji może mieć nieograniczoną liczbę ścieżki wykonywania i dlatego IntelliTest muszą być ograniczone podczas [wejściowych generowania](input-generation.md).

Dwa ustawienia **MaxRuns** i **MaxRunsWithUniquePaths** są ze sobą powiązane w następujący sposób: 

* Program IntelliTest zostanie do wywołania metody test sparametryzowany **MaxRuns** razy z różnymi elementami wejściowymi.
* Jeśli wykonywany kod jest deterministyczna, IntelliTest potrwa ścieżką wykonywania różnych każdorazowo. Jednak w niektórych warunkach wykonywany kod może wykonać ścieżką wykonywania podjętą już wcześniej, za pomocą różnych danych wejściowych. 
* IntelliTest zlicza liczbę ścieżek wykonywania unikatowy znajdzie; Ta liczba jest ograniczona przez **MaxRunsWithUniquePaths** opcji.

<a name="maxexceptions"></a>
## <a name="maxexceptions"></a>MaxExceptions

Maksymalna liczba wyjątków, które mogą występować przed Eksploracja jest zatrzymywane.

Motywacją za tej prezentacji powiązany jest Zatrzymaj eksplorację kodu, który zawiera wiele błędów. Jeśli program IntelliTest znajdzie zbyt wiele błędów w kodzie, Eksploracja została zatrzymana.

<a name="testexcludepathboundsexceeded"></a>
## <a name="testexcludepathboundsexceeded"></a>TestExcludePathBoundsExceeded

Ścieżki wykonywania, które przekraczają granice skonfigurowanej ścieżki [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), i [MaxConditions](#maxconditions) są ignorowane.

Motywacją za tej prezentacji powiązany jest do czynienia z testami niepowodujące (najprawdopodobniej). Gdy program IntelliTest osiągnie Eksplorowanie powiązane, takie jak [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), lub [MaxConditions](#maxconditions), zakłada się czy test nie będzie niepowodujące procesu, a nie spowoduje przepełnienie stosu w dalszej. Może stwarzać problemy do innych środowisk testowych w takich przypadkach testowych, a ten atrybut zapewnia sposób zapobiec IntelliTest wysyłających przypadków testowych dla procesów potencjalnie niepowodujące lub przypadków testowych, które powodują przepełnienia stosu.

<a name="testemissionfilter"></a>
## <a name="testemissionfilter"></a>TestEmissionFilter

Wskazuje typy testów, które powinny wysyłać IntelliTest. Możliwe wartości to:

* **Wszystkie** -emitować testy dla wszystkim, łącznie z założeń naruszenia.
* **FailuresAndIncreasedBranchHits** (domyślnie) — emitują testów dla wszystkich unikatowych błędów i zawsze, gdy przypadek testowy, wydłuża pokrycia w wartości clientauthtrustmode [TestEmissionBranchHits](#testemissionbranchhits).
* **FailuresAndUniquePaths** — emitować testów dla wszystkich niepowodzeń testów funkcji IntelliTest znajduje, a także dla każdej dane wejściowe testu, która powoduje ścieżką wykonywania unikatowy.
* **Błędy** -emitować testy tylko błędów.

<a name="testemissionbranchhits"></a>
## <a name="testemissionbranchhits"></a>TestEmissionBranchHits

W zależności od bieżącego [TestEmissionFilter](#testemissionfilter) ustawienia programu IntelliTest emituje nowe przypadki testowe z podczas obejmują one gałęzi w programie, który nie został objęty przed.

**TestEmissionBranchHits** ustawienie określa, jeśli program IntelliTest tylko należy rozważyć, czy gałęzi zostało omówione w ogóle (**TestEmissionBranchHits = 1**), jeśli test objętych usługą, jego raz lub dwa razy ( **TestEmissionBranchHits = 2**), i tak dalej.

**TestEmissionBranchHits = 1** dadzą bardzo małe zestawy testów, która będzie obejmować wszystkie gałęzie można skontaktować się z funkcją IntelliTest. W szczególności ten zestaw testów obejmują również wszystkie bloki podstawowe i instrukcje, który osiągnął.

Wartość domyślna tej opcji to **TestEmissionBranchHits = 2**, które mają bardziej ekspresyjnego zestaw testów, który jest również lepszą dostosowane do wykrywania błędów w przyszłości regresji.

## <a name="got-feedback"></a>Czy chcesz przesłać opinię?

Opublikuj swoje pomysły i funkcji żądania na [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
