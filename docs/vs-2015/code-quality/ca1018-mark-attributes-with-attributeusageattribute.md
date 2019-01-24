---
title: 'CA1018: Oznacz atrybuty atrybutem Attributeusage | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 628eae181fa685e5173030ebac94387edfe4a194
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54761394"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Oznacz atrybuty atrybutem AttributeUsage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 <xref:System.AttributeUsageAttribute?displayProperty=fullName> Atrybut nie jest obecny na atrybutu niestandardowego.

## <a name="rule-description"></a>Opis reguły
 Podczas definiowania atrybutu niestandardowego, oznacz go za pomocą <xref:System.AttributeUsageAttribute> aby wskazać, gdzie w kodzie źródłowym atrybutu niestandardowego można zastosować. Znaczenie i zamierzone użycie atrybutu określi jego prawidłowe lokalizacje w kodzie. Na przykład można zdefiniować atrybut, który zawiera informacje o osobie, kto jest odpowiedzialny za utrzymanie i udoskonalanie poszczególnych typów w bibliotece, a odpowiedzialność jest zawsze przypisywana na poziomie typu. W takich przypadkach kompilatory należy włączyć atrybut na klas, wyliczeń i interfejsów, ale nie należy włączać na metody, zdarzenia lub właściwości. Procedury i zasady organizacji będzie określają, czy ten atrybut powinien być włączony na zestawach.

 <xref:System.AttributeTargets?displayProperty=fullName> Wyliczenie definiuje obiekty docelowe, które można określić atrybutu niestandardowego. Jeżeli pominięto <xref:System.AttributeUsageAttribute>, niestandardowy atrybut będzie obowiązywał dla wszystkich obiektów docelowych, zgodnie z definicją `All` wartość <xref:System.AttributeTargets> wyliczenia.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy określić cele, dla atrybutu za pomocą <xref:System.AttributeUsageAttribute>. Zobacz poniższy przykład.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Należy naprawić naruszenie tej zasady, zamiast wiadomości z wyjątkiem. Nawet wtedy, gdy atrybut inherits <xref:System.AttributeUsageAttribute>, atrybut powinien być obecny, aby uprościć zarządzanie kodu.

## <a name="example"></a>Przykład
 W poniższym przykładzie zdefiniowano dwa atrybuty. `BadCodeMaintainerAttribute` niepoprawnie pomija <xref:System.AttributeUsageAttribute> instrukcji i `GoodCodeMaintainerAttribute` poprawnie implementuje atrybut, który jest opisany wcześniej w tej sekcji. Należy pamiętać, że właściwość `DeveloperName` jest wymagana przez tę zasadę projektowania [CA1019: Zdefiniuj metody dostępu dla argumentów atrybutu](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) i został uwzględniony, aby informacje były kompletne.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/cs/FxCop.Design.AttributeUsage.cs#1)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/vb/FxCop.Design.AttributeUsage.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1019: Zdefiniuj metody dostępu dla argumentów atrybutu](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: Unikaj niezapieczętowanych atrybutów](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Zobacz też
 [Atrybuty](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
