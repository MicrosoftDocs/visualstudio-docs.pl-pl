---
title: Kanały (Widok wątków) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.channelnames
helpviewer_keywords:
- Concurrency Visualizer, Channels (Threads View)
ms.assetid: 2f798c17-2363-42a4-be94-a5751d208eac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f18a636d83210b2329d103b1babdf47e697fd5c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537088"
---
# <a name="channels-threads-view"></a>Kanały (Widok wątków)
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
- [Widok wątków](../profiling/threads-view-parallel-performance.md)