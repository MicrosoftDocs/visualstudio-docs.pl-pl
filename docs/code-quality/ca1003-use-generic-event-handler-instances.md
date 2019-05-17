---
title: 'CA1003: Użyj ogólnych wystąpień procedury obsługi zdarzeń'
ms.date: 03/11/2019
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
ms.openlocfilehash: f666dc71aaf9683d9a7c936cc4985e97146d9454
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842527"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Użyj ogólnych wystąpień procedury obsługi zdarzeń

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ zawiera delegata zwracającego wartość typu void i którego podpis zawiera dwa parametry (pierwszy typu obiekt i drugi typu, który można przypisać do EventArgs) i zawierającego zestaw elementów docelowych .NET.

Domyślnie ta reguła przegląda tylko typy widoczne na zewnątrz, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

Przed .NET, aby można było przekazać niestandardowe informacje do narzędzia obsługi zdarzeń nowe delegowanie musiały być zadeklarowany, które określone klasy, który został utworzony na podstawie <xref:System.EventArgs?displayProperty=fullName> klasy. Ta zasada obowiązuje już na platformie .NET. Wprowadzona w programie .NET Framework <xref:System.EventHandler%601?displayProperty=fullName> delegata, Delegat ogólny, która umożliwia każdej klasy, która jest pochodną <xref:System.EventArgs> ma być używany razem z programu obsługi zdarzeń.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, Usuń delegata i zastąp jego użycie za pomocą <xref:System.EventHandler%601?displayProperty=fullName> delegować.

Jeśli delegat jest generowana automatycznie przez kompilator języka Visual Basic, zmień Składnia deklaracji zdarzeń, użyj <xref:System.EventHandler%601?displayProperty=fullName> delegować.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```ini
dotnet_code_quality.ca1003.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

Delegat, który narusza regułę określającą, można znaleźć w poniższym przykładzie. W tym przykładzie w języku Visual Basic Komentarze opisują sposób modyfikowania przykładu tak, aby spełniać reguły. Na przykład C# przykład poniżej pokazujący modyfikacji kodu.

[!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
[!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

Poniższy fragment kodu usuwa deklaracja delegata z poprzedniego przykładu, które spełniają reguły. Zastępuje on programy jej użycia w `ClassThatRaisesEvent` i `ClassThatHandlesEvent` metody przy użyciu <xref:System.EventHandler%601?displayProperty=fullName> delegować.

[!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1005: Unikaj nadużywania parametrów na typach generycznych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1000: Nie deklaruj składowych statycznych w typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Metody ogólne powinny podawać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1007: Używaj typów ogólnych wszędzie, gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz także

- [Typy ogólne](/dotnet/csharp/programming-guide/generics/index)