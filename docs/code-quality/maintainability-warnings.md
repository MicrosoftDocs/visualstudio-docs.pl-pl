---
title: Reguły utrzymania
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- rules, maintainability
- managed code analysis rules, maintainability rules
- maintainability rules
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 751cec177e066da1210997ef0f6f8d869ba7d0dc
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808587"
---
# <a name="maintainability-rules"></a>Reguły utrzymania

Reguły utrzymania obsługują konserwację biblioteki i aplikacji.

## <a name="in-this-section"></a>W tej sekcji

| Reguła | Opis |
|-----------|-----------------------------------|
| [CA1501: Unikaj nadmiernego dziedziczenia](../code-quality/ca1501.md) | Typ jest głęboki na więcej niż cztery poziomy w hierarchii dziedziczenia. Hierarchie typów głęboko zagnieżdżonych mogą być trudne do śledzenia, zrozumienia i utrzymania. |
| [CA1502: Unikaj nadmiernej złożoności](../code-quality/ca1502.md) | Ta reguła mierzy liczbę liniowo niezależnych ścieżek za pośrednictwem metody, która jest określona przez liczbę i złożoność rozgałęzień warunkowych. |
| [CA1505: Unikaj kodu trudnego w utrzymaniu](../code-quality/ca1505.md) | Typ lub metoda ma niską wartość indeksu konserwacji. Niski indeks konserwacji wskazuje, że typ lub metoda są prawdopodobnie trudne do utrzymania i są dobrymi kandydatami do przeprojektowania. |
| [CA1506: Unikaj nadmiernego sprzężenia klas](../code-quality/ca1506.md) | Ta reguła mierzy sprzęgnięcie klasy przez liczenie unikatowych odwołań typów, które zawiera typ lub metoda. |
| [CA1507: Użyj operatora nameof zamiast ciągu](../code-quality/ca1507.md) | Literał ciągu jest używany jako argument, w którym `nameof` można użyć wyrażenia. |
| [CA1508: Unikaj martwego kodu warunku](../code-quality/ca1508.md) | Metoda ma kod warunkowy, który zawsze jest obliczany `true` lub `false` w czasie wykonywania. Prowadzi to do nieaktywnego kodu w `false` gałęzi warunku. |
| [CA1509: Nieprawidłowy wpis w pliku konfiguracji metryk kodu](../code-quality/ca1509.md) | Reguły metryk kodu, takie jak [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) i [CA1506](ca1506.md), dostarczyły plik konfiguracji o nazwie `CodeMetricsConfig.txt` z nieprawidłowym wpisem. |

## <a name="see-also"></a>Zobacz też

- [Mierzenie złożoności i łatwość utrzymania kodu zarządzanego](../code-quality/code-metrics-values.md)
