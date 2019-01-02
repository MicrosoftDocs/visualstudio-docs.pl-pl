---
title: Kanały (Widok wątków) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.channelnames
helpviewer_keywords:
- Concurrency Visualizer, Channels (Threads View)
ms.assetid: 2f798c17-2363-42a4-be94-a5751d208eac
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d3ab6254ba56337e3e47379f1f4df800a73c67f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870930"
---
# <a name="channels-threads-view"></a>Kanały (Widok wątków)
Wizualizator współbieżności przedstawia cztery rodzaje kanałów: wątek kanały, kanały dysku, znacznika kanałów i kanały procesora GPU.  
  
## <a name="thread-channels"></a>Kanały wątku  
 Kanał wątku pokazuje stan wątku przez kolor dla tylko jednego wątku. Po wstrzymaniu w nazwie kanału, zostanie wyświetlona funkcji uruchamiania dla danego wątku. Narzędzie Concurrency Visualizer wykrywa kilka rodzajów wątków. W poniższej tabeli przedstawiono najbardziej typowych rodzajów.  
  
|||  
|-|-|  
|Główny wątek|Wątek, który uruchomił aplikację.|  
|Wątek roboczy|Wątek, który został utworzony przez wątku głównego aplikacji.|  
|Wątek roboczy CLR|Wątek roboczy, który został utworzony przez środowisko uruchomieniowe języka wspólnego (CLR).|  
|Pomocnik debugera|Wątek roboczy, który został utworzony przez debuger programu Visual Studio.|  
|Wątek ConcRT|Wątek, który został utworzony przez środowisko uruchomieniowe współbieżności firmy Microsoft.|  
|Wątek GDI|Wątek, który został utworzony przez GDIPlus.|  
|Wątek OLE/RPC|Wątek, który został utworzony jako wątku roboczego RPC.|  
|Wątek RPC|Wątek, który został utworzony jako wątek RPC.|  
|Wątek Winsock|Wątek, który został utworzony jako wątek usługi Winsock.|  
|Pula wątków|Wątek, który został utworzony przez CLR puli wątków.|  
  
## <a name="disk-channels"></a>Kanały dysku  
 Kanały dysku odpowiadają fizycznych dysków w komputerze. Ponieważ istnieje osobny kanał dla operacji odczytu i zapisu dla każdego dysku fizycznego w systemie, każdy dysk ma dwa kanały. Numery dysków odnoszą się do nazwy urządzeń jądra. Kanał dysku jest wyświetlany tylko jeśli były wykonywane działania na dysku.  
  
## <a name="marker-channels"></a>Kanały znacznika  
 Kanały znacznika odpowiadają zdarzenia wygenerowane przez aplikację i bibliotek, które są używane. Na przykład biblioteka zadań równoległych, biblioteka równoległych wzorców i C++ AMP generować zdarzenia, które są wyświetlane w postaci znaczników. Każdy znacznik kanał jest skojarzony z identyfikator wątku, który jest wyświetlany obok opis kanału. Identyfikator identyfikuje wątku, który wygenerował zdarzenie. Opis kanału zawiera nazwę dostawcy śledzenie zdarzeń dla Windows (ETW), który wygenerował zdarzenia. Jeśli kanał Wyświetla zdarzenia z [SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md), wyświetlana jest także nazwa serii.  
  
## <a name="gpu-channels"></a>Kanały procesora GPU  
 Kanały GPU wyświetlania informacji o działaniu programu DirectX 11 w systemie.  Każdy silnik DirectX, która jest skojarzona z karty graficznej ma oddzielny kanał.  Poszczególne segmenty reprezentują czas, jaki ma poświęcony na przetwarzanie pakietu DMA.  
  
## <a name="see-also"></a>Zobacz także  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)