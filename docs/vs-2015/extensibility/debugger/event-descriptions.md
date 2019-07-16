---
title: Opisy zdarzeń | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5aff88047d6b1f79544af927751d7a053eeda218
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152822"
---
# <a name="event-descriptions"></a>Opisy zdarzeń
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>Zobacz też  
 [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md)
