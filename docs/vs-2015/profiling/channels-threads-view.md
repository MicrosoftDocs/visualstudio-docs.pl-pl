---
title: Kanały (Widok wątków) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.channelnames
helpviewer_keywords:
- Concurrency Visualizer, Channels (Threads View)
ms.assetid: 2f798c17-2363-42a4-be94-a5751d208eac
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df93a87285bdf1172e75b63ed956c1aa978fc71e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545538"
---
# <a name="channels-threads-view"></a>Kanały (Widok wątków)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wizualizator współbieżności pokazuje cztery rodzaje kanałów: kanały wątku, kanały dysków, kanały znaczników i kanały GPU.  
  
## <a name="thread-channels"></a>Kanały wątków  
 Kanał wątku pokazuje stan wątku według koloru dla tylko jednego wątku. Po wstrzymaniu nazwy kanału zostanie wyświetlona funkcja Start dla danego wątku. Wizualizator współbieżności wykrywa kilka rodzajów wątków. Najpopularniejsze rodzaje przedstawiono w poniższej tabeli.  
  
|Thread|Opis|  
|-|-|  
|Główny wątek|Wątek, który uruchomił aplikację.|  
|Wątek roboczy|Wątek, który został utworzony przez wątek główny aplikacji.|  
|Wątek roboczy CLR|Wątek roboczy, który został utworzony przez środowisko uruchomieniowe języka wspólnego (CLR).|  
|Pomocnik debugera|Wątek roboczy, który został utworzony przez debuger programu Visual Studio.|  
|Wątek ConcRT|Wątek, który został utworzony przez Microsoft środowisko uruchomieniowe współbieżności.|  
|Wątek GDI|Wątek, który został utworzony za pomocą interfejsu GDIPlus.|  
|Wątek OLE/RPC|Wątek, który został utworzony jako wątek roboczy RPC.|  
|Wątek RPC|Wątek, który został utworzony jako wątek RPC.|  
|Wątek Winsock|Wątek, który został utworzony jako wątek Winsock.|  
|Pula wątków|Wątek, który został utworzony przez pulę wątków CLR.|  
  
## <a name="disk-channels"></a>Kanały dysku  
 Kanały dysku odpowiadają dyskom fizycznym w komputerze. Ponieważ istnieją osobne kanały dla operacji odczytu i zapisu dla każdego dysku fizycznego w systemie, każdy dysk ma dwa kanały. Numery dysków odpowiadają nazwom urządzeń jądra. Kanał dysku jest wyświetlany tylko wtedy, gdy wystąpiła aktywność na dysku.  
  
## <a name="marker-channels"></a>Kanały znaczników  
 Kanały znacznika odpowiadają zdarzeniom wygenerowanym przez aplikację i bibliotekami, z których korzystają. Na przykład Biblioteka zadań równoległych, Biblioteka wzorców równoległych i C++ AMP generować zdarzenia, które są wyświetlane jako znaczniki. Każdy kanał znacznika jest skojarzony z IDENTYFIKATORem wątku, który jest wyświetlany obok opisu kanału. Identyfikator identyfikuje wątek, który wygenerował zdarzenie. Opis kanału zawiera nazwę dostawcy śledzenia zdarzeń systemu Windows (ETW), który wygenerował zdarzenia. Jeśli kanał wyświetla zdarzenia z [zestawu SDK wizualizatora współbieżności](../profiling/concurrency-visualizer-sdk.md), zostanie również wyświetlona nazwa serii.  
  
## <a name="gpu-channels"></a>Kanały procesora GPU  
 Kanały procesora GPU zawierają informacje o aktywności DirectX 11 w systemie.  Każdy aparat DirectX skojarzony z kartą graficzną ma oddzielny kanał.  Poszczególne segmenty reprezentują czas spędzony na przetwarzaniu pakietu DMA.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)
