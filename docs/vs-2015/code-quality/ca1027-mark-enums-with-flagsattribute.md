---
title: 'CA1027: Oznacz typy wyliczeniowe atrybutem FlagsAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 774279dd05bd14c34df7f1d450f00599812d6a5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544511"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Oznacz typy wyliczeniowe atrybutem Flags
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Wartości wyliczenia publicznego są potęgami dwóch lub są kombinacją innych wartości, które są zdefiniowane w wyliczeniu, a <xref:System.FlagsAttribute?displayProperty=fullName> atrybut nie jest obecny. Aby zmniejszyć liczbę fałszywie dodatnich, ta reguła nie zgłasza naruszenia dla wyliczeń, które mają ciągłe wartości.

## <a name="rule-description"></a>Opis reguły
 Wyliczenie to typ wartości, który definiuje zestaw powiązanych, nazwanych stałych. Zastosuj <xref:System.FlagsAttribute> do wyliczenia, gdy jego nazwane stałe mogą być w znaczący sposób połączone. Rozważmy na przykład Wyliczenie dni tygodnia w aplikacji, która śledzi zasoby danego dnia. Jeśli dostępność każdego zasobu jest zakodowana przy użyciu wyliczenia, które jest <xref:System.FlagsAttribute> obecne, można przedstawić dowolną kombinację dni. Bez atrybutu, można przedstawić tylko jeden dzień tygodnia.

 W przypadku pól, które przechowują wyliczenia do przydzielenia, poszczególne wartości wyliczenia są traktowane jako grupy bitów w polu. W związku z tym takie pola są czasami określane jako *pola bitowe*. Aby połączyć wartości wyliczenia dla magazynu w polu bitowym, użyj operatorów warunkowych Boolean. Aby przetestować pole bitowe w celu ustalenia, czy określona wartość wyliczenia jest obecna, użyj logicznych operatorów logicznych. W przypadku pola bitowego do poprawnego przechowywania i pobierania połączonych wartości wyliczenia każda wartość zdefiniowana w wyliczeniu musi być potęgą liczby dwa. O ile tak nie jest, logiczne operatory logiczne nie będą mogły wyodrębnić poszczególnych wartości wyliczenia, które są przechowywane w polu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Dodaj <xref:System.FlagsAttribute> do wyliczenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie z tej reguły, jeśli nie chcesz, aby wartości wyliczenia były możliwe do kombinacji.

## <a name="example"></a>Przykład
 W poniższym przykładzie `DaysEnumNeedsFlags` jest wyliczeniem spełniającym wymagania dotyczące korzystania z programu <xref:System.FlagsAttribute> , ale nie ma go. `ColorEnumShouldNotHaveFlag`Wyliczenie nie zawiera wartości, które są potęgami dwóch, ale nieprawidłowo określa <xref:System.FlagsAttribute> . Narusza to reguły [CA2217: nie oznaczaj typów wyliczeniowych atrybutem FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2217: Nie oznaczaj typów wyliczeniowych atrybutem Flags](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.FlagsAttribute?displayProperty=fullName>
