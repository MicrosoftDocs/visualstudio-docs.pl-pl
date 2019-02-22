---
title: 'Instrukcje: Wyszukiwanie komunikatu w widoku komunikatów | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5830076ab3bd0ea59912900e8a14c807d7c0941
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696262"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Instrukcje: Wyszukiwanie komunikatu w widoku komunikatów
Możesz wyszukać szczegółowy komunikat o błędzie w widoku komunikatów za pomocą jego uchwytu, typ lub identyfikator komunikatu jako kryterium wyszukiwania. Jeden z nich — lub kombinacji — będą prawidłowe kryteria. Można również określić początkową kierunek wyszukiwania. Pola w oknie dialogowym są wstępnie ładowane z atrybutami komunikatów aktualnie wybrany.

### <a name="to-search-for-a-message-in-messages-view"></a>Aby wyszukać komunikatu w widoku komunikatów

1. Rozmieść aplikacji dla systemu windows, więc tego programu Spy ++ i aktywne [widoku komunikatów](../debugger/messages-view.md) okna są widoczne.

2. Z **wyszukiwania** menu, wybierz **Znajdź komunikat**.

    [Wyszukiwanie komunikatów — okno dialogowe](../debugger/message-search-dialog-box.md) zostanie otwarty.

3. Przeciągnij **Wyszukiwarka** przedziale żądaną. Przeciągnij narzędzie **Wyszukiwarka komunikatów** okno dialogowe wyświetla szczegóły wybranego okna.

   - lub —

     Jeśli uchwyt okna komunikatów, którego chcesz zbadać, wpisz go w **obsługi** pola tekstowego.

   - lub —

     Jeśli znasz typ komunikatu i/lub identyfikator wiadomości, które chcesz, aby wybrać je z **typu** i **komunikat** menu rozwijanych i wyczyść **obsługi** pola tekstowego.

4. Wyczyść wszystkie pola, dla których nie chcesz określać wartości.

   > [!TIP]
   >  Aby zwiększyć czytelność ekranu, wybierz pozycję **Ukryj Spy** opcji. Ta opcja zawiera narzędzie Spy ++ oknie głównym, pozostawiając tylko **Znajdź okno** okno dialogowe widoczne na podstawie innych aplikacji. Okno główne programu Spy ++ jest przywracany po kliknięciu **OK** lub **anulować**, lub po usunięciu zaznaczenia **Ukryj Spy ++** opcji.

5. Wybierz **się** lub **dół** dla początkowej kierunek wyszukiwania.

6. Kliknij przycisk **OK**.

   Jeśli zostanie znaleziona pasująca wiadomość, jest wyróżniona w oknie Widok komunikatów. Zobacz [widoku komunikatów](../debugger/messages-view.md).