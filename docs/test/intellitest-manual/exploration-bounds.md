---
title: Granice eksploracji | Narzędzie testowe dla deweloperów Microsoft IntelliTest
description: PexSettingsAttributeBase to abstrakcyjna klasa bazowa dla ustawień związanych z atrybutami. Dowiedz się, jak modyfikować ustawienia przy użyciu nazwanych właściwości.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Exploration bounds
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 44af9fc50e81727d534e7c5a79dba0ccf2edde75
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910670"
---
# <a name="exploration-bounds"></a>Wiązania eksploracji

**PexSettingsAttributeBase** to abstrakcyjna klasa bazowa dla ustawień związanych z atrybutami. Zobacz [Ustawienia kaskadowe](settings-waterfall.md) , aby zapoznać się z omówieniem ustawień w IntelliTest.

Ustawienia można modyfikować za pomocą nazwanych właściwości tego i atrybutów pochodnych:

```csharp
[PexClass(MaxRuns = 10)]
public partial class FooTest {...}
```

* **Ograniczenia rozwiązywania ograniczeń**
  * [MaxConstraintSolverTime](#maxconstraintsolvertime) — liczba sekund, przez jaką funkcja [ograniczenia](input-generation.md#constraint-solver) musi odnajdywać dane wejściowe, które spowodują wykonanie nowej i innej ścieżki wykonania.
  * [MaxConstraintSolverMemory](#maxconstraintsolvermemory) — rozmiar (w megabajtach), który może być używany przez program [Constraint](input-generation.md#constraint-solver) do odnajdywania danych wejściowych.
* **Poszukiwanie powiązań ścieżki**
  * [MaxBranches](#maxbranches) — Maksymalna liczba rozgałęzień, które mogą być wykonywane w ramach jednej ścieżki wykonywania.
  * [MaxCalls](#maxcalls) — Maksymalna liczba wywołań, które mogą być wykonywane w ramach jednej ścieżki wykonywania.
  * [MaxStack](#maxstack) — maksymalny rozmiar stosu w dowolnym momencie podczas jednej ścieżki wykonywania, mierzoną jako liczba aktywnych ramek wywołań.
  * [MaxConditions](#maxconditions) — Maksymalna liczba warunków w danych wejściowych, które mogą być sprawdzane podczas jednej ścieżki wykonywania.
* **Granice eksploracji**
  * [MaxRuns](#maxruns) — Maksymalna liczba uruchomień, które zostaną podjęte podczas eksploracji.
  * [MaxRunsWithoutNewTests](#maxrunswithoutnewtests) — Maksymalna liczba kolejnych uruchomień bez nowego testu.
  * [MaxRunsWithUniquePaths](#maxrunswithuniquepaths) — Maksymalna liczba przebiegów z unikatowymi ścieżkami wykonywania, które będą podejmowane podczas eksploracji.
  * [MaxExceptions](#maxexceptions) — Maksymalna liczba wyjątków, które można znaleźć dla kombinacji wszystkich odnalezionych ścieżek wykonania.
* **Ustawienia generowania kodu zestawu testów**
  * [TestExcludePathBoundsExceeded](#testexcludepathboundsexceeded) — w przypadku wartości true ścieżki wykonywania, które przekraczają wszystkie granice ścieżki ([MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), [MaxConditions](#maxconditions)), są ignorowane.
  * [TestEmissionFilter](#testemissionfilter) — wskazuje, pod którym okoliczności IntelliTest powinny emitować testy.
  * [TestEmissionBranchHits](#testemissionbranchhits) — określa, ile testów IntelliTest emituje.

<a name="maxconstraintsolvertime"></a>
## <a name="maxconstraintsolvertime"></a>MaxConstraintSolverTime

Liczba sekund, przez jaką funkcja [ograniczenia](input-generation.md#constraint-solver) musi obliczać dane wejściowe, które spowodują wykonanie nowej i innej ścieżki wykonania. Jest to opcja elementu **PexSettingsAttributeBase** i jego typów pochodnych.

Im bardziej skomplikowane są, że IntelliTest eksplorują ścieżki wykonywania programu, tym bardziej złożone są systemy ograniczeń, które IntelliTest kompilacje z przepływu sterowania i przepływu danych programu. W zależności od ograniczeń czasowych można ustawić tę wartość, aby umożliwić IntelliTest więcej lub mniej czasu na odnajdywanie nowych ścieżek wykonywania.

Zazwyczaj przyczyną limitu czasu jest to, że IntelliTest próbuje znaleźć rozwiązanie dla systemu ograniczającego, który nie ma rozwiązania, ale nie wie o tym fakcie. Ponieważ jest to najbardziej typowy przypadek w przypadku przekroczenia limitu czasu, może nie mieć sensu, aby zwiększyć granicę.

<a name="maxconstraintsolvermemory"></a>
## <a name="maxconstraintsolvermemory"></a>MaxConstraintSolverMemory

Liczba megabajtów, jaką funkcja [Solver](input-generation.md#constraint-solver) musi obliczyć dane wejściowe, które spowodują wykonanie nowej i innej ścieżki wykonania. Jest to opcja *PexSettingsAttributeBase** i jego typów pochodnych.

Dokładniejsze IntelliTest eksplorują ścieżki wykonywania programu, tym bardziej skomplikowane systemy ograniczeń, które IntelliTest kompilacje z przepływu sterowania i przepływu danych programu. W zależności od dostępnej pamięci komputera można ustawić tę wartość, aby umożliwić programowi IntelliTest Rozwiązywanie bardziej złożonych systemów ograniczeń.

Zazwyczaj przyczyną limitu czasu jest to, że IntelliTest próbuje znaleźć rozwiązanie dla systemu ograniczającego, który nie ma rozwiązania, ale nie wie o tym fakcie. Ponieważ jest to najbardziej powszechna przyczyna sytuacji braku pamięci, może nie mieć sensu, aby zwiększyć zakres.

<a name="maxbranches"></a>
## <a name="maxbranches"></a>MaxBranches

Maksymalna liczba rozgałęzień, które mogą być wykonywane w ramach jednej ścieżki wykonywania.

Uzasadnienie związane z badaniem polega na ograniczeniu długości ścieżki wykonywania, która IntelliTest Eksplorowanie podczas [generowania danych wejściowych](input-generation.md). W szczególności zapobiega to, aby IntelliTest się nie reagować, jeśli program przejdzie w nieskończoną pętlę.

Każda warunkowa i bezwarunkowa gałąź wykonanych i monitorowanych kodów jest naliczana w ramach tego limitu, w tym gałęzi, które nie zależą od danych wejściowych testu sparametryzowanego.

Na przykład poniższy kod zużywa gałęzie w kolejności 100:

```csharp
for (int i=0; i<100; i++) { }
```

<a name="maxcalls"></a>
## <a name="maxcalls"></a>MaxCalls

Maksymalna liczba wywołań, które mogą być wykonywane w ramach jednej ścieżki wykonywania.

Uzasadnienie związane z badaniem polega na ograniczeniu długości ścieżki wykonywania, która IntelliTest Eksplorowanie podczas [generowania danych wejściowych](input-generation.md). W szczególności zapobiega to, aby IntelliTest się nie reagować, jeśli program wywołuje metodę cyklicznie nieskończoną liczbę razy, co spowodowałoby przepełnienie stosu, którego IntelliTest nie może odzyskać.

Każde wywołanie (bezpośrednie, pośrednie, wirtualne, skok) wykonanego i monitorowanego kodu jest zliczane do tego limitu.

<a name="maxstack"></a>
## <a name="maxstack"></a>MaxStack

Maksymalny rozmiar stosu w dowolnym momencie podczas jednej ścieżki wykonywania, mierzony przez liczbę aktywnych ramek wywołań.

Uzasadnienie związane z badaniem polega na ograniczeniu rozmiaru stosu dowolnej ścieżki wykonywania, który IntelliTest Eksplorowanie podczas [generowania danych wejściowych](input-generation.md). W szczególności zapobiega to IntelliTest z używania całego dostępnego miejsca na stosie, co spowodowałoby przepełnienie stosu, którego IntelliTest nie może odzyskać.

<a name="maxconditions"></a>
## <a name="maxconditions"></a>MaxConditions

Emaximum liczba warunków na dane wejściowe, które mogą być sprawdzane podczas jednej ścieżki wykonywania.

Uzasadnienie związane z badaniem polega na ograniczeniu złożoności wszystkich ścieżek wykonywania, które IntelliTest Eksplorowanie podczas [generowania danych wejściowych](input-generation.md). Wszystkie gałęzie warunkowe, które są zależne od danych wejściowych testu sparametryzowanego, są zliczane do tego limitu.

Na przykład każda ścieżka w poniższym kodzie zużywa n + 1 warunek:

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

Emaximum liczba uruchomień, które IntelliTest spróbuje podczas eksploracji testu.

Uzasadnienie związane z badaniem polega na tym, że każdy kod, który zawiera pętle lub rekursję, może mieć nieskończoną liczbę ścieżek wykonywania, a tym samym IntelliTest należy ograniczyć podczas [generowania danych wejściowych](input-generation.md).

Dwa ustawienia **MaxRuns** i **MaxRunsWithUniquePaths** są powiązane w następujący sposób:

* IntelliTest wywoła sparametryzowanej metody testowej do **MaxRuns** razy przy użyciu różnych danych wejściowych testu.
* Jeśli wykonany kod jest deterministyczny, IntelliTest będzie wykonywać inną ścieżkę wykonania za każdym razem. Jednak w niektórych warunkach wykonany kod może być zgodny ze ścieżką wykonywania, która została już wcześniej wykonana, z różnymi danymi wejściowymi.
* IntelliTest zlicza liczbę unikatowych ścieżek wykonywania, które znajdzie; Ta liczba jest ograniczona przez opcję **MaxRunsWithUniquePaths** .

<a name="maxrunswithoutnewtests"></a>
## <a name="maxrunswithoutnewtests"></a>MaxRunsWithoutNewTests

Maksymalna liczba kolejnych uruchomień bez przeemitowania nowego testu.

Mimo że IntelliTest może często znaleźć wiele interesujących danych wejściowych testów w krótkim czasie, gdy nie znajdzie żadnych nowych danych wejściowych testów i nie będzie wysyłać żadnych testów jednostkowych. Ta opcja konfiguracji umieszcza w powiązaniu liczbę kolejnych prób, które IntelliTest mogą wykonać bez emitowania nowego testu. Po osiągnięciu tego czasu zostanie zatrzymana Eksploracja.

<a name="maxrunswithuniquepaths"></a>
## <a name="maxrunswithuniquepaths"></a>MaxRunsWithUniquePaths

Maksymalna liczba unikatowych ścieżek, które IntelliTest wziąć pod uwagę podczas eksploracji.

Uzasadnienie związane z eksplorowaniem polega na tym, że każdy kod zawierający pętle lub rekursję może mieć nieskończoną liczbę ścieżek wykonywania, więc IntelliTest muszą być ograniczone podczas [generowania danych wejściowych](input-generation.md).

Dwa ustawienia **MaxRuns** i **MaxRunsWithUniquePaths** są powiązane w następujący sposób:

* IntelliTest wywoła sparametryzowanej metody testowej do **MaxRuns** razy przy użyciu różnych danych wejściowych testu.
* Jeśli wykonany kod jest deterministyczny, IntelliTest będzie wykonywać inną ścieżkę wykonania za każdym razem. Jednak w niektórych warunkach wykonany kod może być zgodny ze ścieżką wykonywania, która została już wcześniej wykonana, z różnymi danymi wejściowymi.
* IntelliTest zlicza liczbę unikatowych ścieżek wykonywania, które znajdzie; Ta liczba jest ograniczona przez opcję **MaxRunsWithUniquePaths** .

<a name="maxexceptions"></a>
## <a name="maxexceptions"></a>MaxExceptions

Maksymalna liczba wyjątków, które można napotkać przed zatrzymaniem eksploracji.

Uzasadnienie związane z badaniem polega na zatrzymaniu eksploracji kodu, który zawiera wiele błędów. Jeśli IntelliTest odnajdzie zbyt wiele błędów w kodzie, eksploracja zostanie zatrzymana.

<a name="testexcludepathboundsexceeded"></a>
## <a name="testexcludepathboundsexceeded"></a>TestExcludePathBoundsExceeded

Ścieżki wykonywania, które przekraczają skonfigurowane granice ścieżki [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack)i [MaxConditions](#maxconditions) , są ignorowane.

Uzasadnienie związane z badaniem ma na celu rozpatrzenie (najprawdopodobniej) testów niekończących się. Gdy IntelliTest osiągnie powiązane poszukiwanie, takie jak [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack)lub [MaxConditions](#maxconditions), zakłada, że test nie będzie procesem niekończącym i nie spowoduje przepełnienia stosu w późniejszym czasie. Takie przypadki testowe mogą stanowić problemy z innymi platformami testowymi, a ten atrybut umożliwia zapobieganie emitowaniu przypadków testowych dla potencjalnie niekończących się procesów lub przypadków testowych, które spowodują przepełnienie stosu.

<a name="testemissionfilter"></a>
## <a name="testemissionfilter"></a>TestEmissionFilter

Wskazuje typy testów, które IntelliTest powinny emitować. Możliwe wartości są następujące:

* **Wszystkie** -Emituj testy dla wszystkiego, w tym naruszenia założeń.
* **FailuresAndIncreasedBranchHits** (domyślnie) — Emituj testy dla wszystkich unikatowych błędów, a gdy przypadek testowy zwiększy pokrycie jako kontrolowane przez [TestEmissionBranchHits](#testemissionbranchhits).
* **FailuresAndUniquePaths** -Emituj testy dla wszystkich niepowodzeń IntelliTest znalezionych, a także dla każdego testu wejściowego, który powoduje unikatową ścieżkę wykonywania.
* **Błędy** — Emituj testy tylko dla niepowodzeń.

<a name="testemissionbranchhits"></a>
## <a name="testemissionbranchhits"></a>TestEmissionBranchHits

W zależności od bieżącego ustawienia [TestEmissionFilter](#testemissionfilter) , IntelliTest emituje nowe przypadki testowe, gdy obejmują gałąź w programie, który nie został uwzględniony wcześniej.

Ustawienie **TestEmissionBranchHits** określa, czy IntelliTest należy tylko rozważyć, czy gałąź została pokryte w ogóle (**TestEmissionBranchHits = 1**), jeśli test został objęty jedną lub dwa razy (**TestEmissionBranchHits = 2**) i tak dalej.

**TestEmissionBranchHits = 1** spowoduje utworzenie bardzo małego zestawu testów, który będzie obejmować wszystkie gałęzie IntelliTest. W szczególności ten zestaw testów obejmuje również wszystkie podstawowe bloki i instrukcje, które zostały osiągnięte.

Wartość domyślna dla tej opcji to **TestEmissionBranchHits = 2**, która generuje bardziej wyraźny zestaw testów, który jest również lepiej dostosowany do wykrywania przyszłych błędów regresji.

## <a name="got-feedback"></a>Chcesz przesłać opinię?

Opublikuj swoje pomysły i sugestie funkcji w [społeczności deweloperów](https://aka.ms/feedback/suggest?space=8).
