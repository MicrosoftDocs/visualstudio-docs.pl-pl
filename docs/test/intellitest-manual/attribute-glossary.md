---
title: Glosariusz atrybutów | Narzędzie testowe Microsoft IntelliTest Developer
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Attribute glossary
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 00d8b24d26237a3c7b4130eba4614b5ea7b7eccd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302631"
---
# <a name="attribute-glossary"></a>Słownik atrybutów

## <a name="attributes-by-namespace"></a>Atrybuty według obszaru nazw

* **Microsoft.Pex.Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
    * [PexExplorationAttributeBase](#pexexplorationattributebase)

* **Ustawienia microsoft.pex.framework.**
  * [PexAssemblySettings](#pexassemblysettings)

* **Instrumentacja microsoft.Pex.Framework.Instrumentacja**
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

Ten atrybut potwierdza, że wartość regulowana nie może mieć **wartości null**. Może być dołączony do:

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

* **typ**

  ```csharp
  // never consider null for Foo types
  [PexAssumeNotNull]
  public class Foo {}
  ```

Może być również dołączony do zespołu badawczego, urządzenia badawczego lub metody badawczej; w tym przypadku pierwsze argumenty muszą wskazywać, do którego pola lub typu mają zastosowanie założenia. Gdy atrybut ma zastosowanie do typu, ma zastosowanie do wszystkich pól o tym typie formalnym.

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

Ten atrybut oznacza klasę zawierającą *eksploracje*. Jest odpowiednikiem mstest **testclassattribute** (lub NUnit **TestFixtureAttribute**). Ten atrybut jest opcjonalny.

Klasy oznaczone [pexclass](#pexclass) muszą być *domyślnie konstrukcyjne:*

* typ eksportowany publicznie
* konstruktor domyślny
* nie abstrakcyjne

Jeśli klasa nie spełnia tych wymagań, zgłaszany jest błąd i eksploracja kończy się niepowodzeniem.

Zaleca się również, aby te klasy **częściowe,** tak aby IntelliTest można wygenerować nowe testy, które są częścią klasy, ale w oddzielnym pliku. Takie podejście rozwiązuje wiele problemów z powodu [widoczności](input-generation.md#visibility) i jest typową techniką w języku C#.

**Dodatkowy pakiet i kategorie:**

```csharp
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**Określenie typu badany:**

```csharp
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

Klasa może zawierać metody z adnotacjami [o PexMethod](#pexmethod). IntelliTest rozumie również [metody konfigurowania i niszczą.](test-generation.md#setup-teardown)

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

Ten atrybut udostępnia krotek typu do tworzenia wystąpienia [ogólnego sparametryzowanego testu jednostkowego](test-generation.md#generic-parameterized).

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

Ten atrybut oznacza metodę jako [sparametryzowany test jednostkowy](test-generation.md#parameterized-unit-testing).
Metoda musi znajdować się w klasie oznaczonej atrybutem [PexClass.](#pexclass)

IntelliTest wygeneruje tradycyjne, bez parametrów testy, które wywołują [sparametryzowany test jednostkowy](test-generation.md#parameterized-unit-testing) z różnymi parametrami.

Spartylizowany test jednostkowy:

* musi być metodą wystąpienia
* muszą być [widoczne dla](input-generation.md#visibility) klasy testowej, do której są umieszczane wygenerowane testy zgodnie z [ustawieniami Wodospadu](settings-waterfall.md)
* może przyjmować dowolną liczbę parametrów
* może być ogólny

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

Ten atrybut można ustawić na poziomie zestawu, aby zastąpić domyślne wartości ustawień dla wszystkich eksploracji.

```csharp
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "MSTestv2")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

Ten atrybut określa zestaw, który jest testowany przez bieżący projekt testowy.

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

Ten atrybut jest używany do określenia zestawu, który ma być instrumentowany.

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

Ten atrybut informuje IntelliTest, że można użyć określonego typu do tworzenia wystąpienia (abstrakcyjne) typy podstawowe lub interfejsy.

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

Jeśli ten atrybut jest dołączony do [PexMethod](#pexmethod) (lub [PexClass](#pexclass), zmienia domyślną logikę IntelliTest, która wskazuje, gdy testy nie powiedzie się. Test nie zostanie uznany za nieudany, nawet jeśli zgłasza określony wyjątek.

**Przykład**

Poniższy test określa, że konstruktor **Stack** może zgłosić **ArgumentOutOfRangeException:**

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

Filtr jest przymocowany do oprawy w następujący sposób (można go również zdefiniować na poziomie złożenia lub badania):

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

Opublikuj swoje pomysły i sugestie funkcji w [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
