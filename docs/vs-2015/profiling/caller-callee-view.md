---
title: Wyświetl wywołującego/wywoływanego | Dokumentacja firmy Microsoft
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
- vs.performance.view.callercallee
helpviewer_keywords:
- profiling tools, reports, Caller/Callee view
- profiling tools, Caller/Callee view
- performance reports, Caller/Callee view
- Caller/Callee view
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7631085e0560c74ea162f8aeae9147bbcf9412e2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784432"
---
# <a name="callercallee-view"></a>Widok wywołujący/wywoływany
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok wywołujący/wywoływany Wyświetla informacje dotyczące profilowania dla wybranej funkcji i jej funkcji nadrzędnych i podrzędnych. Widok wywołujący/wywoływany zawiera trzy siatki:  
  
 **Bieżąca funkcja** jest wyświetlany w środkowy siatkę, a pokazuje profilowania informacje dotyczące wybranej funkcji. Wartości obejmują wszystkie wywołania do funkcji, które zostały zebrane podczas uruchomienia profilowania.  
  
 **Funkcje, które wywołały bieżącą funkcję** są wyświetlane w siatce górnym i pokazuje liczbę wartości wybranej funkcji (bieżącego), które zostały wygenerowane przez wywołania funkcji wywołującego (nadrzędnego).  
  
 **Funkcje, które zostały wywołane przez bieżącą funkcję** jest wyświetlany w siatce dolnej i pokazuje profilowania informacji dla funkcji elementu wywoływanego (podrzędne) wybranej funkcji, gdy funkcja podrzędnych została wywołana przez bieżącą funkcję.  
  
 Kolumny, które są dostępne w widok wywołujący/wywoływany zależą od metody profilowania (próbkowania i instrumentacji), który został użyty do zbierania danych i czy zebrano dane pamięci platformy .NET w profilowania działać.  
  
 Możesz wybrać inną funkcję do bieżącej funkcji w środkowej części widoku raportu, klikając dwukrotnie dowolny z funkcji, które są wymienione w dwóch częściach widoku. Widok raportu jest aktualizowana automatycznie w celu odzwierciedlenia zmian.  
  
 Dane można sortować, klikając nazw kolumn. Widok wywołujący/wywoływany można dodać dodatkowe kolumny. Aby uzyskać więcej informacji, zobacz [porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Element wywołujący / widok / / wywoływany - dane próbkowania](../profiling/caller-callee-view-sampling-data.md)   
 [Widok wywołujący/wywoływany - dane Instrumentacji](../profiling/caller-callee-view-instrumentation-data.md)   
 [Widok wywołujący/wywoływany - dane Instrumentacji pamięci platformy .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Widok wywołujący/wywoływany - dane próbkowania pamięci platformy .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Element wywołujący / widok / / wywoływany - dane Kontencji](../profiling/caller-callee-view-contention-data.md)



