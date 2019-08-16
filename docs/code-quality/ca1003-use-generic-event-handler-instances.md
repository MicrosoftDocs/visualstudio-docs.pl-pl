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
ms.openlocfilehash: a1ef4258d1b095395be34c7004e3f783b973897d
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547880"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Użyj ogólnych wystąpień procedury obsługi zdarzeń

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ zawiera delegata zwracającego wartość void i którego sygnatura zawiera dwa parametry (pierwszy obiekt i drugi typ, który można przypisać do EventArgs), i zawierający element docelowy zestawu platformy .NET.

Domyślnie ta reguła sprawdza tylko typy widoczne na zewnątrz, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Przed platformą .NET w celu przekazania informacji niestandardowych do programu obsługi zdarzeń należy zadeklarować nowego delegata, który określił klasę pochodną <xref:System.EventArgs?displayProperty=fullName> klasy. W programie .NET generyczny <xref:System.EventHandler%601?displayProperty=fullName> delegat zezwala każdej klasie, która jest <xref:System.EventArgs> pochodną do użycia razem z programem obsługi zdarzeń.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, Usuń delegata i Zastąp jego użycie za pomocą <xref:System.EventHandler%601?displayProperty=fullName> delegata.

Jeśli delegat jest automatycznie generowany przez kompilator Visual Basic, Zmień składnię deklaracji zdarzenia, aby użyć <xref:System.EventHandler%601?displayProperty=fullName> delegata.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1003.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje delegata, który narusza regułę. W Visual Basic przykładzie komentarze opisują sposób modyfikacji przykładu w celu spełnienia reguły. C# Przykładem jest Poniższy przykład, który pokazuje zmodyfikowany kod.

[!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
[!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

Poniższy fragment kodu usuwa deklarację delegata z poprzedniego przykładu, która spełnia kryteria. Zastępuje ich użycie w `ClassThatRaisesEvent` metodach i `ClassThatHandlesEvent` za pomocą <xref:System.EventHandler%601?displayProperty=fullName> delegata.

[!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1005: Unikaj nadmiernego użycia parametrów w typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1000: Nie deklaruj statycznych składowych na typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Metody ogólne powinny podawać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1007 Używaj typów ogólnych, tam gdzie to konieczne](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz także

- [Typy ogólne](/dotnet/csharp/programming-guide/generics/index)