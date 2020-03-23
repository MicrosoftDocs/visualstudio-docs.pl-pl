---
title: Generowanie testów | Narzędzie testowe Microsoft IntelliTest Developer
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Test generation
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c251a1539b42da2b4e92c2996457075f3c3be135
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302610"
---
# <a name="test-generation"></a>Generowanie testu

W tradycyjnych testach jednostkowych test składa się z kilku rzeczy:

* [Sekwencja wywołań metody](test-generation.md#test-generators)
* Argumenty, z którymi metody są wywoływane; argumenty są [danymi wejściowymi testu](input-generation.md)
* Sprawdzanie poprawności zamierzonego zachowania testowanego wniosku przez podanie zestawu [potwierdzeń](#assumptions-and-assertions)

Poniżej przedstawiono przykładową strukturę testową:

```csharp
[Test]
void MyTest() {
    // data
    ArrayList a = new ArrayList();

    // method sequence
    a.Add(5);

    // assertions
    Assert.IsTrue(a.Count==1);
    Assert.AreEqual(a[0], 5);
}
```

IntelliTest często można automatycznie określić odpowiednie wartości argumentów dla bardziej ogólnych [sparametryzowanych testów jednostkowych,](#parameterized-unit-testing)które zapewniają sekwencję wywołań metody i potwierdzeń.

<a name="test-generators"></a>
## <a name="test-generators"></a>Generatory testów

IntelliTest generuje przypadków testowych, wybierając sekwencję metod implementacji w ramach testu do wykonania, a następnie generowania danych wejściowych dla metod podczas sprawdzania potwierdzeń danych pochodnych.

[Sparametryzowany test jednostkowy](#parameterized-unit-testing) bezpośrednio stwierdza sekwencję wywołań metody w jego treści.

Gdy IntelliTest musi konstruować obiekty, wywołania konstruktorów i metod fabrycznych zostaną dodane automatycznie do sekwencji zgodnie z wymaganiami.

<a name="parameterized-unit-testing"></a>
## <a name="parameterized-unit-testing"></a>Sparametryzowane testy jednostkowe

*Sparametryzowane testy jednostkowe* (PUT) to testy, które przyjmują parametry. W przeciwieństwie do tradycyjnych testów jednostkowych, które są zwykle metodami zamkniętymi, puty przyjmują dowolny zestaw parametrów. Czy to takie proste? Tak - stamtąd IntelliTest spróbuje [wygenerować (minimalny) zestaw wejść,](input-generation.md) które [w pełni obejmują](input-generation.md#dynamic-code-coverage) kod osiągalny z testu.

Puty są definiowane przy użyciu atrybutu niestandardowego [PexMethod](attribute-glossary.md#pexmethod) w podobny sposób do MSTest (lub NUnit, xUnit). Put są metody instancji logicznie pogrupowane w klasach z tagiem [PexClass](attribute-glossary.md#pexclass). W poniższym przykładzie pokazano prosty PUT przechowywane w **MyPexTest** klasy:

```csharp
[PexMethod]
void ReplaceFirstChar(string target, char c) {

    string result = StringHelper.ReplaceFirstChar(target, c);

    Assert.AreEqual(result[0], c);
}
```

gdzie **ReplaceFirstChar** jest metodą, która zastępuje pierwszy znak ciągu:

```csharp
class StringHelper {
    static string ReplaceFirstChar(string target, char c) {
        if (target == null) throw new ArgumentNullException();
        if (target.Length == 0) throw new ArgumentOutOfRangeException();
        return c + target.Substring(1);
    }
}
```

Z tego testu IntelliTest można automatycznie [generować dane wejściowe](input-generation.md) dla PUT, który obejmuje wiele ścieżek wykonywania testowanego kodu. Każde dane wejściowe, które obejmuje inną ścieżkę wykonywania pobiera "serialized" jako test jednostkowy:

```csharp
[TestMethod, ExpectedException(typeof(ArgumentNullException))]
void ReplaceFirstChar0() {
    this.ReplaceFirstChar(null, 0);
}
...
[TestMethod]
void ReplaceFirstChar10() {
    this.ReplaceFirstChar("a", 'c');
}
```

<a name="generic-parameterized"></a>
## <a name="generic-parameterized-unit-testing"></a>Ogólne sparametryzowane testy jednostkowe

Sparametryzowane testy jednostkowe mogą być metodami ogólnymi. W takim przypadku użytkownik musi określić typy używane do tworzenia wystąpienia metody przy użyciu [PexGenericArguments](attribute-glossary.md#pexgenericarguments).

```csharp
[PexClass]
public partial class ListTest {
    [PexMethod]
    [PexGenericArguments(typeof(int))]
    [PexGenericArguments(typeof(object))]
    public void AddItem<T>(List<T> list, T value)
    { ... }
}
```

<a name="allowing-exceptions"></a>
## <a name="allowing-exceptions"></a>Zezwalanie na wyjątki

IntelliTest zawiera wiele atrybutów sprawdzania poprawności, aby ułatwić klasyfikowanie wyjątków do oczekiwanych wyjątków i nieoczekiwanych wyjątków.

Oczekiwane wyjątki generują negatywne przypadki testowe z odpowiednią adnotacją, taką jak **ExpectedException(typeof(*xxx*)),** podczas gdy nieoczekiwane wyjątki generują nieudane przypadki testowe.

```csharp
[PexMethod, PexAllowedException(typeof(ArgumentNullException))]
void SomeTest() {...}
```

Walidatorami są:

* [PexAllowedException](attribute-glossary.md#pexallowedexception): zezwala na określony typ wyjątku z dowolnego miejsca
* [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly): umożliwia określony typ wyjątku z określonego zestawu
* [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype): umożliwia określony typ wyjątku od określonego typu
* [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest): zezwala na określony typ wyjątku od typu w teście

<a name="internal-types"></a>
## <a name="testing-internal-types"></a>Testowanie typów wewnętrznych

IntelliTest można "przetestować" typy wewnętrzne, tak długo, jak można je zobaczyć. Dla IntelliTest, aby zobaczyć typy, następujący atrybut jest dodawany do projektu produktu lub testu przez kreatorów IntelliTest programu Visual Studio:

```csharp
[assembly: InternalsVisibleTo("Microsoft.Pex, PublicKey=002400000480000094000000060200000024000052534131000400000100010007d1fa57c4aed9f0a32e84aa0faefd0de9e8fd6aec8f87fb03766c834c99921eb23be79ad9d5dcc1dd9ad236132102900b723cf980957fc4e177108fc607774f29e8320e92ea05ece4e821c0a5efe8f1645c4c0c93c1ab99285d622caa652c1dfad63d745d6f2de5f17e5eaf0fc4963d261c8a12436518206dc093344d5ad293")]
```

<a name="assumptions-and-assertions"></a>
## <a name="assumptions-and-assertions"></a>Założenia i potwierdzenia

Użytkownicy mogą używać założeń i potwierdzeń do [wyrażania warunków wstępnych](#precondition) (założeń) i [postconditions (potwierdzeń)](#postcondition) dotyczących ich testów. Gdy IntelliTest generuje zestaw wartości parametrów i "eksploruje" kod, może naruszać założenie testu. Gdy tak się stanie, nie wygeneruje test dla tej ścieżki, ale po cichu ją zignoruje.

Potwierdzenia są dobrze znane pojęcie w regularnych jednostek testów frameworks, więc IntelliTest już "rozumie" wbudowane **assert** klas dostarczonych przez każdą obsługiwaną strukturę testów. Jednak większość struktur nie zapewniają **Assume** klasy. W takim przypadku IntelliTest zapewnia [PexAssume](static-helper-classes.md#pexassume) klasy. Jeśli nie chcesz używać istniejącej struktury testowej, IntelliTest ma również [PexAssert](static-helper-classes.md#pexassert) klasy.

```csharp
[PexMethod]
public void Test1(object o) {
    // precondition: o should not be null
    PexAssume.IsNotNull(o);

    ...
}
```

W szczególności założenie nieuwagi można zakodować jako atrybut niestandardowy:

```csharp
[PexMethod]
public void Test2([PexAssumeNotNull] object o)
// precondition: o should not be null
{
   ...
}
```

<a name="precondition"></a>
## <a name="precondition"></a>Warunek wstępny

Warunek wstępny metody wyraża warunki, w których metoda zakończy się pomyślnie.

Zazwyczaj warunek wstępny jest wymuszany przez sprawdzanie parametrów i stanu obiektu i rzucanie **ArgumentException** lub **InvalidOperationException,** jeśli zostanie naruszona.

W IntelliTest warunek wstępny [sparametryzowanego testu jednostkowego](#parameterized-unit-testing) jest wyrażony za pomocą [PexAssume](static-helper-classes.md#pexassume).

<a name="postcondition"></a>
## <a name="postcondition"></a>Warunek końcowy

Warunkiem posadym metody jest wyrażenie warunków, które powinny być utrzymywane w trakcie i po wykonaniu metody, przy założeniu, że jej warunki wstępne były początkowo ważne.

Zazwyczaj postcondition jest wymuszane przez wywołania **Assert** metody.

W intellitestie postcondition [sparametryzowanego testu jednostkowego](#parameterized-unit-testing) jest wyrażony za pomocą [PexAssert](static-helper-classes.md#pexassert).

<a name="test-failures"></a>
## <a name="test-failures"></a>Niepowodzenia testów
Kiedy wygenerowany przypadek testowy nie powiedzie się?

1. Jeśli nie zakończy się w [ramach skonfigurowanych granic ścieżki,](exploration-bounds.md)jest uważany za błąd, chyba że zostanie ustawiona opcja [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded)

1. Jeśli test rzuca **PexAssumeFailedException**, to się powiedzie. Jednak zwykle jest odfiltrowany, chyba że [TestEmissionFilter](exploration-bounds.md#testemissionfilter) jest ustawiony na **Wszystkie**

1. Jeśli test narusza [twierdzenie;](#assumptions-and-assertions) na przykład, zgłaszając wyjątek naruszenia twierdzenia w ramach testowania jednostkowego, nie powiedzie się

Jeśli żaden z powyższych produkcji decyzji, test powiedzie się wtedy i tylko wtedy, gdy nie zgłasza wyjątek. Naruszenia asercji są traktowane w taki sam sposób jak wyjątki.

<a name="setup-teardown"></a>
## <a name="setup-and-tear-down"></a>Konfigurowanie i usuwanie

W ramach integracji z platformami testowymi IntelliTest obsługuje wykrywanie i uruchamianie metod konfiguracji i niszczenie.

**Przykład**

```csharp
using Microsoft.Pex.Framework;
using NUnit.Framework;

namespace MyTests
{
    [PexClass]
    [TestFixture]
    public partial class MyTestClass
    {
        [SetUp]
        public void Init()
        {
            // monitored
        }

        [PexMethod]
        public void MyTest(int i)
        {
        }

        [TearDown]
        public void Dispose()
        {
            // monitored
        }
    }
}
```

<a name="further-reading"></a>
## <a name="further-reading"></a>Dodatkowe informacje

* [Test do powiązania kodu](https://devblogs.microsoft.com/devops/smart-unit-tests-test-to-code-binding-test-case-management/)
* [Jeden test, aby rządzić nimi wszystkimi](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)

## <a name="got-feedback"></a>Chcesz przesłać opinię?

Opublikuj swoje pomysły i sugestie funkcji w [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
