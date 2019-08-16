---
title: 'CA1041: Udostępnij komunikat ObsoleteAttribute'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a0545503b80e2f256593012e06cdf7ccd8b3b5b1
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547630"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: Udostępnij komunikat ObsoleteAttribute

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Typ lub element członkowski jest oznaczony przy użyciu <xref:System.ObsoleteAttribute?displayProperty=fullName> atrybutu, który nie <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> ma określonej właściwości.

Domyślnie ta reguła sprawdza tylko widoczne na zewnątrz typy i elementy członkowskie, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

<xref:System.ObsoleteAttribute>służy do oznaczania przestarzałych typów bibliotek i elementów członkowskich. Odbiorcy biblioteki powinni unikać używania dowolnego typu lub elementu członkowskiego, który jest oznaczony jako przestarzały. Wynika to z faktu, że może to nie być obsługiwane i ostatecznie zostanie usunięte z nowszych wersji biblioteki. Po skompilowaniu <xref:System.ObsoleteAttribute.Message%2A> typu lub elementu członkowskiego <xref:System.ObsoleteAttribute> oznaczonego za pomocą jest wyświetlana właściwość atrybutu. Dostarcza to informacje użytkownika o przestarzałym typie lub elemencie członkowskim. Te informacje zazwyczaj obejmują czas, przez jaki przestarzały typ lub składowa będą obsługiwane przez projektantów biblioteki i preferowane zastąpienie do użycia.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy dodać `message` parametr <xref:System.ObsoleteAttribute> do konstruktora.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżenia z tej reguły, <xref:System.ObsoleteAttribute.Message%2A> ponieważ właściwość zawiera krytyczne informacje o nieaktualnym typie lub elemencie członkowskim.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1041.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje przestarzałą składową, która jest prawidłowo zadeklarowana <xref:System.ObsoleteAttribute>.

[!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
[!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
[!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>Zobacz także

- <xref:System.ObsoleteAttribute?displayProperty=fullName>