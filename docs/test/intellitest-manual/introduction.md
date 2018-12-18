---
title: Omówienie | Narzędzie Test Microsoft IntelliTest dla deweloperów
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Visual Studio IntelliTest developer testing tool
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: c2a8e6df93d3af64bd114e0e9994aadce58e7f8d
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296024"
---
# <a name="overview-of-microsoft-intellitest"></a>Omówienie programu Microsoft IntelliTest

IntelliTest pozwala na wczesne znajdowanie usterek i zmniejsza koszty utrzymania testu. Za pomocą automatycznych i przejrzyste podejście testowania, funkcji IntelliTest mogą generować Release candidate zestawu testów dla kodu platformy .NET. Generowanie zestawu testów można dodatkowo kierować się *poprawności właściwości* określisz. Funkcja IntelliTest nawet ewoluuje wraz z zestawu testów automatycznie zgodnie z ewolucją kodu w ramach testu.

**Charakterystyka testy** IntelliTest pozwalają na określenie zachowania kodu pod względem zestawu testów jednostkowych tradycyjnych.
Zestaw testów może służyć jako zestaw regresji na podstawie na co dzień do czynienia złożoności skojarzony refaktoryzacji starszej wersji lub nieznanego kodu.

**Test z przewodnikiem wejściowych generowania** IntelliTest korzysta z analizy kodu open i ograniczenie rozwiązywania podejście do automatycznego generowania wartości wejściowe dokładne testu; zazwyczaj bez konieczności żadnej interwencji użytkownika. Dla złożonych typów obiektów automatycznie generuje fabryk. Generowanie danych wejściowych testu mogą ukierunkować, rozszerzanie i konfigurując fabryk ze swoimi potrzebami. Właściwości poprawności wskazane potwierdzenia w kodzie zostaną również automatycznie przeprowadzenie dalszej wejściowych generowania testu.

**Integracja z IDE** funkcji IntelliTest jest w pełni zintegrowana w środowisku IDE programu Visual Studio. Wszystkie informacje zebrane w trakcie Generowanie zestawu testów (takie jak automatycznie generowanych danych wejściowych, dane wyjściowe z kodu, wygenerowany przypadki testowe i ich przebiegu lub niepowodzenie stanu) pojawia się w obrębie środowiska IDE programu Visual Studio. Łatwo można wykonać iterację między naprawianie kodu i ponowne uruchamianie programu IntelliTest, bez opuszczania środowiska IDE programu Visual Studio.
Testy można zapisywać do rozwiązania jako projekt testu jednostkowego i zostanie wykryty automatycznie później przez Visual Studio Test Explorer.

**Uzupełniać istniejące rozwiązania w zakresie testowania** IntelliTest użycia jako uzupełnienie istniejących testowania rozwiązań, może już wykonaj.

Jeśli chcesz przetestować:

* Algorytmy za pośrednictwem danych pierwotnych lub tablic danych pierwotnych:
  * zapis [parametryzowane testy jednostki](test-generation.md#parameterized-unit-testing)
* Algorytmy za pośrednictwem złożonych danych, takie jak kompilator:
  * Pozwól IntelliTest najpierw wygenerować abstrakcyjną reprezentację danych, a następnie przesłać do algorytmu
  * umożliwiają tworzenie wystąpień przy użyciu funkcji IntelliTest [utworzenie niestandardowego obiektu](input-generation.md#objects) i invariants danych, a następnie wywołaj algorytm
* Kontenery danych:
  * zapis [parametryzowane testy jednostki](test-generation.md#parameterized-unit-testing)
  * umożliwiają tworzenie wystąpień przy użyciu funkcji IntelliTest [utworzenie niestandardowego obiektu](input-generation.md#objects) i invariants danych, a następnie wywołać metodę kontenera i później ponownie sprawdzić invariants
  * zapis [parametryzowane testy jednostki](test-generation.md#parameterized-unit-testing) wywołujące różne metody wdrażania, w zależności od wartości parametrów
* Istniejącej bazy kodu:
  * Rozpoczynanie pracy przez Generowanie zestawu przy użyciu programu Visual Studio Kreatora programu IntelliTest [parametryzowane testy jednostki (umieszcza)](test-generation.md#parameterized-unit-testing)

## <a name="the-hello-world-of-intellitest"></a>Hello World programu IntelliTest

IntelliTest wyszukuje dane wejściowe dotyczą program przetestowane, co oznacza, że służy do generowania sławę **Witaj, świecie!** ciąg. założono, że utworzono C# projekt testów MSTest i dodać odwołanie do **Microsoft.Pex.Framework**. Jeśli używasz framework innego testu, Utwórz C# Biblioteka klas i zapoznaj się z dokumentacją framework testu, w jaki sposób skonfigurować konfigurację projektu.

Poniższy przykład tworzy dwa ograniczenia dla parametru o nazwie **wartość** tak, aby program IntelliTest zostanie wygenerowany wymagane parametry:

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

Gdy skompilowany i wykonany, IntelliTest generuje zestaw testów, takie jak następujące:

1. ""
2. "\0\0\0\0\0"
3. "Hello"
4. "\0\0\0\0\0\0"
5. "Hello\0"
6. "Hello\0\0"
7. "Hello\0World!"
8. "Hello World!"

Odczyt [generowania testów jednostkowych z funkcją Intellitest](../../test/generate-unit-tests-for-your-code-with-intellitest.md) Aby zrozumieć, w którym wygenerowane testy są zapisywane. Kod wygenerowany test powinien zawierać testów, jak w następującym kodzie:

```csharp
[TestMethod]
[PexGeneratedBy(typeof(global::HelloWorldTest))]
[PexRaisedException(typeof(Exception))]
public void HelloWorldThrowsException167()
{
    this.HelloWorld("Hello World!");
}
```

Jest tak proste!

## <a name="limitations"></a>Ograniczenia

W tej sekcji opisano ograniczenia dotyczące funkcji IntelliTest:

* [Nondeterminism](#nondeterminism)
* [Współbieżność](#concurrency)
* [Natywnego kodu platformy .NET](#native-code)
* [Platforma](#platform)
* [Język](#language)
* [Symbolicznych](#symbolic-reasoning)
* [Ślady stosu](#incorrect-stack-traces)

### <a name="nondeterminism"></a>Nondeterminism

IntelliTest założeniu, że program przeanalizowany deterministyczne. Jeśli nie jest, program IntelliTest zostanie cyklu aż do napotkania Eksplorowanie powiązany.

IntelliTest uwzględnia program do innych determistic, jeśli opiera się na danych wejściowych, które program IntelliTest nie można kontrolować.

IntelliTest kontrolki danych wejściowych do [parametryzowane testy jednostki](test-generation.md#parameterized-unit-testing) oraz otrzymane od [PexChoose](static-helper-classes.md#pexchoose).
W tym sensie wyników wywołań do kodu niezarządzanego lub niezinstrumentowanej również będą traktowane jako "dane wejściowe" do instrumentowanego programu, ale IntelliTest nie może kontrolować je. Jeśli przepływ sterowania programu zależy od konkretnych wartości pochodzące z tych źródeł zewnętrznych, IntelliTest nie "kierowania" program kierunku wcześniej niepokryty obszarów.

Ponadto program uważany jest za determistic inne niż w przypadku zmiany wartości ze źródeł zewnętrznych, gdy ponowne uruchomienie programu. W takich przypadkach program IntelliTest utraci kontrolę nad wykonywania programu, a wyszukiwanie staje się nieefektywne.

Czasami nie jest oczywisty w takiej sytuacji.
Należy wziąć pod uwagę następujące przykłady:

* Wynik **element GetHashCode()** metody są dostarczane przez kod niezarządzany, a nie jest przewidywalne.
* **System.Random** klasy korzysta bieżący czas systemowy, aby zapewnić naprawdę losowe wartości.
* **System.DateTime** klasy zawiera bieżący czas, który nie jest pod kontrolą programu IntelliTest.

### <a name="concurrency"></a>Współbieżność

Funkcja IntelliTest nie obsługuje programów wielowątkowych.

### <a name="native-code"></a>Kod natywny

Funkcja IntelliTest nie rozpoznaje kodu natywnego, takich jak x86 instrukcje wywoływanym za pośrednictwem **P/Invoke**. Nie wie jak przekształcać takie wywołania do ograniczenia, które mogą być przekazywane do [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver).
Nawet w przypadku kodu platformy .NET go tylko analizować kod, który umożliwia ona Instrumentację. IntelliTest nie mogą instrumentować niektórych części **mscorlib**, łącznie z biblioteki odbicia. **Elementu DynamicMethod** nie można go zinstrumentować.

Sugerowane rozwiązanie jest tryb testowy lokalizacji tych metod w typach w zestawie dynamicznym. Jednak nawet jeśli niektóre metody niezinstrumentowanej, IntelliTest podejmie próbę obejmują tyle instrumentowanych kodu, jak to możliwe.

### <a name="platform"></a>Platforma

Funkcja IntelliTest jest obsługiwane tylko na X86, 32-bitowych. NETframework.

### <a name="language"></a>Język

W zasadzie IntelliTest można analizować dowolnego programy platformy .NET, napisane w dowolnym języku .NET. Jednak w programie Visual Studio obsługuje tylko C#.

### <a name="symbolic-reasoning"></a>Symbolicznych

Automatyczne korzysta z funkcji IntelliTest [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver) do określenia wartości, które są istotne dla testu i program w ramach testu. Jednak możliwości moduł rozwiązywania ograniczeń są i zawsze będzie, ograniczone.

### <a name="incorrect-stack-traces"></a>Ślady stosu niepoprawne

Ponieważ program IntelliTest przechwytuje i "ponownie zgłasza" wyjątków w każdej metodzie instrumentowanych numery wierszy w śladach stosu nie będą poprawne. Jest to ograniczenie zgodnie z projektem w instrukcji "Zgłoś ponownie".

## <a name="further-reading"></a>Dalsze informacje

* [Wpis w blogu wprowadzające](https://blogs.msdn.microsoft.com/devops/2014/11/19/introducing-smart-unit-tests/).
* [Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
