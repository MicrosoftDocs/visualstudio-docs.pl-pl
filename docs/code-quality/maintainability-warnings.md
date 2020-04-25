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
ms.openlocfilehash: fd7fe79665ac8de665116a6832d5ef9327fb356c
ms.sourcegitcommit: dab57cebd484228e6f0cf7ab1b9685c575410c06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/25/2020
ms.locfileid: "82152990"
---
# <a name="maintainability-warnings"></a>Ostrzeżenia dotyczące dostępności

Ostrzeżenia o utrzymaniu obsługują obsługę bibliotek i aplikacji.

## <a name="in-this-section"></a>W tej sekcji

| Reguła | Opis |
|-----------|-----------------------------------|
| [CA1500: Nazwy zmiennych nie powinny odpowiadać nazwom pól](../code-quality/ca1500.md) | Metoda wystąpienia deklaruje parametr lub zmienną lokalną, której nazwa pasuje do pola wystąpienia typu deklarującego, który prowadzi do błędów. |
| [CA1501: Unikaj nadmiernego dziedziczenia](../code-quality/ca1501.md) | Typ jest głęboki na więcej niż cztery poziomy w hierarchii dziedziczenia. Hierarchie typów głęboko zagnieżdżonych mogą być trudne do śledzenia, zrozumienia i utrzymania. |
| [CA1502: Unikaj nadmiernej złożoności](../code-quality/ca1502.md) | Ta reguła mierzy liczbę liniowo niezależnych ścieżek za pośrednictwem metody, która jest określona przez liczbę i złożoność rozgałęzień warunkowych. |
| [CA1504: Przejrzyj mylące nazwy pól](../code-quality/ca1504.md) | Nazwa pola wystąpienia rozpoczyna się od "s_" lub nazwa statycznego pola (udostępnionego w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) rozpoczyna się od "m_". |
| [CA1505: Unikaj kodu niemożliwego w utrzymaniu](../code-quality/ca1505.md) | Typ lub metoda ma niską wartość indeksu konserwacji. Niski indeks konserwacji wskazuje, że typ lub metoda są prawdopodobnie trudne do utrzymania i są dobrymi kandydatami do przeprojektowania. |
| [CA1506: Unikaj nadmiernego sprzężenia klas](../code-quality/ca1506.md) | Ta reguła mierzy sprzęgnięcie klasy przez liczenie unikatowych odwołań typów, które zawiera typ lub metoda. |
| [CA1507: Użyj nameof zamiast ciągu](../code-quality/ca1507.md) | Literał ciągu jest używany jako argument, w którym można `nameof` użyć wyrażenia. |
| [CA1508: Unikaj nieaktywnego kodu warunkowego](../code-quality/ca1508.md) | Metoda ma kod warunkowy, który zawsze jest `true` obliczany `false` lub w czasie wykonywania. Prowadzi to do nieaktywnego kodu `false` w gałęzi warunku. |

## <a name="see-also"></a>Zobacz też

- [Mierzenie złożoności i łatwość utrzymania kodu zarządzanego](../code-quality/code-metrics-values.md)
