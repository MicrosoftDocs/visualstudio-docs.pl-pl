---
title: Reguły wydajności użycia programu .NET Framework | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ab573755-6370-48aa-853d-a7321c424c79
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5a740885d8876398bf86e279aa259e9169fcf7c2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779290"
---
# <a name="net-framework-usage-performance-rules"></a>Reguły wydajności dotyczące użycia programu .NET Framework
Reguły wydajności w the.NET framework Kategoria użycia zidentyfikować określone metody, które można zoptymalizować, a także zidentyfikować bardziej ogólne wzorce użycia, takie jak wyrzucanie elementów bezużytecznych i rywalizacji blokady, które mogą być badane pod kątem problemów z wydajnością.

|||
|-|-|
|[DA0001: Użyj klasy StringBuilder do konkatenacji](../profiling/da0001-use-stringbuilder-for-concatenations.md)|Wywołania <xref:System.String.Concat(System.String,System.String)?displayProperty=fullName> są znaczną częścią danych profilowania. Należy rozważyć <xref:System.Text.StringBuilder> użycie klasy do konstruowania ciągów z wielu segmentów.|
|[DA0005: Częste kolekcje GC2](../profiling/da0005-frequent-gc2-collections.md)|Stosunkowo duża liczba obiektów pamięci .NET są odzyskiwane w generacji 2 wyrzucania elementów bezużytecznych. Jeśli zbyt wiele obiektów krótkotrwałe przetrwać generacji 1 kolekcji, koszt zarządzania pamięcią może łatwo stać się nadmierne.|
|[DA0006: Przesłoń metodę equals typami wartości](../profiling/da0006-override-equals-parens-for-value-types.md)|Wywołania `Equals` metody lub operatorów równości typu wartości publicznej są znaczną częścią danych profilowania. Należy rozważyć wdrożenie bardziej wydajnej metody.|
|[DA0007: Unikaj używania wyjątków do przepływu sterowania](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|Wysoki wskaźnik .NET Framework obsługi wyjątków zostały wywołane w danych profilowania. Należy rozważyć użycie innych logiki przepływu sterowania, aby zmniejszyć liczbę wyjątków, które są generowane.|
|[DA0010: Kosztowna funkcja GetHashCode](../profiling/da0010-expensive-gethashcode.md)|Wywołania `GetHashCode` metody typu są znaczną część danych profilowania `GetHashCode` lub metoda przydziela pamięci. Zmniejsz złożoność metody.|
|[DA0011: Kosztowna funkcja CompareTo](../profiling/da0011-expensive-compareto.md)|Metoda `CompareTo` typu jest kosztowne lub metoda przydziela pamięci. Zmniejsz złożoność `CompareTo` metody.|
|[DA0012: Znaczne odbicie](../profiling/da0012-significant-amount-of-reflection.md)|Wywołania <xref:System.Reflection?displayProperty=fullName> metod, <xref:System.Reflection.IReflect.InvokeMember%2A> takich <xref:System.Reflection.IReflect.GetMember%2A> jak i lub <xref:System.Type.InvokeMember%2A> typ metody, takie jak są znaczną część danych profilowania. Jeśli to możliwe, należy rozważyć zastąpienie tych metod wczesnym wiązaniem z metodami zestawów zależnych.|
|[DA0013: Znaczące wykorzystanie funkcji String.Split i String.Substring](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|Wywołania <xref:System.String.Split%2A?displayProperty=fullName> lub <xref:System.String.Substring%2A> metody są znaczną część danych profilowania. Należy <xref:System.String.IndexOf%2A> rozważyć <xref:System.String.IndexOfAny%2A> użycie lub jeśli testujesz podciąg w ciągu.|
|[DA0018: aplikacja 32-bitowa działająca w limitach pamięci zarządzanych przez proces](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|Dane systemowe, które są zbierane podczas wykonywania profilowania wskazuje .NET Framework sterty pamięci zbliżył maksymalny rozmiar, który zarządzanych stert może osiągnąć w procesie 32-bitowym. Rozważ profilowanie ponownie przy użyciu metody profilowania pamięci .NET i optymalizacji użycia zasobów zarządzanych przez aplikację.|
|[DA0021: Duża częstotliwość odzyskiwania pamięci generacji 1](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|Stosunkowo duża liczba obiektów pamięci .NET są odzyskiwane w generacji 1 wyrzucania elementów bezużytecznych. Jeśli zbyt wiele obiektów krótkotrwałe przetrwać generacji 0 kolekcji, koszt zarządzania pamięcią może łatwo stać się nadmierne.|
|[DA0022: Wysoki stopień wyrzucania elementów bezużytecznych Gen 2](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|Duża liczba obiektów pamięci .NET są odzyskiwane w generacji 2 wyrzucania elementów bezużytecznych. Jeśli zbyt wiele obiektów krótkotrwałe przetrwać generacji 1 kolekcji, koszt zarządzania pamięcią może łatwo stać się nadmierne. Ta reguła jest uruchamiana, gdy szybkość rywalizacji o blokadę przekracza górną wartość progową reguły DA0005.|
|[DA0023: Wysokie wykorzystanie czasu GC CPU](../profiling/da0023-high-gc-cpu-time.md)|Dane wydajności systemu, który jest zbierany podczas profilowania wskazuje, że ilość czasu spędzonego w wyrzucaniu elementów bezużytecznych jest znacząca w porównaniu z całkowitym czasem przetwarzania aplikacji.|
|[DA0024: Nadmierny czas procesora GC](../profiling/da0024-excessive-gc-cpu-time.md)|Dane wydajności systemu, który jest zbierany podczas profilowania wskazuje, że ilość czasu spędzonego w wyrzucaniu elementów bezużytecznych jest zbyt wysoka w porównaniu z całkowitym czasem przetwarzania aplikacji. Ta reguła jest uruchamiana, gdy czas spędzony w wyrzucaniu elementów bezużytecznych przekracza górną wartość progową reguły DA0023.|
|[DA0038: Wysoki wskaźnik rywalizacji o blokadę](../profiling/da0038-high-rate-of-lock-contentions.md)|Dane wydajności systemu, które są zbierane z danymi profilowania wskazuje, że znacznie wysoki wskaźnik rywalizacji blokady wystąpił podczas wykonywania aplikacji. Należy rozważyć profilowanie ponownie przy użyciu metody profilowania współbieżności, aby znaleźć przyczynę rywalizacji.|
|[DA0039: Bardzo wysoki wskaźnik rywalizacji o blokadę](../profiling/da0039-very-high-rate-of-lock-contentions.md)|Dane wydajności systemu, które są zbierane z danymi profilowania wskazuje, że zbyt wysoki wskaźnik rywalizacji blokady wystąpił podczas wykonywania aplikacji. Należy rozważyć profilowanie ponownie przy użyciu metody profilowania współbieżności, aby znaleźć przyczynę rywalizacji. Ta reguła jest uruchamiana, gdy szybkość rywalizacji o blokadę przekracza górną wartość progową reguły DA0038.|
