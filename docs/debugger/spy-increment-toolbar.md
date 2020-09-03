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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72729738"
---
# <a name="spy-toolbar"></a>Spy++ — Pasek narzędzi
Pasek narzędzi zostanie wyświetlony pod paskiem menu w programie Spy + +. Aby wyświetlić lub ukryć pasek narzędzi, w menu **Widok** kliknij polecenie **pasek narzędzi**.

 Na pasku narzędzi są dostępne następujące kontrolki.

## <a name="uielement-list"></a>Lista elementów UI

|Przycisk|Efekt|
|------------|------------|
|![Przycisk Spy&#43;&#43; systemu Windows](../debugger/media/icon_spy--_windows.gif "Icon_Spy + + _Windows")|Wyświetla widok drzewa okien i kontrolek w systemie. Aby uzyskać więcej informacji, zobacz [Widok systemu Windows](../debugger/windows-view.md).|
|![Przycisk procesów&#43;&#43; Spy](../debugger/media/icon_spy--_processes.gif "Icon_Spy + + _Processes")|Wyświetla widok drzewa procesów w systemie. Aby uzyskać więcej informacji, zobacz [widok procesów](../debugger/processes-view.md).|
|![Przycisk Spy&#43;&#43; wątki](../debugger/media/icon_spy--_threads.gif "Icon_Spy + + _Threads")|Wyświetla widok drzewa wątków w systemie. Aby uzyskać więcej informacji, zobacz [Widok wątków](../debugger/threads-view.md).|
|![Przycisk komunikatów&#43;&#43; Spy](../debugger/media/icon_spy--_messages.gif "Icon_Spy + + _Messages")|Tworzy okno do wyświetlania komunikatów okna i otwiera okno dialogowe **Opcje wiadomości** , dzięki czemu można wybrać okno, którego komunikaty będą wyświetlane, a także wybrać inne opcje. Aby uzyskać więcej informacji, zobacz [Widok komunikatów](../debugger/messages-view.md).|
|![Przycisk Uruchom dziennik w programie Spy&#43;&#43; ](../debugger/media/icon_spy--_startlog.gif "Icon_Spy + + _StartLog")|Uruchamia rejestrowanie komunikatów i wyświetla strumień komunikatów. Ten formant jest dostępny tylko wtedy, gdy okno **komunikatów** jest oknem aktywnym. Aby uzyskać więcej informacji, zobacz [jak: uruchamianie i zatrzymywanie wyświetlania dziennika komunikatów](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Przycisk zatrzymywania dziennika&#43;&#43; Spy](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy + + _StopLog")|Powoduje zatrzymanie rejestrowania komunikatów i wyświetlenie strumienia komunikatów. Ten formant jest dostępny tylko wtedy, gdy okno **komunikatów** jest oknem aktywnym. Aby uzyskać więcej informacji, zobacz [jak: uruchamianie i zatrzymywanie wyświetlania dziennika komunikatów](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Przycisk opcji dziennika&#43;&#43; Spy](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy + + _LogOptions")|Wyświetla okno dialogowe [Opcje wiadomości](../debugger/message-options-dialog-box.md) . To okno dialogowe służy do wybierania typów okien i komunikatów do wyświetlania. Ten formant jest dostępny tylko wtedy, gdy okno **komunikatów** jest oknem aktywnym.|
|![Przycisk Spy&#43;&#43; Wyczyść dziennik](../debugger/media/spy--_clearlog.gif "_ClearLog Spy + +")|Czyści zawartość okna aktywne **komunikaty** . Ten formant jest dostępny tylko wtedy, gdy okno **komunikatów** jest oknem aktywnym.|
|![Przycisk okna wyszukiwania Spy&#43;&#43; ](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy + + _FindWindow")|Otwiera okno dialogowe [Znajdowanie okna](../debugger/find-window-dialog-box.md) , które umożliwia ustawianie kryteriów wyszukiwania okna i wyświetlanie właściwości lub komunikatów. Aby uzyskać więcej informacji, zobacz [How to: Use the Finder Tool](../debugger/how-to-use-the-finder-tool.md).|
|![Przycisk Spy&#43;&#43; Znajdowanie pierwszego okna](../debugger/media/icon_spy--_window.gif "Icon_Spy + + _Window")|Wyszukuje w bieżącym widoku pasujące okno, proces, wątek lub komunikat.|
|![Przycisk Spy&#43;&#43; znaleźć następnego okna](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy + + _NextWindow")|Wyszukuje w bieżącym widoku następne pasujące okno, proces, wątek lub komunikat. Ten formant (i powiązane polecenie menu) jest dostępny tylko wtedy, gdy istnieje prawidłowy wynik wyszukiwania, który nie jest unikatowy. Na przykład w przypadku korzystania z uchwytu okna jako kryterium wyszukiwania w drzewie okna tworzy ona unikatowe wyniki, ponieważ w drzewie okien istnieje tylko jedno okno, które ma ten uchwyt; w tym wystąpieniu **Znajdź następny** jest niedostępny.|
|![Przycisk Spy&#43;&#43; Znajdź poprzednie okno](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy + + _PrevWindow")|Wyszukuje w bieżącym widoku poprzednie zgodne okno, proces, wątek lub komunikat. Ten formant (i powiązane polecenie menu) jest dostępny tylko wtedy, gdy istnieje prawidłowy wynik wyszukiwania, który nie jest unikatowy. Na przykład w przypadku korzystania z uchwytu okna jako kryterium wyszukiwania w drzewie okna tworzy ona unikatowe wyniki, ponieważ w drzewie okien istnieje tylko jedno okno, które ma ten uchwyt; w tym wystąpieniu **Znajdź poprzedni** nie jest dostępny.|
|![Przycisk Eksploratora właściwości programu Spy&#43;&#43; ](../debugger/media/icon_spy--_propexp.gif "Icon_Spy + + _PropExp")|Wyświetla właściwości okna wybranego w widoku systemu Windows.|
|![Przycisk "Spy&#43;&#43; Refresh"](../debugger/media/icon_spy--_refresh.gif "Icon_Spy + + _Refresh")|Odświeża widoki systemowe.|

## <a name="see-also"></a>Zobacz też
- [Korzystanie z programu Spy++](../debugger/using-spy-increment.md)
- [Spy++ — Widoki](../debugger/spy-increment-views.md)
- [Spy++ — Odwołanie](../debugger/spy-increment-reference.md)