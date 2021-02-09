---
title: DA0024 — nadmierny czas procesora GC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0024
- vs.performance.24
- vs.performance.rules.DA0024
ms.assetid: 228872da-77d0-4da5-b455-ac57fb1867c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 28b9f5af736e07d6e61d3c175b13202c54a4d0d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847872"
---
# <a name="da0024-excessive-gc-cpu-time"></a>DA0024: nadmierny czas procesora operacji GC

|Element|Wartość|
|-|-|
|Identyfikator reguły|DA0024|
|Kategoria|Użycie .NET Framework|
|Metoda profilowania|Wszystko|
|Komunikat|Czas trwania operacji odzyskiwania pamięci (%) jest bardzo wysoki. Występuje nadmierna ilość wyrzucania elementów bezużytecznych.|
|Typ reguły|Ostrzeżenie|

 Podczas profilowania przy użyciu metod pobierania próbek, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="cause"></a>Przyczyna
 Dane wydajności systemu zebrane podczas profilowania wskazują, że czas spędzony na wyrzucaniu elementów bezużytecznych jest zbyt duży w porównaniu z całkowitym czasem przetwarzania aplikacji.

## <a name="rule-description"></a>Opis reguły
 Microsoft .NET Common Language Time (CLR) zapewnia automatyczny mechanizm zarządzania pamięcią, który używa modułu wyrzucania elementów bezużytecznych do odzyskiwania pamięci z obiektów, które nie są już używane przez aplikację. Moduł wyrzucania elementów bezużytecznych jest oparty na generacji, w oparciu o założenie, że wiele alokacji jest krótkoterminowych. Zmienne lokalne, na przykład, powinny być krótkotrwałe. Nowo utworzone obiekty rozpoczynają się w generacji 0 (Gen 0), a następnie postępować w generacji 1, gdy zajmują się uruchomieniem odzyskiwania pamięci, a wreszcie przechodzą do generacji 2, jeśli aplikacja nadal używa tych danych.

 Obiekty w generacji 0 są zbierane często i zwykle bardzo wydajnie. Obiekty w generacji 1 są zbierane rzadziej i mniej wydajne. Na koniec obiekty długotrwałe w generacji 2 powinny być zbierane nawet rzadziej. Kolekcja 2 generacji, która jest pełnym przebiegiem odzyskiwania pamięci, jest również najtańszą operacją.

 Ta zasada jest wyzwalana, gdy ilość czasu poświęcanego na wyrzucanie elementów bezużytecznych jest zbyt wysoka w porównaniu z całkowitym czasem przetwarzania aplikacji.

> [!NOTE]
> Gdy czas spędzony na wyrzucaniu elementów bezużytecznych jest znaczący, ale nie jest zbyt duży w porównaniu z całkowitym czasem przetwarzania aplikacji, wyzwalane jest ostrzeżenie [o wysokim czasie procesora (DA0023](../profiling/da0023-high-gc-cpu-time.md) ), a nie ta reguła.

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczniki](../profiling/marks-view.md) danych profilowania. Znajdź **pamięć środowiska CLR \\ % Time w kolumnie GC** . Ustal, czy istnieją określone fazy wykonywania programu, w których narzuty wyrzucania elementów bezużytecznych pamięci zarządzanej są większe niż inne fazy. Porównaj wartości parametru% Time w usłudze GC z szybkością wyrzucania elementów bezużytecznych raportowaną w liczbie kolekcji **generacji 0**, kolekcjach **generacji 1**, liczbach **kolekcji generacji 2** .

 Wartość% Time w usłudze GC próbuje zgłosić ilość czasu, przez który aplikacja spędza wykonywanie wyrzucania elementów bezużytecznych proporcjonalnie do całkowitej ilości przetwarzania. Należy pamiętać, że istnieją sytuacje, w których wartość% Time w usłudze GC może zgłosić wysoką wartość, ale nie jest ze względu na nadmierne wyrzucanie elementów bezużytecznych. Aby uzyskać więcej informacji na temat sposobu, w jaki wartość% Time w ramach usługi GC jest obliczana, zobacz [różnicę między danymi wydajności zgłaszanymi przez różne narzędzia — 4 wprowadzanie danych](https://devblogs.microsoft.com/maoni/archive/difference-between-perf-data-reported-by-different-tools-4.aspx) **dziennika usługi Maoni** w witrynie MSDN. Jeśli wystąpią błędy stron lub aplikacja jest przedwypartena przez inne wyższe priorytety na komputerze podczas wyrzucania elementów bezużytecznych, czas (%) w liczniku GC będzie odzwierciedlał te dodatkowe opóźnienia.
