---
title: 'CA1000: Nie deklaruj statycznych składowych na typach ogólnych'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f10433330642ee06dd7f705cdd8e35333cd8a79d
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547924"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000: Nie deklaruj statycznych składowych na typach ogólnych

|||
|-|-|
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|
|CheckId|CA1000|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ ogólny zawiera `static` składową (`Shared` w Visual Basic).

Domyślnie ta reguła sprawdza tylko typy widoczne na zewnątrz, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Gdy jest wywoływana składowa typu ogólnego, argument typu musi być określony dla tego typu. `static` Po wywołaniu wystąpienia ogólnego elementu członkowskiego, które nie obsługuje wnioskowania, dla elementu członkowskiego musi zostać określony argument typu. Składnia służąca do określania argumentu Type w tych dwóch przypadkach jest różna i łatwa do pomylenia, ponieważ następujące wywołania demonstrują:

```vb
' Shared method in a generic type.
GenericType(Of Integer).SharedMethod()

' Generic instance method that does not support inference.
someObject.GenericMethod(Of Integer)()
```

```csharp
// Static method in a generic type.
GenericType<int>.StaticMethod();

// Generic instance method that does not support inference.
someObject.GenericMethod<int>();
```

Ogólnie rzecz biorąc, należy unikać obu wcześniejszych deklaracji, aby argument typu nie musiał być określony, gdy element członkowski jest wywoływany. Powoduje to składnię wywoływania elementów członkowskich w typach ogólnych, które nie różnią się od składni dla innych niż ogólne. Aby uzyskać więcej informacji, [Zobacz CA1004: Metody ogólne powinny podawać parametr](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)typu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Usuń statyczny element członkowski lub zmień go na element członkowski wystąpienia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły. Dostarczanie typów ogólnych w składni, która jest łatwa do zrozumienia i użycia, skraca czas wymagany do uczenia i zwiększania szybkości wdrażania nowych bibliotek.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1000.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Powiązane reguły

- [CA1005: Unikaj nadmiernego użycia parametrów w typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Metody ogólne powinny podawać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003: Użyj ogólnych wystąpień programu obsługi zdarzeń](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007 Używaj typów ogólnych, tam gdzie to konieczne](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz także

- [Typy ogólne](/dotnet/csharp/programming-guide/generics/index)