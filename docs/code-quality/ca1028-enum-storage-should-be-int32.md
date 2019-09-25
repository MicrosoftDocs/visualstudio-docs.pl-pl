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
ms.openlocfilehash: 47a934a6e35296927eea64465ff8e7007219bec5
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236094"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: Magazyn typu wyliczeniowego powinien być typu Int32

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ podstawowy wyliczenia nie <xref:System.Int32?displayProperty=fullName>jest.

Domyślnie ta reguła sprawdza tylko publiczne wyliczenia, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Wyliczenie to typ wartości, który definiuje zestaw powiązanych, nazwanych stałych. Domyślnie <xref:System.Int32?displayProperty=fullName> typ danych jest używany do przechowywania wartości stałej. Mimo że można zmienić ten typ podstawowy, nie jest to konieczne ani zalecane w przypadku większości scenariuszy. Nie zostanie osiągnięty znaczący wzrost wydajności przy użyciu typu danych, który jest <xref:System.Int32>mniejszy niż. Jeśli nie można użyć domyślnego typu danych, należy <xref:System.Byte>użyć jednego z typów <xref:System.Int16> <xref:System.Int32>całkowitych zgodnych ze specyfikacją CLS (Common Language system),,, lub <xref:System.Int64> , aby upewnić się, że wszystkie wartości wyliczenia mogą być reprezentowane w Języki programowania zgodne ze specyfikacją CLS.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, chyba że występują problemy z rozmiarem lub zgodnością <xref:System.Int32>, użyj programu. W sytuacjach, <xref:System.Int32> gdy nie jest wystarczająco duży, aby pomieścić wartości <xref:System.Int64>, użyj. Jeśli zgodność z poprzednimi wersjami wymaga mniejszego <xref:System.Byte> typu <xref:System.Int16>danych, użyj lub.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Pomiń ostrzeżenie z tej reguły tylko w przypadku, gdy wymagają to problemów ze zgodnością z poprzednimi wersjami. W aplikacjach niezgodność z tą regułą zwykle nie powoduje problemów. W bibliotekach, w których wymagane jest współdziałanie języków, niezgodność z tą regułą może mieć negatywny wpływ na użytkowników.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1028.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Przykład naruszenia

W poniższym przykładzie przedstawiono dwa wyliczenia, które nie używają zalecanego bazowego typu danych.

[!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
[!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>Przykład naprawy

Poniższy przykład naprawia poprzednie naruszenie, zmieniając typ danych bazowych na <xref:System.Int32>.

[!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
[!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1008 Wyliczenia powinny mieć wartość zerową](../code-quality/ca1008-enums-should-have-zero-value.md)
- [CA1027 Oznacz typy wyliczeniowe atrybutem FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217 Nie oznaczaj typów wyliczeniowych atrybutem FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: Nie Nazwij wartości wyliczeniowych "zarezerwowane"](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: Nie określaj prefiksu wartości wyliczenia z nazwą typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Byte?displayProperty=fullName>
- <xref:System.Int16?displayProperty=fullName>
- <xref:System.Int32?displayProperty=fullName>
- <xref:System.Int64?displayProperty=fullName>