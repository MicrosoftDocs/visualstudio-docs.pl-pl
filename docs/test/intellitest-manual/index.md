---
title: Omówienie | Narzędzie do testowania Microsoft IntelliTest dla deweloperów
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Visual Studio IntelliTest developer testing tool
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 5eb619269dfd8922919999249b4ced0b9b98ebb7
ms.sourcegitcommit: ee12b14f306ad8f49b77b08d3a16d9f54426e7ca
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80256208"
---
# <a name="overview-of-microsoft-intellitest"></a>Omówienie narzędzia Microsoft IntelliTest

Narzędzie IntelliTest umożliwia wczesne znajdowanie usterek i zmniejsza koszty konserwacji testów. Stosując zautomatyzowane i przejrzyste podejście do testowania, narzędzie IntelliTest może generować kandydujący pakiet testów dla kodu platformy .NET. Generowaniem zestawu testów można dokładniej sterować za pomocą *właściwości poprawności* określonych przez użytkownika. Narzędzie IntelliTest będzie nawet automatycznie rozwijać zestaw testów w miarę rozwoju testowanego kodu.

**Testy charakterystyki** Narzędzie IntelliTest umożliwia ustalanie zachowania kodu pod względem zestawu tradycyjnych testów jednostkowych.
Taki zestaw testów może służyć jako zestaw regresji, stanowiący podstawę do rozwiązywania problemów ze złożonością podczas refaktoryzacji starszego lub nieznanego kodu.

**Sterowane generowanie danych wejściowych testów** Narzędzie IntelliTest stosuje podejście oparte na otwartej analizie kodu i rozwiązywaniu ograniczeń, aby automatycznie generować precyzyjne wartości wejściowe testów, zwykle bez konieczności interwencji użytkownika. W przypadku złożonych typów obiektów automatycznie generuje ono fabryki. Można sterować generowaniem danych wejściowych testów, rozszerzając i konfigurując fabryki w celu dopasowania do własnych wymagań. Właściwości poprawności określone jako asercje w kodzie również są automatycznie używane do dokładniejszego sterowania generowaniem danych wejściowych testów.

**Integracja ze środowiskiem IDE** Narzędzie IntelliTest jest w pełni zintegrowane ze środowiskiem IDE programu Visual Studio. Wszystkie informacje zebrane podczas generowania zestawu testów (takie jak automatycznie wygenerowane dane wejściowe, dane wyjściowe z kodu, wygenerowane przypadki testowe i ich stan powodzenia lub niepowodzenia) pojawiają się w środowisku IDE programu Visual Studio. Można łatwo iterować między poprawianiem kodu i ponownym uruchamianiem narzędzia IntelliTest, bez opuszczania środowiska IDE programu Visual Studio.
Testy można zapisywać w rozwiązaniu jako projekt testów jednostkowych — zostaną one automatycznie wykryte później przez eksploratora testów programu Visual Studio.

**Uzupełnianie istniejących metod testowania** Narzędzie IntelliTest może uzupełniać istniejące metody testowania, które mogą być już stosowane.

Jeśli chcesz przetestować:

* Algorytmy dla danych pierwotnych lub tablic danych pierwotnych:
  * Napisz [sparametryzowane testy jednostkowe](test-generation.md#parameterized-unit-testing)
* Algorytmy dla danych złożonych, takie jak kompilator:
  * Za pomocą narzędzia IntelliTest wygeneruj abstrakcyjną reprezentację danych, a następnie przekaż ją do algorytmu
  * Za pomocą narzędzia IntelliTest utwórz wystąpienia przy użyciu [tworzenia obiektów niestandardowych](input-generation.md#objects) i niezmienników danych, a następnie wywołaj algorytm
* Kontenery danych:
  * Napisz [sparametryzowane testy jednostkowe](test-generation.md#parameterized-unit-testing)
  * Za pomocą narzędzia IntelliTest utwórz wystąpienia przy użyciu [tworzenia obiektów niestandardowych](input-generation.md#objects) i niezmienników danych, a następnie wywołaj metodę kontenera i sprawdź ponownie niezmienniki
  * Napisz [sparametryzowane testy jednostkowe](test-generation.md#parameterized-unit-testing), które będą wywoływać różne metody implementacji, zależnie od wartości parametrów
* Istniejąca baza kodu:
  * Użyj kreatora narzędzia IntelliTest w programie Visual Studio, aby rozpocząć, generując zestaw [sparametryzowanych testów jednostkowych (PUT, parameterized unit test)](test-generation.md#parameterized-unit-testing)

## <a name="the-hello-world-of-intellitest"></a>Przykład Hello world w narzędziu IntelliTest

Narzędzie IntelliTest znajduje dane wejściowe istotne dla testowanego programu, co oznacza, że można go użyć do wygenerowania znanego ciągu **Hello world!** . Przyjęto tu założenie, że został utworzony projekt testowy w języku C# oparty na narzędziu MSTest oraz zostało dodane odwołanie do struktury **Microsoft.Pex.Framework**. Jeśli używasz innej struktury testów, utwórz bibliotekę klas języka C# i zapoznaj się z dokumentacją struktury testów dotyczącą konfigurowania projektu.

Poniższy przykład tworzy dwa ograniczenia dotyczące parametru o nazwie **value**, tak aby narzędzie IntelliTest wygenerowało wymagany ciąg:

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

Po skompilowaniu i uruchomieniu narzędzie IntelliTest wygeneruje zestaw testów, taki jak następujący zestaw:

1. ""
2. "\0\0\0\0\0"
3. "Hello"
4. "\0\0\0\0\0\0"
5. "Hello\0"
6. "Hello\0\0"
7. "Hello\0World!"
8. "Hello World!"

> [!NOTE]
> W przypadku problemów z kompilacją spróbuj zamienić odwołania Microsoft.VisualStudio.TestPlatform.TestFramework i Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions na odwołanie Microsoft.VisualStudio.QualityTools.UnitTestFramework.

Przeczytaj temat [Generowanie testów jednostkowych za pomocą narzędzia IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md), aby dowiedzieć się, gdzie są zapisywane wygenerowane testy. Wygenerowany kod testu powinien zawierać test taki jak w następującym kodzie:

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

Dodatkowe zasoby:
  * Obejrzyj [klip wideo w witrynie Channel 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)
  * Przeczytaj to [omówienie w magazynie MSDN Magazine](https://msdn.microsoft.com/magazine/dn904672.aspx)

## <a name="important-attributes"></a>Ważne atrybuty

* [PexClass](attribute-glossary.md#pexclass) — oznacza typ zawierający test **PUT**
* [PexMethod](attribute-glossary.md#pexmethod) — oznacza test **PUT**
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) — oznacza parametr o wartości innej niż null

```csharp
using Microsoft.Pex.Framework;

[..., PexClass(typeof(Foo))]
public partial class FooTest {
    [PexMethod]
    public void Bar([PexAssumeNotNull]Foo target, int i) {
        target.Bar(i);
    }
}
```

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) — wiąże projekt testowy z danym projektem
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) — określa zestaw do instrumentacji

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="important-static-helper-classes"></a><a name="helper-classes"></a> Ważne statyczne klasy pomocnicze

* [PexAssume](static-helper-classes.md#pexassume) — ocenia założenia (filtrowanie danych wejściowych)
* [PexAssert](static-helper-classes.md#pexassert) — ocenia asercje
* [PexChoose](static-helper-classes.md#pexchoose) — generuje nowe opcje (dodatkowe dane wejściowe)
* [PexObserve](static-helper-classes.md#pexobserve) — rejestruje wartości na żywo w generowanych testach

```csharp
[PexMethod]
void StaticHelpers(Foo target) {
    PexAssume.IsNotNull(target);

    int i = PexChoose.Value<int>("i");
    string result = target.Bar(i);

    PexObserve.ValueForViewing<string>("result", result);
    PexAssert.IsNotNull(result);
}
```

## <a name="limitations"></a>Ograniczenia

W tej sekcji opisano ograniczenia narzędzia IntelliTest:

* [Niedeterminizm](#nondeterminism)
* [Współbieżność](#concurrency)
* [Natywny kod platformy .NET](#native-code)
* [Platforma](#platform)
* [Język](#language)
* [Wnioskowanie symboliczne](#symbolic-reasoning)
* [Ślady stosu](#incorrect-stack-traces)

### <a name="nondeterminism"></a>Niedeterminizm

Narzędzie IntelliTest zakłada, że analizowany program jest deterministyczny. W przeciwnym razie narzędzie IntelliTest będzie działać w cyklu, aż osiągnie granicę eksploracji.

Narzędzie IntelliTest uznaje program za niedeterministyczny, jeśli bazuje on na danych wejściowych, którymi narzędzie IntelliTest nie może sterować.

Narzędzie IntelliTest steruje danymi wejściowymi dostarczanymi dla [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing) i uzyskanymi z elementu [PexChoose](static-helper-classes.md#pexchoose).
W tym sensie wyniki wywołań niezarządzanego lub nieinstrumentowanego kodu również są uznawane za „dane wejściowe” dla instrumentowanego programu, ale narzędzie IntelliTest nie może nimi sterować. Jeśli przepływ sterowania programu zależy od określonych wartości pochodzących z tych źródeł zewnętrznych, narzędzie IntelliTest nie może „kierować” programu w stronę poprzednio niepokrytych obszarów.

Ponadto program jest uznawany za niedeterministyczny, jeśli wartości ze źródeł zewnętrznych zmieniają się przy ponownym uruchamianiu programu. W takich przypadkach narzędzie IntelliTest traci kontrolę nad wykonywaniem programu i jego wyszukiwanie staje się nieefektywne.

Czasami nie jest oczywiste, kiedy tak się dzieje. Rozważmy następujące przykłady:

* Wynik metody **GetHashCode()** jest dostarczany przez kod niezarządzany i jest nieprzewidywalny.
* Klasa **System.Random** używa bieżącego czasu systemowego do dostarczania rzeczywiście losowych wartości.
* Klasa **System.DateTime** udostępnia bieżący czas, który nie jest pod kontrolą narzędzia IntelliTest.

### <a name="concurrency"></a>Współbieżność

Narzędzie IntelliTest nie obsługuje programów wielowątkowych.

### <a name="native-code"></a>Kod natywny

Narzędzie IntelliTest nie może analizować kodu natywnego, takiego jak instrukcje x86 wywoływane za pomocą funkcji **P/Invoke**. Nie wie ono, jak przekształcić takie wywołania w ograniczenia, które można przekazać do [modułu rozwiązywania ograniczeń](input-generation.md#constraint-solver).
Nawet w przypadku kodu .NET może ono analizować tylko kod, który instrumentuje. Narzędzie IntelliTest nie może instrumentować niektórych części biblioteki **mscorlib**, w tym biblioteki odbić. Nie można instrumentować elementu **DynamicMethod**.

Sugerowane obejście polega na użyciu trybu testów, w którym takie metody znajdują się w typach w zestawie dynamicznym. Jednak nawet jeśli niektóre metody są nieinstrumentowane, narzędzie IntelliTest spróbuje pokryć jak największą ilość instrumentowanego kodu.

### <a name="platform"></a>Platforma

Narzędzie IntelliTest jest obsługiwane tylko na 32-bitowej platformie .NET Framework w architekturze x86.

### <a name="language"></a>Język

W zasadzie narzędzie IntelliTest może analizować dowolne programy .NET, napisane w dowolnym języku tej platformy. Jednak w programie Visual Studio obsługuje ono tylko język C#.

### <a name="symbolic-reasoning"></a>Wnioskowanie symboliczne

Narzędzie IntelliTest używa automatycznego [modułu rozwiązywania ograniczeń](input-generation.md#constraint-solver), aby określać, które wartości są istotne dla testu i testowanego programu. Jednak możliwości modułu rozwiązywania ograniczeń są (i zawsze będą) ograniczone.

### <a name="incorrect-stack-traces"></a>Nieprawidłowe ślady stosu

Narzędzie IntelliTest przechwytuje i zgłasza ponownie wyjątki w każdej instrumentowanej metodzie, więc numery wierszy w śladach stosu nie będą poprawne. Jest to ograniczenie zgodne z projektem instrukcji „rethrow”.

## <a name="further-reading"></a>Dodatkowe informacje

* [Wprowadzający wpis w blogu](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/).
* [Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
