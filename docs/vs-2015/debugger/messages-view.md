---
title: Widoku komunikatów | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3765b9804224549c98b57cd1b0a44f0330d278b5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157491"
---
# <a name="messages-view"></a>Widok komunikatów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Każde okno ma strumienia skojarzonych komunikatów. Okno widoku komunikatów wyświetla ten strumień komunikatu. Uchwyt okna, kod komunikatu i wiadomości są wyświetlane. Można utworzyć widoku komunikatów dla wątku lub również proces. Dzięki temu można wyświetlić komunikaty wysyłane do wszystkich okien należące do określonego proces lub wątek, który jest szczególnie przydatne w przypadku przechwytywania komunikaty inicjowania okna.  
  
 Typowe okno widoku komunikatów pojawia się poniżej. Pamiętaj, że pierwsza kolumna zawiera uchwyt okna, a druga kolumna zawiera kod komunikatu (wyjaśnione w [kody komunikatów](../debugger/message-codes.md)). Zdekodowany komunikat parametrów i zwracanych wartości są po prawej stronie.  
  
 ![Szpieguj&#43; &#43; widoku komunikatów](../debugger/media/spy-messagesview.png "Spy ++ _MessagesView")  
Widok komunikatów programu Spy ++  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Aby otworzyć widok wiadomości dla okna, proces lub wątek  
  
1. Przenieś fokus do [widoku Windows](../debugger/windows-view.md), [widok procesy](../debugger/processes-view.md), lub [Widok wątków](../debugger/threads-view.md) okna.  
  
2. Znajdź węzeł dla elementu, dla których wiadomości, które chcesz zbadać i zaznacz go.  
  
3. Z **Spy** menu, wybierz **komunikaty w dzienniku**.  
  
     [Okno dialogowe opcji komunikatów](../debugger/message-options-dialog-box.md) zostanie otwarty.  
  
4. Wybierz opcje dla komunikatu, który chcesz wyświetlić.  
  
5. Naciśnij klawisz **OK** aby rozpocząć rejestrowanie komunikatów.  
  
     Zostanie otwarte okno Widok wiadomości oraz w **wiadomości** menu jest dodawany do programu Spy ++ — pasek narzędzi. W zależności od opcji wybranych wiadomości było rozpocząć przesyłanie strumieniowe do aktywnego okna widoku komunikatów.  
  
6. Jeśli masz wystarczającej liczby wiadomości, wybierz **Zatrzymaj rejestrowanie** z **wiadomości** menu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kontrolowanie widoku komunikatów](../debugger/how-to-control-messages-view.md)  
 Wyjaśnia, jak zarządzać widoku komunikatów.  
  
 [Wyszukiwanie komunikatu w widoku komunikatów](../debugger/how-to-search-for-a-message-in-messages-view.md)  
 Wyjaśnia, jak znaleźć szczegółowy komunikat o błędzie w widoku komunikatów.  
  
 [Uruchamianie i zatrzymywanie wyświetlania dziennika komunikatów](../debugger/how-to-start-and-stop-the-message-log-display.md)  
 Wyjaśnia, jak uruchamianie i zatrzymywanie rejestrowania komunikatów.  
  
 [Kody komunikatów](../debugger/message-codes.md)  
 Definiuje kody komunikaty wyświetlane w widoku komunikatów.  
  
 [Wyświetlanie właściwości komunikatu](../debugger/how-to-display-message-properties.md)  
 Jak wyświetlić więcej informacji na temat wiadomości.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Widoki w programie Spy++](../debugger/spy-increment-views.md)  
 W tym artykule wyjaśniono widoków programu Spy ++ drzewa systemu windows, wiadomości, procesów i wątków.  
  
 [Korzystanie z programu Spy++](../debugger/using-spy-increment.md)  
 Wprowadza narzędzie Spy ++ i wyjaśnia, jak mogą być używane.  
  
 [Opcje komunikatów, okno dialogowe](../debugger/message-options-dialog-box.md)  
 Używany do wybierania, wiadomości, które są wymienione w bieżącym widokiem wiadomości.  
  
 [Wyszukiwanie komunikatów, okno dialogowe](../debugger/message-search-dialog-box.md)  
 Umożliwia znalezienie węzeł, aby uzyskać szczegółowy komunikat o błędzie w widoku komunikatów.  
  
 [Właściwości komunikatu, okno dialogowe](../debugger/message-properties-dialog-box.md)  
 Umożliwia wyświetlenie właściwości wiadomości wybrany w widoku komunikatów.  
  
 [Spy++ — dokumentacja](../debugger/spy-increment-reference.md)  
 Zawiera sekcje, zawierająca opis każdego Spy ++ menu i okno dialogowe.
