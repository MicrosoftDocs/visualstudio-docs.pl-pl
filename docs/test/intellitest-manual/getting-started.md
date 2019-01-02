---
title: Wprowadzenie do funkcji IntelliTest
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Get started
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 41fd7b7b32a2e81ec2a217a54a6220cbafb38668
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952919"
---
# <a name="get-started-with-microsoft-intellitest"></a>Rozpoczynanie pracy z usługą Microsoft IntelliTest

* Jeśli jest to pierwsza z funkcją IntelliTest:
  * Obejrzyj [wideo Channel 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)
  * Przeczytaj ten artykuł [omówienie magazynu MSDN Magazine](https://msdn.microsoft.com/magazine/dn904672.aspx)
  * Przeczytaj nasze [dokumentacji](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
* Zadaj pytania na [Stack Overflow](http://stackoverflow.com/questions/tagged/intellitest)
* Czytania dalszej części tego podręcznika
* Wydrukowanie tej strony jako podręczna karta informacyjna

## <a name="important-attributes"></a>Ważnych atrybutów

* [PexClass](attribute-glossary.md#pexclass) oznacza typ zawierający **PUT**
* [PexMethod](attribute-glossary.md#pexmethod) znaczniki **PUT**
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) oznacza parametrów innych niż null

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

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) projektu testowego jest powiązana z projektem
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) określa zestaw do Instrumentacji

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="helper-classes"></a> Ważne statyczne klasy pomocy

* [PexAssume](static-helper-classes.md#pexassume) ocenia założenia (filtrowanie wejściowych)
* [PexAssert](static-helper-classes.md#pexassert) ocenia potwierdzenia
* [PexChoose](static-helper-classes.md#pexchoose) generuje nowe opcje (dodatkowe dane wejściowe)
* [PexObserve](static-helper-classes.md#pexobserve) zaloguje się na żywo wartości wygenerowanych testów

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

## <a name="got-feedback"></a>Czy chcesz przesłać opinię?

Opublikuj swoje pomysły i funkcji żądania na [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
