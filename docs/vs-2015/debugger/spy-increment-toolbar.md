---
title: Spy ++ — pasek narzędzi | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a96a5765c98bf8e7d1c600fbd47478a88fa7175d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153892"
---
# <a name="spy-toolbar"></a>Spy++ — Pasek narzędzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pasek narzędzi pojawi się w pasku menu w programie Spy ++. Aby wyświetlić lub ukryć pasek narzędzi, na **widoku** menu, kliknij przycisk **narzędzi**.  
  
 Następujące elementy sterujące są dostępne na pasku narzędzi.  
  
## <a name="uielement-list"></a>Lista elementów UI  
  
|Przycisk|Efekt|  
|------------|------------|  
|![Szpieguj&#43; &#43; przycisku Windows](../debugger/media/icon-spy-windows.gif "Icon_Spy ++ systemu _Windows")|Wyświetla widok drzewa, okien i formantów w systemie. Aby uzyskać więcej informacji, zobacz [widoku Windows](../debugger/windows-view.md).|  
|![Szpieguj&#43; &#43; przetwarza przycisk](../debugger/media/icon-spy-processes.gif "Icon_Spy ++ _Processes")|Wyświetla widok drzewa procesów w systemie. Aby uzyskać więcej informacji, zobacz [widok procesy](../debugger/processes-view.md).|  
|![Szpieguj&#43; &#43; wątki przycisk](../debugger/media/icon-spy-threads.gif "Icon_Spy ++ _Threads")|Wyświetla widok drzewa wątki w systemie. Aby uzyskać więcej informacji, zobacz [Widok wątków](../debugger/threads-view.md).|  
|![Szpieguj&#43; &#43; komunikaty przycisk](../debugger/media/icon-spy-messages.gif "Icon_Spy ++ _Messages")|Tworzy okno Aby wyświetlić komunikaty okna i otwiera **opcje wiadomości** okno dialogowe, dzięki czemu można wybrać okna, w których komunikaty będą wyświetlane jak również inne opcje. Aby uzyskać więcej informacji, zobacz [widoku komunikatów](../debugger/messages-view.md).|  
|![Szpieguj&#43; &#43; dziennika przycisk Start](../debugger/media/icon-spy-startlog.gif "Icon_Spy ++ _StartLog")|Rejestrowanie komunikatów i wyświetlenie strumienia komunikatów. Ten formant jest dostępna tylko wtedy, gdy **wiadomości** okno jest aktywne okno. Aby uzyskać więcej informacji, zobacz [jak: Uruchamianie i zatrzymywanie wyświetlania dziennika komunikatów](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Szpieguj&#43; &#43; dziennika przycisk Zatrzymaj](../debugger/media/icon-spy-stoplog.gif "Icon_Spy ++ _StopLog")|Zatrzymuje komunikatu, rejestrowanie i wyświetlanie strumienia komunikatów. Ten formant jest dostępna tylko wtedy, gdy **wiadomości** okno jest aktywne okno. Aby uzyskać więcej informacji, zobacz [jak: Uruchamianie i zatrzymywanie wyświetlania dziennika komunikatów](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43;&#43; Log Options Button](../debugger/media/icon-spy-logoptions.gif "Icon_Spy++_LogOptions")|Wyświetla [opcje wiadomości](../debugger/message-options-dialog-box.md) okno dialogowe. To okno dialogowe służy do systemu windows wybierz i typy do wyświetlania komunikatów. Ten formant jest dostępna tylko wtedy, gdy **wiadomości** okno jest aktywne okno.|  
|![Szpieguj&#43; &#43; dziennika przycisk Wyczyść](../debugger/media/spy-clearlog.gif "Spy ++ _ClearLog")|Czyści zawartość aktywna **wiadomości** okna. Ten formant jest dostępna tylko wtedy, gdy **wiadomości** okno jest aktywne okno.|  
|![Szpieguj&#43; &#43; znaleźć przycisk okna](../debugger/media/icon-spy-findwindow.gif "Icon_Spy ++ _FindWindow")|Otwiera [Znajdź okno](../debugger/find-window-dialog-box.md) okno dialogowe, które pozwala ustawić kryteria wyszukiwania okna i wyświetlić właściwości lub komunikaty. Aby uzyskać więcej informacji, zobacz [jak: Korzystanie z narzędzia wyszukiwania](../debugger/how-to-use-the-finder-tool.md).|  
|![Szpieguj&#43; &#43; znaleźć pierwszego przycisku okna](../debugger/media/icon-spy-window.gif "Icon_Spy ++ _Window")|Wyszukuje w bieżącym widoku zgodne okno, proces, wątek lub wiadomość.|  
|![Szpieguj&#43; &#43; znaleźć przycisk Dalej okna](../debugger/media/icon-spy-nextwindow.gif "Icon_Spy ++ _NextWindow")|Wyszukuje w bieżącym widoku następne zgodne okno, proces, wątek lub wiadomość. Ta kontrolka (i polecenia menu powiązane) są dostępne tylko wtedy, gdy wynik wyszukiwania prawidłowe, która nie jest unikatowa. Na przykład gdy używasz uchwyt okna jako kryterium wyszukiwania w drzewie w oknie generuje unikatowy wyników, ponieważ istnieje tylko jedno okno w drzewie okna, który ma dojścia; w tym wypadku **Znajdź następny** nie jest dostępna.|  
|![Szpieguj&#43; &#43; Znajdź poprzednie okno przycisk](../debugger/media/icon-spy-prevwindow.gif "Icon_Spy ++ _PrevWindow")|Wyszukuje w bieżącym widoku poprzednie zgodne okno, proces, wątek lub wiadomość. Ta kontrolka (i polecenia menu powiązane) są dostępne tylko wtedy, gdy wynik wyszukiwania prawidłowe, która nie jest unikatowa. Na przykład gdy używasz uchwyt okna jako kryterium wyszukiwania w drzewie w oknie generuje unikatowy wyników, ponieważ istnieje tylko jedno okno w drzewie okna, który ma dojścia; w tym wypadku **Find Previous** nie jest dostępna.|  
|![Szpieguj&#43; &#43; przycisk Eksploratora właściwość](../debugger/media/icon-spy-propexp.gif "Icon_Spy ++ _PropExp")|Wyświetla właściwości okna, które wybrano w widoku Windows.|  
|![Szpieguj&#43; &#43; przycisk Odśwież](../debugger/media/icon-spy-refresh.gif "Icon_Spy ++ _Refresh")|Odświeża widoki systemowe.|  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z programu Spy ++](../debugger/using-spy-increment.md)   
 [Widoków programu Spy ++](../debugger/spy-increment-views.md)   
 [Spy++ — dokumentacja](../debugger/spy-increment-reference.md)
