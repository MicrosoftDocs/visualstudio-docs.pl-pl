---
title: 'CA2102: Przechwyć wyjątki inne niż CLSCompliant w ogólnych programach obsługi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e2335b6d2bc3a5e99f0e6de1afefac4f42de0501
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521306"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Przechwytuj wyjątki bez atrybutu CLSCompliant w ogólnych procedurach obsługi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Element członkowski w zestawie, który nie jest oznaczony <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> lub jest oznaczony, `RuntimeCompatibility(WrapNonExceptionThrows = false)` zawiera blok catch, który obsługuje <xref:System.Exception?displayProperty=fullName> i nie zawiera natychmiast po ogólnym bloku catch. Ta reguła ignoruje [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] zestawy.

## <a name="rule-description"></a>Opis reguły
 Blok catch obsługujący <xref:System.Exception> przechwycenie wszystkich wyjątków zgodnych z Common Language Specification (CLS). Nie są jednak przechwytywane wyjątki niezgodne ze specyfikacją CLS. Wyjątki niezgodne ze specyfikacją CLS mogą być zgłaszane z kodu natywnego lub kodu zarządzanego, który został wygenerowany przez asembler języka pośredniego firmy Microsoft (MSIL). Należy zauważyć, że język C# i [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kompilatory nie zezwalają na zgłaszanie wyjątków niezgodnych ze specyfikacją CLS i nie [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] przechwytuje wyjątków niezgodnych ze specyfikacją CLS. Jeśli cel bloku catch ma obsługiwać wszystkie wyjątki, należy użyć następującej składni ogólnego bloku catch.

- Znajd`catch {}`

- C++: `catch(...) {}` lub`catch(Object^) {}`

  Nieobsłużony wyjątek nieobsługiwany przez CLS jest problemem z zabezpieczeniami, gdy wcześniej dozwolone uprawnienia zostaną usunięte w bloku catch. Ponieważ wyjątki niezgodne ze specyfikacją CLS nie są przechwytywane, złośliwa Metoda, która zgłasza wyjątek niezgodny ze specyfikacją CLS, może działać z podniesionymi uprawnieniami.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, gdy celem jest przechwycenie wszystkich wyjątków, podstawianie lub Dodawanie ogólnego bloku catch lub oznaczanie zestawu `RuntimeCompatibility(WrapNonExceptionThrows = true)` . Jeśli uprawnienia są usuwane w bloku catch, należy zduplikować funkcje w bloku ogólnego catch. Jeśli nie jest to cel, aby obsługiwać wszystkie wyjątki, Zastąp blok catch obsługujący <xref:System.Exception> bloki catch obsługujące określone typy wyjątków.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli blok try nie zawiera żadnych instrukcji, które mogą generować wyjątek niezgodny ze specyfikacją CLS, można bezpiecznie pominąć ostrzeżenie z tej reguły. Ponieważ każdy kod macierzysty lub zarządzany może zgłosić wyjątek niezgodny ze specyfikacją CLS, wymaga znajomości wszystkich kodów, które mogą być wykonywane we wszystkich ścieżkach kodu wewnątrz bloku try. Należy zauważyć, że wyjątki niezgodne ze specyfikacją CLS nie są zgłaszane przez środowisko uruchomieniowe języka wspólnego.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano klasę MSIL, która zgłasza wyjątek niezgodny ze specyfikacją CLS.

```
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

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę, która zawiera ogólny blok catch, który spełnia kryteria.

 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.CatchNonClsCompliantException/cs/FxCop.Security.CatchNonClsCompliantException.cs#1)]

 Skompiluj poprzednie przykłady w następujący sposób.

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Powiązane reguły
 [CA1031: Nie przechwytuj typów wyjątków ogólnych](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Zobacz też
 [Wyjątki i obsługa wyjątków](https://msdn.microsoft.com/library/0001887f-4fa2-47e2-8034-2819477e2344) [Ilasm.exe (Asembler IL)](https://msdn.microsoft.com/library/4ca3a4f0-4400-47ce-8936-8e219961c76f) [przesłaniają](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [niezależność języka kontroli zabezpieczeń i składniki niezależne od języka](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
