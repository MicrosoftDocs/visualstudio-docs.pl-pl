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
ms.openlocfilehash: 5dad282bfc1c539216b55e41d77d7743808311d6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587371"
---
# <a name="maintainability-warnings"></a>Ostrzeżenia dotyczące dostępności

Ostrzeżenia o utrzymaniu obsługują obsługę bibliotek i aplikacji.

## <a name="in-this-section"></a>W tej sekcji

| Reguła | Opis |
|-----------|-----------------------------------|
| [CA1500: Nazwy zmiennych nie powinny odpowiadać nazwom pól](../code-quality/ca1500.md) | Metoda wystąpienia deklaruje parametr lub zmienną lokalną, której nazwa pasuje do pola wystąpienia typu deklarującego, który prowadzi do błędów. |
| [CA1501: Unikaj nadmiernego dziedziczenia](../code-quality/ca1501.md) | Typ jest głęboki na więcej niż cztery poziomy w hierarchii dziedziczenia. Hierarchie typów głęboko zagnieżdżonych mogą być trudne do śledzenia, zrozumienia i utrzymania. |
| [CA1502: Unikaj nadmiernej złożoności](../code-quality/ca1502.md) | Ta reguła mierzy liczbę liniowo niezależnych ścieżek za pośrednictwem metody, która jest określona przez liczbę i złożoność rozgałęzień warunkowych. |
| [CA1504: Przejrzyj mylące nazwy pól](../code-quality/ca1504.md) | Nazwa pola wystąpienia rozpoczyna się od "s_" lub nazwa pola statycznego (udostępnionego w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) rozpoczyna się od "m_". |
| [CA1505: Unikaj kodu trudnego w utrzymaniu](../code-quality/ca1505.md) | Typ lub metoda ma niską wartość indeksu konserwacji. Niski indeks konserwacji wskazuje, że typ lub metoda są prawdopodobnie trudne do utrzymania i są dobrymi kandydatami do przeprojektowania. |
| [CA1506: Unikaj nadmiernego sprzężenia klas](../code-quality/ca1506.md) | Ta reguła mierzy sprzęgnięcie klasy przez liczenie unikatowych odwołań typów, które zawiera typ lub metoda. |
| [CA1507: Użyj nameof zamiast ciągu](../code-quality/ca1507.md) | Literał ciągu jest używany jako argument, w którym można użyć wyrażenia `nameof`. |

## <a name="see-also"></a>Zobacz także

- [Mierzenie złożoności i łatwość utrzymania kodu zarządzanego](../code-quality/code-metrics-values.md)
