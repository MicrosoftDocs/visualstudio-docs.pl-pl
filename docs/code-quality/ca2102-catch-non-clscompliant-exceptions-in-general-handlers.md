---
title: 'CA2102: Przechwytuj wyjątki bez atrybutu CLSCompliant w ogólnych procedurach obsługi'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f62ad97bbb96f49a7263edd29f0f8a7c263bec4c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233008"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Przechwytuj wyjątki bez atrybutu CLSCompliant w ogólnych procedurach obsługi

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Element członkowski w zestawie, który nie jest oznaczony lub jest <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> oznaczony `RuntimeCompatibility(WrapNonExceptionThrows = false)` , zawiera blok catch, który obsługuje <xref:System.Exception?displayProperty=fullName> i nie zawiera natychmiast po ogólnym bloku catch. Ta reguła ignoruje [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] zestawy.

## <a name="rule-description"></a>Opis reguły

Blok catch obsługujący <xref:System.Exception> przechwycenie wszystkich wyjątków zgodnych z Common Language Specification (CLS). Nie są jednak przechwytywane wyjątki niezgodne ze specyfikacją CLS. Wyjątki niezgodne ze specyfikacją CLS mogą być zgłaszane z kodu natywnego lub kodu zarządzanego, który został wygenerowany przez asembler języka pośredniego firmy Microsoft (MSIL). Należy zauważyć, C# że [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kompilatory i nie zezwalają na zgłaszanie wyjątków niezgodnych ze [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] specyfikacją CLS i nie przechwytuje wyjątków niezgodnych ze specyfikacją CLS. Jeśli cel bloku catch ma obsługiwać wszystkie wyjątki, należy użyć następującej składni ogólnego bloku catch.

- C#:`catch {}`

- C++: `catch(...) {}` lub`catch(Object^) {}`

Nieobsłużony wyjątek nieobsługiwany przez CLS jest problemem z zabezpieczeniami, gdy wcześniej dozwolone uprawnienia zostaną usunięte w bloku catch. Ponieważ wyjątki niezgodne ze specyfikacją CLS nie są przechwytywane, złośliwa Metoda, która zgłasza wyjątek niezgodny ze specyfikacją CLS, może działać z podniesionymi uprawnieniami.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, gdy celem jest przechwycenie wszystkich wyjątków, podstawianie lub Dodawanie ogólnego bloku catch lub oznaczanie zestawu `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Jeśli uprawnienia są usuwane w bloku catch, należy zduplikować funkcje w bloku ogólnego catch. Jeśli nie jest to cel, aby obsługiwać wszystkie wyjątki, Zastąp blok catch obsługujący <xref:System.Exception> bloki catch obsługujące określone typy wyjątków.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli blok try nie zawiera żadnych instrukcji, które mogą generować wyjątek niezgodny ze specyfikacją CLS, można bezpiecznie pominąć ostrzeżenie z tej reguły. Ponieważ każdy kod macierzysty lub zarządzany może zgłosić wyjątek niezgodny ze specyfikacją CLS, wymaga znajomości wszystkich kodów, które mogą być wykonywane we wszystkich ścieżkach kodu wewnątrz bloku try. Należy zauważyć, że wyjątki niezgodne ze specyfikacją CLS nie są zgłaszane przez środowisko uruchomieniowe języka wspólnego.

## <a name="example-1"></a>Przykład 1

W poniższym przykładzie pokazano klasę MSIL, która zgłasza wyjątek niezgodny ze specyfikacją CLS.

```cpp
.assembly ThrowNonClsCompliantException {}
.class public auto ansi beforefieldinit ThrowsExceptions
{
   .method public hidebysig static void
         ThrowNonClsException() cil managed
   {
      .maxstack  1
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()
      IL_0005:  throw
   }
}
```

## <a name="example-2"></a>Przykład 2

Poniższy przykład przedstawia metodę, która zawiera ogólny blok catch, który spełnia kryteria.

[!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]

Skompiluj poprzednie przykłady w następujący sposób.

```cpp
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Powiązane reguły

[CA1031 Nie Przechwytuj typów wyjątków ogólnych](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Zobacz także

- [Wyjątki i obsługa wyjątków](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)
- [Ilasm.exe (asembler IL)](/dotnet/framework/tools/ilasm-exe-il-assembler)
- [Niezależność od języka i składniki niezależne od języka](/dotnet/standard/language-independence-and-language-independent-components)