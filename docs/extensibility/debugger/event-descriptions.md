---
title: Opisy zdarzeń | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 096d73c46ce53d05ec00fc8ba206bd8d7b20f390
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922694"
---
# <a name="event-descriptions"></a>Opisy zdarzeń
Każdy typ zdarzenia ma określonego celu.  
  
## <a name="events-and-the-reasons-for-their-use"></a>Zdarzenia i przyczyny ich użycie  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|Aktywuj dokument zdarzenia|Występują, gdy aparat debugowania (DE) chce IDE próbę otwarcia lub przenieść dokument na pierwszym planie.|  
|Powiązany punkt przerwania lub punkt przerwania zdarzenia błędu|Wysyłany, gdy punkt przerwania jest powiązany lub gdy nie można powiązać punkt przerwania i zostanie zwrócony błąd.|  
|Punkt przerwania niepowiązanych zdarzenia|Występują, gdy powiązany punkt przerwania Rozpina z kodu.|  
|Można zatrzymać zdarzenia|Wysyłane do IDE, aby ustalić, czy użytkownik chce Zatrzymaj w określonym momencie w kodzie.|  
|Zdarzenia przerwania|Występuje po trafieniu punktu przerwania kodu lub danych.|  
|Zdarzenia tekstu dokumentu|Występuje po zmianie tekstu dokumentu. Te zdarzenia nie są wysyłane za pośrednictwem `IDebugEventCallBack2::Event` metody.|  
|Aparat tworzenia zdarzeń|Wysyłany, gdy tworzona jest najpierw silnika.|  
|Zdarzenia punktu wejścia|Wysyłany, gdy debugowanego ma uruchomić kod inicjowania i osiągnięto jej pierwszego punktu wejścia użytkownika.|  
|Zdarzenia wyjątków|Wysyłany, gdy uruchomiony program osiąga wyjątek.|  
|Zdarzenia ukończone oceny wyrażeń|Wysyłane po zakończeniu oceny wyrażenia asynchroniczne.|  
|Znajdź wydarzenia symboli|Wysyłane zawsze, gdy DE musi poprosić użytkownika o znalezienie symboli dla modułu.|  
|Zakończenie zdarzeń ładowania|Wysłane tylko po zakończeniu ładowania początkowego programu i pierwszy kod zostanie uruchomiony w programie.|  
|Komunikat zdarzenia|Wysyłany, gdy komunikaty są wysyłane do użytkowników.|  
|Zdarzenia ładowania modułu|Wysyłany, gdy nowy moduł jest załadowany lub zwolnione.|  
|Zdarzenia parametry wyjściowe|Wysyłany, gdy program zapisuje dane wyjściowe debugowania.|  
|Tworzyć i niszczyć zdarzenia|Wysyłane do anonsowania utworzenia lub zniszczenia procesów, programy, właściwości, sesje i wątki, środowiska IDE programu Visual Studio może przechowywać informacje o stan debugowane programy.|  
|Krok zdarzenia ukończone|Wysyłany, gdy krok został ukończony.|  
|Zdarzenia zmiany nazwy wątków|Wysyłany, gdy użytkownik zmienia nazwę wątku.|  
|Zdarzenia zmiany nazwy programu|Wysyłany, gdy użytkownik zmieni nazwę programu.|  
  
## <a name="see-also"></a>Zobacz także  
 [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md)