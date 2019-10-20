---
title: Wprowadzenie do IntelliTest
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Get started
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 0d0d681c59935bbbb4591438f538d0c800cba489
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653207"
---
# <a name="get-started-with-microsoft-intellitest"></a>Wprowadzenie do programu Microsoft IntelliTeste

* Jeśli jest to po raz pierwszy z IntelliTest:
  * Obejrzyj [wideo w kanale 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)
  * Przeczytaj ten [Przegląd na platformie MSDN Magazine](https://msdn.microsoft.com/magazine/dn904672.aspx)
  * Przeczytaj naszą [dokumentację](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
* Zadawaj pytania dotyczące [Stack Overflow](http://stackoverflow.com/questions/tagged/intellitest)
* Przeczytaj resztę tego podręcznika odwołania
* Drukuj Tę stronę na potrzeby szybkiego odwoływania się

## <a name="important-attributes"></a>Ważne atrybuty

* [PexClass](attribute-glossary.md#pexclass) oznacza typ zawierający **Put**
* [PexMethod](attribute-glossary.md#pexmethod) oznacza **Umieszczanie**
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) oznacza parametr o wartości innej niż null

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

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) tworzy powiązanie projektu testowego z projektem
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) określa zestaw do instrumentu

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="helper-classes"></a>Ważne klasy pomocników statycznych

* [PexAssume](static-helper-classes.md#pexassume) oblicza założenia (filtrowanie danych wejściowych)
* [PexAssert](static-helper-classes.md#pexassert) oblicza potwierdzenia
* [PexChoose](static-helper-classes.md#pexchoose) generuje nowe wybory (dodatkowe dane wejściowe)
* [Funkcja PexObserve](static-helper-classes.md#pexobserve) rejestruje wartości na żywo w wygenerowanych testach

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

## <a name="got-feedback"></a>Masz opinię?

Publikuj swoje pomysły i żądania funkcji w [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
