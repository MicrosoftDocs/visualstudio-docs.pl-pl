---
title: Wyszukiwanie komunikatu w widoku komunikatów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 7c4b597870d7a87b396b4c6e828da814c49f9bfb
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852012"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Porady: wyszukiwanie komunikatu w widoku komunikatów
Konkretny komunikat można wyszukać w widoku komunikatów przy użyciu jego uchwytu, typu lub identyfikatora komunikatu jako kryterium wyszukiwania. Jeden z tych — lub kombinacja — będzie prawidłowymi kryteriami wyszukiwania. Można również określić początkowy kierunek wyszukiwania. Pola w oknie dialogowym są wstępnie załadowane przy użyciu atrybutów aktualnie wybranego komunikatu.

### <a name="to-search-for-a-message-in-messages-view"></a>Aby wyszukać komunikat w widoku komunikatów

1. Rozmieść okna w taki sposób, że widoczne jest okno przeglądarki Spy + + i aktywne [komunikaty](../debugger/messages-view.md) .

2. Z menu **Wyszukaj** wybierz polecenie **Znajdź wiadomość**.

    Zostanie otwarte okno [dialogowe Wyszukiwanie komunikatów](../debugger/message-search-dialog-box.md) .

3. Przeciągnij **Narzędzie wyszukiwania** nad odpowiednim oknem. Podczas przeciągania narzędzia okno dialogowe **wyszukiwanie komunikatów** wyświetla szczegóły w wybranym oknie.

   - oraz

     Jeśli masz uchwyt okna, którego wiadomości chcesz przeanalizować, wpisz je w polu tekstowym **uchwyt** .

   - oraz

     Jeśli znasz typ wiadomości i/lub identyfikator wiadomości, wybierz je z menu rozwijanego **Typ** i **wiadomość** , a następnie usuń zaznaczenie pola tekstowego **uchwyt** .

4. Wyczyść wszystkie pola, dla których nie chcesz określać wartości.

   > [!TIP]
   > Aby zmniejszyć czytelność ekranu, wybierz opcję **Ukryj program Spy** . Ta opcja ukrywa główne okno programu Spy + +, pozostawiając tylko okno dialogowe **Znajdowanie okna** widoczne na wierzchu innych aplikacji. Okno główne programu Spy + + jest przywracane po kliknięciu przycisku **OK** lub **Anuluj**lub po wyczyszczeniu opcji **Ukryj program Spy + +** .

5. Wybierz pozycję w **górę** lub **w dół** , aby określić początkowy kierunek wyszukiwania.

6. Kliknij przycisk **OK**.

   Jeśli zostanie znaleziony pasujący komunikat, zostanie on wyróżniony w oknie widok komunikatów. Zobacz [Widok komunikatów](../debugger/messages-view.md).