---
title: Statyczne klasy pomocy | Narzędzie Test Microsoft IntelliTest dla deweloperów
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Static helper classes
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 56493da196a0d53ead738b2eff6d10a2f9328c37
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929328"
---
# <a name="static-helper-classes"></a>Statyczne klasy pomocy

IntelliTest udostępnia zestaw klasy pomocnika statyczne, które mogą być używane podczas tworzenia [parametryzowane testy jednostki](test-generation.md#parameterized-unit-testing):

* [PexAssume](#pexassume): służy do definiowania założenia na dane wejściowe i jest przydatne w przypadku filtrowania niepożądanych danych wejściowych
* [PexAssert](#pexassert): klasa potwierdzenie prosty do użycia, jeśli swojej struktury testów nie zapewnia
* [PexChoose](#pexchoose): strumień danych wejściowych dodatkowe badanie, które zarządza program IntelliTest
* [PexObserve](#pexobserve): rejestruje konkretnych wartości i, opcjonalnie, sprawdza poprawność ich w wygenerowanym kodzie

Niektóre klasy umożliwiają interakcję z silnikiem logikę IntelliTest niskiego poziomu:

* [PexSymbolicValue](#pexsymbolicvalue): narzędzia, aby inspekcja lub modyfikowanie symboliczne ograniczenia dotyczące zmiennych

<a name="pexassume"></a>
## <a name="pexassume"></a>PexAssume

Klasa statyczna stosowany w celu założenia, takich jak [warunki wstępne](test-generation.md#precondition)w [parametryzowane testy jednostki](test-generation.md#parameterized-unit-testing). Metody tej klasy można odfiltrować dane wejściowe testu niepożądane.

Jeśli nie ma warunku zakładanego niektórych testów do wprowadzania, **PexAssumeFailedException** zgłaszany. To spowoduje, że test jest dyskretnie ignorowana.

**Przykład**

Następujący test sparametryzowany, nie uwzględni **"j" = 0**:

```csharp
public void TestSomething(int i, int j) {
     PexAssume.AreNotEqual(j, 0);
     int k = i/j;
     ...
}
```

**Uwagi**

Powyższy kod jest prawie równoważne:

```csharp
     if (j==0)
          return;
```

z tą różnicą, że niepowodzenie **PexAssume** powoduje brak przypadków testowych. W przypadku właściwości **Jeśli** instrukcji, program IntelliTest generuje oddzielny przypadek testowy do pokrycia **następnie** gałęzi **Jeśli** instrukcji.

**PexAssume** zawiera również specjalistyczne klas zagnieżdżonych do założenia na ciąg, tablice i kolekcje.

<a name="pexassert"></a>
## <a name="pexassert"></a>PexAssert

Klasa statyczna stosowany w celu potwierdzenia, takich jak [warunków końcowych](test-generation.md#postcondition)w [parametryzowane testy jednostki](test-generation.md#parameterized-unit-testing).

Jeśli warunek potwierdzone nie przechowuje dla niektórych testów do wprowadzania, **PexAssertFailedException** jest zgłaszany, co powoduje, że test zakończył się niepowodzeniem.

**Przykład**

Następujące potwierdza, że wartość bezwzględną liczby całkowitej jest dodatni:

```csharp
public void TestSomething(int i) {
     int j = Maths.Abs(i);
     PexAssert.IsTrue(j >= 0);
     ...
}
```

<a name="pexchoose"></a>
## <a name="pexchoose"></a>PexChoose

Klasa statyczna, dostarczającego pomocnicze w ramach wprowadzania wartości do testu, który może służyć do implementowania [sparametryzowane Mocks](input-generation.md#parameterized-mocks).

**PexChoose** klasy nie jest pomocne w określeniu, czy test się pomyślnie lub niepowodzeniem dla określonej wartości wejściowych. **PexChoose** po prostu zawiera wartości wejściowych, które są również nazywane *opcje*. Jest nadal użytkownika do ograniczania wartości wejściowych oraz do zapisywania potwierdzenia, które definiują, gdy test kończy się pomyślnie lub nie powiedzie się.

**Tryby operacyjne**

**PexChoose** klasy mogą działać w dwóch trybach:

* Podczas testów funkcji IntelliTest wykonuje symboliczne analizy testu i przetestowane kodu podczas [wejściowych generowania](input-generation.md), okno wyboru zwraca wartości dowolnego i funkcji IntelliTest śledzi, jak każda wartość jest używana w testu i przetestowane kodu. IntelliTest wygeneruje odpowiednie wartości, aby wyzwolić wykonywanie różnych ścieżek w testu i przetestowane kodu.

* Kod generowany dla poszczególnych przypadków testowych konfiguruje dostawcy wybór w określony sposób, aby ponowne wykonanie przypadek testowy spowoduje, że określone opcje, aby wyzwolić ścieżkę wykonania określonego.

**Użycie**

* Proste wywołanie **PexChoose.Value** aby wygenerować nową wartość:

```csharp
public int Foo() {
    return PexChoose.Value<int>("foo");
}
```

<a name="pexobserve"></a>
## <a name="pexobserve"></a>PexObserve

Klasa statyczna logowania nazwanych wartości.

Gdy program IntelliTest analizuje kod, **PexObserve** służy do rejestrowania wartości obliczanej przy użyciu ich oświadczenia sformatowany ciąg. Wartości są skojarzone z unikatowych nazw.

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

Klasa statyczna używane do ignorowania ograniczenia dotyczące parametrów i Drukuj symboliczne informacje związane z wartości.

**Użycie**

Normalnie próbuje obejmują wszystkie ścieżki wykonywania kodu podczas wykonywania testów funkcji IntelliTest. Jednak szczególnie w przypadku, gdy obliczenia warunków założeń i potwierdzenie, jego powinna nie zapoznaj się z wszystkich przypadków możliwe.

**Przykład**

W tym przykładzie przedstawiono implementację **PexAssume.Arrays.ElementsAreNotNull** metody.
W metodzie możesz zignorować ograniczenia długości wartości tablicy, aby uniknąć IntelliTest próby wygenerowania różne rozmiary tablicy. Ograniczenia są ignorowane, tylko w tym miejscu. Jeśli przetestowane kod zachowuje się inaczej dla innej tablicy długości IntelliTest nie można wygenerować różnych tablic o rozmiarze od ograniczenia przetestowane kodu.

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

## <a name="got-feedback"></a>Czy chcesz przesłać opinię?

Opublikuj swoje pomysły i funkcji żądania na [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).