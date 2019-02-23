---
title: Spy ++ — pasek narzędzi | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 101b4ad50777f796a3de82127f6ce3253b26ccaa
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706759"
---
# <a name="spy-toolbar"></a>Spy++ — Pasek narzędzi
Pasek narzędzi pojawi się w pasku menu w programie Spy ++. Aby wyświetlić lub ukryć pasek narzędzi, na **widoku** menu, kliknij przycisk **narzędzi**.

 Następujące elementy sterujące są dostępne na pasku narzędzi.

## <a name="uielement-list"></a>Lista elementów UI

|Przycisk|Efekt|
|------------|------------|
|![Spy&#43;&#43; Windows Button](../debugger/media/icon_spy--_windows.gif "Icon_Spy++_Windows")|Wyświetla widok drzewa, okien i formantów w systemie. Aby uzyskać więcej informacji, zobacz [widoku Windows](../debugger/windows-view.md).|
|![Spy&#43;&#43; Processes Button](../debugger/media/icon_spy--_processes.gif "Icon_Spy++_Processes")|Wyświetla widok drzewa procesów w systemie. Aby uzyskać więcej informacji, zobacz [widok procesy](../debugger/processes-view.md).|
|![Szpieguj&#43; &#43; wątki przycisk](../debugger/media/icon_spy--_threads.gif "Icon_Spy ++ _Threads")|Wyświetla widok drzewa wątki w systemie. Aby uzyskać więcej informacji, zobacz [Widok wątków](../debugger/threads-view.md).|
|![Spy&#43;&#43; Messages Button](../debugger/media/icon_spy--_messages.gif "Icon_Spy++_Messages")|Tworzy okno Aby wyświetlić komunikaty okna i otwiera **opcje wiadomości** okno dialogowe, dzięki czemu można wybrać okna, w których komunikaty będą wyświetlane jak również inne opcje. Aby uzyskać więcej informacji, zobacz [widoku komunikatów](../debugger/messages-view.md).|
|![Szpieguj&#43; &#43; dziennika przycisk Start](../debugger/media/icon_spy--_startlog.gif "Icon_Spy ++ _StartLog")|Rejestrowanie komunikatów i wyświetlenie strumienia komunikatów. Ten formant jest dostępna tylko wtedy, gdy **wiadomości** okno jest aktywne okno. Aby uzyskać więcej informacji, zobacz [jak: Uruchamianie i zatrzymywanie wyświetlania dziennika komunikatów](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Spy&#43;&#43; Stop Log Button](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy++_StopLog")|Zatrzymuje komunikatu, rejestrowanie i wyświetlanie strumienia komunikatów. Ten formant jest dostępna tylko wtedy, gdy **wiadomości** okno jest aktywne okno. Aby uzyskać więcej informacji, zobacz [jak: Uruchamianie i zatrzymywanie wyświetlania dziennika komunikatów](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Spy&#43;&#43; Log Options Button](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy++_LogOptions")|Wyświetla [opcje wiadomości](../debugger/message-options-dialog-box.md) okno dialogowe. To okno dialogowe służy do systemu windows wybierz i typy do wyświetlania komunikatów. Ten formant jest dostępna tylko wtedy, gdy **wiadomości** okno jest aktywne okno.|
|![Szpieguj&#43; &#43; dziennika przycisk Wyczyść](../debugger/media/spy--_clearlog.gif "Spy ++ _ClearLog")|Czyści zawartość aktywna **wiadomości** okna. Ten formant jest dostępna tylko wtedy, gdy **wiadomości** okno jest aktywne okno.|
|![Spy&#43;&#43; Find Window Button](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy++_FindWindow")|Otwiera [Znajdź okno](../debugger/find-window-dialog-box.md) okno dialogowe, które pozwala ustawić kryteria wyszukiwania okna i wyświetlić właściwości lub komunikaty. Aby uzyskać więcej informacji, zobacz [jak: Korzystanie z narzędzia wyszukiwania](../debugger/how-to-use-the-finder-tool.md).|
|![Szpieguj&#43; &#43; znaleźć pierwszego przycisku okna](../debugger/media/icon_spy--_window.gif "Icon_Spy ++ _Window")|Wyszukuje w bieżącym widoku zgodne okno, proces, wątek lub wiadomość.|
|![Szpieguj&#43; &#43; znaleźć przycisk Dalej okna](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy ++ _NextWindow")|Wyszukuje w bieżącym widoku następne zgodne okno, proces, wątek lub wiadomość. Ta kontrolka (i polecenia menu powiązane) są dostępne tylko wtedy, gdy wynik wyszukiwania prawidłowe, która nie jest unikatowa. Na przykład gdy używasz uchwyt okna jako kryterium wyszukiwania w drzewie w oknie generuje unikatowy wyników, ponieważ istnieje tylko jedno okno w drzewie okna, który ma dojścia; w tym wypadku **Znajdź następny** nie jest dostępna.|
|![Szpieguj&#43; &#43; Znajdź poprzednie okno przycisk](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy ++ _PrevWindow")|Wyszukuje w bieżącym widoku poprzednie zgodne okno, proces, wątek lub wiadomość. Ta kontrolka (i polecenia menu powiązane) są dostępne tylko wtedy, gdy wynik wyszukiwania prawidłowe, która nie jest unikatowa. Na przykład gdy używasz uchwyt okna jako kryterium wyszukiwania w drzewie w oknie generuje unikatowy wyników, ponieważ istnieje tylko jedno okno w drzewie okna, który ma dojścia; w tym wypadku **Find Previous** nie jest dostępna.|
|![Spy&#43;&#43; Property Explorer Button](../debugger/media/icon_spy--_propexp.gif "Icon_Spy++_PropExp")|Wyświetla właściwości okna, które wybrano w widoku Windows.|
|![Szpieguj&#43; &#43; przycisk Odśwież](../debugger/media/icon_spy--_refresh.gif "Icon_Spy ++ _Refresh")|Odświeża widoki systemowe.|

## <a name="see-also"></a>Zobacz też
- [Korzystanie z programu Spy++](../debugger/using-spy-increment.md)
- [Widoki w programie Spy++](../debugger/spy-increment-views.md)
- [Spy++ — dokumentacja](../debugger/spy-increment-reference.md)