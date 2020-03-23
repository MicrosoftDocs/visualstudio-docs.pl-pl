---
title: Przegląd | Narzędzie testowe Microsoft IntelliTest Developer
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Visual Studio IntelliTest developer testing tool
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: dfa81e7afe313a112e2355ddf5efadb70c555477
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591604"
---
# <a name="overview-of-microsoft-intellitest"></a>Omówienie testu IntelliTest firmy Microsoft

IntelliTest umożliwia wczesne znajdowanie błędów i zmniejsza koszty konserwacji testów. Przy użyciu podejścia do testowania zautomatyzowane i przejrzyste IntelliTest można wygenerować zestaw kandydatów testów dla kodu .NET. Generowanie zestawu testów może być dalej prowadzone przez *właściwości poprawności,* które określisz. IntelliTest będzie nawet rozwijać zestaw testów automatycznie w miarę ewolucji kodu w ramach testu.

**Testy charakterystyki** IntelliTest umożliwia określenie zachowania kodu pod względem zestawu tradycyjnych testów jednostkowych.
Taki zestaw testów może służyć jako pakiet regresji, tworząc podstawę do rozwiązania złożoności związanej z refaktoryzacji starszego lub nieznanego kodu.

**Generowanie danych wejściowych testu z przewodnikiem** IntelliTest używa otwartej analizy kodu i podejścia do rozwiązywania ograniczeń do automatycznego generowania precyzyjnych wartości wejściowych testu; zwykle bez konieczności interwencji użytkownika. W przypadku typów obiektów złożonych automatycznie generuje fabryki. Można poprowadzić generowanie danych wejściowych testowych, rozszerzając i konfigurując fabryki zgodnie z wymaganiami. Właściwości poprawności określone jako potwierdzenia w kodzie będą również automatycznie używane do dalszego generowania danych wejściowych testu.

**Integracja IDE** IntelliTest jest w pełni zintegrowany z ide programu Visual Studio. Wszystkie informacje zebrane podczas generowania zestawu testów (takie jak automatycznie generowane dane wejściowe, dane wyjściowe z kodu, wygenerowane przypadki testowe i ich stan przebiegu lub niepowodzenia) są wyświetlane w środowisku IDE programu Visual Studio. Można łatwo iterować między naprawianie kodu i ponowne uruchamianie IntelliTest, bez opuszczania środowiska IDE programu Visual Studio.
Testy mogą być zapisywane w rozwiązaniu jako projekt testu jednostkowego i zostaną automatycznie wykryte później przez Visual Studio Test Explorer.

**Uzupełnienie istniejących praktyk testowych** Użyj IntelliTest, aby uzupełnić wszelkie istniejące praktyki testowania, które mogą już być przestrzegane.

Jeśli chcesz przetestować:

* Algorytmy nad prymitywnymi danymi lub tablice danych pierwotnych:
  * zapis [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing)
* Algorytmy nad złożonymi danymi, takimi jak kompilator:
  * niech IntelliTest najpierw wygeneruje abstrakcyjną reprezentację danych, a następnie podaj go do algorytmu
  * niech IntelliTest budować wystąpień przy użyciu [niestandardowych obiektów tworzenia](input-generation.md#objects) i niezmiennie danych, a następnie wywołać algorytm
* Kontenery danych:
  * zapis [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing)
  * niech IntelliTest budować wystąpień przy użyciu [niestandardowych tworzenia obiektów](input-generation.md#objects) i niezmienne dane, a następnie wywołać metodę kontenera i ponownie sprawdzić invariants później
  * zapis [sparametryzowanych testów jednostkowych,](test-generation.md#parameterized-unit-testing) które wywołują różne metody implementacji, w zależności od wartości parametrów
* Istniejąca baza kodu:
  * korzystanie z Kreatora testów intellitestowych programu Visual Studio w celu rozpoczęcia tworzenia zestawu [sparametryzowanych testów jednostkowych (PUT)](test-generation.md#parameterized-unit-testing)

## <a name="the-hello-world-of-intellitest"></a>Przykład Witaj Świecie w funkcji IntelliTest

IntelliTest znajduje dane wejściowe istotne dla testowanego programu, co oznacza, że można go używać do generowania słynnego **Hello World!** Ciąg. Zakłada się, że utworzono projekt testowy oparty na mstestze języka C# i dodano odwołanie do **programu Microsoft.Pex.Framework.** Jeśli używasz innej struktury testów, utwórz bibliotekę klas Języka C# i zapoznaj się z dokumentacją struktury testów dotyczącą konfigurowania projektu.

Poniższy przykład tworzy dwa ograniczenia na parametr o nazwie **wartość,** tak aby IntelliTest wygeneruje wymagany ciąg:

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
2. "\0\0\0\0\0"
3. "Cześć"
4. "\0\0\0\0\0\0"
5. "Cześć\0"
6. "Cześć\0\0"
7. "Cześć\0World!"
8. "Witaj świecie!"

> [!NOTE]
> W przypadku problemów z kompilacją spróbuj zastąpić odwołania microsoft.VisualStudio.TestPlatform.TestFramework i Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions odwołaniem do microsoft.VisualStudio.QualityTools.UnitTestFramework.

Przeczytaj [Generowanie testów jednostkowych za pomocą intellitestu,](../../test/generate-unit-tests-for-your-code-with-intellitest.md) aby zrozumieć, gdzie są zapisywane wygenerowane testy. Wygenerowany kod testowy powinien zawierać test, taki jak następujący kod:

```csharp
[TestMethod]
[PexGeneratedBy(typeof(global::HelloWorldTest))]
[PexRaisedException(typeof(Exception))]
public void HelloWorldThrowsException167()
{
    this.HelloWorld("Hello World!");
}
```

To takie proste!

## <a name="limitations"></a>Ograniczenia

W tej sekcji opisano ograniczenia intellitestu:

* [Niedeterminizm](#nondeterminism)
* [Współbieżność](#concurrency)
* [Natywny kod platformy .NET](#native-code)
* [Platforma](#platform)
* [Język](#language)
* [Wnioskowanie symboliczne](#symbolic-reasoning)
* [Ślady stosu](#incorrect-stack-traces)

### <a name="nondeterminism"></a>Niedeterminizm

IntelliTest zakłada, że analizowany program jest deterministyczny. Jeśli tak nie jest, IntelliTest będzie cykl, dopóki nie osiągnie eksploracji związane.

IntelliTest uważa, że program jest nie determistic jeśli opiera się na danych wejściowych, które IntelliTest nie może kontrolować.

IntelliTest kontroluje wejścia dostarczone do [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing) i uzyskane z [PexChoose](static-helper-classes.md#pexchoose).
W tym sensie wyniki wywołań niezarządzanego lub nieinstrumentowanego kodu są również uważane za "dane wejściowe" do programu instrumentowanego, ale IntelliTest nie może ich kontrolować. Jeśli przepływ sterowania programu zależy od określonych wartości pochodzących z tych źródeł zewnętrznych, IntelliTest nie może "sterować" programem w kierunku wcześniej odkrytych obszarów.

Ponadto program jest uważany za nie determistyczny, jeśli wartości ze źródeł zewnętrznych zmieniają się podczas ponownego uruchamiania programu. W takich przypadkach IntelliTest traci kontrolę nad wykonaniem programu, a jego wyszukiwanie staje się nieefektywne.

Czasami nie jest oczywiste, kiedy to się dzieje. Weź pod uwagę następujące przykłady:

* Wynik **GetHashCode()** metoda jest dostarczana przez kod niezarządzane i nie jest przewidywalne.
* **Klasa System.Random** używa bieżącego czasu systemowego do dostarczania wartości prawdziwie losowych.
* **Klasa System.DateTime** udostępnia bieżący czas, który nie jest pod kontrolą IntelliTest.

### <a name="concurrency"></a>Współbieżność

IntelliTest nie obsługuje programów wielowątkowych.

### <a name="native-code"></a>Kod natywny

IntelliTest nie rozumie kodu macierzystego, takiego jak instrukcje x86 wywoływane za pośrednictwem **P/Invoke**. Nie wie, jak przetłumaczyć takie wywołania na ograniczenia, które mogą być przekazywane do [solvera ograniczeń](input-generation.md#constraint-solver).
Nawet dla kodu .NET, można analizować tylko kod instrumentów. IntelliTest nie może przyrządzalizować niektórych części **mscorlib,** w tym biblioteki odbić. **DynamicMethod** nie może być instrumentowany.

Sugerowane obejście jest mieć tryb testowy, w którym takie metody znajdują się w typach w zespole dynamicznym. Jednak nawet jeśli niektóre metody są niedoinstrumentowane, IntelliTest spróbuje pokryć jak najwięcej oprzyrządowanego kodu, jak to możliwe.

### <a name="platform"></a>Platforma

IntelliTest jest obsługiwany tylko na X86, 32-bitowy . Netframework.

### <a name="language"></a>Język

W zasadzie IntelliTest może analizować dowolne programy .NET, napisane w dowolnym języku .NET. Jednak w programie Visual Studio obsługuje tylko C#.

### <a name="symbolic-reasoning"></a>Wnioskowanie symboliczne

IntelliTest używa automatycznego [solvera ograniczeń](input-generation.md#constraint-solver) do określenia, które wartości są istotne dla testu i testowego programu. Jednak możliwości solvera ograniczeń są i zawsze będą ograniczone.

### <a name="incorrect-stack-traces"></a>Nieprawidłowe ślady stosu

Ponieważ IntelliTest połowy i "rethrows" wyjątki w każdej metody instrumentacji, numery wierszy w ślady stosu nie będą poprawne. Jest to ograniczenie przez projekt instrukcji "rethrow".

## <a name="further-reading"></a>Dodatkowe informacje

* [Wprowadzający wpis na blogu](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/).
* [Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
