---
title: Opisy zdarzeń | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3c2582717fd4da3b833da90a951f9b8f72a59f71
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738788"
---
# <a name="event-descriptions"></a>Opisy zdarzeń
Każdy typ zdarzenia ma określony cel.

## <a name="events-and-the-reasons-for-their-use"></a>Wydarzenia i powody ich wykorzystania

|Wydarzenie|Opis|
|-----------|-----------------|
|Aktywowanie zdarzeń dokumentu|Występuje, gdy aparat debugowania (DE) chce IDE otworzyć lub przenieść dokument na pierwszym planie.|
|Zdarzenia związane z punktem przerwania lub punkt przerwania|Wysyłane, gdy punkt przerwania jest powiązany lub gdy punkt przerwania nie może powiązać i zwracany jest błąd.|
|Zdarzenia niezwiązane z punktem przerwania|Występuje, gdy powiązany punkt przerwania odłącza się od kodu.|
|Może zatrzymać zdarzenia|Wysłane do IDE, aby ustalić, czy użytkownik chciałby zatrzymać się w określonym punkcie w kodzie.|
|Zdarzenia punktu przerwania|Występuje, gdy kod lub punkt przerwania danych zostanie trafiony.|
|Dokumentowanie zdarzeń tekstowych|Występuje, gdy tekst w dokumencie jest zmieniany. Te zdarzenia nie są `IDebugEventCallBack2::Event` wysyłane za pośrednictwem metody.|
|Aparat tworzenia zdarzeń|Wysyłane podczas tworzenia aparatu.|
|Zdarzenia punktu wejścia|Wysyłane, gdy program jest debugowany ma uruchomić kod inicjowania i osiągnął swój pierwszy punkt wejścia użytkownika.|
|Zdarzenia wyjątków|Wysyłane, gdy uruchomiony program osiągnie wyjątek.|
|Pełna ocena wyrażenia zdarzenia|Wysyłane po zakończeniu oceny wyrażenia asynchronicznej.|
|Znajdź zdarzenia symboli|Wysyłane za każdym razem, gdy DE musi poprosić użytkownika o znalezienie symboli dla modułu.|
|Załaduj pełne zdarzenia|Wysyłane tylko wtedy, gdy początkowe ładowanie programu jest zakończone, a pierwszy kod ma być uruchomiony w programie.|
|Zdarzenia wiadomości|Wysyłane, gdy wiadomości są wysyłane do użytkowników.|
|Zdarzenia ładowania modułu|Wysyłane po załadowaniu lub wyładowaniu nowego modułu.|
|Zdarzenia ciągu wyjściowego|Wysyłane, gdy program zapisuje dane wyjściowe debugowania.|
|Tworzenie i niszczenie zdarzeń|Wysłane do ogłoszenia tworzenia lub niszczenia procesów, programów, właściwości, sesji i wątków, dzięki czemu ide programu Visual Studio może śledzić stan programów są debugowane.|
|Zdarzenia ukończenia kroków|Wysyłane po zakończeniu kroku.|
|Zdarzenia zmiany nazwy wątku|Wysyłane, gdy użytkownik zmienia nazwę wątku.|
|Zdarzenia zmiany nazwy programu|Wysyłane, gdy użytkownik zmieni nazwę programu.|

## <a name="see-also"></a>Zobacz też
- [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md)
