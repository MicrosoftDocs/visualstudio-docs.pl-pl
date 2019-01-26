---
title: 'CA1810: Inicjuj pola statyczne typu referencyjnego śródwierszowo'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 42877ea2b3b42f0fc9bed5c88a6809ba31cab3e2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996925"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: Inicjuj pola statyczne typu referencyjnego śródwierszowo

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ odwołania deklaruje jawny, statyczny Konstruktor.

## <a name="rule-description"></a>Opis reguły
 Podczas gdy typ deklaruje jawny, statyczny konstruktor, kompilator just in time (JIT) do każdej metody statycznej dodaje sprawdzenie i konstruktora wystąpienia, aby upewnić się, że konstruktor statyczny został wcześniej wywołany. Inicjowanie statyczne są wyzwalane podczas uzyskiwania dostępu do dowolnego członka statycznego lub gdy tworzone jest wystąpienie tego typu. Jednak statyczne inicjowanie nie jest wyzwalany, jeśli zadeklarować zmienną typu, ale nie należy jej używać, które mogą być ważne, jeśli inicjowanie zmieni się stan globalny.

 Gdy wszystkie dane statyczne są wbudowane zainicjowane i jawny, statyczny Konstruktor nie jest zadeklarowana, Kompilatory języka intermediate language (MSIL) firmy Microsoft, Dodaj `beforefieldinit` flagę i niejawne Konstruktor statyczny, który inicjuje danych statycznych, typowi MSIL Definicja. Kiedy kompilator JIT napotka `beforefieldinit` Flaga w większości przypadków sprawdzenia konstruktora statycznego nie zostały dodane. Statyczne inicjowanie może wystąpić na pewien czas, zanim wszystkie pola statyczne są dostępne, ale nie, przed wywołaniem konstruktora statycznej metody lub wystąpienia. Należy pamiętać, że Inicjowanie statyczne mogą występować w dowolnej chwili po zadeklarowaniu zmiennej o typie.

 Sprawdzenia konstruktora statycznego mogą obniżyć wydajność. Często statyczny Konstruktor jest używana tylko do zainicjowania pola statyczne, w których przypadku musisz tylko upewnić się, że inicjowanie statycznych występuje przed pierwszym dostępie pole statyczne. `beforefieldinit` Zachowanie jest odpowiednia dla tych i innych typów. Jest tylko nieodpowiednie, gdy statyczne inicjowanie ma wpływ na stan globalny jest spełniony jeden z następujących czynności:

- Wpływ na stan globalny jest kosztowne, a nie jest wymagane, jeśli typ nie jest używany.

- Efekty stan globalny jest możliwy bez uzyskiwania dostępu do dowolnego pola statyczne typu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, zainicjuj wszystkie dane statyczne, gdy jest on zadeklarowany, i usuń konstruktor statyczny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest to bezpieczne pominąć ostrzeżenie od tej reguły, jeśli wydajność nie ma znaczenia; lub jeśli stan globalny zmiany, które są spowodowane przez statyczne inicjowanie są kosztowne musi można zagwarantować przed statycznej metody tego typu jest nazywany lub tworzone jest wystąpienie tego typu.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano typem `StaticConstructor`, który narusza regułę i typu `NoStaticConstructor`, który zamienia statyczny Konstruktor inicjalizacji wbudowane spełniają reguły.

[!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
[!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]

Należy pamiętać, dodanie `beforefieldinit` Flaga w definicji MSIL dla `NoStaticConstructor` klasy.

```
.class public auto ansi StaticConstructor
extends [mscorlib]System.Object
{
} // end of class StaticConstructor

.class public auto ansi beforefieldinit NoStaticConstructor
extends [mscorlib]System.Object
{
} // end of class NoStaticConstructor
```

## <a name="related-rules"></a>Powiązane reguły

- [CA2207: Typu wartości Inicjuj pola statyczne bezpośrednio](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)