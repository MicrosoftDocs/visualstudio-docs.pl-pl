---
title: 'CA1810: Inicjuj pola statyczne typu referencyjnego śródwierszowo'
ms.date: 11/04/2016
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
ms.openlocfilehash: 8838de46c6b14f698194f343aebec30402452970
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921525"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: Inicjuj pola statyczne typu referencyjnego śródwierszowo

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Typ referencyjny deklaruje jawny Konstruktor statyczny.

## <a name="rule-description"></a>Opis reguły
Podczas gdy typ deklaruje jawny, statyczny konstruktor, kompilator just in time (JIT) do każdej metody statycznej dodaje sprawdzenie i konstruktora wystąpienia, aby upewnić się, że konstruktor statyczny został wcześniej wywołany. Inicjalizacja statyczna jest wyzwalana, gdy zostanie uzyskany dostęp do dowolnego statycznego elementu członkowskiego lub gdy tworzone jest wystąpienie typu. Jednak Inicjalizacja statyczna nie jest wyzwalana, Jeśli deklarujesz zmienną typu, ale nie korzystasz z niej, co może być istotne w przypadku zmiany stanu globalnego inicjalizacji.

Gdy wszystkie dane statyczne są inicjowane wewnętrznie i jawny Konstruktor statyczny nie jest zadeklarowany, kompilatory języka pośredniego ( `beforefieldinit` MSIL) firmy Microsoft dodają flagę i niejawnego konstruktora statycznego, który inicjuje dane statyczne, do typu MSIL definicji. Gdy kompilator JIT napotka `beforefieldinit` flagę, większość czasu sprawdzenia konstruktora statycznego nie jest dodawana. Inicjalizacja statyczna jest gwarantowana w pewnym czasie przed uzyskaniem dostępu do dowolnych pól statycznych, ale nie przed wywołaniem statycznej metody lub konstruktora wystąpień. Należy zauważyć, że inicjalizacja statyczna może wystąpić w dowolnym momencie po zadeklarowaniu zmiennej typu.

Sprawdzenia konstruktora statycznego mogą obniżyć wydajność. Często statyczny Konstruktor jest używany tylko do inicjowania pól statycznych, w takim przypadku należy tylko upewnić się, że inicjalizacja statyczna występuje przed pierwszym dostępem do pola statycznego. `beforefieldinit` Zachowanie jest odpowiednie dla tych i większości innych typów. Jest on nieodpowiedni tylko wtedy, gdy statyczna Inicjalizacja ma wpływ na stan globalny i jeden z następujących warunków jest spełniony:

- Wpływ na stan globalny jest kosztowny i nie jest wymagany, jeśli typ nie jest używany.

- Do globalnych efektów stanu można uzyskać dostęp bez uzyskiwania dostępu do żadnych pól statycznych typu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, zainicjuj wszystkie dane statyczne, gdy jest on zadeklarowany, i usuń konstruktor statyczny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Jeśli wydajność nie jest istotna, można bezpiecznie pominąć ostrzeżenie z tej reguły. lub jeśli globalne zmiany stanu, które są spowodowane inicjalizacją statyczną, są kosztowne lub muszą mieć gwarancje przed wywołaniem metody statycznej typu lub utworzenia wystąpienia typu.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje typ, `StaticConstructor`, który narusza regułę i typ, `NoStaticConstructor`, która zastępuje statyczny Konstruktor z inicjalizacją wbudowaną w celu spełnienia reguły.

[!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
[!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]

Zwróć uwagę na dodanie `beforefieldinit` flagi do definicji MSIL `NoStaticConstructor` dla klasy.

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

- [CA2207 Zainicjuj wbudowane pola typu wartości](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)