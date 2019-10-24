---
title: Pasek narzędzi Spy + + | Microsoft Docs
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
ms.openlocfilehash: 4fa1dfe0917fece3c814678295c5abd6013b426b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729738"
---
# <a name="spy-toolbar"></a>Spy++ — Pasek narzędzi
Pasek narzędzi zostanie wyświetlony pod paskiem menu w programie Spy + +. Aby wyświetlić lub ukryć pasek narzędzi, w menu **Widok** kliknij polecenie **pasek narzędzi**.

 Na pasku narzędzi są dostępne następujące kontrolki.

## <a name="uielement-list"></a>Lista elementów UI

|Przycisk|Efekt|
|------------|------------|
|![Przycisk&#43; &#43; Spy systemu Windows](../debugger/media/icon_spy--_windows.gif "Icon_Spy + + _Windows")|Wyświetla widok drzewa okien i kontrolek w systemie. Aby uzyskać więcej informacji, zobacz [Widok systemu Windows](../debugger/windows-view.md).|
|![Przycisk&#43; &#43; procesy Spy](../debugger/media/icon_spy--_processes.gif "Icon_Spy + + _Processes")|Wyświetla widok drzewa procesów w systemie. Aby uzyskać więcej informacji, zobacz [widok procesów](../debugger/processes-view.md).|
|![Przycisk&#43; &#43; Spy Threads](../debugger/media/icon_spy--_threads.gif "Icon_Spy + + _Threads")|Wyświetla widok drzewa wątków w systemie. Aby uzyskać więcej informacji, zobacz [Widok wątków](../debugger/threads-view.md).|
|![Przycisk&#43; &#43; komunikatów Spy](../debugger/media/icon_spy--_messages.gif "Icon_Spy + + _Messages")|Tworzy okno do wyświetlania komunikatów okna i otwiera okno dialogowe **Opcje wiadomości** , dzięki czemu można wybrać okno, którego komunikaty będą wyświetlane, a także wybrać inne opcje. Aby uzyskać więcej informacji, zobacz [Widok komunikatów](../debugger/messages-view.md).|
|![Przycisk&#43; &#43; Uruchom dziennik w programie Spy](../debugger/media/icon_spy--_startlog.gif "Icon_Spy + + _StartLog")|Uruchamia rejestrowanie komunikatów i wyświetla strumień komunikatów. Ten formant jest dostępny tylko wtedy, gdy okno **komunikatów** jest oknem aktywnym. Aby uzyskać więcej informacji, zobacz [jak: uruchamianie i zatrzymywanie wyświetlania dziennika komunikatów](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Przycisk&#43; &#43; zatrzymywania dziennika w programie Spy](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy + + _StopLog")|Powoduje zatrzymanie rejestrowania komunikatów i wyświetlenie strumienia komunikatów. Ten formant jest dostępny tylko wtedy, gdy okno **komunikatów** jest oknem aktywnym. Aby uzyskać więcej informacji, zobacz [jak: uruchamianie i zatrzymywanie wyświetlania dziennika komunikatów](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Przycisk&#43; &#43; opcji dziennika Spy](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy + + _LogOptions")|Wyświetla okno dialogowe [Opcje wiadomości](../debugger/message-options-dialog-box.md) . To okno dialogowe służy do wybierania typów okien i komunikatów do wyświetlania. Ten formant jest dostępny tylko wtedy, gdy okno **komunikatów** jest oknem aktywnym.|
|![Przycisk&#43; &#43; "Wyczyść dziennik" w usłudze Spy](../debugger/media/spy--_clearlog.gif "_ClearLog")|Czyści zawartość okna aktywne **komunikaty** . Ten formant jest dostępny tylko wtedy, gdy okno **komunikatów** jest oknem aktywnym.|
|![Przycisk&#43; &#43; okna wyszukiwania Spy](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy + + _FindWindow")|Otwiera okno dialogowe [Znajdowanie okna](../debugger/find-window-dialog-box.md) , które umożliwia ustawianie kryteriów wyszukiwania okna i wyświetlanie właściwości lub komunikatów. Aby uzyskać więcej informacji, zobacz [How to: Use the Finder Tool](../debugger/how-to-use-the-finder-tool.md).|
|![Przycisk&#43; &#43; Spy Znajdź pierwsze okno](../debugger/media/icon_spy--_window.gif "Icon_Spy + + _Window")|Wyszukuje w bieżącym widoku pasujące okno, proces, wątek lub komunikat.|
|![Przycisk&#43; &#43; Spy Znajdź następny okno](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy + + _NextWindow")|Wyszukuje w bieżącym widoku następne pasujące okno, proces, wątek lub komunikat. Ten formant (i powiązane polecenie menu) jest dostępny tylko wtedy, gdy istnieje prawidłowy wynik wyszukiwania, który nie jest unikatowy. Na przykład w przypadku korzystania z uchwytu okna jako kryterium wyszukiwania w drzewie okna tworzy ona unikatowe wyniki, ponieważ w drzewie okien istnieje tylko jedno okno, które ma ten uchwyt; w tym wystąpieniu **Znajdź następny** jest niedostępny.|
|![Przycisk&#43; &#43; Spy Znajdź poprzednie okno](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy + + _PrevWindow")|Wyszukuje w bieżącym widoku poprzednie zgodne okno, proces, wątek lub komunikat. Ten formant (i powiązane polecenie menu) jest dostępny tylko wtedy, gdy istnieje prawidłowy wynik wyszukiwania, który nie jest unikatowy. Na przykład w przypadku korzystania z uchwytu okna jako kryterium wyszukiwania w drzewie okna tworzy ona unikatowe wyniki, ponieważ w drzewie okien istnieje tylko jedno okno, które ma ten uchwyt; w tym wystąpieniu **Znajdź poprzedni** nie jest dostępny.|
|![Przycisk&#43; &#43; Eksploratora właściwości Spy](../debugger/media/icon_spy--_propexp.gif "Icon_Spy + + _PropExp")|Wyświetla właściwości okna wybranego w widoku systemu Windows.|
|![Przycisk&#43; &#43; "Spy Refresh"](../debugger/media/icon_spy--_refresh.gif "Icon_Spy + + _Refresh")|Odświeża widoki systemowe.|

## <a name="see-also"></a>Zobacz także
- [Korzystanie z programu Spy++](../debugger/using-spy-increment.md)
- [Widoki w programie Spy++](../debugger/spy-increment-views.md)
- [Spy++ — dokumentacja](../debugger/spy-increment-reference.md)