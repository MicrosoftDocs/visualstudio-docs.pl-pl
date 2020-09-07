---
title: Utrzymanie — Ostrzeżenia
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb985a6482b76b79604ce58f85e7f8cf3e83e97c
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509903"
---
# <a name="maintainability-warnings"></a>Ostrzeżenia dotyczące dostępności

Ostrzeżenia o utrzymaniu obsługują obsługę bibliotek i aplikacji.

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

## <a name="see-also"></a>Zobacz także

- [Mierzenie złożoności i łatwość utrzymania kodu zarządzanego](../code-quality/code-metrics-values.md)
