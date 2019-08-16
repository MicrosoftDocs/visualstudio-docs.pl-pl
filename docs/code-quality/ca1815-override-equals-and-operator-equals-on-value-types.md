---
title: 'CA1815: Przesłaniaj metodę equals i operator równości w typach wartości'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97f56e406d00de1891647c4211d21336f9d1a266
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547047"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: Przesłaniaj metodę equals i operator równości w typach wartości

|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Typ wartości nie przesłania <xref:System.Object.Equals%2A?displayProperty=fullName> lub nie implementuje operatora równości (= =). Ta reguła nie sprawdza wyliczeń.

Domyślnie ta reguła sprawdza tylko typy widoczne na zewnątrz, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

W przypadku typów wartości dziedziczona implementacja programu <xref:System.Object.Equals%2A> używa biblioteki odbicia i porównuje zawartość wszystkich pól. Odbicie jest obliczeniowo kosztowne, a porównanie równości każdego pola może być niepotrzebne. Jeśli oczekujesz, że użytkownicy porównują lub sortują wystąpienia lub używają ich jako kluczy tabeli skrótów, należy zaimplementować <xref:System.Object.Equals%2A>typ wartości. Jeśli język programowania obsługuje przeciążanie operatora, należy również podać implementację operatorów równości i nierówności.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy wprowadzić implementację programu <xref:System.Object.Equals%2A>. Jeśli jest to możliwe, zaimplementuj operator równości.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli wystąpienia typu wartości nie będą porównywane ze sobą, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1815.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (wydajność). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

Poniższy kod przedstawia strukturę (typ wartości), która narusza tę regułę:

[!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]

Poniższy kod naprawia poprzednie naruszenie, zastępując <xref:System.ValueType.Equals%2A?displayProperty=fullName> i implementując operatory równości (= =,! =):

[!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]

## <a name="related-rules"></a>Powiązane reguły

- [CA2224 Zastąp wartość Equals przy przeciążeniu operatora Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2231 Operator przeciążenia jest równy przy przesłanianiu wartości ValueType. Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
- [CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Object.Equals%2A?displayProperty=fullName>