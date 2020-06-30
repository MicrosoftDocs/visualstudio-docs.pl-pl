---
title: 'CA1041: Podaj komunikat ObsoleteAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d738cf15ebe734cb74e553f38f6eb26af17e8cfd
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542314"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: Udostępnij komunikat ObsoleteAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Typ lub element członkowski jest oznaczony przy użyciu <xref:System.ObsoleteAttribute?displayProperty=fullName> atrybutu, który nie ma <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> określonej właściwości.

## <a name="rule-description"></a>Opis reguły
 <xref:System.ObsoleteAttribute>służy do oznaczania przestarzałych typów bibliotek i elementów członkowskich. Odbiorcy biblioteki powinni unikać używania dowolnego typu lub elementu członkowskiego, który jest oznaczony jako przestarzały. Wynika to z faktu, że może to nie być obsługiwane i ostatecznie zostanie usunięte z nowszych wersji biblioteki. Po skompilowaniu typu lub elementu członkowskiego oznaczonego za pomocą <xref:System.ObsoleteAttribute> jest <xref:System.ObsoleteAttribute.Message%2A> wyświetlana właściwość atrybutu. Dostarcza to informacje użytkownika o przestarzałym typie lub elemencie członkowskim. Te informacje zazwyczaj obejmują czas, przez jaki przestarzały typ lub składowa będą obsługiwane przez projektantów biblioteki i preferowane zastąpienie do użycia.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy dodać `message` parametr do <xref:System.ObsoleteAttribute> konstruktora.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenia z tej reguły, ponieważ <xref:System.ObsoleteAttribute.Message%2A> Właściwość zawiera krytyczne informacje o nieaktualnym typie lub elemencie członkowskim.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje przestarzałą składową, która jest prawidłowo zadeklarowana <xref:System.ObsoleteAttribute> .

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.ObsoleteAttribute?displayProperty=fullName>
