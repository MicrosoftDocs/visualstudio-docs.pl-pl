---
title: 'DA0024: Nadmierne zużycie czasu Procesora | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0024
- vs.performance.24
- vs.performance.rules.DA0024
ms.assetid: 228872da-77d0-4da5-b455-ac57fb1867c9
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eae77a7685bbc9e8dc1613603baec9a5c93ad285
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771072"
---
# <a name="da0024-excessive-gc-cpu-time"></a>DA0024: Nadmierne zużycie czasu Procesora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rule Id|DA0024|  
|Category|.NET Framework Usage|  
| Metoda profilowania | Wszystkie |  
| Komunikat | czas działania modułu GC (%) jest bardzo duża. Brak nadmiernej liczby wyrzucania elementów bezużytecznych. |  
| Typ reguły | Ostrzeżenie |  
  
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
  
 Czas w wartości GC (%) próbuje ilość czasu, że aplikacja zużywa wykonywania wyrzucania elementów bezużytecznych proporcjonalna do sumy przetwarzania raportu. Należy pamiętać, że istnieją okoliczności, gdy czas w wartości GC (%) może zgłaszać bardzo wysoka wartość, ale nie jest się z powodu nadmiernego wyrzucania elementów bezużytecznych. Aby uzyskać więcej informacji na temat sposobu, czas w wartości GC (%) jest obliczana, zobacz [różnica między wydajności — dane zgłaszane przez różnych narzędzi — 4](http://go.microsoft.com/fwlink/?LinkId=177863) wpisu **Weblog firmy Maoni** w witrynie MSDN. Jeśli występują błędy stron lub aplikacja są zastępowane przez inne prace wyższy priorytet, na maszynie podczas wyrzucania elementów bezużytecznych, czas licznika GC (%) zostanie naliczona te dodatkowe opóźnienia.
