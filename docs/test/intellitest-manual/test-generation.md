---
title: Generowanie testu | Narzędzie Test Microsoft IntelliTest dla deweloperów
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Test generation
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 8b5db931444d4bfd1c658fca9c067e698d079418
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936994"
---
# <a name="test-generation"></a>Generowanie testu

W tradycyjnych testy jednostkowe testu składa się kilka rzeczy:

* A [sekwencji wywołania metody](test-generation.md#test-generators)
* Argumenty, które metody są wywoływane; argumenty są [testowanie danych wejściowych](input-generation.md)
* Sprawdzanie poprawności to oczekiwane zachowanie przetestowanej aplikacji poprzez podanie zestawu [potwierdzenia](#assumptions-and-assertions)

Poniżej przedstawiono przykład struktury testów:

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

IntelliTest często automatycznie określić wartości argumentu istotne dla bardziej ogólnej [sparametryzowanych testów jednostkowych](#parameterized-unit-testing), które zawierają sekwencję wywołań metody i potwierdzenia.

<a name="test-generators"></a>
## <a name="test-generators"></a>Generatory testu

IntelliTest generuje przypadków testowych, wybierając sekwencję metod wdrażania w ramach testu do wykonania i generować dane wejściowe dla metody podczas sprawdzania potwierdzenia pochodne danych.

A [sparametryzowanego testu jednostkowego](#parameterized-unit-testing) bezpośrednio stany sekwencji metody wywołania w jej treści.

Gdy program IntelliTest potrzebuje do konstruowania obiektów, wywołania do konstruktorów i metod fabryki zostanie dodany automatycznie sekwencji zgodnie z potrzebami.

<a name="parameterized-unit-testing"></a>
## <a name="parameterized-unit-testing"></a>Sparametryzowane testy jednostkowe

*Parametryzowane testy jednostki* (umieszcza) są testy, które przyjmują parametry. W przeciwieństwie do tradycyjnych testów, które zwykle są zamknięte metod, umieszcza wykonaj dowolny zbiór parametrów. Jest to proste? Tak — w tym miejscu, IntelliTest podejmie próbę [Generowanie (minimalny) zestaw danych wejściowych](input-generation.md) , [obejmują w pełni](input-generation.md#dynamic-code-coverage) kod nieosiągalny z testu.

Umieszcza są definiowane przy użyciu [PexMethod](attribute-glossary.md#pexmethod) atrybutu niestandardowego w sposób podobny do MSTest (lub NUnit, xUnit). Umieszcza są metody wystąpienia, które logicznie pogrupowane w klasach oznakowane za pomocą [PexClass](attribute-glossary.md#pexclass). W poniższym przykładzie przedstawiono prosty PUT, przechowywane w **MyPexTest** klasy:

```csharp
[PexMethod]
void ReplaceFirstChar(string target, char c) {

    string result = StringHelper.ReplaceFirstChar(target, c);

    Assert.AreEqual(result[0], c);
}
```

gdzie **ReplaceFirstChar** to metoda, która zastępuje pierwszego znaku ciągu:

```csharp
class StringHelper {
    static string ReplaceFirstChar(string target, char c) {
        if (target == null) throw new ArgumentNullException();
        if (target.Length == 0) throw new ArgumentOutOfRangeException();
        return c + target.Substring(1);
    }
}
```

Z tego testu funkcji IntelliTest mogą automatycznie [wygenerowanie danych wejściowych](input-generation.md) dla PUT, który obejmuje wiele ścieżek wykonywania kodu przetestowane. Każdy wejściowej, który obejmuje wykonanie innej ścieżki pobiera "serializacji" jako test jednostkowy:

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
## <a name="generic-parameterized-unit-testing"></a>Ogólny sparametryzowanych testów jednostkowych

Sparametryzowane testy jednostkowe mogą być metod ogólnych. W takim przypadku użytkownik musi określić typy, użytego do utworzenia wystąpienia metody przy użyciu [PexGenericArguments](attribute-glossary.md#pexgenericarguments).

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

Funkcja IntelliTest zawiera wiele atrybutów sprawdzania poprawności, które ułatwia klasyfikowanie wyjątki w oczekiwane wyjątki i nieoczekiwanego wyjątku.

Oczekiwane wyjątki takie jak Generowanie ujemna przypadki testowe z odpowiednią adnotacją **ExpectedException (typeof (*xxx*))**, nieoczekiwane wyjątki generować w przypadku braku przypadków testowych.

```csharp
[PexMethod, PexAllowedException(typeof(ArgumentNullException))]
void SomeTest() {...}
```

Dostępne są następujące moduły weryfikacji:

* [PexAllowedException](attribute-glossary.md#pexallowedexception): umożliwia typ określony wyjątek, z dowolnego miejsca
* [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly): pozwala na typ określony wyjątek z określonego zestawu
* [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype): pozwala na typ określony wyjątek z określonego typu
* [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest): pozwala na typ określony wyjątek z testowanego typu

<a name="internal-types"></a>
## <a name="testing-internal-types"></a>Testowanie typy wewnętrzne

IntelliTest mogą "test" typy wewnętrzne, tak długo, jak go zobaczyć je. Funkcję IntelliTest wyświetlić typy następujący atrybut zostanie dodany do projektu produktu lub testów przez kreatorów Visual Studio program IntelliTest:

```csharp
[assembly: InternalsVisibleTo("Microsoft.Pex, PublicKey=002400000480000094000000060200000024000052534131000400000100010007d1fa57c4aed9f0a32e84aa0faefd0de9e8fd6aec8f87fb03766c834c99921eb23be79ad9d5dcc1dd9ad236132102900b723cf980957fc4e177108fc607774f29e8320e92ea05ece4e821c0a5efe8f1645c4c0c93c1ab99285d622caa652c1dfad63d745d6f2de5f17e5eaf0fc4963d261c8a12436518206dc093344d5ad293
```

<a name="assumptions-and-assertions"></a>
## <a name="assumptions-and-assertions"></a>Założenia i potwierdzeń

Użytkownicy mogą używać założenia i potwierdzeń express [warunki wstępne](#precondition) (założeń) i [warunków końcowych](#postcondition) (potwierdzenia) o swoich testów. Jeśli program IntelliTest generuje zestaw wartości parametrów, "Eksploruje" kod może naruszać założenie testu. Jeśli tak się stanie, nie zostanie wygenerowany test dla tej ścieżki, ale będzie po cichu ignorować go.

Potwierdzenia są dobrze znane pojęcia w struktur testów jednostek regularnych, więc IntelliTest już "rozumie" wbudowane **Asercja** klas dostarczonych przez każdy struktury testowej obsługiwane. Jednak większość platform nie są oferowane **Przyjmij** klasy. W takim przypadku udostępnia funkcję IntelliTest [PexAssume](static-helper-classes.md#pexassume) klasy. Jeśli nie chcesz używać istniejącej struktury testowej, IntelliTest ma również [PexAssert](static-helper-classes.md#pexassert) klasy.

```csharp
[PexMethod]
public void Test1(object o) {
    // precondition: o should not be null
    PexAssume.IsNotNull(o);

    ...
}
```

W szczególności założeń pod nie mogą być zakodowane jako atrybut niestandardowy:

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

Warunkiem wstępnym metody określa warunki, w których metoda zakończy się powodzeniem.

Zazwyczaj warunek konieczny jest wymuszana przez sprawdzanie parametrów i stan obiektu i zgłaszanie **ArgumentException** lub **InvalidOperationException** Jeśli jest ona naruszona.

W funkcji IntelliTest, warunkiem wstępnym [sparametryzowanego testu jednostkowego](#parameterized-unit-testing) jest wyrażany za pomocą [PexAssume](static-helper-classes.md#pexassume).

<a name="postcondition"></a>
## <a name="postcondition"></a>Postcondition

Postcondition metody określa warunki, które mają być przechowywane w trakcie i po nim wykonywanie metody, przy założeniu, że jego warunki wstępne zostały początkowo prawidłowe.

Zazwyczaj postcondition jest wymuszana przez wywołania **Asercja** metody.

Z funkcją IntelliTest, postcondition z [sparametryzowanego testu jednostkowego](#parameterized-unit-testing) jest wyrażany za pomocą [PexAssert](static-helper-classes.md#pexassert).

<a name="test-failures"></a>
## <a name="test-failures"></a>Niepowodzenia testu
Kiedy wygenerowany przypadek testowy nie powiódł się?

1. Jeśli nie kończy się w obrębie [skonfigurowane ścieżką granic](exploration-bounds.md), jest traktowane jako błąd, chyba że [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded) ustawiono opcję

1. Jeśli test zgłosi **PexAssumeFailedException**, jego powodzenia. Jednak jest zwykle filtrowane się, chyba że [TestEmissionFilter](exploration-bounds.md#testemissionfilter) ustawiono **wszystkie**

1. Jeśli test narusza [potwierdzenie](#assumptions-and-assertions); na przykład, zgłaszając wyjątek asercji naruszenie testowania jednostkowego, zakończy się niepowodzeniem

Jeśli żadne z powyższych decyzji, test zakończy się powodzeniem, tylko wtedy, gdy nie zostanie zgłoszony wyjątek. Potwierdzenie naruszeń są traktowane w taki sam sposób jak wyjątki.

<a name="setup-teardown"></a>
## <a name="setup-and-tear-down"></a>Konfigurowanie i zatrzymywania

W ramach integracji ze środowisk testowych IntelliTest obsługuje wykrywanie i uruchamiania instalacji i zatrzymywania metody.

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
## <a name="further-reading"></a>Dalsze informacje

* [Test, aby kod powiązania](https://blogs.msdn.microsoft.com/devops/2015/04/18/smart-unit-tests-test-to-code-binding-test-case-management/)
* [Jeden test, by wszystkimi rządzić](https://blogs.msdn.microsoft.com/devops/2015/07/05/intellitest-one-test-to-rule-them-all/)

## <a name="got-feedback"></a>Czy chcesz przesłać opinię?

Opublikuj swoje pomysły i funkcji żądania na [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).