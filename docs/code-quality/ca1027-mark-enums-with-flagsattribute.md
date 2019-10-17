---
title: 'CA1027: Oznaczaj wyliczenia za pomocą FlagsAttribute'
ms.date: 03/11/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fc9dde4aeb3363e542e475c253b292047f5c1c2
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72441374"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Oznaczaj wyliczenia za pomocą FlagsAttribute

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Kategoria|Microsoft. Design|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Wartości wyliczenia są potęgami dwóch lub są kombinacjami innych wartości, które są zdefiniowane w wyliczeniu, i atrybut <xref:System.FlagsAttribute?displayProperty=fullName> nie jest obecny. Aby zmniejszyć liczbę fałszywie dodatnich, ta reguła nie zgłasza naruszenia dla wyliczeń, które mają ciągłe wartości.

Domyślnie ta reguła sprawdza tylko publiczne wyliczenia, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Wyliczenie to typ wartości, który definiuje zestaw powiązanych, nazwanych stałych. Zastosuj <xref:System.FlagsAttribute> do wyliczenia, gdy jego nazwane stałe mogą być w znaczący sposób połączone. Rozważmy na przykład Wyliczenie dni tygodnia w aplikacji, która śledzi zasoby danego dnia. Jeśli dostępność każdego zasobu jest zaszyfrowana przy użyciu wyliczenia, które ma <xref:System.FlagsAttribute>, można przedstawić dowolną kombinację dni. Bez atrybutu, można przedstawić tylko jeden dzień tygodnia.

W przypadku pól, które przechowują wyliczenia do przydzielenia, poszczególne wartości wyliczenia są traktowane jako grupy bitów w polu. W związku z tym takie pola są czasami określane jako *pola bitowe*. Aby połączyć wartości wyliczenia dla magazynu w polu bitowym, użyj operatorów warunkowych Boolean. Aby przetestować pole bitowe w celu ustalenia, czy określona wartość wyliczenia jest obecna, użyj logicznych operatorów logicznych. W przypadku pola bitowego do poprawnego przechowywania i pobierania połączonych wartości wyliczenia każda wartość zdefiniowana w wyliczeniu musi być potęgą liczby dwa. O ile tak nie jest, logiczne operatory logiczne nie będą mogły wyodrębnić poszczególnych wartości wyliczenia, które są przechowywane w polu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Dodaj <xref:System.FlagsAttribute> do wyliczenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Pomiń ostrzeżenie z tej reguły, jeśli nie chcesz, aby wartości wyliczenia były możliwe do kombinacji.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1027.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

W poniższym przykładzie `DaysEnumNeedsFlags` to Wyliczenie spełniające wymagania dotyczące korzystania z <xref:System.FlagsAttribute>, ale nie ma go. Wyliczenie `ColorEnumShouldNotHaveFlag` nie zawiera wartości, które mają uprawnienia dwa, ale nieprawidłowo określa <xref:System.FlagsAttribute>. Narusza to reguły [CA2217: nie oznaczaj typów wyliczeniowych atrybutem FlagsAttribute](../code-quality/ca2217.md).

[!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]

## <a name="related-rules"></a>Powiązane reguły

- [CA2217: Nie oznaczaj wyliczeń za pomocą atrybutu FlagsAttribute](../code-quality/ca2217.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.FlagsAttribute?displayProperty=fullName>
