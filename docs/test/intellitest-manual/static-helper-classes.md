---
title: Statyczne klasy pomocników | Narzędzie testowe dla deweloperów Microsoft IntelliTest
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Static helper classes
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 5010761213cf79756cf8da3d2fffe60dd0b61efd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315190"
---
# <a name="static-helper-classes"></a>Statyczne klasy pomocy

IntelliTest udostępnia zestaw statycznej klasy pomocnika, który może być używany podczas tworzenia [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing):

* [PexAssume](#pexassume): używany do definiowania założeń dla danych wejściowych i jest przydatny do filtrowania niepożądanych danych wejściowych
* [PexAssert](#pexassert): prosta Klasa potwierdzenia do użycia, jeśli struktura testowa nie udostępnia jednego
* [PexChoose](#pexchoose): strumień dodatkowych danych wejściowych testów zarządzanych przez IntelliTest
* [Funkcja PexObserve](#pexobserve): rejestruje konkretne wartości i, opcjonalnie, sprawdza poprawność ich w wygenerowanym kodzie

Niektóre klasy umożliwiają posługiwanie się aparatem IntelliTest z powodu niskiego poziomu:

* [PexSymbolicValue](#pexsymbolicvalue): narzędzia do inspekcji lub modyfikowania ograniczeń symbolicznych dla zmiennych

<a name="pexassume"></a>
## <a name="pexassume"></a>PexAssume

Klasa statyczna służąca do wyrażenia założeń, takich jak [warunki wstępne](test-generation.md#precondition), w [sparametryzowanych testach jednostkowych](test-generation.md#parameterized-unit-testing). Metody tej klasy mogą służyć do filtrowania niepożądanych danych wejściowych testu.

Jeśli przyjęty warunek nie jest przechowywany w przypadku niektórych danych wejściowych testu, zgłaszany jest **PexAssumeFailedException** . Spowoduje to, że test będzie ignorowany w trybie dyskretnym.

**Przykład**

Następujący test sparametryzowany nie będzie uwzględniać **j = 0**:

```csharp
public void TestSomething(int i, int j) {
     PexAssume.AreNotEqual(j, 0);
     int k = i/j;
     ...
}
```

**Uwagi**

Powyższy kod jest niemal odpowiednikiem:

```csharp
     if (j==0)
          return;
```

z tą różnicą, że niepowodzenie **PexAssume** powoduje brak przypadków testowych. W przypadku instrukcji **if** IntelliTest generuje oddzielny przypadek testowy, aby pokryć gałąź **then** instrukcji **if** .

**PexAssume** zawiera również wyspecjalizowane klasy zagnieżdżone dla założeń dla ciągów, tablic i kolekcji.

<a name="pexassert"></a>
## <a name="pexassert"></a>PexAssert

Klasa statyczna używana do wyznaczania potwierdzeń, takich jak [warunki końcowe](test-generation.md#postcondition), w [sparametryzowanych testach jednostkowych](test-generation.md#parameterized-unit-testing).

Jeśli potwierdzony warunek nie utrzymuje niektórych danych wejściowych testu, zgłaszany jest **PexAssertFailedException** , co powoduje niepowodzenie testu.

**Przykład**

Następujące potwierdzenia, że wartość bezwzględną liczby całkowitej jest dodatnia:

```csharp
public void TestSomething(int i) {
     int j = Maths.Abs(i);
     PexAssert.IsTrue(j >= 0);
     ...
}
```

<a name="pexchoose"></a>
## <a name="pexchoose"></a>PexChoose

Klasa statyczna, która dostarcza pomocnicze wartości wejściowe do testu, który może służyć do implementowania [makiet sparametryzowanych](input-generation.md#parameterized-mocks).

Klasa **PexChoose** nie pomaga w określeniu, czy test kończy się powodzeniem, czy nie, dla określonych wartości wejściowych. **PexChoose** po prostu zawiera wartości wejściowe, które są również określane jako *Opcje*. Nadal istnieje możliwość ograniczenia wartości wejściowych oraz do zapisu, które definiują, kiedy test lub kończy się niepowodzeniem.

**Tryby operacyjne**

Klasa **PexChoose** może działać w dwóch trybach:

* Podczas gdy IntelliTest wykonuje analizę symboliczną testu i testowany kod podczas [generowania danych wejściowych](input-generation.md), selektor zwraca dowolne wartości i IntelliTest śledzi, jak każda wartość jest używana w teście i testowanym kodzie. IntelliTest generuje odpowiednie wartości, aby wyzwolić różne ścieżki wykonywania w teście i testowanym kodzie.

* Wygenerowany kod dla określonych przypadków testowych konfiguruje dostawcę wyboru w określony sposób, tak aby ponowne wykonanie takiego przypadku testowego powodowało wybór konkretnych opcji wyzwalania określonej ścieżki wykonania.

**Użycie**

* Proste wywołanie **PexChoose. Value** w celu wygenerowania nowej wartości:

```csharp
public int Foo() {
    return PexChoose.Value<int>("foo");
}
```

<a name="pexobserve"></a>
## <a name="pexobserve"></a>PexObserve

Klasa statyczna do rejestrowania nazwanych wartości.

Gdy IntelliTest eksploruje kod, **Funkcja PexObserve** jest używany do rejestrowania wartości obliczanych przy użyciu ich sformatowanych reprezentacji w postaci ciągów. Wartości są skojarzone z unikatowymi nazwami.

```csharp
PexObserve.Value<string>("result", result);
```

**Przykład**

```csharp
// product code
public static class MathEx {
     public static int Square(int value) { return value * value; }
}

// fixture
[TestClass]
public partial class MathExTests {
     [PexMethod]
     public int SquareTest(int a) {
        int result = MathEx.Square(a);
        // storing result
        return result;
     }
}
```

<a name="pexsymbolicvalue"></a>
## <a name="pexsymbolicvalue"></a>PexSymbolicValue

Klasa statyczna używana do ignorowania ograniczeń dotyczących parametrów oraz do drukowania informacji symbolicznych skojarzonych z wartościami.

**Użycie**

Zwykle IntelliTest próbuje uwzględnić wszystkie ścieżki wykonywania kodu podczas wykonywania. Jednak szczególnie w przypadku obliczania warunków założeń i potwierdzeń nie należy eksplorować wszystkich możliwych przypadków.

**Przykład**

Ten przykład pokazuje implementację metody **PexAssume. Arrays. ElementsAreNotNull** .
W metodzie można zignorować ograniczenia dotyczące lengh wartości tablicy, aby uniknąć IntelliTest prób wygenerowania różnych rozmiarów tablicy. Ograniczenia są ignorowane tylko w tym miejscu. Jeśli testowany kod działa inaczej dla różnych długości tablicy, IntelliTest nie może generować różnych tablic o różnej wielkości z ograniczeń przetestowanego kodu.

```csharp
public static void AreElementsNotNull<T>(T[] value)
    where T : class
{
    PexAssume.NotNull(value);
    // the followings prevents the exploration of all array lengths
    int len = PexSymbolicValue.Ignore<int>(value.Length);

    // building up a boolean value as follows prevents exploration
    // of all combinations of non-null (instead, there are just two cases)
    bool anyNull = false;
    for (int i = 0; i < len; ++i)
        anyNull |= value[i] == null;

    // was any element null?
    if (anyNull)
        PexAssume.Fail("some element of array is a null reference");
}
```

## <a name="got-feedback"></a>Chcesz przesłać opinię?

Opublikuj swoje pomysły i sugestie funkcji w [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
