---
title: DA0023 — wysoki czas procesora (GC) | Microsoft Docs
description: Dane wydajności systemu zbierane podczas profilowania wskazują, że czas spędzony na wyrzucaniu elementów bezużytecznych jest znaczny w porównaniu z całkowitym czasem przetwarzania aplikacji.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0023
- vs.performance.23
- vs.performance.rules.DA0023
ms.assetid: aba875fe-9cbc-418d-a2c4-6eb47519a5bb
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: eccf44528b18d43a97a5a9c202c72b59abbdf431
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466081"
---
# <a name="da0023-high-gc-cpu-time"></a>DA0023: Duże zużycie czasu procesora przez odzyskiwanie pamięci

|Element|Wartość|
|-|-|
|Identyfikator reguły|DA0023|
|Kategoria|Użycie .NET Framework|
|Metoda profilowania|Wszystko|
|Komunikat|Czas trwania operacji odzyskiwania pamięci (%) jest stosunkowo wysoki. Ten wskaźnik nadmiernej ilości wyrzucania elementów bezużytecznych może mieć wpływ na czas odpowiedzi aplikacji. Można zebrać dane alokacji pamięci platformy .NET i informacje o okresie istnienia obiektu, aby zrozumieć wzorzec alokacji pamięci, która jest stosowana przez aplikację.|
|Typ reguły|Informacyjne|

 Podczas profilowania przy użyciu metod pobierania próbek, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="cause"></a>Przyczyna
 Dane wydajności systemu zbierane podczas profilowania wskazują, że czas spędzony na wyrzucaniu elementów bezużytecznych jest znaczny w porównaniu z całkowitym czasem przetwarzania aplikacji.

## <a name="rule-description"></a>Opis reguły
 Microsoft .NET Common Language Time (CLR) zapewnia automatyczny mechanizm zarządzania pamięcią, który używa modułu wyrzucania elementów bezużytecznych do odzyskiwania pamięci z obiektów, które nie są już używane przez aplikację. Moduł wyrzucania elementów bezużytecznych jest oparty na generacji, w oparciu o założenie, że wiele alokacji jest krótkoterminowych. Zmienne lokalne, na przykład, powinny być krótkotrwałe. Nowo utworzone obiekty rozpoczynają się w generacji 0 (Gen 0), a następnie postępować w generacji 1, gdy zajmują się uruchomieniem odzyskiwania pamięci, a wreszcie przechodzą do generacji 2, jeśli aplikacja nadal używa tych danych.

 Obiekty w generacji 0 są zbierane często i efektywnie. Obiekty w generacji 1 są zbierane rzadziej i mniej wydajne. Na koniec obiekty długotrwałe w generacji 2 powinny być zbierane nawet rzadziej. Kolekcja 2 generacji, która jest pełnym przebiegiem odzyskiwania pamięci, jest również najtańszą operacją.

 Ta reguła jest wyzwalana, gdy ilość czasu poświęcanego na wyrzucanie elementów bezużytecznych jest istotna w porównaniu z całkowitym czasem przetwarzania aplikacji.

> [!NOTE]
> Gdy czas spędzony na wyrzucaniu elementów bezużytecznych jest nadmiernie porównywany z całkowitym czasem przetwarzania aplikacji, [DA0024: nadmierne ostrzeżenie czasu procesora GC](../profiling/da0024-excessive-gc-cpu-time.md) wyzwalane zamiast tej reguły.

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczniki](../profiling/marks-view.md) danych profilowania. Znajdź **pamięć środowiska CLR \\ % Time w kolumnie GC** . Ustal, czy istnieją określone fazy wykonywania programu, w których narzuty wyrzucania elementów bezużytecznych pamięci zarządzanej są większe niż inne fazy. Porównaj wartości parametru% Time w usłudze GC z szybkością wyrzucania elementów bezużytecznych raportowaną w liczbie kolekcji **generacji 0**, kolekcjach **generacji 1**, liczbach **kolekcji generacji 2** .

 Wartość% Time w usłudze GC próbuje zgłosić ilość czasu, przez który aplikacja spędza wykonywanie wyrzucania elementów bezużytecznych proporcjonalnie do całkowitej ilości przetwarzania. Należy pamiętać, że w przypadku wartości% Time w usłudze GC można zgłosić wysoką wartość, ale nie jest to spowodowane nadmiernym wyrzucaniem elementów bezużytecznych. Aby uzyskać więcej informacji na temat sposobu, w jaki wartość% Time w ramach usługi GC jest obliczana, zobacz [różnicę między danymi wydajności zgłaszanymi przez różne narzędzia — 4 wprowadzanie danych](https://devblogs.microsoft.com/maoni/archive/difference-between-perf-data-reported-by-different-tools-4.aspx) **dziennika usługi Maoni** w witrynie MSDN. Jeśli wystąpią błędy stron lub aplikacja jest zastosowana przez inne zadania o wyższym priorytecie podczas wyrzucania elementów bezużytecznych, czas (%) w liczniku GC będzie odzwierciedlał te dodatkowe opóźnienia.
