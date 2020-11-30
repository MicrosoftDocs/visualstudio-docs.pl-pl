---
title: Generowanie testu | Narzędzie testowe dla deweloperów Microsoft IntelliTest
description: Dowiedz się, w jaki sposób usługa IntelliTest generuje przypadki testowe z metod implementacji, a następnie generuje dane wejściowe dla metod i sprawdza potwierdzenia danych.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Test generation
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 790146e3014765224f22bd247732c7ac3f062269
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329448"
---
# <a name="test-generation"></a>Generowanie testu

W tradycyjnych testach jednostkowych test obejmuje kilka rzeczy:

* [Sekwencja wywołań metod](test-generation.md#test-generators)
* Argumenty, dla których metody są wywoływane; argumenty są [danymi wejściowymi testu](input-generation.md)
* Sprawdzanie poprawności zamierzonego zachowania testowanej aplikacji przez podanie zestawu [potwierdzeń](#assumptions-and-assertions)

Poniżej znajduje się przykładowa struktura testu:

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

IntelliTest może często automatycznie określić odpowiednie wartości argumentów dla bardziej ogólnych [testów jednostkowych](#parameterized-unit-testing), które zapewniają sekwencję wywołań metod i potwierdzeń.

<a name="test-generators"></a>
## <a name="test-generators"></a>Generatory testów

IntelliTest generuje przypadki testowe poprzez wybranie sekwencji metod implementacji w ramach testu do wykonania, a następnie wygenerowanie danych wejściowych dla metod podczas sprawdzania potwierdzenia danych pochodnych.

[Sparametryzowany test jednostkowy](#parameterized-unit-testing) bezpośrednio Określa sekwencję wywołań metod w swojej treści.

Gdy IntelliTest wymaga konstruowania obiektów, wywołania do konstruktorów i metod fabrycznych zostaną automatycznie dodane do sekwencji zgodnie z wymaganiami.

<a name="parameterized-unit-testing"></a>
## <a name="parameterized-unit-testing"></a>Sparametryzowane testy jednostkowe

*Sparametryzowane testy jednostkowe* (Put) to testy, które pobierają parametry. W przeciwieństwie do tradycyjnych testów jednostkowych, które są zazwyczaj metodami zamkniętymi, umieszcza każdy zestaw parametrów. Czy jest to proste? Tak — w tym miejscu IntelliTest podejmie próbę [wygenerowania zestawu danych wejściowych (minimalny)](input-generation.md) , który w [pełni pokrywa](input-generation.md#dynamic-code-coverage) kod osiągalny z testu.

Umieszczanie są zdefiniowane przy użyciu atrybutu niestandardowego [PexMethod](attribute-glossary.md#pexmethod) w podobny sposób do MSTest (lub nunit, xUnit). Umieszczanie to metody wystąpień logicznie pogrupowane w klasach oznaczonych za pomocą [PexClass](attribute-glossary.md#pexclass). W poniższym przykładzie pokazano proste umieszczenie przechowywane w klasie **MyPexTest** :

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

Z tego testu IntelliTest może automatycznie [generować dane wejściowe](input-generation.md) dla umieszczania, które obejmują wiele ścieżek wykonywania testowanego kodu. Każde dane wejściowe, które obejmują inną ścieżkę wykonywania, uzyskuje "serializacji" jako test jednostkowy:

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

Sparametryzowane testy jednostkowe mogą być metodami ogólnymi. W takim przypadku użytkownik musi określić typy używane do tworzenia wystąpienia metody za pomocą [PexGenericArguments](attribute-glossary.md#pexgenericarguments).

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

IntelliTest udostępnia wiele atrybutów walidacji, które pomagają Klasyfikacja wyjątki z oczekiwanymi wyjątkami i nieoczekiwanymi wyjątkami.

Oczekiwane wyjątki generują negatywne przypadki testowe z odpowiednią adnotacją, taką jak **oczekiwano ("TypeOf *xxx***"), podczas gdy nieoczekiwane wyjątki generują błędne przypadki testowe.

```csharp
[PexMethod, PexAllowedException(typeof(ArgumentNullException))]
void SomeTest() {...}
```

Moduły sprawdzania poprawności są następujące:

* [PexAllowedException](attribute-glossary.md#pexallowedexception): umożliwia określenie określonego typu wyjątku z dowolnego miejsca
* [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly): zezwala na określony typ wyjątku z określonego zestawu
* [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype): zezwala na określony typ wyjątku z określonego typu
* [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest): zezwala na określony typ wyjątku z testowanego typu

<a name="internal-types"></a>
## <a name="testing-internal-types"></a>Testowanie typów wewnętrznych

IntelliTest mogą "testować" typy wewnętrzne, o ile mogą je zobaczyć. Aby IntelliTest wyświetlić typy, do produktu lub projektu testowego zostanie dodany następujący atrybut: kreatory programu Visual Studio IntelliTest

```csharp
[assembly: InternalsVisibleTo("Microsoft.Pex, PublicKey=002400000480000094000000060200000024000052534131000400000100010007d1fa57c4aed9f0a32e84aa0faefd0de9e8fd6aec8f87fb03766c834c99921eb23be79ad9d5dcc1dd9ad236132102900b723cf980957fc4e177108fc607774f29e8320e92ea05ece4e821c0a5efe8f1645c4c0c93c1ab99285d622caa652c1dfad63d745d6f2de5f17e5eaf0fc4963d261c8a12436518206dc093344d5ad293")]
```

<a name="assumptions-and-assertions"></a>
## <a name="assumptions-and-assertions"></a>Założenia i potwierdzenia

Użytkownicy mogą używać założeń i potwierdzeń do wyznaczania [warunków wstępnych](#precondition) (założeń) i [warunki końcowe](#postcondition) (potwierdzenia) o ich testach. Gdy IntelliTest generuje zbiór wartości parametrów i "eksploruje" kod, może naruszać założenie testu. Gdy tak się stanie, nie zostanie wygenerowany test dla tej ścieżki, ale zostanie on zignorowany w trybie dyskretnym.

Potwierdzenia są dobrze znaną koncepcją w regularnych strukturach testów jednostkowych, więc IntelliTest już "rozumie" wbudowane klasy **potwierdzeń** udostępniane przez poszczególne obsługiwane platformy testowe. Jednak większość struktur nie udostępnia klasy **przyjmij** . W takim przypadku IntelliTest udostępnia klasę [PexAssume](static-helper-classes.md#pexassume) . Jeśli nie chcesz używać istniejącej struktury testowej, IntelliTest również ma klasę [PexAssert](static-helper-classes.md#pexassert) .

```csharp
[PexMethod]
public void Test1(object o) {
    // precondition: o should not be null
    PexAssume.IsNotNull(o);

    ...
}
```

W szczególności założenie o wartości innej niż null może być zakodowany jako atrybut niestandardowy:

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

Warunek wstępny metody przedstawia warunki, w których metoda zakończy się pomyślnie.

Zwykle warunek wstępny jest wymuszany przez sprawdzenie parametrów i stanu obiektu i wyrzucanie **argumentuexception** lub **InvalidOperationException** , jeśli zostanie naruszony.

W IntelliTest, warunek wstępny [sparametryzowanego testu jednostkowego](#parameterized-unit-testing) jest wyrażany z [PexAssume](static-helper-classes.md#pexassume).

<a name="postcondition"></a>
## <a name="postcondition"></a>Warunek końcowy

Błąd warunku końcowego metody oznacza warunki, które powinny być przechowywane w czasie i po wykonaniu metody, przy założeniu, że jego warunki wstępne były początkowo prawidłowe.

Zazwyczaj błąd warunku końcowego jest wymuszana przez wywołania metod **Assert** .

W przypadku IntelliTest, błąd warunku końcowego z [sparametryzowanym testem jednostkowym](#parameterized-unit-testing) jest wyrażany przy użyciu [PexAssert](static-helper-classes.md#pexassert).

<a name="test-failures"></a>
## <a name="test-failures"></a>Niepowodzenia testów
Kiedy wygenerowany przypadek testowy kończy się niepowodzeniem?

1. Jeśli usługa nie zakończy działania w [skonfigurowanych granicach ścieżki](exploration-bounds.md), jest traktowana jako błąd, chyba że jest ustawiona opcja [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded)

1. Jeśli test zgłasza **PexAssumeFailedException**, powiedzie się. Jest to jednak zwykle odfiltrowane, chyba że [TestEmissionFilter](exploration-bounds.md#testemissionfilter) jest ustawiona na wartość **All**

1. Jeśli test narusza [potwierdzenie](#assumptions-and-assertions); na przykład przez wygenerowanie wyjątku naruszenia dla struktury testów jednostkowych nie powiedzie się

Jeśli żaden z powyższych elementów nie wygeneruje decyzji, test zakończy się pomyślnie, jeśli nie zgłosi wyjątku. Naruszenia potwierdzeń są traktowane w taki sam sposób jak wyjątki.

<a name="setup-teardown"></a>
## <a name="setup-and-tear-down"></a>Konfigurowanie i usuwanie

W ramach integracji z platformami testowymi IntelliTest obsługuje wykrywanie i uruchamianie instalatora oraz odrywanie metod.

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

* [Testuj do powiązania kodu](https://devblogs.microsoft.com/devops/smart-unit-tests-test-to-code-binding-test-case-management/)
* [Jeden test do reguły dla nich](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)

## <a name="got-feedback"></a>Chcesz przesłać opinię?

Opublikuj swoje pomysły i sugestie funkcji w [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
