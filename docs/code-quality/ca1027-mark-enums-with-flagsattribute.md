---
title: 'CA1027: Oznacz Typy wyliczeniowe atrybutem Flags'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a559c20cd45ae39210421b647e8efd6c0928ade
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882107"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Oznacz Typy wyliczeniowe atrybutem Flags

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Wartości wyliczenia publiczne są potęgi liczb lub kombinacji innych wartości, które są zdefiniowane w wyliczeniu, i <xref:System.FlagsAttribute?displayProperty=fullName> atrybut nie jest obecny. W celu zmniejszenia liczby wyników fałszywie dodatnich, ta reguła nie raportuje naruszenie dla wyliczenia, które mają wartości ciągłe.

## <a name="rule-description"></a>Opis reguły
 Wyliczenie to typ wartości, który definiuje zestaw powiązanych, nazwanych stałych. Zastosuj <xref:System.FlagsAttribute> z wyliczeniem, gdy jego stałe nazwane mogą zostać sensownie połączone. Rozważmy na przykład wyliczenie dni tygodnia w aplikacji, która przechowuje informacje o dostępnych zasobów który dzień. Jeśli dostępność każdego zasobu jest zaszyfrowana przy użyciu wyliczenia, które ma <xref:System.FlagsAttribute> obecne i dowolną kombinację dni, które mogą być reprezentowane. Bez atrybutu może być reprezentowany tylko jeden dzień tygodnia.

 W przypadku pól, które przechowują wyliczenia możliwych do łączenia wartości wyliczenia poszczególnych są traktowane jako grup bitów w polu. Dlatego takie pola są czasami określane jako *pola bitowe*. Aby połączyć wartości wyliczenia do przechowywania w pole bitowe, należy użyć logiczna operatorów warunkowych. Aby przetestować polem bitowym, aby ustalić, czy występuje wartość wyliczenia określonego, użyj operatorów logicznych logicznych. Pola bitowe do przechowywania i pobierania wartości wyliczenia połączone poprawnie każda wartość, która jest zdefiniowana w wyliczeniu musi być potęgą liczby dwa. Jeśli tak jest, wartość logiczna operatorów logicznych nie będzie można wyodrębnić wartości poszczególnych wyliczenia, które są przechowywane w polu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy dodać <xref:System.FlagsAttribute> do wyliczenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły, jeśli nie chcesz, aby wartości wyliczenia możliwych do łączenia się.

## <a name="example"></a>Przykład
 W poniższym przykładzie `DaysEnumNeedsFlags` jest wyliczeniem, który spełnia wymagania dotyczące korzystania z <xref:System.FlagsAttribute>, ale nie ma. `ColorEnumShouldNotHaveFlag` Wyliczenia nie ma wartości, które są potęgi liczby dwa, ale niepoprawnie Określa <xref:System.FlagsAttribute>. Narusza regułę [CA2217: Nie oznaczaj wyliczeń za pomocą FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2217: Nie oznaczaj wyliczeń za pomocą FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Zobacz także
 <xref:System.FlagsAttribute?displayProperty=fullName>