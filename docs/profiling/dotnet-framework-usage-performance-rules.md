---
title: Reguły wydajności dotyczące użycia platformy .NET framework | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ab573755-6370-48aa-853d-a7321c424c79
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bf47871b8b1c2e6f8e4f67bf26ba5f73ca078c7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56625377"
---
# <a name="net-framework-usage-performance-rules"></a>Reguły wydajności dotyczące użycia programu .NET Framework
Reguły wydajności w.NET Framework użycia kategorii zidentyfikować konkretnych metod, które mogą być optymalizowane, a także identyfikują bardziej ogólnych wzorce użycia, takie jak wyrzucanie elementów bezużytecznych i Rywalizacja o blokady, które mogą zostać sprawdzone pod kątem problemów z wydajnością.

|||
|-|-|
|[DA0001: Użyj klasy StringBuilder do konkatenacji](../profiling/da0001-use-stringbuilder-for-concatenations.md)|Wywołania <xref:System.String.Concat(System.String,System.String)?displayProperty=fullName> jest znaczna część danych profilowania. Należy rozważyć użycie <xref:System.Text.StringBuilder> klasy w celu tworzenia ciągów z wielu segmentów.|
|[DA0005: Częste odzyskiwanie pamięci GC2](../profiling/da0005-frequent-gc2-collections.md)|Stosunkowo dużą liczbę obiektów pamięci platformy .NET są są odzyskiwane w generacji 2 wyrzucania elementów bezużytecznych. Jeśli zbyt wiele obiektów tymczasowych przetrwać bezużytecznych generacji 1, koszty zarządzania pamięci mogą łatwo stać się nadmierne.|
|[DA0006: Przesłoń metodę Equals() dla typów wartości](../profiling/da0006-override-equals-parens-for-value-types.md)|Wywołania `Equals` metody lub operatory równości typu publicznego wartości są znaczna część danych profilowania. Rozważ zaimplementowanie bardziej efektywną metodę.|
|[DA0007: Unikaj używania wyjątków w przepływie sterowania](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|Wysoki współczynnik obsługi wyjątków w .NET Framework zostały wywołane w danych profilowania. Należy rozważyć użycie inną logikę przepływu sterowania w celu zmniejszenia liczby wyjątków, które są generowane.|
|[DA0010: Kosztowna funkcja GetHashCode](../profiling/da0010-expensive-gethashcode.md)|Wywołania `GetHashCode` metodę typu jest znaczna część danych profilowania lub `GetHashCode` metoda przydziela pamięć. Zmniejsz złożoność metody.|
|[DA0011: Kosztowna funkcja CompareTo](../profiling/da0011-expensive-compareto.md)|`CompareTo` Metodę typu jest kosztowne lub metoda przydziela pamięć. Zmniejsz złożoność `CompareTo` metody.|
|[DA0012: Znaczne odbicie](../profiling/da0012-significant-amount-of-reflection.md)|Wywołania <xref:System.Reflection?displayProperty=fullName> metody takie jak <xref:System.Reflection.IReflect.InvokeMember%2A> i <xref:System.Reflection.IReflect.GetMember%2A> lub typ metody takie jak <xref:System.Type.InvokeMember%2A> jest znaczna część danych profilowania. Jeśli to możliwe, należy wziąć pod uwagę zastąpienie tych metod wczesne powiązania do metod zestawów zależnych.|
|[DA0013: Znaczące wykorzystanie funkcji String.Split i String.Substring](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|Wywołania <xref:System.String.Split%2A?displayProperty=fullName> lub <xref:System.String.Substring%2A> metody są znaczna część danych profilowania. Należy rozważyć użycie <xref:System.String.IndexOf%2A> lub <xref:System.String.IndexOfAny%2A> Jeśli testujesz istnienie podciągów w ciągu.|
|[DA0018: Aplikacja 32-bitowa działa w granicach pamięci zarządzanej dla procesu](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|Dane systemowe, zebrane podczas uruchomienia profilowania wskazuje, że pamięci .NET Framework stosów skontaktowali maksymalnego rozmiaru sterty zarządzanej może nawiązać połączenie w procesie 32-bitowym. Należy wziąć pod uwagę, profilowanie ponownie przy użyciu metody profilowania pamięci .NET i optymalizację użycia zasobów zarządzanych przez aplikację.|
|[DA0021: Duża częstotliwość odzyskiwania pamięci 1. generacji](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|Stosunkowo dużą liczbę obiektów pamięci platformy .NET są są odzyskiwane w generację 1 wyrzucania elementów bezużytecznych. Jeśli zbyt wiele obiektów tymczasowych przetrwać bezużytecznych generacji 0, koszty zarządzania pamięci mogą łatwo stać się nadmierne.|
|[DA0022: Duża częstotliwość odzyskiwania pamięci 2. generacji](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|Dużą liczbę obiektów pamięci platformy .NET są są odzyskiwane w generacji 2 wyrzucania elementów bezużytecznych. Jeśli zbyt wiele obiektów tymczasowych przetrwać bezużytecznych generacji 1, koszty zarządzania pamięci mogą łatwo stać się nadmierne. Ta reguła jest uruchamiana, gdy liczba rywalizacji blokad przekracza górna wartość progowa reguły DA0005.|
|[DA0023: Duże zużycie czasu procesora przez odzyskiwanie pamięci](../profiling/da0023-high-gc-cpu-time.md)|Dane o wydajności systemu, które są zbierane podczas profilowania wskazuje, że ilość czasu spędzonego w wyrzucania elementów bezużytecznych jest istotne w porównaniu z czasem przetwarzania kompletnej aplikacji.|
|[DA0024: Nadmierne zużycie czasu procesora CPU](../profiling/da0024-excessive-gc-cpu-time.md)|Dane o wydajności systemu, które są zbierane podczas profilowania wskazuje, że ilość czasu spędzonego w wyrzucania elementów bezużytecznych jest zbyt wysoka w porównaniu z czasem przetwarzania kompletnej aplikacji. Ta reguła jest uruchamiana, gdy czas poświęcony na wyrzucanie elementów bezużytecznych przekracza górna wartość progowa reguły DA0023.|
|[DA0038: Wysoki współczynnik rywalizacji blokad](../profiling/da0038-high-rate-of-lock-contentions.md)|Dane wydajności systemu, które są zbierane przy użyciu danych profilowania wskazuje znacznie wysoka liczba rywalizacji blokad, które wystąpiły podczas wykonywania aplikacji. Należy wziąć pod uwagę, profilowanie, aby znaleźć przyczynę rywalizacji ponownie, używając metoda profilowania współbieżności.|
|[DA0039: Bardzo wysoka liczba rywalizacji blokad](../profiling/da0039-very-high-rate-of-lock-contentions.md)|Dane wydajności systemu, które są zbierane przy użyciu danych profilowania wskazuje zbyt wysoka liczba rywalizacji blokad, które wystąpiły podczas wykonywania aplikacji. Należy wziąć pod uwagę, profilowanie, aby znaleźć przyczynę rywalizacji ponownie, używając metoda profilowania współbieżności. Ta reguła jest uruchamiana, gdy liczba rywalizacji blokad przekracza górna wartość progowa reguły DA0038.|