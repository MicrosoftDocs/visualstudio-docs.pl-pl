---
title: Widoku komunikatów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b20ed28518c9156e82c6fe75ecceda74c66615d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60049132"
---
# <a name="messages-view"></a>Widok komunikatów
Każde okno ma strumienia skojarzonych komunikatów. Okno widoku komunikatów wyświetla ten strumień komunikatu. Uchwyt okna, kod komunikatu i wiadomości są wyświetlane. Można utworzyć widoku komunikatów dla wątku lub również proces. Dzięki temu można wyświetlić komunikaty wysyłane do wszystkich okien należące do określonego proces lub wątek, który jest szczególnie przydatne w przypadku przechwytywania komunikaty inicjowania okna.

 Typowe okno widoku komunikatów pojawia się poniżej. Pamiętaj, że pierwsza kolumna zawiera uchwyt okna, a druga kolumna zawiera kod komunikatu (wyjaśnione w [kody komunikatów](../debugger/message-codes.md)). Zdekodowany komunikat parametrów i zwracanych wartości są po prawej stronie.

 ![Spy&#43;&#43; Messages View](../debugger/media/spy--_messagesview.png "Spy++_MessagesView") Spy++ Messages View

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
 [Kontrolowanie widoku komunikatów](../debugger/how-to-control-messages-view.md) wyjaśnia, jak zarządzać widoku komunikatów.

 [Otwieranie widoku komunikatów w Znajdź okno](../debugger/how-to-open-messages-view-from-find-window.md) wyjaśnia, jak otwieranie widoku komunikatów w Znajdź okno dialogowe.

 [Wyszukiwanie komunikatu w widoku komunikatów](../debugger/how-to-search-for-a-message-in-messages-view.md) wyjaśnia, jak znaleźć szczegółowy komunikat o błędzie w widoku komunikatów.

 [Uruchamianie i zatrzymywanie wyświetlania dziennika komunikatów](../debugger/how-to-start-and-stop-the-message-log-display.md) wyjaśnia, jak uruchamianie i zatrzymywanie rejestrowania komunikatów.

 [Kody komunikatów](../debugger/message-codes.md) definiuje kody komunikatów na liście w widoku komunikatów.

 [Wyświetlanie właściwości komunikatu](../debugger/how-to-display-message-properties.md) sposób wyświetlić więcej informacji na temat wiadomości.

## <a name="related-sections"></a>Sekcje pokrewne
 [Widoków programu Spy ++](../debugger/spy-increment-views.md) wyjaśnia widoków programu Spy ++ drzewa systemu windows, wiadomości, procesów i wątków.

 [Korzystanie z programu Spy ++](../debugger/using-spy-increment.md) wprowadzono narzędzie Spy ++ i opisano, jak mogą być używane.

 [Okno dialogowe Opcje komunikatów](../debugger/message-options-dialog-box.md) używany do wybierania, wiadomości, które są wymienione w bieżącym widokiem wiadomości.

 [Okno dialogowe Wyszukiwanie komunikatów](../debugger/message-search-dialog-box.md) używana do znajdowania węzeł, aby uzyskać szczegółowy komunikat o błędzie w widoku komunikatów.

 [Okno dialogowe Właściwości komunikatu](../debugger/message-properties-dialog-box.md) używany do wyświetlania właściwości wiadomości wybrany w widoku komunikatów.

 [Spy ++ — odwołanie](../debugger/spy-increment-reference.md) zawiera sekcje opisujące każdy Spy ++ menu i okno dialogowe.