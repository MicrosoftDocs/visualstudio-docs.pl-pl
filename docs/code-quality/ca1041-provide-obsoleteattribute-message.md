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
ms.openlocfilehash: 354d1d2fe99fa55bba7f8a00bf3e9f760ff1dbaf
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842184"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: Udostępnij komunikat ObsoleteAttribute

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Typ lub element członkowski jest oznaczony za pomocą <xref:System.ObsoleteAttribute?displayProperty=fullName> atrybut, który nie ma jej <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> określona właściwość.

Domyślnie ta reguła przegląda tylko typy widoczne na zewnątrz i elementów członkowskich, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

<xref:System.ObsoleteAttribute> Służy do oznaczania przestarzałe biblioteki typów i elementów członkowskich. Konsumenci biblioteki należy unikać użycia dowolnego typu lub elementu członkowskiego, który jest oznaczony jako przestarzały. Jest to spowodowane może nie być obsługiwany i po pewnym czasie zostaną usunięte z nowszymi wersjami biblioteki. Gdy typ lub element członkowski oznaczony za pomocą <xref:System.ObsoleteAttribute> jest kompilowany <xref:System.ObsoleteAttribute.Message%2A> właściwość atrybutu jest wyświetlana. Dostarcza to informacje użytkownika o przestarzałym typie lub elemencie członkowskim. Informacje te obejmują zazwyczaj ile przestarzałego typu lub elementu członkowskiego, które będą obsługiwane przez projektantów biblioteki i zastąpienie preferowany do użycia.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy dodać `message` parametr <xref:System.ObsoleteAttribute> konstruktora.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły, ponieważ <xref:System.ObsoleteAttribute.Message%2A> dostarcza krytycznych informacji na temat przestarzałego typu lub składowej.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```ini
dotnet_code_quality.ca1041.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano przestarzałą składową, która ma poprawnie zadeklarowane <xref:System.ObsoleteAttribute>.

[!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
[!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
[!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>Zobacz także

- <xref:System.ObsoleteAttribute?displayProperty=fullName>