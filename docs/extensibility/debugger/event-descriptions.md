---
title: Opisy zdarzeń | Microsoft Docs
description: Dowiedz się więcej o typach zdarzeń i przyczynach ich użycia. Każdy typ zdarzenia ma określony cel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ee2eedac924b3bbd58fac6980da9151a88da9196
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902647"
---
# <a name="event-descriptions"></a>Opisy zdarzeń
Każdy typ zdarzenia ma określony cel.

## <a name="events-and-the-reasons-for-their-use"></a>Zdarzenia i przyczyny ich użycia

|Zdarzenie|Opis|
|-----------|-----------------|
|Aktywowanie zdarzeń dokumentu|Występuje, gdy aparat debugowania (DE) chce, aby idee otwierały lub przeniosły dokument na pierwszy plan.|
|Zdarzenia błędów związanych z punktem przerwania lub punktem przerwania|Wysyłane, gdy punkt przerwania jest powiązany lub gdy nie można powiązać punktu przerwania i zwracany jest błąd.|
|Zdarzenia niepowiązanych punktów przerwania|Występuje, gdy powiązany punkt przerwania odłącza się od kodu.|
|Może zatrzymywać zdarzenia|Wysyłane do środowiska IDE w celu określenia, czy użytkownik chce zatrzymać się w określonym punkcie w kodzie.|
|Zdarzenia punktu przerwania|Występuje po trafieniu kodu lub punktu przerwania danych.|
|Zdarzenia tekstowe dokumentu|Występuje w przypadku zmiany tekstu w dokumencie. Te zdarzenia nie są wysyłane za pośrednictwem `IDebugEventCallBack2::Event` metody .|
|Zdarzenia tworzenia aparatu|Wysyłane przy pierwszym utworzeniu aparatu.|
|Zdarzenia punktu wejścia|Wysyłane, gdy debugowany program uruchamia swój kod inicjowania i osiąga swój pierwszy punkt wejścia użytkownika.|
|Zdarzenia wyjątków|Wysyłane, gdy uruchomiony program wystąpi wyjątek.|
|Zdarzenia zakończone oceną wyrażeń|Wysyłane po zakończeniu oceny wyrażeń asynchronicznych.|
|Znajdowanie zdarzeń symboli|Wysyłane za każdym razem, gdy de musi poprosić użytkownika o znalezienie symboli dla modułu.|
|Załaduj zdarzenia zakończone|Wysyłane tylko po zakończeniu początkowego ładowania programu i pierwszym kodzie, który zostanie uruchomiony w programie.|
|Zdarzenia komunikatów|Wysyłane, gdy komunikaty są wysyłane do użytkowników.|
|Zdarzenia ładowania modułów|Wysyłane po załadowaniu lub zwolniniu nowego modułu.|
|Zdarzenia ciągu wyjściowego|Wysyłane, gdy program zapisuje dane wyjściowe debugowania.|
|Tworzenie i niszczenie zdarzeń|Wysyłane w celu ogłaszania tworzenia lub niszczenia procesów, programów, właściwości, sesji i wątków, dzięki czemu Visual Studio IDE może śledzić stan debugowanych programów.|
|Zdarzenia ukończenia kroku|Wysyłane po zakończeniu kroku.|
|Zdarzenia zmiany nazwy wątku|Wysyłane, gdy użytkownik zmienia nazwę wątku.|
|Zdarzenia zmiany nazwy programu|Wysyłane, gdy użytkownik zmieni nazwę programu.|

## <a name="see-also"></a>Zobacz też
- [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md)
