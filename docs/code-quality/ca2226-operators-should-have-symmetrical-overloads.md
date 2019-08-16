---
title: 'CA2226: Operatory powinny mieć symetryczne przeciążenia'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4557b61afab08c7db05c734c6f2ac927a40edb71
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546853"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: Operatory powinny mieć symetryczne przeciążenia

|||
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna

Typ implementuje operator równości lub nierówności, ale nie implementuje operatora przeciwnego.

Domyślnie ta reguła sprawdza tylko typy widoczne na zewnątrz, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Nie istnieją sytuacje, w których równość lub nierówność ma zastosowanie do wystąpień typu, a operator odwrotny jest niezdefiniowany. Typy zwykle implementują operator nierówności poprzez zwrócenie negacji wartości operatora równości.

C# Kompilator wystawia błąd w przypadku naruszeń tej reguły.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zaimplementować operatory równości i nierówności albo usunąć tę, która jest obecna.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły. Jeśli to zrobisz, typ nie będzie działał w sposób spójny z platformą .NET.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca2226.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (użycie). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Powiązane reguły

- [CA1046: Nie przeciążać operatora równości w typach referencyjnych](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2225: Przeciążenia operatorów mają nazwane alternatywy](../code-quality/ca2225-operator-overloads-have-named-alternates.md)
- [CA2224 Zastąp wartość Equals przy przeciążeniu operatora Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218 Zastąp GetHashCode przy zastępowaniu równości](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231 Operator przeciążenia jest równy przy przesłanianiu wartości ValueType. Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)