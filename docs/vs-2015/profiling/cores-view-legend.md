---
title: Widok rdzeni — Legenda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.cores.legend
helpviewer_keywords:
- Concurrency Visualizer, Cores View Legend
ms.assetid: e160384c-fcfe-49b3-86b7-229adb736c51
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c00b6ccf56eb9e171fbaf9afdaea1828b5a1325
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783106"
---
# <a name="cores-view-legend"></a>Widok rdzeni — Legenda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>Zobacz też  
 [Widok rdzeni](../profiling/cores-view.md)



