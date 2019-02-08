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
ms.openlocfilehash: 2f361720f45a24e561ab2a886537bda02c73c006
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55923711"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Przechwytuj wyjątki bez atrybutu CLSCompliant w ogólnych procedurach obsługi

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Element członkowski w zestawie, który nie jest oznaczony atrybutem <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> lub jest oznaczony jako `RuntimeCompatibility(WrapNonExceptionThrows = false)` zawiera blok catch obsługujący <xref:System.Exception?displayProperty=fullName> i nie zawiera bezpośrednio następującego ogólnego bloku catch. Ta zasada powoduje ignorowanie [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] zestawów.

## <a name="rule-description"></a>Opis reguły

W bloku catch, który obsługuje <xref:System.Exception> przechwytuje wszystkie wyjątki zgodne Common Language Specification (CLS). Jednak nie przechwytuje wyjątków zgodne ze specyfikacją CLS. Niezgodny ze specyfikacją CLS zgodne wyjątki mogą zostać wygenerowane, z kodu macierzystego lub kodu zarządzanego, który został wygenerowany przez firmę Microsoft pośredniego (MSIL) języka asemblera. Należy zauważyć, że języka C# i [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kompilatory nie zezwalają na niezgodnych ze specyfikacją CLS zgodnych wyjątki zostanie wygenerowany i [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nie przechwytuje wyjątków zgodne ze specyfikacją CLS. Jeśli celem blok catch ma obsługiwać wszystkie wyjątki, należy użyć następującej składni bloku catch ogólne.

- C#: `catch {}`

- C++: `catch(...) {}` lub `catch(Object^) {}`

Wyjątek nieobsługiwany niezgodnych ze specyfikacją CLS staje się problem z zabezpieczeniami, usunięcie wcześniej dozwolone uprawnienia w bloku catch. Ponieważ wyjątki zgodne ze specyfikacją CLS nie są wychwytywane, złośliwy metodę, która zgłasza wyjątek niezgodny ze specyfikacją można uruchomić z podwyższonym poziomem uprawnień.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, gdy celem jest przechwytywać wszystkie wyjątki, Zastąp lub Dodaj ogólnego bloku catch lub oznaczyć zestaw `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Jeśli uprawnienia zostaną usunięte w bloku catch, zduplikowane funkcji w ogólne blok catch. Jeśli nie jest celem do obsługi wszystkich wyjątków, Zastąp blok catch, który obsługuje <xref:System.Exception> przy użyciu bloków catch, które obsługują typy określonego wyjątku.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli blok try nie zawiera żadnych instrukcji, które mogą generować wyjątek zgodne ze specyfikacją CLS. Ponieważ każdy kod macierzysty lub zarządzany może zgłosić wyjątek niezgodny ze specyfikacją, wymaga znajomości cały kod, który może być wykonywana w wszystkie ścieżki kodu wewnątrz bloku try. Zauważ, że wyjątki zgodne ze specyfikacją CLS nie zostaną zgłoszone przez środowisko uruchomieniowe języka wspólnego.

## <a name="example-1"></a>Przykład 1

Poniższy przykład przedstawia klasę MSIL, które zgłasza wyjątek zgodne ze specyfikacją CLS.

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

Poniższy przykład przedstawia metodę, która zawiera blok catch ogólnego, który spełnia reguły.

[!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]

Skompiluj następujący poprzednich przykładach.

```cpp
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Powiązane reguły

[CA1031: Nie przechwytuj wyjątków typów ogólnych](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Zobacz także

- [Wyjątki i obsługa wyjątków](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)
- [Ilasm.exe (asembler IL)](/dotnet/framework/tools/ilasm-exe-il-assembler)
- [Niezależność od języka i składniki niezależne od języka](/dotnet/standard/language-independence-and-language-independent-components)