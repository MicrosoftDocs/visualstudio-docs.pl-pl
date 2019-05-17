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
ms.openlocfilehash: 73f11638d8ba5ca373c8fb1479be8d862e62b247
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841407"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: Operatory powinny mieć symetryczne przeciążenia

|||
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Typ implementuje operator równości lub nierówności, ale nie implementuje operatora przeciwnego.

Domyślnie ta reguła przegląda tylko typy widoczne na zewnątrz, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

Nie ma żadnych okoliczności gdzie równości i nierówności ma zastosowanie do wystąpień typu i operatora przeciwnego jest niezdefiniowana. Typy zwykle implementuje operator nierówności, zwracając zanegowaną wartość operatora równości.

Kompilator języka C# generuje błąd dla naruszenie tej zasady.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, implementują równości i nierówności operatorów lub Usuń ten, który jest obecny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły. Jeśli to zrobisz, nie będzie działać w sposób, który jest zgodny z platformą .NET danego typu.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```ini
dotnet_code_quality.ca2226.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (użycie). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Powiązane reguły

- [CA1046: Nie przeciążaj operatora równości w typach referencyjnych](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2225: Operator overloads ma nazwanych zastępców](../code-quality/ca2225-operator-overloads-have-named-alternates.md)
- [CA2224: Przesłoń metodę equals, przeciążając operator equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218: Przesłaniaj metodę GetHashCode w przesłaniania metody Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231: Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)