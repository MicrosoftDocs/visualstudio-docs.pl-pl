---
title: 'CA1813: Unikaj niezapieczętowanych atrybutów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8d86f4a9ecbdfff451fed21f93c0fe6a7679d471
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543952"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: Unikaj niezapieczętowanych atrybutów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Kategoria|Microsoft. Performance|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny dziedziczy z <xref:System.Attribute?displayProperty=fullName> , nie jest abstrakcyjny i nie jest zapieczętowany ( `NotInheritable` w Visual Basic).

## <a name="rule-description"></a>Opis reguły
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Biblioteka klas zawiera metody pobierania atrybutów niestandardowych. Domyślnie te metody przeszukują hierarchię dziedziczenia atrybutów; na przykład <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> wyszukuje określony typ atrybutu lub dowolny typ atrybutu, który rozszerza określony typ atrybutu. Opieczętowanie atrybutu eliminuje wyszukiwanie w hierarchii dziedziczenia i może zwiększyć wydajność.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zapieczętować typ atrybutu lub uczynić go abstrakcyjnym.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie z tej reguły. Należy to zrobić tylko wtedy, gdy definiujesz hierarchię atrybutów i nie można zapieczętować atrybutu ani uczynić abstrakcyjnym.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje niestandardowy atrybut, który spełnia tę regułę.

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/cs/FxCop.Performance.AttributesSealed.cs#1)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/vb/FxCop.Performance.AttributesSealed.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1019: Zdefiniuj metody dostępu dla argumentów atrybutów](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018: Oznacz atrybuty atrybutem AttributeUsage](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Zobacz też
 [Atrybuty](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
