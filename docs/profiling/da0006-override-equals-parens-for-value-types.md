---
title: 'DA0006: Zastępowanie equals() dla typów wartości | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9e097d6d8c9a7b82fac53fd37951644eb7eb5e59
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779535"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Przesłoń metodę equals typami wartości

|||
|-|-|
|Identyfikator reguły|DA0006|
|Kategoria|Użycie programu .NET Framework|
|Metody profiilingu|Próbkowanie|
|Komunikat|Zastądeń Equals i równości operatora na typy wartości.|
|Typ Messge|Ostrzeżenie|

## <a name="cause"></a>Przyczyna
 Wywołania Equals metody lub równości operatorów typu wartości publicznej są znaczną część danych profilowania. Należy rozważyć wdrożenie bardziej wydajnej metody.

## <a name="rule-description"></a>Opis reguły
 W przypadku typów wartości dziedziczona implementacja <xref:System.Reflection> Equals używa biblioteki i porównuje zawartość wszystkich pól w typie. Odbicie jest obliczeniowo kosztowne, a porównanie równości każdego pola może być niepotrzebne. Jeśli oczekujesz, że użytkownicy do porównania lub sortowania wystąpień lub używać ich jako klucze tabeli mieszania, typ wartości należy implementować Equals. Jeśli język programowania obsługuje przeciążenie operatora, należy również zapewnić implementację równości i nierówności operatorów.

 Aby uzyskać więcej informacji na temat zastępowania operatorów Equals i równości, zobacz [Wytyczne dotyczące implementowania równości i operatora równości (==)](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Na przykład implementowania Equals i równości operatorów, zobacz regułę analizy kodu [CA1815: Zastępowanie jest równe i operator jest równy typom wartości](../code-quality/ca1815.md)
