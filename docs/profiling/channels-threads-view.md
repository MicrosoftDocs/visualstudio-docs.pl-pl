---
title: Kanały (widok wątków) | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 94ac6e9e85a2d7dd504b2d2bd83bd1bbdb265ea0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62776780"
---
# <a name="channels-threads-view"></a>Kanały (widok wątków)
Wizualizator współbieżności pokazuje cztery rodzaje kanałów: kanały wątków, kanały dyskowe, kanały znaczników i kanały GPU.

## <a name="thread-channels"></a>Kanały wątków
 Kanał wątku pokazuje stan wątku, według koloru, dla tylko jednego wątku. Po wstrzymaniu nazwy kanału wyświetlana jest funkcja start dla danego wątku. Wizualizator współbieżności wykrywa kilka rodzajów wątków. Najczęstsze rodzaje są pokazane w poniższej tabeli.

|||
|-|-|
|Gwint główny|Wątek, który uruchomił aplikację.|
|Wątek roboczy|Wątek, który został utworzony przez główny wątek aplikacji.|
|Wątek roboczy CLR|Wątek roboczy, który został utworzony przez środowisko uruchomieniowe języka wspólnego (CLR).|
|Pomocnik debugera|Wątek roboczy, który został utworzony przez debuger programu Visual Studio.|
|Wątek ConcRT|Wątek, który został utworzony przez środowisko uruchomieniowe współbieżności firmy Microsoft.|
|Gwint GDI|Wątek, który został stworzony przez GDIPlus.|
|Wątek OLE/RPC|Wątek, który został utworzony jako wątek roboczy RPC.|
|Wątek RPC|Wątek, który został utworzony jako wątek RPC.|
|Wątek Winsocka|Wątek, który został utworzony jako wątek Winsock.|
|Pula wątków|Wątek, który został utworzony przez clr puli wątków.|

## <a name="disk-channels"></a>Kanały dyskowe
 Kanały dysków odpowiadają dyskom fizycznym w komputerze. Ponieważ istnieją oddzielne kanały dla operacji odczytu i zapisu dla każdego dysku fizycznego w systemie, każdy dysk ma dwa kanały. Numery dysków odpowiadają nazwom urządzeń jądra. Kanał dysku jest wyświetlany tylko wtedy, gdy na dysku była aktywność.

## <a name="marker-channels"></a>Kanały znaczników
 Kanały znaczników odpowiadają zdarzeń generowanych przez aplikację i bibliotek, których używa. Na przykład biblioteka równoległa zadań, biblioteka równoległych wzorców i C++ AMP generują zdarzenia, które są wyświetlane jako znaczniki. Każdy kanał znacznika jest skojarzony z identyfikatorem wątku, który jest wyświetlany obok opisu kanału. Identyfikator identyfikuje wątek, który wygenerował zdarzenie. Opis kanału zawiera nazwę dostawcy śledzenia zdarzeń dla systemu Windows (ETW), który wygenerował zdarzenia. Jeśli kanał wyświetla zdarzenia z [SDK wizualizatora współbieżności,](../profiling/concurrency-visualizer-sdk.md)wyświetlana jest również nazwa serii.

## <a name="gpu-channels"></a>Kanały GPU
 Kanały GPU wyświetlają informacje o aktywności DirectX 11 w systemie.  Każdy aparat DirectX skojarzony z kartą graficzną ma osobny kanał.  Poszczególne segmenty reprezentują czas spędzony na przetwarzaniu pakietu DMA.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)