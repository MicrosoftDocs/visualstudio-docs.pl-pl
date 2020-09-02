---
title: Widok komunikatów | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62845858"
---
# <a name="messages-view"></a>Widok komunikatów
Każde okno ma skojarzony strumień komunikatów. W oknie widok komunikatów jest wyświetlany ten strumień komunikatów. Wyświetlany jest uchwyt okna, kod komunikatu i komunikat. Możesz również utworzyć widok komunikatów dla wątku lub procesu. Umożliwia to wyświetlanie komunikatów wysyłanych do wszystkich okien należących do określonego procesu lub wątku, co jest szczególnie przydatne w przypadku przechwytywania komunikatów o inicjacji okna.

 Poniżej znajduje się typowe okno wyświetlania komunikatów. Należy zauważyć, że pierwsza kolumna zawiera uchwyt okna, a druga kolumna zawiera kod komunikatu (wyjaśniony w [kodach komunikatów](../debugger/message-codes.md)). Dekodowane parametry komunikatu i zwracane wartości są po prawej stronie.

 ![Widok komunikatów&#43;&#43; Spy](../debugger/media/spy--_messagesview.png "_MessagesView Spy + +") Widok komunikatów w programie Spy + +

## <a name="procedures"></a>Procedury

#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Aby otworzyć widok komunikatów dla okna, procesu lub wątku

1. Przenieś fokus do okna widok [systemu Windows](../debugger/windows-view.md), [procesów widoku](../debugger/processes-view.md)lub [wątków](../debugger/threads-view.md) .

2. Znajdź węzeł elementu, którego wiadomości chcesz sprawdzić, i wybierz go.

3. Z menu **Spy** wybierz pozycję **komunikaty dziennika**.

     Zostanie otwarte okno [dialogowe Opcje komunikatów](../debugger/message-options-dialog-box.md) .

4. Wybierz Opcje wiadomości, które chcesz wyświetlić.

5. Naciśnij przycisk **OK** , aby rozpocząć rejestrowanie komunikatów.

     Zostanie otwarte okno widok komunikatów, a do paska narzędzi Spy + + zostanie dodane menu **komunikatów** . W zależności od wybranych opcji komunikaty rozpoczynają przesyłanie strumieniowe do okna widok aktywnych komunikatów.

6. Gdy masz wystarczającą liczbę komunikatów, wybierz pozycję **Zatrzymaj rejestrowanie** z menu **wiadomości** .

## <a name="in-this-section"></a>W tej sekcji
 [Kontrolowanie widoku komunikatów](../debugger/how-to-control-messages-view.md) Wyjaśnia, jak zarządzać widokiem komunikatów.

 [Otwieranie widoku komunikatów z okna wyszukiwania](../debugger/how-to-open-messages-view-from-find-window.md) Wyjaśnia, jak otworzyć widok komunikatów z okna dialogowego Znajdowanie okna.

 [Wyszukiwanie komunikatu w widoku komunikatów](../debugger/how-to-search-for-a-message-in-messages-view.md) Wyjaśnia, jak znaleźć konkretny komunikat w widoku komunikatów.

 [Uruchamianie i zatrzymywanie wyświetlania dziennika komunikatów](../debugger/how-to-start-and-stop-the-message-log-display.md) Wyjaśnia sposób uruchamiania i zatrzymywania rejestrowania komunikatów.

 [Kody komunikatów](../debugger/message-codes.md) Definiuje kody komunikatów znajdujących się w widoku komunikatów.

 [Wyświetlanie właściwości komunikatów](../debugger/how-to-display-message-properties.md) Jak wyświetlić więcej informacji o komunikacie.

## <a name="related-sections"></a>Sekcje pokrewne
 [Widoki Spy + +](../debugger/spy-increment-views.md) Wyjaśnia widoki drzewa Spy + + systemu Windows, komunikatów, procesów i wątków.

 [Korzystanie z programu Spy + +](../debugger/using-spy-increment.md) Wprowadzenie do narzędzia Spy + + i wyjaśnienie, jak można go użyć.

 Okno [dialogowe opcji komunikatów](../debugger/message-options-dialog-box.md) Służy do wybierania komunikatów, które są wyświetlane w widoku aktywnych komunikatów.

 [Wyszukiwanie komunikatów](../debugger/message-search-dialog-box.md) — okno dialogowe Służy do znajdowania węzła określonego komunikatu w widoku komunikatów.

 Okno [dialogowe Właściwości komunikatu](../debugger/message-properties-dialog-box.md) Służy do wyświetlania właściwości komunikatu wybranego w widoku wiadomości.

 [Spy + + — Odwołanie](../debugger/spy-increment-reference.md) Zawiera sekcje opisujące poszczególne menu Spy + + i okna dialogowego.