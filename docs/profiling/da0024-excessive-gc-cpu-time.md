---
title: 'DA0024: Nadmierne zużycie czasu Procesora | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0024
- vs.performance.24
- vs.performance.rules.DA0024
ms.assetid: 228872da-77d0-4da5-b455-ac57fb1867c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e058748c1614641fd831f7c159d3cf7e2ac59d1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53881344"
---
# <a name="da0024-excessive-gc-cpu-time"></a>DA0024: Nadmierne zużycie czasu procesora CPU

|||  
|-|-|  
|Identyfikator reguły|DA0024|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metoda profilowania|Wszystkie|  
|Komunikat|% Czasu odzyskiwania pamięci jest bardzo duża. Brak nadmiernej liczby wyrzucania elementów bezużytecznych.|  
|Typ reguły|Ostrzeżenie|  

 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  

## <a name="cause"></a>Przyczyna  
 Dane o wydajności systemu, które zostały zebrane podczas profilowania wskazuje, że czas poświęcony na wyrzucanie elementów bezużytecznych jest zbyt wysoka w porównaniu z czasem przetwarzania kompletnej aplikacji.  

## <a name="rule-description"></a>Opis reguły  
 Microsoft .NET wspólnego języka środowiska wykonawczego (języka wspólnego CLR) zapewnia mechanizm zarządzania pamięcią automatyczną, który używa modułu odśmiecania pamięci, aby odzyskać pamięci z obiektów, które aplikacja już używa. Moduł odśmiecania pamięci jest zorientowana na generowanie na podstawie założenia, że wiele alokacje są krótkotrwałe. Na przykład, zmienne lokalne, powinny być krótkotrwały. Nowo utworzonych obiektach Uruchom w generacji 0 (gen 0), a następnie przejść do generacji 1, po ich przetrwać wyrzucania elementów bezużytecznych, uruchom, a na koniec przejścia do generacji 2, jeśli aplikacja nadal korzysta z nich.  

 Obiekty w generacji 0 są zbierane, często i zazwyczaj bardzo wydajny sposób. Obiekty w generacji 1 są zbierane rzadziej i mniej skuteczne. Na koniec długotrwałe obiekty w generacji 2 powinny być zbierane nawet rzadziej. Kolekcji generacji 2, która znajduje się pełne wyrzucanie elementów bezużytecznych, uruchamianie, jest również najbardziej kosztowną operacją.  

 Ta reguła jest uruchamiana, gdy czas poświęcony na wyrzucanie elementów bezużytecznych jest zbyt wysoka w porównaniu z czasem przetwarzania kompletnej aplikacji.  

> [!NOTE]
>  Gdy część czasu spędzonego w wyrzucania elementów bezużytecznych jest ważna, ale nie nadmierne w porównaniu z czasem przetwarzania kompletnej aplikacji [DA0023: Wysokie wykorzystanie czasu GC CPU](../profiling/da0023-high-gc-cpu-time.md) generowane ostrzeżenie zamiast tej reguły.  

## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczniki](../profiling/marks-view.md) danych profilowania. Znajdź **pamięć .NET CLR\\czas działania modułu GC (%)** kolumny. Określa, czy określone faz wykonywania programu gdzie obciążenie pamięci zarządzanej wyrzucania elementów bezużytecznych jest większe niż pozostałych faz. Porównaj wartości czas działania modułu GC (%) wartość ma zostać współczynnik operacji wyrzucania elementów bezużytecznych zgłoszone w **# pokolenia 0**, **# zbierania obiektów pokolenia 1**, **# zbierania obiektów pokolenia 2** wartości .  

 Czas w wartości GC (%) próbuje ilość czasu, że aplikacja zużywa wykonywania wyrzucania elementów bezużytecznych proporcjonalna do sumy przetwarzania raportu. Należy pamiętać, że istnieją okolicznościach, gdy czas w wartości GC (%) może raportować o wysokiej wartości, ale nie jest się z powodu nadmiernego wyrzucania elementów bezużytecznych. Aby uzyskać więcej informacji na temat sposobu, czas w wartości GC (%) jest obliczana, zobacz [różnica między wydajności — dane zgłaszane przez różne narzędzia - 4](http://go.microsoft.com/fwlink/?LinkId=177863) wpisu **Weblog firmy Maoni** w witrynie MSDN. Jeśli występują błędy stron lub aplikacja jest wyparte przez inne prace wyższy priorytet, na maszynie podczas wyrzucania elementów bezużytecznych, czas licznika GC (%) zostanie naliczona te dodatkowe opóźnienia.