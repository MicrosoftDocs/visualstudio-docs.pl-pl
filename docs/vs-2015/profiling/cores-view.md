---
title: Widok rdzeni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 869980fe7bbb773d566dffd38088b003e3a97a3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145644"
---
# <a name="cores-view"></a>Widok rdzeni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok rdzeni pokazuje, jak wykonywanie wątku zostało zamapowane na rdzenie procesora logicznego. W przypadku pisania aplikacji serwerowych ten widok może pomóc zoptymalizować wydajność pamięci podręcznej za pomocą koligacji wątków lub zarządzania pulą wątków. Może również pomóc w sprawdzeniu przypadków, w których użycie koligacji wątku mogło spowodować problem z migracją między rdzeniami. Widok rdzeni ma dwie części, wykres i legendę.  
  
 Wykres przedstawia rdzenie logiczne na osi y i godzinę na osi x. Każdy wątek na grafie ma unikatowy kolor, aby można było śledzić jego przenoszenie między rdzeniami w czasie. Możesz filtrować wątki na tym grafie, zaznaczając je w obszarze legendy.  
  
 Obszar legendy zawiera wpis dla każdego koloru na grafie. Każdy wpis przedstawia kolor i nazwę wątku, liczbę przełączeń kontekstu między rdzeniami, całkowitą liczbę przełączeń kontekstu i procent przełączeń kontekstu między rdzeniami. Legenda jest sortowana według liczby przełączeń kontekstu między rdzeniami, w kolejności malejącej. Wyświetla listę tylko wątków, które są wykonywane w trakcie wyświetlanego zakresu czasu.  Lista jest aktualizowana w przypadku powiększania lub kadrowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Wizualizator współbieżności](../profiling/concurrency-visualizer.md)   
 [Widok wykorzystania](../profiling/utilization-view.md)   
 [Widok wątków](../profiling/threads-view-parallel-performance.md)
