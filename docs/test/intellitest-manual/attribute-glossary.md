---
title: Słownik atrybutów | Narzędzie Test Microsoft IntelliTest dla deweloperów
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Attribute glossary
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 7c5f1883a5d8c09713d520aa934f91b32cbaf388
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978986"
---
# <a name="attribute-glossary"></a>Słownik atrybutów

## <a name="attributes-by-namespace"></a>Atrybuty w zależności od przestrzeni nazw

* **Microsoft.Pex.Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
     - [PexExplorationAttributeBase](#pexexplorationattributebase)

* **Microsoft.Pex.Framework.Settings**
  * [PexAssemblySettings](#pexassemblysettings)

* **Microsoft.Pex.Framework.Instrumentation**
  * [PexAssemblyUnderTest](#pexassemblyundertest)
  * [PexInstrumentAssembly](#pexinstrumentassemblyattribute)

* **Microsoft.Pex.Framework.Using**
  * [PexUseType](#pexusetype)

* **Microsoft.Pex.Framework.Validation**
  * [PexAllowedException](#pexallowedexception)
  * [PexAllowedExceptionFromAssembly](#pexallowedexceptionfromassembly)
  * [PexAllowedExceptionFromType](#pexallowedexceptionfromtype)
  * [PexAllowedExceptionFromTypeUnderTest](#pexallowedexceptionfromtypeundertest)

<a name="pexassumenotnull"></a>
## <a name="pexassumenotnull"></a>PexAssumeNotNull

Ten atrybut potwierdza, że zarządzanych wartość nie może być **null**. Mogą być dołączane do:

* **parametr** metody test sparametryzowany

  ```csharp
  // assume foo is not null
  [PexMethod]
  public void SomeTest([PexAssumeNotNull]IFoo foo, ...) {}
  ```

* **pola**

  ```csharp
  public class Foo {
     // this field should not be null
     [PexAssumeNotNull]
     public object Bar;
  }
  ```

* A **typu**

  ```csharp
  // never consider null for Foo types
  [PexAssumeNotNull]
  public class Foo {}
  ```

Również może być dołączane do zestawu testowego, warunki początkowe testu lub metodę testową; w tym przypadku pierwsze argumentów musi wskazywać, pole lub typ założeń dotyczyć. Gdy ten atrybut ma zastosowanie do typu, ma zastosowanie do wszystkich pól w przypadku tego typu formalnego.

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

Ten atrybut oznacza klasę, która zawiera *eksploracji*. Jest to równoważne MSTest **TestClassAttribute** (lub NUnit **TestFixtureAttribute**). Ten atrybut jest opcjonalny.

Klasy oznaczone atrybutem [PexClass](#pexclass) musi być *domyślne konstrukcyjną*:

* publicznie wyeksportowanego typu
* konstruktor domyślny
* nie jest abstrakcyjna

Jeśli klasa nie spełnia tych wymagań, jest zgłaszany błąd i eksplorowania zakończy się niepowodzeniem.

Ponadto zdecydowanie zaleca się tych klas **częściowe** tak, aby program IntelliTest mogą generować nowe testy, które należą do klasy, ale w oddzielnym pliku. To podejście pozwala rozwiązać wiele problemów ze względu na [widoczność](input-generation.md#visibility) i jest to typowa technika w C#.

**Dodatkowy pakiet i kategorie**:

```csharp
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**Określanie typu testowanej**:

```csharp
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

Klasa może zawierać metody oznaczony za pomocą [PexMethod](#pexmethod). IntelliTest również rozumie [ustawiania i zatrzymywania metody](test-generation.md#setup-teardown).

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

Ten atrybut zapewnia krotki typu podczas tworzenia wystąpienia [ogólny sparametryzowanego testu jednostkowego](test-generation.md#generic-parameterized).

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

Ten atrybut oznacza metodę jako [sparametryzowanego testu jednostkowego](test-generation.md#parameterized-unit-testing).
Metoda musi znajdować się w klasie oznaczonej [PexClass](#pexclass) atrybutu.

Program IntelliTest zostanie wygenerowany testów tradycyjnych, bez parametrów, które wymagają [sparametryzowanego testu jednostkowego](test-generation.md#parameterized-unit-testing) z innymi parametrami.

Sparametryzowanego testu jednostkowego:

* musi być metodą wystąpienia
* musi być [widoczne](input-generation.md#visibility) do klasy testowej, w którym wygenerowane testy są umieszczane na podstawie [kaskadowy model ustawień](settings-waterfall.md)
* może potrwać dowolną liczbę parametrów
* może być ogólna

**Przykład**

```csharp
[PexClass]
public partial class MyTests {
     [PexMethod]
     public void MyTest(int i)
     { ... }
}
```

<a name="pexexplorationattributebase"></a>
## <a name="pexexplorationattributebase"></a>PexExplorationAttributeBase

[Więcej informacji](xref:Microsoft.Pex.Framework.PexExplorationAttributeBase)

<a name="pexassemblysettings"></a>
## <a name="pexassemblysettings"></a>PexAssemblySettings

Ten atrybut można ustawić na poziomie zestawu, aby zastąpić wartości ustawienia domyślne dla wszystkich eksploracji.

```csharp
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "Naked")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

Ten atrybut określa zestaw, który jest testowany przez bieżący projekt testowy.

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

Ten atrybut służy do określania zestawu instrumentacji.

**Przykład**

```csharp
using Microsoft.Pex.Framework;

// the assembly containing ATypeFromTheAssemblyToInstrument should be instrumented
[assembly: PexInstrumentAssembly(typeof(ATypeFromTheAssemblyToInstrument))]

// the assembly name can be used as well
[assembly: PexInstrumentAssembly("MyAssemblyName")]
```

<a name="pexusetype"></a>
## <a name="pexusetype"></a>PexUseType

Ten atrybut informuje program IntelliTest danego typu może użyć do utworzenia wystąpienia typów podstawowych (abstrakcyjny) lub interfejsów.

**Przykład**

```csharp
[PexMethod]
[PexUseType(typeof(A))]
[PexUseType(typeof(B))]
public void MyTest(object testParameter)
{
     ... // IntelliTest will consider types A and B to instantiate 'testParameter'
}
```

<a name="pexallowedexception"></a>
## <a name="pexallowedexception"></a>PexAllowedException

Jeśli ten atrybut jest dołączany do [PexMethod](#pexmethod) (lub [PexClass](#pexclass), zmienia się domyślnej logiki IntelliTest, która wskazuje, kiedy testów kończy się niepowodzeniem. Test nie zostanie uwzględniony jako nieudany — nawet wtedy, gdy w wyniku weryfikacji zgłasza wyjątek określonego wyjątku.

**Przykład**

Następującego testu określa, że Konstruktor **stosu** może zgłaszać **trwa wyjątku ArgumentOutOfRangeException**:

```csharp
class Stack {
  int[] _elements;
  int _count;
  public Stack(int capacity) {
    if (capacity<0) throw new ArgumentOutOfRangeException();
    _elements = new int[capacity];
    _count = 0;
  }
  ...
}
```

Filtr jest dołączony do warunków początkowych w następujący sposób (go można też zdefiniować na poziomie zestawu lub testowania):

```csharp
[PexMethod]
[PexAllowedException(typeof(ArgumentOutOfRangeException))]
class CtorTest(int capacity) {
  Stack s = new Stack(capacity); // may throw ArgumentOutOfRangeException
}
```

<a name="pexallowedexceptionfromassembly"></a>
## <a name="pexallowedexceptionfromassembly"></a>PexAllowedExceptionFromAssembly

[Więcej informacji](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromAssemblyAttribute)

<a name="pexallowedexceptionfromtype"></a>
## <a name="pexallowedexceptionfromtype"></a>PexAllowedExceptionFromType

[Więcej informacji](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromTypeAttribute)

<a name="pexallowedexceptionfromtypeundertest"></a>
## <a name="pexallowedexceptionfromtypeundertest"></a>PexAllowedExceptionFromTypeUnderTest

[Więcej informacji](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromTypeUnderTestAttribute)

## <a name="got-feedback"></a>Czy chcesz przesłać opinię?

Opublikuj swoje pomysły i funkcji żądania na [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
