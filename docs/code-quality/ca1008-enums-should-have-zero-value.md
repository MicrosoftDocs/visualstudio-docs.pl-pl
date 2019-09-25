---
title: 'CA1008: Typy wyliczeniowe powinny mieć wartość zero'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c9b6e48fb82be5a41c420827a32926630bb725ed
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236488"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Typy wyliczeniowe powinny mieć wartość zero

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Rozdzielenie — gdy zostanie wyświetlony monit o dodanie wartości **Brak** do wyliczenia bez flagi. Przerywanie — gdy zostanie wyświetlony monit o zmianę nazwy lub usunięcie wartości wyliczenia.|

## <a name="cause"></a>Przyczyna

Wyliczenie bez zastosowania <xref:System.FlagsAttribute?displayProperty=fullName> nie definiuje elementu członkowskiego, który ma wartość zero. Lub Wyliczenie, które ma zastosowanie <xref:System.FlagsAttribute> , definiuje element członkowski, który ma wartość zero, ale jego nazwą nie jest "none". Lub, Wyliczenie definiuje wiele elementów członkowskich o wartości zero.

Domyślnie ta reguła sprawdza się tylko na wyliczeniu widocznym na zewnątrz, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Wartość domyślna niezainicjowanego wyliczenia, podobnie jak inne typy wartości, wynosi zero. Wyliczenie z atrybutami bez flag powinna definiować element członkowski, który ma wartość zero, aby wartość domyślna była prawidłową wartością wyliczenia. W razie potrzeby Nadaj nazwę elementowi członkowskiemu "none". W przeciwnym razie Przypisz zero do najczęściej używanej składowej. Domyślnie, jeśli wartość pierwszego wyliczenia elementu członkowskiego nie jest ustawiona w deklaracji, jego wartość wynosi zero.

Jeśli Wyliczenie, które ma <xref:System.FlagsAttribute> zastosowanie definiuje element członkowski o wartości zero, jego nazwa powinna mieć wartość "Brak", aby wskazać, że nie zostały ustawione żadne wartości w wyliczeniu. Użycie elementu członkowskiego o wartości zerowej do dowolnego innego celu jest sprzeczne z użyciem <xref:System.FlagsAttribute> w, że operatory i i lub bitowe są bezużyteczne dla elementu członkowskiego. Oznacza to, że tylko jeden element członkowski powinien mieć przypisaną wartość zero. Jeśli wiele elementów członkowskich, które mają wartość zero, występuje w wyliczeniu z atrybutami flagi, `Enum.ToString()` zwraca nieprawidłowe wyniki dla elementów członkowskich, które nie są równe zero.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły dla wyliczeń o atrybutach innych niż flagi, zdefiniuj element członkowski, który ma wartość zero; to nie jest zmiana nieprzerwana. Dla flag — wyliczenia z atrybutami, które definiują element członkowski o wartości zero, Nazwij ten element członkowski "none" i Usuń wszystkie inne elementy członkowskie, które mają wartość zero; jest to istotna zmiana.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżenia z tej reguły z wyjątkiem flag — wyliczenia przypisane do atrybutów, które zostały wcześniej wysłane.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1008.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono dwa wyliczenia, które spełniają zasadę i Wyliczenie, `BadTraceOptions`które naruszają daną regułę.

[!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
[!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
[!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>Powiązane reguły

- [CA2217 Nie oznaczaj typów wyliczeniowych atrybutem FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: Nie Nazwij wartości wyliczeniowych "zarezerwowane"](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: Nie określaj prefiksu wartości wyliczenia z nazwą typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)
- [CA1028 Magazyn wyliczeniowy powinien mieć wartość Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)
- [CA1027 Oznacz typy wyliczeniowe atrybutem FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Enum?displayProperty=fullName>