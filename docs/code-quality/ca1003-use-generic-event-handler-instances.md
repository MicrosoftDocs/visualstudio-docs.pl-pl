---
title: 'CA1003: Użyj ogólnych wystąpień procedury obsługi zdarzeń'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 89ee70694d81253c66fc83062c9736ba63f7e6e6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907311"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Użyj ogólnych wystąpień procedury obsługi zdarzeń

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ zawiera delegata zwracającego wartość typu void, którego podpis zawiera dwa parametry (pierwszy typu obiekt i drugi typu, który można przypisać do EventArgs) i cele zestawu zawierającego [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="rule-description"></a>Opis reguły
 Przed [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], aby można było przekazać niestandardowe informacje do narzędzia obsługi zdarzeń nowe delegowanie musiały być zadeklarowany, które określone klasy, który został utworzony na podstawie <xref:System.EventArgs?displayProperty=fullName> klasy. Nie jest to już wartość true w [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], który wprowadzono <xref:System.EventHandler%601?displayProperty=fullName> delegować. Ten delegat ogólny umożliwia każdej klasy, która jest pochodną <xref:System.EventArgs> ma być używany razem z programu obsługi zdarzeń.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Usuń delegata i zastąp jego użycie za pomocą <xref:System.EventHandler%601?displayProperty=fullName> delegować. Jeśli delegat jest generowana automatycznie przez [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kompilatora, zmień Składnia deklaracji zdarzeń, użyj <xref:System.EventHandler%601?displayProperty=fullName> delegować.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Delegat, który narusza regułę określającą, można znaleźć w poniższym przykładzie. W [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] przykład komentarze opisują sposób modyfikowania przykładu tak, aby spełniać reguły. Na przykład C# przykład poniżej pokazujący modyfikacji kodu.

 [!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
 [!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

## <a name="example"></a>Przykład
 Poniższy przykład usuwa deklaracja delegata z poprzedniego przykładu, spełnia regułę, która zastępuje jej użycia w `ClassThatRaisesEvent` i `ClassThatHandlesEvent` metody przy użyciu <xref:System.EventHandler%601?displayProperty=fullName> delegować.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1005: Unikaj nadużywania parametrów na typach generycznych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Nie deklaruj składowych statycznych w typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Metody ogólne powinny podawać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: Używaj typów ogólnych wszędzie, gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz także

- [Typy ogólne](/dotnet/csharp/programming-guide/generics/index)