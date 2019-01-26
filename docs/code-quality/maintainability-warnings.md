---
title: Utrzymanie — Ostrzeżenia
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57bb9e239fdc8272fbf01b45456edcde95503198
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965331"
---
# <a name="maintainability-warnings"></a>Utrzymanie — Ostrzeżenia

Ostrzeżenia dotyczące utrzymania obsługuje konserwacji biblioteki i aplikacji.

## <a name="in-this-section"></a>W tej sekcji

| Reguła | Opis |
|-----------|-----------------------------------|
| [CA1500: Nazwy zmiennych nie powinny odpowiadać nazwom pól](../code-quality/ca1500-variable-names-should-not-match-field-names.md) | Metoda wystąpienia deklaruje parametr lub zmienna lokalna, których nazwa pasuje do pola wystąpienia typu deklarującego, co prowadzi do błędów. |
| [CA1501: Unikaj nadmiernego dziedziczenia](../code-quality/ca1501-avoid-excessive-inheritance.md) | Typ jest głęboki na więcej niż cztery poziomy w hierarchii dziedziczenia. Hierarchie typów głęboko zagnieżdżonych mogą być trudne do śledzenia, zrozumienia i utrzymania. |
| [CA1502: Unikaj nadmiernej złożoności](../code-quality/ca1502-avoid-excessive-complexity.md) | Ta reguła mierzy liczbę liniowo niezależnych ścieżek za pośrednictwem metody, która jest określona przez liczbę i złożoność rozgałęzień warunkowych. |
| [CA1504: Przegląd mylących nazw pól](../code-quality/ca1504-review-misleading-field-names.md) | Nazwa pola wystąpienia zaczyna się od "s_" lub nazwa statycznego (udostępnionego w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) pola rozpoczyna się od "m_". |
| [CA1505: Unikaj kodu trudnego w utrzymaniu](../code-quality/ca1505-avoid-unmaintainable-code.md) | Typ lub metoda ma niską wartość indeksu konserwacji. Niski indeks konserwacji wskazuje, że typ lub metoda są prawdopodobnie trudne do utrzymania i są dobrymi kandydatami do przeprojektowania. |
| [CA1506: Unikaj nadmiernego sprzężenia klas](../code-quality/ca1506-avoid-excessive-class-coupling.md) | Ta reguła mierzy sprzęgnięcie klasy przez liczenie unikatowych odwołań typów, które zawiera typ lub metoda. |

## <a name="see-also"></a>Zobacz też

- [Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/code-metrics-values.md)