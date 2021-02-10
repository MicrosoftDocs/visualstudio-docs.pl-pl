---
title: Reguły wydajności .NET Framework użycia | Microsoft Docs
description: Informacje o regułach wydajności w kategorii użycie .NET Framework. Zidentyfikuj konkretne metody, które można zoptymalizować i zidentyfikować bardziej ogólne wzorce użycia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ab573755-6370-48aa-853d-a7321c424c79
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f8ec2756353ac56b3b5d44e2a50c4d4f5b1c7ebf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955388"
---
# <a name="net-framework-usage-performance-rules"></a>Reguły wydajności dotyczące użycia programu .NET Framework
Reguły wydajności w kategorii użycie programu the.NET Framework identyfikują konkretne metody, które mogą być optymalizowane, a także identyfikować bardziej ogólne wzorce użycia, takie jak odzyskiwanie pamięci i rywalizacja o blokady, które mogą być zbadane pod kątem problemów z wydajnością.

|Reguła|Opis|
|-|-|
|[DA0001: Użyj klasy StringBuilder do konkatenacji](../profiling/da0001-use-stringbuilder-for-concatenations.md)|Wywołania <xref:System.String.Concat(System.String,System.String)?displayProperty=fullName> są znaczną częścią danych profilowania. Rozważ użycie <xref:System.Text.StringBuilder> klasy do konstruowania ciągów z wielu segmentów.|
|[DA0005: Częste odzyskiwanie pamięci GC2](../profiling/da0005-frequent-gc2-collections.md)|W wyrzucaniu elementów bezużytecznych generacji 2 jest odzyskiwana stosunkowo duża liczba obiektów pamięci platformy .NET. Jeśli zbyt wiele niestabilnych obiektów jest w trakcie tworzenia kolekcji 1, koszty zarządzania pamięcią mogą być łatwo nadmiernie zawyżone.|
|[DA0006: Przesłoń metodę Equals() dla typów wartości](../profiling/da0006-override-equals-parens-for-value-types.md)|Wywołania `Equals` metody lub operatory równości typu wartości publicznej są znaczną częścią danych profilowania. Rozważ zaimplementowanie bardziej wydajnej metody.|
|[DA0007: Unikaj używania wyjątków w przepływie sterowania](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|W danych profilowania wywołano wysoką częstotliwość obsługi wyjątków .NET Framework. Rozważ użycie innej logiki przepływu sterowania, aby zmniejszyć liczbę zgłaszanych wyjątków.|
|[DA0010: Kosztowna funkcja GetHashCode](../profiling/da0010-expensive-gethashcode.md)|Wywołania `GetHashCode` metody typu są znaczną częścią danych profilowania lub `GetHashCode` metoda przydziela pamięć. Zmniejsz złożoność metody.|
|[DA0011: Kosztowna funkcja CompareTo](../profiling/da0011-expensive-compareto.md)|`CompareTo`Metoda typu jest kosztowna lub metoda przydziela pamięć. Zmniejsz złożoność `CompareTo` metody.|
|[DA0012: Znaczne odbicie](../profiling/da0012-significant-amount-of-reflection.md)|Wywołania <xref:System.Reflection?displayProperty=fullName> metod takich jak <xref:System.Reflection.IReflect.InvokeMember%2A> i <xref:System.Reflection.IReflect.GetMember%2A> lub do typu metody, takie jak, <xref:System.Type.InvokeMember%2A> są znaczną częścią danych profilowania. Jeśli to możliwe, rozważ zastąpienie tych metod wczesnym wiązaniem do metod zestawów zależnych.|
|[DA0013: Znaczące wykorzystanie funkcji String.Split i String.Substring](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|Wywołania <xref:System.String.Split%2A?displayProperty=fullName> lub <xref:System.String.Substring%2A> metody są znaczną częścią danych profilowania. Rozważ użycie <xref:System.String.IndexOf%2A> lub <xref:System.String.IndexOfAny%2A> , jeśli testujesz obecność podciągu w ciągu.|
|[DA0018: Działająca aplikacja 32-bitowa zbliżyła się do limitu pamięci zarządzanej dla procesu](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|Dane systemowe zbierane podczas przebiegu profilowania wskazują, że sterty pamięci .NET Framework zbliżają się do maksymalnego rozmiaru sterty zarządzanej w procesie 32-bitowym. Rozważ ponowne przeprowadzenie profilowania przy użyciu metody profilowania pamięci platformy .NET i zoptymalizowanie użycia zasobów zarządzanych przez aplikację.|
|[DA0021: Duża częstotliwość odzyskiwania pamięci 1. generacji](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|W wyrzucaniu elementów bezużytecznych generacji 1 jest odzyskiwana stosunkowo duża liczba obiektów pamięci platformy .NET. Jeśli zbyt wiele nietrwałych obiektów jest w trakcie zbierania 0, koszty zarządzania pamięcią mogą być łatwo nadmierne.|
|[DA0022: Duża częstotliwość odzyskiwania pamięci 2. generacji](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|W wyrzucaniu elementów bezużytecznych generacji 2 są odzyskiwane duże ilości obiektów pamięci platformy .NET. Jeśli zbyt wiele niestabilnych obiektów jest w trakcie tworzenia kolekcji 1, koszty zarządzania pamięcią mogą być łatwo nadmiernie zawyżone. Ta zasada jest wyzwalana, gdy współczynnik rywalizacji o blokadę przekracza górną wartość progową reguły DA0005.|
|[DA0023: Duże zużycie czasu procesora przez odzyskiwanie pamięci](../profiling/da0023-high-gc-cpu-time.md)|Dane wydajności systemu zbierane podczas profilowania wskazują, że czas spędzony na wyrzucaniu elementów bezużytecznych jest znaczny w porównaniu z całkowitym czasem przetwarzania aplikacji.|
|[DA0024: nadmierny czas procesora operacji GC](../profiling/da0024-excessive-gc-cpu-time.md)|Dane wydajności systemu zbierane podczas profilowania wskazują, że czas spędzony na wyrzucaniu elementów bezużytecznych jest zbyt duży w porównaniu z całkowitym czasem przetwarzania aplikacji. Ta reguła jest wyzwalana, gdy ilość czasu poświęcanego na wyrzucanie elementów bezużytecznych przekracza górną wartość progową reguły DA0023.|
|[DA0038: wysoki współczynnik rywalizacji o blokadę](../profiling/da0038-high-rate-of-lock-contentions.md)|Dane wydajności systemu zbierane z danymi profilowania wskazują, że podczas wykonywania aplikacji wystąpiła znacznie duża liczba rywalizacji blokad. Rozważ ponowne przeprowadzenie profilowania przy użyciu metody profilowania współbieżności, aby znaleźć przyczynę rywalizacji.|
|[DA0039: bardzo wysoki współczynnik rywalizacji o blokadę](../profiling/da0039-very-high-rate-of-lock-contentions.md)|Dane wydajności systemu zbierane z danymi profilowania wskazują, że zbyt wysoka liczba rywalizacji blokad podczas wykonywania aplikacji. Rozważ ponowne przeprowadzenie profilowania przy użyciu metody profilowania współbieżności, aby znaleźć przyczynę rywalizacji. Ta zasada jest wyzwalana, gdy współczynnik rywalizacji o blokadę przekracza górną wartość progową reguły DA0038.|
