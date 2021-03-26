---
title: Opisy zdarzeń | Microsoft Docs
description: Dowiedz się więcej o typach zdarzeń i przyczynach ich użycia. Każdy typ zdarzenia ma określony cel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cd8c6dbb4eddfcffa779b70b17819bf5e92c0c45
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096970"
---
# <a name="event-descriptions"></a>Opisy zdarzeń
Każdy typ zdarzenia ma określony cel.

## <a name="events-and-the-reasons-for-their-use"></a>Zdarzenia i przyczyny ich użycia

|Zdarzenie|Opis|
|-----------|-----------------|
|Aktywuj zdarzenia dokumentu|Występuje, gdy aparat debugowania (DE) chce, aby środowisko IDE miało otwarcie lub przełączenie dokumentu na pierwszy plan.|
|Zdarzenia błędów powiązane lub punkty przerwania|Wysyłany, gdy punkt przerwania jest powiązany lub gdy punkt przerwania nie może powiązać i zwracany jest błąd.|
|Zdarzenia niepowiązane z punktem przerwania|Występuje, gdy powiązany punkt przerwania tworzy powiązanie z kodem.|
|Może zatrzymać zdarzenia|Wysyłany do IDE, aby określić, czy użytkownik chce zatrzymać w określonym punkcie w kodzie.|
|Zdarzenia punktu przerwania|Występuje, gdy zostanie trafiony kod lub punkt przerwania danych.|
|Zdarzenia tekstu dokumentu|Występuje, gdy tekst w dokumencie zostanie zmieniony. Te zdarzenia nie są wysyłane przez `IDebugEventCallBack2::Event` metodę.|
|Zdarzenia tworzenia aparatu|Wysyłany podczas pierwszego tworzenia aparatu.|
|Zdarzenia punktu wejścia|Wysyłany, gdy debugowany program uruchomił swój kod inicjujący i osiągnął swój pierwszy punkt wejścia użytkownika.|
|Zdarzenia wyjątków|Wysyłany, gdy uruchomiony program osiągnie wyjątek.|
|Zdarzenia kończenia oceny wyrażeń|Wysyłany, gdy Obliczanie wyrażenia asynchronicznego zostało zakończone.|
|Znajdowanie zdarzeń symboli|Wysyłany przy każdym zaproszeniu użytkownika o znalezienie symboli dla modułu.|
|Załaduj zdarzenia zakończone|Wysyłane tylko wtedy, gdy początkowe ładowanie programu zostało zakończone, a pierwszy kod zostanie uruchomiony w programie.|
|Zdarzenia komunikatów|Wysyłany, gdy wiadomości są wysyłane do użytkowników.|
|Zdarzenia ładowania modułu|Wysyłany podczas ładowania lub zwalniania nowego modułu.|
|Zdarzenia ciągu wyjściowego|Wysyłany, gdy program zapisuje dane wyjściowe debugowania.|
|Tworzenie i niszczenie zdarzeń|Wysyłany do ogłaszania tworzenia lub niszczenia procesów, programów, właściwości, sesji i wątków, dzięki czemu środowisko IDE programu Visual Studio może śledzić stan debugowanych programów.|
|Zdarzenia zakończone krok po kroku|Wysyłany po zakończeniu kroku.|
|Zdarzenia zmiany nazwy wątku|Wysyłany, gdy użytkownik zmienia nazwę wątku.|
|Zdarzenia zmiany nazwy programu|Wysyłany, gdy użytkownik zmienia nazwę programu.|

## <a name="see-also"></a>Zobacz też
- [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md)
