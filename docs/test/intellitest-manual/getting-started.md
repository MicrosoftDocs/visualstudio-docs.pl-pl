---
title: Wprowadzenie do intellitestu
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Get started
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 113233c985053cfe838f385a36ec59cc211bfcb9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591661"
---
# <a name="get-started-with-microsoft-intellitest"></a>Wprowadzenie do programu Microsoft IntelliTest

* Jeśli jest to twój pierwszy raz z IntelliTest:
  * obejrzyj film na [kanale 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)
  * przeczytaj ten [przegląd na MSDN Magazine](https://msdn.microsoft.com/magazine/dn904672.aspx)
  * przeczytaj naszą [dokumentację](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
* Zadawaj pytania dotyczące [przepełnienia stosu](https://stackoverflow.com/questions/tagged/intellitest)
* Przeczytaj pozostałą część niniejszej instrukcji referencyjnej
* Wydrukuj tę stronę w celu szybkiego wykorzystania

## <a name="important-attributes"></a>Ważne atrybuty

* [PexClass](attribute-glossary.md#pexclass) oznacza typ zawierający **PUT**
* [PexMethod](attribute-glossary.md#pexmethod) oznacza **PUT**
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) oznacza parametr niezerowy

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

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) wiąże projekt testowy z projektem
* [PexInstrumentAszespół](attribute-glossary.md#pexinstrumentassemblyattribute) określa zespół do przyrządu

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="important-static-helper-classes"></a><a name="helper-classes"></a>Ważne statyczne klasy pomocników

* [PexAssume](static-helper-classes.md#pexassume) ocenia założenia (filtrowanie wejściowe)
* [PexAssert](static-helper-classes.md#pexassert) ocenia twierdzenia
* [PexChoose](static-helper-classes.md#pexchoose) generuje nowe opcje (dodatkowe wejścia)
* [PexObserve](static-helper-classes.md#pexobserve) rejestruje wartości na żywo do wygenerowanych testów

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

## <a name="got-feedback"></a>Chcesz przesłać opinię?

Opublikuj swoje pomysły i sugestie funkcji w [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
