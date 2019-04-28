---
title: 'CA1028: Magazyn typu wyliczeniowego powinien być typu Int32'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 95e2a8892bb7b52122dd34afa3f300123149bb26
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779239"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: Magazyn typu wyliczeniowego powinien być typu Int32

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Nie jest podstawowym typem wyliczenia <xref:System.Int32?displayProperty=fullName>.

Domyślnie ta reguła przegląda tylko wyliczenia publiczne, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

Wyliczenie to typ wartości, który definiuje zestaw powiązanych, nazwanych stałych. Domyślnie <xref:System.Int32?displayProperty=fullName> typ danych jest używany do przechowywania wartości stałej. Mimo że możesz to zmienić, typ podstawowy, nie jest wymagane lub zalecane w przypadku większości scenariuszy. Żadnych korzyści istotnie poprawiającą wydajność odbywa się za pomocą typu danych, który jest mniejszy niż <xref:System.Int32>. Jeśli nie możesz użyć domyślnego typu danych, należy użyć jednej wspólnej systemu Language (CLS)-zgodnych typów całkowitych <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, lub <xref:System.Int64> aby upewnić się, że wszystkie wartości wyliczenia mogą być reprezentowane w Zgodne ze specyfikacją CLS języków programowania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, chyba że występują problemy z rozmiar lub zgodność, należy użyć <xref:System.Int32>. W sytuacjach, gdzie <xref:System.Int32> nie jest wystarczająco duży, aby przechowywać wartości, użyj <xref:System.Int64>. Jeśli zgodność ze starszymi wersjami wymaga mniejszych typów danych, należy użyć <xref:System.Byte> lub <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Pomijaj ostrzeżeń dla tej reguły, tylko wtedy, gdy problemy ze zgodnością z poprzednimi wersjami tego wymagają. W aplikacjach Niezachowanie zgodności z tą regułą, zazwyczaj nie powoduje problemów. W bibliotekach, gdy wymagana jest współdziałanie języków, brak zgodności z tą regułą może niekorzystnie wpłynąć na użytkowników.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```
dotnet_code_quality.ca1028.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Przykładem naruszenia

Poniższy przykład przedstawia dwa wyliczenia, których nie należy używać zalecane odpowiedniego typu danych.

[!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
[!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>Przykład sposobu rozwiązania

Poniższy przykład naprawia wcześniejszego naruszenia praw, zmieniając odpowiedniego typu danych w celu <xref:System.Int32>.

[!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
[!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1008: Typy wyliczeniowe powinny mieć wartości zerowej](../code-quality/ca1008-enums-should-have-zero-value.md)
- [CA1027: Oznacz Typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: Nie oznaczaj wyliczeń za pomocą FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: Nie nadawaj wartościom wyliczenia nazwy "Reserved"](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: Nie poprzedzaj wartości wyliczenia nazwą typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Byte?displayProperty=fullName>
- <xref:System.Int16?displayProperty=fullName>
- <xref:System.Int32?displayProperty=fullName>
- <xref:System.Int64?displayProperty=fullName>