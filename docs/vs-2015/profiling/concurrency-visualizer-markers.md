---
title: Znaczniki wizualizatora współbieżności | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 43b6115c45f9583b90711ef030834da662106f08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704353"
---
# <a name="concurrency-visualizer-markers"></a>Znaczniki Concurrency Visualizer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W wizualizatorze współbieżności znaczniki są ikonami, które reprezentują zdarzenia w aplikacji.  Zazwyczaj aplikacja generuje te zdarzenia, aby wyznaczyć fazy lub wystąpienia w aplikacji.  Zdarzenia mogą być generowane przez aplikację lub przez biblioteki i środowiska uruchomieniowe używane przez aplikację.  
  
## <a name="kinds-of-markers"></a>Rodzaje znaczników  
 Wizualizator współbieżności używa trzech rodzajów znaczników do reprezentowania zdarzeń aplikacji: flag, wiadomości i zakresów.  
  
1. Użyj *flagi* , aby wskazać interesujący punkt w czasie w aplikacji.  Na przykład możesz użyć flagi, aby reprezentować, że wartość zmiennej osiągnęła określony próg lub że wyjątek został zgłoszony.  
  
2. *Komunikat* oznacza również punkt w czasie, ale można go użyć do śledzenia w stylu rejestrowania.  Na przykład, jakie mogły zostać zrzucone do pliku dziennika, można teraz zawijać w wywołaniu komunikatu, aby można było je śledzić i wyświetlać w wizualizatorze współbieżności. Możesz również użyć wizualizatora współbieżności, aby wyeksportować te dane do pliku CSV.  
  
3. *Zakres* reprezentuje przedział czasu w aplikacji, na przykład jedną z jej faz.  
  
## <a name="marker-linkage-to-threads"></a>Powiązanie znacznika z wątkami  
 Każdy wątek generujący znaczniki ma oddzielny kanał osi czasu.  Identyfikator wątku, który jest odpowiedzialny za generowanie zdarzeń znacznika, jest wyświetlany obok opisu kanału znacznika.  Identyfikator, który jest wyświetlany po lewej stronie kanału znacznika, jest zgodny z IDENTYFIKATORem innego wątku w bieżącym procesie.  
  
## <a name="marker-importance"></a>Ważność znacznika  
 Znaczniki mogą mieć jeden z czterech poziomów ważności: niski, normalny, wysoki i krytyczny.  Źródła znaczników można filtrować na podstawie poziomu ważności.  Na przykład, jeśli chcesz zobaczyć tylko znaczniki z konkretnego źródła, które ma znaczenie normalne lub krytyczne, można skonfigurować filtr w oknie dialogowym [Ustawienia zaawansowane](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) . Ważność znacznika jest wyświetlana w jego etykietce narzędzia, a w [raporcie znaczniki](../profiling/markers-report.md).  
  
## <a name="marker-category"></a>Kategoria znacznika  
 Kategoria znacznika wskazuje grupę zdarzeń znacznika, które pochodzą z tego samego źródła.  Wizualizator współbieżności używa koloru do rozróżniania różnych kategorii flag i zakresów. Można skonfigurować Wizualizator współbieżności, aby użyć kategorii do filtrowania zdarzeń znacznika od określonego dostawcy zdarzeń.  Użyj okna dialogowego [Ustawienia zaawansowane](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) , aby skonfigurować filtr.  
  
## <a name="known-sources-of-markers"></a>Znane źródła znaczników  
 Każdy dostawca ETW może generować znaczniki, o ile dostawca przestrzega określonych ograniczeń. Można skonfigurować Wizualizator współbieżności, aby nasłuchiwać dodatkowych źródeł zdarzeń dla znaczników. Domyślnie nasłuchuje w tych źródłach zdarzeń:  
  
- [Concurrency Visualizer SDK](../profiling/concurrency-visualizer-sdk.md)  
  
- [Biblioteka zadań równoległych (TPL)](https://msdn.microsoft.com/library/b8f99f43-9104-45fd-9bff-385a20488a23)  
  
- [Przepływu danych](https://msdn.microsoft.com/library/643575d0-d26d-4c35-8de7-a9c403e97dd6)  
  
- [Równoległe LINQ (PLINQ)](https://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455)  
  
- [Współbieżność środowiska wykonawczego](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)  
  
- [Obsługa znaczników scenariusza](https://msdn.microsoft.com/e3b55bc2-b451-4214-ae00-0c7f5a5baec8)  
  
- [C++ AMP (C++ Accelerated Massive Parallelism)](https://msdn.microsoft.com/library/e27824cb-3167-409b-8c3f-a0e476d8f349)  
  
  Możesz użyć karty Znaczniki w oknie dialogowym [Ustawienia zaawansowane](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) , aby określić, czy znaczniki z różnych źródeł są wyświetlane w wizualizatorze współbieżności i czy można filtrować znaczniki na podstawie ważności i kategorii.  
  
## <a name="markers-from-eventsource"></a>Znaczniki ze źródła EventSource  
 Wizualizator współbieżności może również wyświetlać zdarzenia EventSource.  Aby uzyskać więcej informacji, zobacz [wizualizowanie zdarzeń EventSource jako znaczników](../profiling/visualizing-eventsource-events-as-markers.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Znaczniki flagi](../profiling/flag-markers.md)   
 [Znaczniki komunikatów](../profiling/message-markers.md)   
 [Znaczniki zakresu](../profiling/span-markers.md)   
 [Wizualizowanie zdarzeń i znaczników EventSource](../profiling/visualizing-eventsource-events-as-markers.md)
