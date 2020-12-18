---
title: Słownik atrybutów | Narzędzie testowe dla deweloperów Microsoft IntelliTest
description: Ten artykuł zawiera listę atrybutów IntelliTest zorganizowanych według przestrzeni nazw oraz szczegóły dotyczące atrybutów.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Attribute glossary
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 0c406f8900ee890eaf8419ce27adeba2d06c81dd
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668797"
---
# <a name="attribute-glossary"></a>Słownik atrybutów

## <a name="attributes-by-namespace"></a>Atrybuty według przestrzeni nazw

* **Microsoft. Pex. Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
    * [PexExplorationAttributeBase](#pexexplorationattributebase)

* **Microsoft. Pex. Framework. Settings**
  * [PexAssemblySettings](#pexassemblysettings)

* **Microsoft. Pex. Framework. Instrumentation**
  * [PexAssemblyUnderTest](#pexassemblyundertest)
  * [PexInstrumentAssembly](#pexinstrumentassemblyattribute)

* **Microsoft. Pex. Framework. using**
  * [PexUseType](#pexusetype)

* **Microsoft. Pex. Framework. Validation**
  * [PexAllowedException](#pexallowedexception)
  * [PexAllowedExceptionFromAssembly](#pexallowedexceptionfromassembly)
  * [PexAllowedExceptionFromType](#pexallowedexceptionfromtype)
  * [PexAllowedExceptionFromTypeUnderTest](#pexallowedexceptionfromtypeundertest)

<a name="pexassumenotnull"></a>
## <a name="pexassumenotnull"></a>PexAssumeNotNull

Ten atrybut potwierdza, że wartość zarządzana nie może mieć **wartości null**. Można go dołączyć do:

* **parametr** sparametryzowanej metody testowej

  ```csharp
  // assume foo is not null
  [PexMethod]
  public void SomeTest([PexAssumeNotNull]IFoo foo, ...) {}
  ```

* **pole**

  ```csharp
  public class Foo {
     // this field should not be null
     [PexAssumeNotNull]
     public object Bar;
  }
  ```

* **Typ**

  ```csharp
  // never consider null for Foo types
  [PexAssumeNotNull]
  public class Foo {}
  ```

Można go również dołączyć do zestawu testowego, armatury testowej lub metody testowej; w tym przypadku pierwsze argumenty muszą wskazywać, do którego pola lub typu mają zastosowanie założenia. Gdy atrybut ma zastosowanie do typu, ma zastosowanie do wszystkich pól z tym typem formalnym.

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

Ten atrybut oznacza klasę, która zawiera *eksploracje*. Jest odpowiednikiem MSTest **TestClassAttribute** (lub nunit **TestFixtureAttribute**). Ten atrybut jest opcjonalny.

Klasy oznaczone atrybutem [PexClass](#pexclass) muszą mieć *wartość default konstrukcyjną*:

* Typ publiczny wyeksportowany
* konstruktor domyślny
* nieabstrakcyjny

Jeśli Klasa nie spełnia tych wymagań, zgłaszany jest błąd i Eksploracja kończy się niepowodzeniem.

Zdecydowanie zaleca się również uczynić te klasy **częściową** , aby IntelliTest mogły generować nowe testy, które są częścią klasy, ale w oddzielnym pliku. Takie podejście rozwiązuje wiele problemów spowodowanych [widocznością](input-generation.md#visibility) i jest typową techniką w języku C#.

**Dodatkowy zestaw i kategorie**:

```csharp
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**Określanie testowanego typu**:

```csharp
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

Klasa może zawierać metody z adnotacją [PexMethod](#pexmethod). IntelliTest rozumie również [metody konfiguracji i odrywania](test-generation.md#setup-teardown).

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

Ten atrybut zawiera krotkę typu dla tworzenia wystąpienia [generycznego, sparametryzowanego testu jednostkowego](test-generation.md#generic-parameterized).

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

Ten atrybut oznacza metodę jako [sparametryzowany test jednostkowy](test-generation.md#parameterized-unit-testing).
Metoda musi znajdować się w klasie oznaczonej atrybutem [PexClass](#pexclass) .

IntelliTest wygeneruje tradycyjne, bezparametryczne testy, które wywołują [sparametryzowany test jednostkowy](test-generation.md#parameterized-unit-testing) z innymi parametrami.

Sparametryzowany test jednostkowy:

* musi być metodą wystąpienia
* musi być [widoczny](input-generation.md#visibility) dla klasy testowej, w której są umieszczane wygenerowane testy zgodnie z [ustawieniami kaskadowymi](settings-waterfall.md)
* może przyjmować dowolną liczbę parametrów
* może być rodzajowa

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

Ten atrybut można ustawić na poziomie zestawu, aby przesłonić domyślne wartości ustawień dla wszystkich eksploracji.

```csharp
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "MSTestv2")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

Ten atrybut określa zestaw, który jest testowany przez bieżący projekt testu.

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

Ten atrybut służy do określania zestawu, który ma być Instrumentacją.

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

Ten atrybut informuje IntelliTest, że może użyć określonego typu do wystąpienia (Abstract) typów podstawowych lub interfejsów.

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

Jeśli ten atrybut jest dołączony do [PexMethod](#pexmethod) (lub do [PexClass](#pexclass), zmienia domyślną logikę IntelliTest, która wskazuje, kiedy testy zakończą się niepowodzeniem. Test nie będzie uznawany za zakończony niepowodzeniem, nawet jeśli zgłasza określony wyjątek.

**Przykład**

Następujący test określa, że Konstruktor **stosu** może zgłosić **wyjątku ArgumentOutOfRangeException**:

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

Filtr jest dołączany do armatury w następujący sposób (można go również zdefiniować na poziomie zestawu lub testu):

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

## <a name="got-feedback"></a>Chcesz przesłać opinię?

Opublikuj swoje pomysły i sugestie funkcji w [społeczności deweloperów](https://aka.ms/feedback/suggest?space=8).
