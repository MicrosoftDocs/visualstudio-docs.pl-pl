---
title: 'DA0023: Wysokie wykorzystanie czasu GC CPU | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0023
- vs.performance.23
- vs.performance.rules.DA0023
ms.assetid: aba875fe-9cbc-418d-a2c4-6eb47519a5bb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e340c7a46b469eda296b09da96a01249bc860e2e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53839115"
---
# <a name="da0023-high-gc-cpu-time"></a>DA0023: Wysokie wykorzystanie czasu GC CPU

|||  
|-|-|  
|Identyfikator reguły|DA0023|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metoda profilowania|Wszystkie|  
|Komunikat|% Czasu odzyskiwania pamięci jest stosunkowo wysoka. Wskazuje to na nadmierne wyrzucania elementów bezużytecznych może mieć wpływ na czas odpowiedzi aplikacji. Możesz zbierać .NET pamięć alokacji danych i obiekt informacji o czasie życia poznać wzorce przydzielania pamięci używane przez aplikację lepiej.|  
|Typ reguły|Informacyjny|  

 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  

## <a name="cause"></a>Przyczyna  
 Dane o wydajności systemu, które są zbierane podczas profilowania wskazuje, że ilość czasu spędzonego w wyrzucania elementów bezużytecznych jest istotne w porównaniu z czasem przetwarzania kompletnej aplikacji.  

## <a name="rule-description"></a>Opis reguły  
 Microsoft .NET wspólnego języka środowiska wykonawczego (języka wspólnego CLR) zapewnia mechanizm zarządzania pamięcią automatyczną, który używa modułu odśmiecania pamięci, aby odzyskać pamięci z obiektów, które aplikacja już używa. Moduł odśmiecania pamięci jest zorientowana na generowanie na podstawie założenia, że wiele alokacje są krótkotrwałe. Na przykład, zmienne lokalne, powinny być krótkotrwały. Nowo utworzonych obiektach Uruchom w generacji 0 (gen 0), a następnie przejść do generacji 1, po ich przetrwać wyrzucania elementów bezużytecznych, uruchom, a na koniec przejścia do generacji 2, jeśli aplikacja nadal korzysta z nich.  

 Obiekty w generacji 0 są zbierane, często i wydajne. Obiekty w generacji 1 są zbierane rzadziej i mniej skuteczne. Na koniec długotrwałe obiekty w generacji 2 powinny być zbierane nawet rzadziej. Kolekcji generacji 2, która znajduje się pełne wyrzucanie elementów bezużytecznych, uruchamianie, jest również najbardziej kosztowną operacją.  

 Ta reguła jest uruchamiana, gdy ilość czasu spędzonego w wyrzucania elementów bezużytecznych jest istotne w porównaniu z czasem przetwarzania kompletnej aplikacji.  

> [!NOTE]
>  Gdy część czasu spędzonego w wyrzucania elementów bezużytecznych jest nadmierne w porównaniu z czasu przetwarzania kompletnej aplikacji, [DA0024: Nadmierne zużycie czasu Procesora](../profiling/da0024-excessive-gc-cpu-time.md) generowane ostrzeżenie zamiast tej reguły.  

## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczniki](../profiling/marks-view.md) danych profilowania. Znajdź **pamięć .NET CLR\\czas działania modułu GC (%)** kolumny. Określa, czy określone faz wykonywania programu gdzie obciążenie pamięci zarządzanej wyrzucania elementów bezużytecznych jest większe niż pozostałych faz. Porównaj wartości czas działania modułu GC (%) wartość ma zostać współczynnik operacji wyrzucania elementów bezużytecznych zgłoszone w **# pokolenia 0**, **# zbierania obiektów pokolenia 1**, **# zbierania obiektów pokolenia 2** wartości .  

 Czas w wartości GC (%) próbuje ilość czasu, że aplikacja zużywa wykonywania wyrzucania elementów bezużytecznych proporcjonalna do sumy przetwarzania raportu. Należy pamiętać, istnieją okolicznościach, gdy czas w wartości GC (%) może raportować o wysokiej wartości, ale nie jest się z powodu nadmiernego wyrzucania elementów bezużytecznych. Aby uzyskać więcej informacji na temat sposobu, czas w wartości GC (%) jest obliczana, zobacz [różnica między wydajności — dane zgłaszane przez różne narzędzia - 4](http://go.microsoft.com/fwlink/?LinkId=177863) wpisu **Weblog firmy Maoni** w witrynie MSDN. Jeśli występują błędy stron lub aplikacja są zastępowane przez inne prace wyższy priorytet, na maszynie podczas wyrzucania elementów bezużytecznych, czas licznika GC (%) zostanie naliczona te dodatkowe opóźnienia.