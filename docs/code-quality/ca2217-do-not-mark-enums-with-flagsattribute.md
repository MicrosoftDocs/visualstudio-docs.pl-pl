---
title: 'CA2217: Nie oznaczaj typów wyliczeniowych atrybutem Flags'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
dev_langs:
- VB
- CSharp
- CPP
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce4036ef3c0c9ea177ea4225ed10ca7cfe128697
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55926817"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217: Nie oznaczaj typów wyliczeniowych atrybutem Flags

|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Widoczne na zewnątrz wyliczenie jest oznaczona za pomocą <xref:System.FlagsAttribute>i ma jedną lub więcej wartości, które nie są potęgami dwa lub kombinacji innych zdefiniowanych wartości w wyliczeniu.

## <a name="rule-description"></a>Opis reguły

Wyliczenie powinny mieć <xref:System.FlagsAttribute> obecny tylko wtedy, gdy każda wartość zdefiniowana w wyliczeniu jest potęgą liczby dwa lub kombinację zdefiniowane wartości.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, Usuń <xref:System.FlagsAttribute> z wyliczenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example-that-should-not-have-the-attribute"></a>Przykład, który nie powinien mieć atrybutu

W poniższym przykładzie przedstawiono wyliczenie `Color`, która zawiera wartość 3. 3 nie jest potęgą liczby dwa lub więcej dowolnych zdefiniowanymi wartościami. `Color` Wyliczenia nie powinien być oznaczony przez <xref:System.FlagsAttribute>.

[!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

## <a name="example-that-should-have-the-attribute"></a>Przykład, w którym powinien mieć atrybutu

W poniższym przykładzie przedstawiono wyliczenie `Days`, który spełnia wymagania są oznaczone <xref:System.FlagsAttribute>.

[!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>Powiązane reguły

[CA1027: Oznacz Typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.FlagsAttribute?displayProperty=fullName>
