---
title: Informacje o wartościach danych próbkowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
ms.assetid: fad540a8-24b6-4ff9-91ce-e67e9a58399d
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 91a4a50ecc745c0b56167d6a5dbb1932af7ed2bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145428"
---
# <a name="understanding-sampling-data-values"></a>Zapoznanie z wartościami danych próbkowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metoda profilowania *próbkowania* [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzia profilowania przerywa procesor komputera w ustalonych odstępach czasu i zbiera stos wywołań funkcji. *Stos wywołań* jest strukturą dynamiczną, która przechowuje informacje o funkcjach wykonywanych na procesorze.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Analiza profilera określa, czy procesor wykonuje kod w procesie docelowym. Jeśli procesor nie wykonuje kodu w procesie docelowym, przykład zostanie odrzucony.  
  
  Jeśli procesor wykonuje kod docelowy, profiler zwiększa liczbę próbek dla każdej funkcji na stosie wywołań. W czasie, gdy pobierana jest próbka, tylko jedna funkcja na stosie wywołań wykonuje obecnie kod. Inne funkcje na stosie są elementami nadrzędnymi w hierarchii wywołań funkcji, które oczekują na zwrócenie przez nich elementów podrzędnych.  
  
  W przypadku przykładowego zdarzenia Profiler *zwiększa losową* liczbę funkcji, która wykonuje obecnie instrukcje. Ze względu na to, że próbka wyłączna jest również częścią łącznej (*włącznie*) próbek funkcji, jest również zwiększana liczba włączonych próbek dla obecnie aktywnej funkcji.  
  
  Profiler zwiększa liczbę włączonych próbek wszystkich innych funkcji na stosie wywołań.  
  
## <a name="inclusive-samples"></a>Próbki włączne  
 Całkowita liczba próbek zbieranych podczas wykonywania funkcji docelowej.  
  
 Obejmuje to próbki, które są zbierane podczas bezpośredniego wykonywania kodu funkcji i próbek, które są zbierane podczas wykonywania funkcji podrzędnych, które są wywoływane przez funkcję docelową.  
  
## <a name="exclusive-samples"></a>Próbki wyłączne  
 Liczba próbek zbieranych podczas bezpośredniego wykonywania instrukcji funkcji docelowej.  
  
 Próbki wyłączne nie obejmują próbek, które są zbierane podczas wykonywania funkcji, które są wywoływane przez funkcję docelową.  
  
## <a name="inclusive-percent"></a>Łączny procent  
 Wartość procentowa łącznej liczby próbek włącznie w przebiegu profilowania, które obejmują próbki funkcji lub zakresu danych.  
  
## <a name="exclusive-percent"></a>Procent wyłączny  
 Procent całkowitej liczby próbek wyłącznych w przebiegu profilowania, które są wyłącznymi próbkami funkcji lub zakresu danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: wybieranie metod zbierania](../profiling/how-to-choose-collection-methods.md)   
 [Analizowanie danych dotyczących narzędzi do oceny wydajności](../profiling/analyzing-performance-tools-data.md)
