---
title: Granice eksploracji | Narzędzie testowe Microsoft IntelliTest Developer
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Exploration bounds
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 2a57d79fb64675f90edf50e6a0d7d50b8a3c6fd7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302638"
---
# <a name="exploration-bounds"></a>Wiązania eksploracji

**PexSettingsAttributeBase** jest abstrakcyjną klasą podstawową dla granic ustawień jako atrybuty. Zobacz [Ustawienia wodospadu](settings-waterfall.md) dla przeglądu ustawień w IntelliTest.

Ustawienia można modyfikować przy użyciu nazwanych właściwości tego i jego atrybutów pochodnych:

```csharp
[PexClass(MaxRuns = 10)]
public partial class FooTest {...}
```

* **Granice rozwiązywania ograniczeń**
  * [MaxConstraintSolverTime](#maxconstraintsolvertime) — liczba sekund [solver ograniczenia](input-generation.md#constraint-solver) musi odnajdywać dane wejściowe, które spowoduje, że nowa i inna ścieżka wykonywania, które mają być przestrzegane.
  * [MaxConstraintSolverMemory](#maxconstraintsolvermemory) — rozmiar w megabajtach, który [solver ograniczeń](input-generation.md#constraint-solver) może używać do odnajdowania danych wejściowych.
* **Granice ścieżki eksploracji**
  * [MaxBranches](#maxbranches) — maksymalna liczba gałęzi, które mogą być podejmowane wzdłuż jednej ścieżki wykonywania.
  * [MaxCalls](#maxcalls) — maksymalna liczba wywołań, które mogą być wykonane podczas ścieżki pojedynczego wykonywania.
  * [MaxStack](#maxstack) - Maksymalny rozmiar stosu w dowolnym momencie podczas pojedynczej ścieżki wykonywania, mierzona jako liczba aktywnych klatek wywołań.
  * [MaxConditions](#maxconditions) — maksymalna liczba warunków dla danych wejściowych, które mogą być sprawdzane podczas ścieżki wykonywania pojedynczego.
* **Wiązania eksploracji**
  * [MaxRuns](#maxruns) — maksymalna liczba przebiegów, które będą podejmowane podczas eksploracji.
  * [MaxRunsWithoutNewTests](#maxrunswithoutnewtests) — maksymalna liczba kolejnych przebiegów bez emisji nowego testu.
  * [MaxRunsWithUniquePaths](#maxrunswithuniquepaths) — maksymalna liczba przebiegów z unikatowych ścieżek wykonywania, które będą podejmowane podczas eksploracji.
  * [MaxExceptions](#maxexceptions) — maksymalna liczba wyjątków, które można znaleźć dla kombinacji wszystkich odnalezionych ścieżek wykonywania.
* **Ustawienia generowania kodu pakietu testowego**
  * [TestExcludePathBoundsExceed](#testexcludepathboundsexceeded) - Gdy true, ścieżki wykonywania, które przekraczają dowolne granice ścieżki ([MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), [MaxConditions](#maxconditions)) są ignorowane.
  * [TestEmissionFilter](#testemissionfilter) — wskazuje, w jakich okolicznościach IntelliTest powinien emitować testy.
  * [TestEmissionBranchHits](#testemissionbranchhits) — określa, ile testów emituje IntelliTest.

<a name="maxconstraintsolvertime"></a>
## <a name="maxconstraintsolvertime"></a>MaxConstraintSolverTime

Liczba sekund [solver ograniczenia](input-generation.md#constraint-solver) musi obliczyć dane wejściowe, które spowoduje, że nowa i inna ścieżka wykonywania do wykonania. Jest to opcja **PexSettingsAttributeBase** i jego typy pochodne.

Im głębiej IntelliTest eksploruje ścieżki wykonywania programu, tym bardziej złożone systemy ograniczeń, które IntelliTest buduje z przepływu sterowania i przepływu danych programu stają się. W zależności od ograniczenia czasu można ustawić tę wartość, aby umożliwić IntelliTest zająć więcej lub mniej czasu na odnajdywanie nowych ścieżek wykonywania.

Zazwyczaj powodem limitu czasu jest, że IntelliTest próbuje znaleźć rozwiązanie dla systemu ograniczeń, który nie ma rozwiązania, ale nie jest świadomy tego faktu. Ponieważ jest to najczęstszy przypadek limitu czasu, może nie ma sensu, aby zwiększyć powiązanie.

<a name="maxconstraintsolvermemory"></a>
## <a name="maxconstraintsolvermemory"></a>MaxConstraintSolverMemory

Liczba megabajtów, które [solver ograniczenia](input-generation.md#constraint-solver) musi obliczyć dane wejściowe, które spowoduje nową i inną ścieżkę wykonywania do wykonania. Jest to opcja *PexSettingsAttributeBase** i jego typy pochodne.

Głębszy IntelliTest eksploruje ścieżki wykonywania programu, tym bardziej złożone stają się systemy ograniczeń, które IntelliTest tworzy z przepływu sterowania i przepływu danych programu. W zależności od dostępnej pamięci komputera można ustawić tę wartość, aby umożliwić IntelliTest rozwiązanie bardziej złożonych systemów ograniczeń.

Zazwyczaj powodem limitu czasu jest, że IntelliTest próbuje znaleźć rozwiązanie dla systemu ograniczeń, który nie ma rozwiązania, ale nie jest świadomy tego faktu. Ponieważ jest to najczęstsza przyczyna sytuacji braku pamięci, może nie ma sensu, aby zwiększyć związane.

<a name="maxbranches"></a>
## <a name="maxbranches"></a>MaxBranches

Maksymalna liczba gałęzi, które mogą być podejmowane wzdłuż jednej ścieżki wykonywania.

Motywacją tej eksploracji jest ograniczenie długości każdej ścieżki wykonywania, którą IntelliTest eksploruje podczas [generowania danych wejściowych.](input-generation.md) W szczególności zapobiega IntelliTest staje się nie odpowiada, jeśli program przechodzi w nieskończoną pętlę.

Każda warunkowa i bezwarunkowa gałąź wykonanego i monitorowanego kodu jest wliczona do tego limitu, w tym gałęzi, które nie zależą od danych wejściowych sparametryzowanego testu.

Na przykład następujący kod zużywa gałęzie w kolejności 100:

```csharp
for (int i=0; i<100; i++) { }
```

<a name="maxcalls"></a>
## <a name="maxcalls"></a>MaxCalls

Maksymalna liczba wywołań, które mogą być wykonane podczas ścieżki pojedynczego wykonywania.

Motywacją tej eksploracji jest ograniczenie długości każdej ścieżki wykonywania, którą IntelliTest eksploruje podczas [generowania danych wejściowych.](input-generation.md) W szczególności zapobiega IntelliTest staje się nie odpowiada, jeśli program wywołuje metodę cyklicznie nieskończoną liczbę razy, co spowodowałoby przepełnienie stosu, że IntelliTest nie można odzyskać.

Każde wywołanie (bezpośrednie, pośrednie, wirtualne, skok) wykonanego i monitorowanego kodu jest wliczane do tego limitu.

<a name="maxstack"></a>
## <a name="maxstack"></a>MaxStack

Maksymalny rozmiar stosu w dowolnym momencie podczas ścieżki pojedynczego wykonywania, mierzona liczbą aktywnych ramek wywołań.

Motywacją tej eksploracji jest ograniczenie rozmiaru stosu dowolnej ścieżki wykonywania, którą IntelliTest eksploruje podczas [generowania danych wejściowych.](input-generation.md) W szczególności zapobiega IntelliTest przy użyciu wszystkich dostępnych miejsca na stosie, co spowodowałoby przepełnienie stosu, który IntelliTest nie można odzyskać z.

<a name="maxconditions"></a>
## <a name="maxconditions"></a>MaxConditions

Emaximum liczba warunków nad wejściami, które mogą być sprawdzane podczas jednej ścieżki wykonywania.

Motywacją tej eksploracji jest ograniczenie złożoności każdej ścieżki wykonywania, którą IntelliTest eksploruje podczas [generowania danych wejściowych.](input-generation.md) Każda gałąź warunkowa, która zależy od danych wejściowych sparametryzowanego testu jest wliczany do tego limitu.

Na przykład każda ścieżka w poniższym kodzie zużywa n +1 warunki:

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

Th emaximum liczba uruchomień, które IntelliTest spróbuje podczas eksploracji testu.

Motywacją tej eksploracji jest to, że każdy kod, który zawiera pętle lub rekursję może mieć nieskończoną liczbę ścieżek wykonywania, a zatem IntelliTest musi być ograniczony podczas [generowania danych wejściowych.](input-generation.md)

Dwa ustawienia **MaxRuns** i **MaxRunsWithUniquePaths** są powiązane w następujący sposób:

* IntelliTest wywoła sparametryzowaną metodę testową do **czasów MaxRuns** z różnymi wejściami testowymi.
* Jeśli wykonany kod jest deterministyczny, IntelliTest będzie przy innej ścieżce wykonywania za każdym razem. Jednak w niektórych warunkach wykonany kod może podążać ścieżką wykonywania, którą już wcześniej wykonał, z różnymi wejściami.
* IntelliTest zlicza liczbę unikatowych ścieżek wykonywania, które znajdzie; liczba ta jest ograniczona przez opcję **MaxRunsWithUniquePaths.**

<a name="maxrunswithoutnewtests"></a>
## <a name="maxrunswithoutnewtests"></a>MaxRunsWithoutNewTests

Maksymalna liczba kolejnych przebiegów bez emisji nowego testu.

Chociaż IntelliTest często można znaleźć wiele interesujących danych wejściowych testu w krótkim czasie, po pewnym czasie nie znajdzie więcej nowych danych wejściowych testu i nie będzie emitować więcej testów jednostkowych. Ta opcja konfiguracji umieszcza powiązanie na liczbę kolejnych prób IntelliTest może wykonać bez emitowania nowego testu. Po osiągnięciu, to zatrzyma poszukiwania.

<a name="maxrunswithuniquepaths"></a>
## <a name="maxrunswithuniquepaths"></a>MaxRunsWithUniquePaths

Maksymalna liczba unikatowych ścieżek, które IntelliTest rozważy podczas eksploracji.

Motywacją za tę eksplorację związany jest to, że każdy kod zawierający pętle lub rekursji może mieć nieskończoną liczbę ścieżek wykonywania, a więc IntelliTest musi być ograniczona podczas [generowania danych wejściowych.](input-generation.md)

Dwa ustawienia **MaxRuns** i **MaxRunsWithUniquePaths** są powiązane w następujący sposób:

* IntelliTest wywoła sparametryzowaną metodę testową do **czasów MaxRuns** z różnymi wejściami testowymi.
* Jeśli wykonany kod jest deterministyczny, IntelliTest będzie przy innej ścieżce wykonywania za każdym razem. Jednak w niektórych warunkach wykonany kod może podążać ścieżką wykonywania, którą już wcześniej wykonał, z różnymi wejściami.
* IntelliTest zlicza liczbę unikatowych ścieżek wykonywania, które znajdzie; liczba ta jest ograniczona przez opcję **MaxRunsWithUniquePaths.**

<a name="maxexceptions"></a>
## <a name="maxexceptions"></a>MaxExceptions

Maksymalna liczba wyjątków, które można napotkać przed eksploracji jest zatrzymany.

Motywacją tej eksploracji jest zatrzymanie eksploracji kodu, który zawiera wiele błędów. Jeśli IntelliTest znajdzie zbyt wiele błędów w kodzie, eksploracja jest zatrzymana.

<a name="testexcludepathboundsexceeded"></a>
## <a name="testexcludepathboundsexceeded"></a>TestExcludePathBoundsExceeded

Ścieżki wykonywania, które przekraczają skonfigurowane granice ścieżki [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack)i [MaxConditions](#maxconditions) są ignorowane.

Motywacją tej eksploracji jest radzenie sobie z (najprawdopodobniej) nieukańczyszczącymi testami. Gdy IntelliTest osiągnie eksploracji związane, takie jak [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack)lub [MaxConditions](#maxconditions), zakłada, że test nie będzie procesem nie kończące się i nie spowoduje przepełnienie stosu później. Takie przypadki testowe mogą powodować problemy z innymi platformami testowymi, a ten atrybut umożliwia uniemożliwienie intellitestowi emitowania przypadków testowych dla potencjalnie nieubiegających się procesów lub przypadków testowych, które spowodują przepełnienie stosu.

<a name="testemissionfilter"></a>
## <a name="testemissionfilter"></a>TestEmissionFilter

Wskazuje typy testów, które intellitest powinien emitować. Możliwe wartości są następujące:

* **Wszystkie** — emitują testy na wszystko, w tym naruszenia założeń.
* **FailuresAndIncreasedBranchHits** (domyślnie) — emitują testy dla wszystkich unikatowych błędów i za każdym razem, gdy przypadek testowy zwiększa zasięg kontrolowany przez [TestEmissionBranchHits](#testemissionbranchhits).
* **FailuresAndUniquePaths** — emituje testy dla wszystkich awarii IntelliTest znajdzie, a także dla każdego testu danych wejściowych, który powoduje ścieżkę wykonywania unikatowe.
* **Błędy** — emitują testy tylko dla błędów.

<a name="testemissionbranchhits"></a>
## <a name="testemissionbranchhits"></a>TestEmissionBranchHits

W zależności od bieżącego [TestEmissionFilter](#testemissionfilter) ustawienie IntelliTest emituje nowe przypadki testowe, gdy obejmują one gałąź w programie, który nie został omówiony wcześniej.

**Ustawienie TestEmissionBranchHits** określa, czy IntelliTest należy po prostu rozważyć, czy gałąź została w ogóle omówiona **(TestEmissionBranchHits=1**), jeśli test obejmował go raz lub dwa razy **(TestEmissionBranchHits=2)** i tak dalej.

**TestEmissionBranchHits=1** będzie produkować bardzo mały zestaw testów, który obejmie wszystkie gałęzie IntelliTest może osiągnąć. W szczególności ten zestaw testów obejmie również wszystkie podstawowe bloki i oświadczenia, które osiągnął.

Domyślnym dla tej opcji jest **TestEmissionBranchHits = 2**, który generuje bardziej ekspresyjny zestaw testów, który jest również lepiej nadaje się do wykrywania przyszłych błędów regresji.

## <a name="got-feedback"></a>Chcesz przesłać opinię?

Opublikuj swoje pomysły i sugestie funkcji w [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
