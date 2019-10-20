---
title: Przegląd | Narzędzie testowe dla deweloperów Microsoft IntelliTest
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Visual Studio IntelliTest developer testing tool
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 94bd67ecb4646e3b8079d2d1aadda097c655af4c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653172"
---
# <a name="overview-of-microsoft-intellitest"></a>Omówienie programu Microsoft IntelliTest

IntelliTest umożliwia szybkie znajdowanie usterek i zmniejsza koszty konserwacji testów. Korzystając z zautomatyzowanego i przejrzystego podejścia do testowania, IntelliTest może generować pakiet kandydujący testów dla kodu platformy .NET. Generowanie zestawu testów może być dokładniejsze zgodnie z określonymi *właściwościami poprawnego* działania. IntelliTest będzie nawet automatycznie rozwijać zestaw testów w miarę rozwoju testowanego kodu.

**Testy scharakteryzowania** IntelliTest umożliwia określenie zachowania kodu pod względem zestawu tradycyjnych testów jednostkowych.
Taki zestaw testów może służyć jako pakiet regresji, który stanowi podstawę do zapoznania się z złożonością skojarzoną z refaktoryzacją starszego lub nieznanego kodu.

**Generowanie danych wejściowych testów z przewodnikiem** IntelliTest używa metody analizy kodu i rozwiązywania problemów, aby automatycznie generować precyzyjne wartości wejściowe testów; zwykle bez potrzeby interwencji użytkownika. W przypadku złożonych typów obiektów automatyczne generowanie fabryk. Możesz wykonać testową generację danych wejściowych, rozszerzając i konfigurując fabryki zgodnie z wymaganiami. Właściwości poprawności określone jako potwierdzenia w kodzie również będą używane automatycznie do dalszej analizy generowania danych wejściowych.

**Integracja IDE** IntelliTest jest w pełni zintegrowany ze środowiskiem IDE programu Visual Studio. Wszystkie informacje zebrane podczas generowania zestawu testów (takie jak automatycznie generowane dane wejściowe, dane wyjściowe z kodu, wygenerowane przypadki testowe i ich stan powodzenia lub niepowodzenia) pojawiają się w środowisku IDE programu Visual Studio. Możesz łatwo wykonać iterację między naprawianiem kodu i ponownym uruchomieniu IntelliTest, bez opuszczania środowiska IDE programu Visual Studio.
Testy można zapisać w rozwiązaniu jako projekt testu jednostkowego i zostaną one automatycznie wykryte później przez program Visual Studio Test Explorer.

**Uzupełnienie istniejących metod testowania** Użyj IntelliTest, aby uzupełnić istniejące metody testowania, które mogą już wystąpić.

Jeśli chcesz przetestować:

* Algorytmy dla danych pierwotnych lub tablice danych pierwotnych:
  * Napisz [sparametryzowane testy jednostkowe](test-generation.md#parameterized-unit-testing)
* Algorytmy w porównaniu z danymi złożonymi, takimi jak kompilator:
  * Niech IntelliTest najpierw wygenerował abstrakcyjną reprezentację danych, a następnie przekaże ją do algorytmu
  * Pozwól IntelliTest kompilację wystąpień przy użyciu [niestandardowych obiektów tworzenia obiektu](input-generation.md#objects) i nieodmian danych, a następnie Wywołaj algorytm
* Kontenery danych:
  * Napisz [sparametryzowane testy jednostkowe](test-generation.md#parameterized-unit-testing)
  * Pozwól IntelliTest kompilację wystąpień przy użyciu [niestandardowych obiektów tworzenia obiektu](input-generation.md#objects) i nieodmian danych, a następnie Wywołaj metodę kontenera i ponownie sprawdź, czy nie usunięto wariantów
  * Napisz [sparametryzowane testy jednostkowe](test-generation.md#parameterized-unit-testing) , które wywołują różne metody implementacji, w zależności od wartości parametrów
* Istniejąca baza kodu:
  * Użyj Kreatora IntelliTest programu Visual Studio, aby rozpocząć od wygenerowania zestawu [sparametryzowanych testów jednostkowych (umieszczania)](test-generation.md#parameterized-unit-testing)

## <a name="the-hello-world-of-intellitest"></a>Hello world IntelliTest

IntelliTest znajduje dane wejściowe dotyczące przetestowanego programu, co oznacza, że można go użyć do wygenerowania sławę **Hello World!** parametry. przyjęto założenie, że utworzono C# projekt testu oparty na MSTest i dodano odwołanie do **Microsoft. Pex. Framework**. Jeśli używasz innego środowiska testowego, Utwórz bibliotekę C# klas i zapoznaj się z dokumentacją platformy testowej dotyczącą sposobu konfigurowania projektu.

Poniższy przykład tworzy dwa ograniczenia dla parametru o nazwie **Value** , tak aby IntelliTest wygenerował wymagany ciąg:

```csharp
using System;
using Microsoft.Pex.Framework;
using Microsoft.VisualStudio.TestTools.UnitTesting;

[TestClass]
public partial class HelloWorldTest {
    [PexMethod]
    public void HelloWorld([PexAssumeNotNull]string value) {
        if (value.StartsWith("Hello")
            && value.EndsWith("World!")
            && value.Contains(" "))
            throw new Exception("found it!");
    }
}
```

Po skompilowaniu i wykonaniu IntelliTest generuje zestaw testów, takich jak następujący zestaw:

1. ""
2. "\ 0 \ 0 \ 0 \ 0 \ 0"
3. Hello
4. "\ 0 \ 0 \ 0 \ 0 \ 0 \ 0"
5. "Hello\0"
6. "Hello\0\0"
7. "Hello\0World!"
8. "Hello world!"

Odczytaj [Wygeneruj testy jednostkowe za pomocą IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md) , aby zrozumieć, gdzie są zapisywane wygenerowane testy. Wygenerowany kod testu powinien zawierać test, taki jak następujący kod:

```csharp
[TestMethod]
[PexGeneratedBy(typeof(global::HelloWorldTest))]
[PexRaisedException(typeof(Exception))]
public void HelloWorldThrowsException167()
{
    this.HelloWorld("Hello World!");
}
```

To bardzo proste!

## <a name="limitations"></a>Ograniczenia

W tej sekcji opisano ograniczenia IntelliTest:

* [Nieustalenia](#nondeterminism)
* [Współbieżność](#concurrency)
* [Natywny kod platformy .NET](#native-code)
* [Platformach](#platform)
* [Język](#language)
* [Powód symboliczny](#symbolic-reasoning)
* [Ślady stosu](#incorrect-stack-traces)

### <a name="nondeterminism"></a>Nieustalenia

IntelliTest zakłada, że przeanalizowany program jest deterministyczny. Jeśli tak nie jest, IntelliTest rozpocznie się do momentu osiągnięcia powiązanej eksploracji.

IntelliTest uważa, że program nie jest determistic, jeśli opiera się na danych wejściowych, których IntelliTest nie może sterować.

IntelliTest kontroluje dane wejściowe do [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing) i uzyskanych z [PexChoose](static-helper-classes.md#pexchoose).
W tym sensie wyniki wywołań do kodu niezarządzanego lub nienależącego do instrumentu są również uznawane za "dane wejściowe" do programu instrumentacji, ale IntelliTest nie może sterować nimi. Jeśli przepływ sterowania programu zależy od określonych wartości pochodzących z tych zewnętrznych źródeł, IntelliTest nie może "sterować" programem do wcześniej niekrytych obszarów.

Ponadto program jest traktowany jako niedetermistic, jeśli wartości ze źródeł zewnętrznych zmienią się podczas ponownego uruchamiania programu. W takich przypadkach IntelliTest traci kontrolę nad wykonywaniem programu, a jego wyszukiwanie jest niewydajne.

Czasami nie jest to oczywiste, gdy tak się dzieje. Rozważ następujące przykłady:

* Wynik metody **GetHashCode ()** jest dostarczany przez kod niezarządzany i nie jest przewidywalny.
* Klasa **System. Random** używa bieżącego czasu systemowego do dostarczania rzeczywiście losowo wartości.
* Klasa **System. DateTime** zapewnia bieżącą godzinę, która nie jest pod kontrolą IntelliTest.

### <a name="concurrency"></a>Współbieżność

IntelliTest nie obsługuje programów wielowątkowych.

### <a name="native-code"></a>Kod natywny

IntelliTest nie rozpoznaje kodu natywnego, takiego jak instrukcje x86 wywoływane przez **P/Invoke**. Nie wiadomo, jak przetłumaczyć takie wywołania na ograniczenia, które mogą być przesyłane do [ograniczenia](input-generation.md#constraint-solver).
Nawet w przypadku kodu .NET można analizować tylko kod IT. IntelliTest nie może instrumentować niektórych części **mscorlib**, w tym biblioteki odbicia. Nie można instrumentować **elementu DynamicMethod** .

Sugerowane obejście ma na celu zastosowanie trybu testowego, w którym takie metody znajdują się w typach w zestawie dynamicznym. Jednak nawet jeśli niektóre metody są odkryte, IntelliTest podejmie próbę pozyskania możliwie największej ilości kodu Instrumentacji.

### <a name="platform"></a>Platforma

IntelliTest jest obsługiwany tylko w architekturze x86, 32-bitowej. NETframework.

### <a name="language"></a>Język

W zasadzie IntelliTest może analizować dowolne programy .NET, które są zapisywane w dowolnym języku .NET. Jednak w programie Visual Studio obsługuje tylko C#.

### <a name="symbolic-reasoning"></a>Powód symboliczny

IntelliTest używa funkcji automatycznego [ograniczenia](input-generation.md#constraint-solver) , aby określić, które wartości są istotne dla testu i testowanego programu. Jednak możliwości funkcji ograniczenia są inne, a zawsze będą ograniczone.

### <a name="incorrect-stack-traces"></a>Nieprawidłowe ślady stosu

Ponieważ IntelliTest przechwytuje i "rethrows" w każdej metodzie instrumentacji, numery wierszy w śladach stosu nie będą poprawne. Jest to ograniczenie według projektu instrukcji "Rethrow".

## <a name="further-reading"></a>Dalsze odczytywanie

* [Wprowadza wpis w blogu](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/).
* [Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
