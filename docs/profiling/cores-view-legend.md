---
title: Widok rdzeni — Legenda | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.legend
helpviewer_keywords:
- Concurrency Visualizer, Cores View Legend
ms.assetid: e160384c-fcfe-49b3-86b7-229adb736c51
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 61d05ffc3bb2a43b29e2e5c91a7b28f5b8d1224a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949527"
---
# <a name="cores-view-legend"></a>Widok rdzeni — Legenda
Widok rdzeni — Legenda identyfikuje każdy wątek, kolor i nazwę. Zawiera on kolumny, które pokazują liczby przełączeń kontekstu między rdzeniami, całkowita liczba przełączeń kontekstu i procent przełączeń kontekstu przecinających rdzenie. Wiersze w legendzie są sortowane według liczby przełączeń kontekstu między rdzeniami, w kolejności malejącej.  
  
 Możesz wybrać wierszy w legendzie, aby filtrować wątki, które są wyświetlane na osi czasu. Tylko wybrane wątki są wyświetlane na osi czasu. Jeśli nie zaznaczono żadnych wierszy, wszystkie wiersze są wyświetlane na osi czasu.  
  
 Kontekstu między rdzeniami zmienia kosztów, koszty i wydajność w ponad przełączników, które pozostają na tym samym rdzeń logiczny. Podczas przełączeń kontekstu rejestry procesora jest zapisywany i przywracany, wykonywany jest kod jądra systemu operacyjnego, wpisy buforu referencyjnych tłumaczenia są ponownie załadowany i jest opróżniany potoku procesora. Przełączenia kontekstu między rdzeniami może być jeszcze bardziej kosztowne niż inne przełączeń kontekstu, ponieważ danych w pamięci podręcznej jest nieprawidłowa dla tego wątku na inny core. Z kolei jeśli wątek jest przełączania kontekstu na rdzeń, który wcześniej został uruchomiony, jest prawdopodobne, że przydatne dane są nadal w pamięci podręcznej. Gdy zostały zwiększone przełączeń kontekstu między rdzeniami przez próby Zarządzanie wątku koligacji i wydajność jest obniżona, rozważ, czy rozwiązać ten problem. Rozpocznij poprzez wyeliminowanie koligacji wątku, a następnie obserwować wynikowe zachowania między rdzeniami.  
  
 W poniższej tabeli opisano elementy legendy.  
  
|Element|Definicja|  
|-------------|----------------|  
|Nazwa wątku|Zawiera kolor wątku w poprzednim osi czasu rdzeni i nazwę tego wątku.|  
|Przełączenia kontekstu między rdzeniami|Liczba przełączeń kontekstu dla wątku, który również przełączono z jednego rdzenia logicznego do innego. Go nie odróżnia przełączeń kontekstu między rdzeniami przecinających się z jednym procesorem struktury do innej i te, które pozostanie w tej samej struktury.|  
|Całkowita liczba przełączeń kontekstu|Całkowita liczba przełączeń kontekstu dla danego wątku w okresie próbkowania. Każdej zmianie wątku jedno przełączenie kontekstu kontekstu (na przykład z wykonywania w celu synchronizacji) jest liczony.|  
|Procent przełączeń kontekstu przecinających rdzenie|Obliczane jako wartość procentowa w wyniku dzielenia liczby przełączeń kontekstu między rdzeniami przez liczbę całkowita liczba przełączeń kontekstu. Im większa ta wartość procentowa, tym większe ogólny efekt pracy związanej z kontekstu między rdzeniami przełącza się na wydajność tego określonego wątku.|  
  
## <a name="see-also"></a>Zobacz także  
 [Widok rdzeni](../profiling/cores-view.md)