---
title: 'CA1018: Oznacz atrybuty atrybutem AttributeUsageAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 256fc281b27c483f1dda0317f7d2695fa36c47f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535060"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Oznacz atrybuty atrybutem AttributeUsage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 <xref:System.AttributeUsageAttribute?displayProperty=fullName>Atrybut nie występuje w atrybucie niestandardowym.

## <a name="rule-description"></a>Opis reguły
 Podczas definiowania atrybutu niestandardowego należy oznaczyć go przy użyciu, <xref:System.AttributeUsageAttribute> Aby wskazać, gdzie w kodzie źródłowym można zastosować atrybut niestandardowy. Znaczenie i zamierzone użycie atrybutu określi jego prawidłowe lokalizacje w kodzie. Na przykład można zdefiniować atrybut, który identyfikuje osoby odpowiedzialne za utrzymanie i udoskonalenie każdego typu w bibliotece, a odpowiedzialność jest zawsze przypisana na poziomie typu. W takim przypadku kompilatory powinny włączyć atrybut dla klas, wyliczeń i interfejsów, ale nie powinien włączać go dla metod, zdarzeń lub właściwości. Zasady i procedury organizacyjne określają, czy atrybut powinien być włączony dla zestawów.

 <xref:System.AttributeTargets?displayProperty=fullName>Wyliczenie definiuje elementy docelowe, które można określić dla atrybutu niestandardowego. W przypadku pominięcia <xref:System.AttributeUsageAttribute> atrybut niestandardowy będzie prawidłowy dla wszystkich obiektów docelowych, zgodnie z definicją `All` wartości <xref:System.AttributeTargets> wyliczenia.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, określ elementy docelowe dla atrybutu przy użyciu <xref:System.AttributeUsageAttribute> . Zobacz poniższy przykład.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Przed wykluczeniem komunikatu należy usunąć naruszenie tej reguły. Nawet jeśli atrybut dziedziczy <xref:System.AttributeUsageAttribute> , atrybut powinien być obecny, aby uprościć konserwację kodu.

## <a name="example"></a>Przykład
 W poniższym przykładzie zdefiniowano dwa atrybuty. `BadCodeMaintainerAttribute` niepoprawnie pomija <xref:System.AttributeUsageAttribute> instrukcję i `GoodCodeMaintainerAttribute` poprawnie implementuje atrybut opisany wcześniej w tej sekcji. Należy zauważyć, że właściwość `DeveloperName` jest wymagana przez regułę projektowania [CA1019: Zdefiniuj metody dostępu dla argumentów atrybutów](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) i jest dołączany do kompletności.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/cs/FxCop.Design.AttributeUsage.cs#1)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/vb/FxCop.Design.AttributeUsage.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1019: Zdefiniuj metody dostępu dla argumentów atrybutów](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: Unikaj niezapieczętowanych atrybutów](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Zobacz też
 [Atrybuty](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
