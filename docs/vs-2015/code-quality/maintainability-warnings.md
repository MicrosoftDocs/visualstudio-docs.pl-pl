---
title: Ostrzeżenia o utrzymaniu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e448a72e2ff92b3e3028829d4b1e7658c304ee3c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667896"
---
# <a name="maintainability-warnings"></a>Utrzymanie — Ostrzeżenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ostrzeżenia o utrzymaniu obsługują obsługę bibliotek i aplikacji.

## <a name="in-this-section"></a>W tej sekcji

|Reguła|Opis|
|----------|-----------------|
|[CA1500: Nazwy zmiennych nie powinny odpowiadać nazwom pól](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Metoda wystąpienia deklaruje parametr lub zmienną lokalną, której nazwa pasuje do pola wystąpienia typu deklarującego, który prowadzi do błędów.|
|[CA1501: Unikaj nadmiernego dziedziczenia](../code-quality/ca1501-avoid-excessive-inheritance.md)|Typ jest głęboki na więcej niż cztery poziomy w hierarchii dziedziczenia. Hierarchie typów głęboko zagnieżdżonych mogą być trudne do śledzenia, zrozumienia i utrzymania.|
|[CA1502: Unikaj nadmiernej złożoności](../code-quality/ca1502-avoid-excessive-complexity.md)|Ta reguła mierzy liczbę liniowo niezależnych ścieżek za pośrednictwem metody, która jest określona przez liczbę i złożoność rozgałęzień warunkowych.|
|[CA1504: Przejrzyj mylące nazwy pól](../code-quality/ca1504-review-misleading-field-names.md)|Nazwa pola wystąpienia zaczyna się od "s_" lub nazwa statycznego pola udostępnionego w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) rozpoczyna się od "m_".|
|[CA1505: Unikaj kodu trudnego w utrzymaniu](../code-quality/ca1505-avoid-unmaintainable-code.md)|Typ lub metoda ma niską wartość indeksu konserwacji. Niski indeks konserwacji wskazuje, że typ lub metoda są prawdopodobnie trudne do utrzymania i są dobrymi kandydatami do przeprojektowania.|
|[CA1506: Unikaj nadmiernego sprzężenia klas](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Ta reguła mierzy sprzęgnięcie klasy przez liczenie unikatowych odwołań typów, które zawiera typ lub metoda.|

## <a name="see-also"></a>Zobacz też
 [Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
