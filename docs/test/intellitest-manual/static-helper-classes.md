---
title: Klasy statyczne pomocnika | Narzędzie testowe Microsoft IntelliTest Developer
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302617"
---
# <a name="static-helper-classes"></a>Statyczne klasy pomocy

IntelliTest zawiera zestaw statycznych klasy pomocnika, które mogą być używane podczas tworzenia [sparametryzowanych testów jednostkowych:](test-generation.md#parameterized-unit-testing)

* [PexAssume](#pexassume): służy do definiowania założeń dotyczących danych wejściowych i jest przydatny do filtrowania niepożądanych danych wejściowych
* [PexAssert:](#pexassert)prosta klasa asercji do użycia, jeśli struktura testowa nie zapewnia
* [PexChoose](#pexchoose): strumień dodatkowych danych wejściowych testowych, którymi zarządza IntelliTest
* [PexObserve](#pexobserve): rejestruje konkretne wartości i, opcjonalnie, sprawdza je w wygenerowanym kodzie

Niektóre klasy umożliwiają interakcję z silnikiem rozumowania IntelliTest na niskim poziomie:

* [PexSymbolicValue](#pexsymbolicvalue): narzędzia do sprawdzania lub modyfikowania ograniczeń symbolicznych zmiennych

<a name="pexassume"></a>
## <a name="pexassume"></a>PexAssume

Klasa statyczna używana do wyrażania założeń, takich jak [warunki wstępne,](test-generation.md#precondition)w [sparametryzowanych testach jednostkowych.](test-generation.md#parameterized-unit-testing) Metody tej klasy może służyć do filtrowania niepożądanych danych wejściowych testu.

Jeśli zakłada się warunek nie posiada dla niektórych danych wejściowych testu, **PexAssumeFailedException** jest generowany. Spowoduje to, że test będzie po cichu ignorowane.

**Przykład**

Następujący sparametryzowany test nie uwzględnia **j=0:**

```csharp
public void TestSomething(int i, int j) {
     PexAssume.AreNotEqual(j, 0);
     int k = i/j;
     ...
}
```

**Uwagi**

Powyższy kod jest prawie równoważny:

```csharp
     if (j==0)
          return;
```

z wyjątkiem tego, że upadające **wyniki PexAssume** nie powoduje przypadków testowych. W przypadku **if** instrukcji IntelliTest generuje oddzielny przypadek testowy na pokrycie **następnie** gałęzi **if** instrukcji.

**PexAssume** zawiera również wyspecjalizowane klasy zagnieżdżone dla założeń dotyczących ciągów, tablic i kolekcji.

<a name="pexassert"></a>
## <a name="pexassert"></a>PexAssert

Klasa statyczna używana do wyrażania potwierdzeń, takich jak [postconditions,](test-generation.md#postcondition)w [sparametryzowanych testach jednostkowych.](test-generation.md#parameterized-unit-testing)

Jeśli potwierdzone warunek nie posiada dla niektórych danych wejściowych testu, **PexAssertFailedException** jest generowany, co powoduje, że test zakończy się niepowodzeniem.

**Przykład**

Poniżej stwierdza się, że wartość bezwzględna liczby całkowitej jest dodatnia:

```csharp
public void TestSomething(int i) {
     int j = Maths.Abs(i);
     PexAssert.IsTrue(j >= 0);
     ...
}
```

<a name="pexchoose"></a>
## <a name="pexchoose"></a>PexChoose

Klasa statyczna, która dostarcza pomocnicze wartości wejściowe do testu, który może służyć do implementacji [makiet sparametryzowanych](input-generation.md#parameterized-mocks).

**PexChoose** Klasa nie pomaga w określeniu, czy test kończy się niepowodzeniem dla określonych wartości wejściowych. **PexChoose** po prostu zapewnia wartości wejściowe, które są również określane jako *wybory*. Nadal jest do użytkownika, aby ograniczyć wartości wejściowe i napisać potwierdzenia, które definiują, gdy test przechodzi lub kończy się niepowodzeniem.

**Tryby operacyjne**

Klasa **PexChoose** może działać w dwóch trybach:

* Podczas intellitest wykonuje symboliczną analizę testu i testowanego kodu podczas [generowania danych wejściowych,](input-generation.md)wybierak zwraca dowolne wartości i IntelliTest śledzi, jak każda wartość jest używana w teście i testowany kod. IntelliTest wygeneruje odpowiednie wartości, aby wyzwolić różne ścieżki wykonywania w teście i testowany kod.

* Wygenerowany kod dla określonych przypadków testowych konfiguruje dostawcę wyboru w określony sposób, tak aby ponowne wykonanie takiego przypadku testowego dokona określonych wyborów, aby wyzwolić określoną ścieżkę wykonywania.

**Użycia**

* Proste **wywołanie PexChoose.Value** do generowania nowej wartości:

```csharp
public int Foo() {
    return PexChoose.Value<int>("foo");
}
```

<a name="pexobserve"></a>
## <a name="pexobserve"></a>PexObserve

Klasa statyczna do rejestrowania nazwanych wartości.

Gdy IntelliTest eksploruje kod, **PexObserve** jest używany do rejestrowania obliczonych wartości przy użyciu ich sformatowanych reprezentacji ciągów. Wartości są skojarzone z unikatowymi nazwami.

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

Klasa statyczna używana do ignorowania ograniczeń parametrów i drukowania informacji symbolicznych skojarzonych z wartościami.

**Użycia**

Zwykle IntelliTest próbuje pokryć wszystkie ścieżki wykonywania kodu podczas wykonywania. Jednak, zwłaszcza podczas obliczania założenia i warunki potwierdzenia, nie należy badać wszystkie możliwe przypadki.

**Przykład**

W tym przykładzie pokazano implementację **PexAssume.Arrays.ElementsAreNotNull** metody.
W metodzie można zignorować ograniczenia długości wartości tablicy, aby uniknąć IntelliTest próbuje wygenerować różne rozmiary tablicy. Ograniczenia są ignorowane tylko w tym miejscu. Jeśli testowany kod zachowuje się inaczej dla różnych długości tablicy, IntelliTest nie może generować macierzy o różnych rozmiarach z ograniczeń testowanego kodu.

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
