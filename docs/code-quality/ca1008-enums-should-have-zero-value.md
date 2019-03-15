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
ms.openlocfilehash: 4bb79d2944bdb49c59fd53fb30e1497c57c5c516
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57868288"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Typy wyliczeniowe powinny mieć wartość zero

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Dzielenie non - po wyświetleniu monitu o dodanie **Brak** wartość wyliczenia bez flagi. Przerywanie — po wyświetleniu monitu, aby zmienić nazwę lub Usuń wszystkie wartości wyliczenia.|

## <a name="cause"></a>Przyczyna

Wyliczenia bez zastosowanych <xref:System.FlagsAttribute?displayProperty=fullName> nie definiuje element członkowski, który ma wartość zero. Lub wyliczeniem, który został zastosowany <xref:System.FlagsAttribute> definiuje składową z wartością zero, ale jego nazwa nie jest "None". Lub wyliczenie definiuje wiele składowych o wartości zero.

Domyślnie ta reguła przegląda tylko wyliczenia widocznego na zewnątrz, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

Wartość domyślna niezainicjowanego typu wyliczeniowego, podobnie jak inne typy wartości, wynosi zero. Wyliczanie przypisane flagi należy zdefiniować element członkowski, który ma wartość zero, więc wartość domyślna jest prawidłową wartością wyliczenia. Jeśli to stosowne, nazwa elementu członkowskiego "None". W przeciwnym razie przypisać zero do najczęściej używanych elementu członkowskiego. Domyślnie jeśli nie ustawiono wartość pierwszego elementu członkowskiego wyliczenia w deklaracji, jego wartość wynosi zero.

Jeśli wyliczenie, które ma <xref:System.FlagsAttribute> stosowane definiuje składową o wartości zero, powinno być nazwane "Brak", aby wskazać, że żadne wartości nie zostały ustawione w wyliczeniu. Za pomocą elementu członkowskiego o wartości zero dla żadnych innych celów jest sprzeczne z użytkowania <xref:System.FlagsAttribute> , AND i operatory bitowe są bezużyteczne z elementem członkowskim. Oznacza to, że można przypisać tylko jednego członka wartości zero. Jeśli wiele elementów członkowskich, które mają wartość zero występują w wyliczeniu przypisywane flag `Enum.ToString()` zwraca niepoprawne wyniki dla elementów członkowskich, które nie mają wartość zero.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady dla wyliczenia przypisywane flag, należy zdefiniować element członkowski, który ma wartość zero. jest to zmian niepowodujących niezgodności. W przypadku opartego na atrybutach flagi wyliczeń, które definiują elementu członkowskiego o wartości zero nadaj nazwę tego elementu członkowskiego "None", a następnie usunąć innych elementów członkowskich, które mają wartość zero. jest to istotnej zmiany.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły, z wyjątkiem wyliczenia przypisywane flag, które wcześniej zostały wprowadzone do użytku.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```
dotnet_code_quality.ca1008.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano dwa wyliczenia, które spełniają reguły i wyliczenia `BadTraceOptions`, który narusza regułę.

[!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
[!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
[!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>Powiązane reguły

- [CA2217: Nie oznaczaj wyliczeń za pomocą FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: Nie nadawaj wartościom wyliczenia nazwy "Reserved"](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: Nie poprzedzaj wartości wyliczenia nazwą typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)
- [CA1028: Magazyn typu wyliczeniowego powinien być typu Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)
- [CA1027: Oznacz Typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Enum?displayProperty=fullName>