---
title: Opis wartościami danych próbkowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
ms.assetid: fad540a8-24b6-4ff9-91ce-e67e9a58399d
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1234c88383e67ad1e4ae12db89679dad59a3d9b7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817623"
---
# <a name="understanding-sampling-data-values"></a>Zapoznanie z wartościami danych próbkowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Próbkowania* profilowanie metody [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profiling Tools przerywa działanie procesora komputera w ustalonych odstępach czasu i gromadzi stos wywołań funkcji. A *stos wywołań* jest dynamiczne struktury, która przechowuje informacje dotyczące funkcji, które są wykonywane na procesorze.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Analiza profiler Określa, czy procesor jest wykonywanie kodu w procesie docelowym. Jeśli procesor nie wykonuje kod w procesie docelowym, plik zostanie odrzucony.  
  
  Jeśli procesor, jest wykonywany kod docelowy, program profilujący zwiększa liczby próbek dla każdej funkcji na stosie wywołań. W tym czasie jest próbka tylko jednej funkcji — na stosie wywołań aktualnie wykonuje kod. Innych funkcji na stosie są elementów nadrzędnych w hierarchii wywołań funkcji, które oczekują na ich elementy podrzędne do zwrócenia.  
  
  Zdarzenia przykładowe przyrosty profiler *wyłączne* liczba funkcji, która jest w trakcie wykonywania instrukcji próbek. Ponieważ próbek wyłącznych wchodzi w skład całości (*włącznie*) przykłady funkcji liczność próbki włączne aktualnie aktywnych funkcji również jest zwiększany.  
  
  Program profilujący zwiększa liczność próbki włączne wszystkich funkcji w stosie wywołań.  
  
## <a name="inclusive-samples"></a>Próbki włączne  
 Łączna liczba próbek, które są zbierane podczas wykonywania funkcji docelowej.  
  
 Obejmuje to przykłady, które są zbierane podczas bezpośredniego wykonywania kodu funkcji i przykłady, które są zbierane podczas wykonywania funkcji podrzędnych, które są wywoływane przez funkcję docelowego.  
  
## <a name="exclusive-samples"></a>Próbki wyłączne  
 Liczba próbek, które są zbierane podczas bezpośredniego wykonywania instrukcji docelowej funkcji.  
  
 Próbki wyłączne nie zawierają przykłady, które są zbierane podczas wykonywania funkcji wywołanych przez funkcję docelowego.  
  
## <a name="inclusive-percent"></a>Procent (włącznie)  
 Procent całkowitej liczby włącznych próbek podczas uruchomienia profilowania, które są włącznych próbek zakresu funkcję lub dane.  
  
## <a name="exclusive-percent"></a>% Wyłącznych  
 Procent całkowitej liczby próbek wyłącznych podczas uruchomienia profilowania, które są wyłącznych próbek zakres funkcji lub danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md)   
 [Analizowanie danych dotyczących narzędzi do oceny wydajności](../profiling/analyzing-performance-tools-data.md)



