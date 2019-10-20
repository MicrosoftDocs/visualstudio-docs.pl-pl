---
title: 'CA1003: Użyj ogólnych wystąpień programu obsługi zdarzeń | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 34318d3fb01f3f8dee50da2bc534908cecbdaf32
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646296"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Użyj wystąpień obsługi zdarzeń generycznych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ zawiera delegata zwracającego wartość void, którego sygnatura zawiera dwa parametry (pierwszy obiekt i drugi typ, który można przypisać do EventArgs), oraz element docelowy zawierający zestaw [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].

## <a name="rule-description"></a>Opis reguły
 Przed [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], w celu przekazania informacji niestandardowych do programu obsługi zdarzeń, należy zadeklarować nowego delegata, który określił klasę pochodną klasy <xref:System.EventArgs?displayProperty=fullName>. Ta wartość nie jest już prawdziwa w [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], która wprowadziła <xref:System.EventHandler%601?displayProperty=fullName> delegata. Ten ogólny delegat zezwala dowolnej klasie, która jest pochodną <xref:System.EventArgs> do użycia razem z programem obsługi zdarzeń.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Usuń delegata i Zastąp jego użycie za pomocą delegata <xref:System.EventHandler%601?displayProperty=fullName>. Jeśli delegat jest automatycznie generowany przez kompilator [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], Zmień składnię deklaracji zdarzenia tak, aby korzystała z delegata <xref:System.EventHandler%601?displayProperty=fullName>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje delegata, który narusza regułę. W [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] przykładzie komentarze opisują sposób modyfikacji przykładu w celu spełnienia reguły. C# Przykładem jest Poniższy przykład, który pokazuje zmodyfikowany kod.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>Przykład
 Poniższy przykład usuwa deklarację delegata z poprzedniego przykładu, która spełnia regułę, i zastępuje jej użycie w metodach `ClassThatRaisesEvent` i `ClassThatHandlesEvent` za pomocą delegata <xref:System.EventHandler%601?displayProperty=fullName>.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1005: Unikaj nadużywania parametrów w typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Nie deklaruj składowych statycznych w typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Metody ogólne powinny udostępniać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: Używaj typów ogólnych wszędzie tam, gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz też
 [Typy ogólne](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
