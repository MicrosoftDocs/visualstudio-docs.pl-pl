---
title: Karta komunikaty, okno dialogowe opcji komunikatów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de50e6fe997ce10266cbb51f2fd91c318ab2bd1f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905535"
---
# <a name="messages-tab-message-options-dialog-box"></a>Karta Komunikaty, okno dialogowe opcji komunikatów
Użyj **wiadomości** kartę, aby wybrać, które wiadomości typów do listy w [widoku komunikatów](../debugger/messages-view.md)i określić kryteria wyszukiwania komunikatu. Aby wyświetlić [okno dialogowe opcji komunikatów](../debugger/message-options-dialog-box.md), wybierz **komunikaty dziennika** z **Spy** menu.

 Zwykle, najpierw wybierz **grupy komunikatów**, a następnie dostosować wybór, wybierając poszczególne **wiadomości do widoku**. **Wszystkich** przycisk wybiera wszystkie typy komunikatów, a **Brak** przycisku powoduje wyczyszczenie wszystkich typów.

 Następujące ustawienia są dostępne na **wiadomości** karty:

 **Komunikaty do widoku** wybierz określone komunikaty do wyświetlenia. Podczas tworzenia nowego okna komunikatów ją wyświetlić wszystkie komunikaty. Podczas filtrowania wiadomości z **wiadomości** kartę, czy filtr ma zastosowanie tylko do nowych wiadomości, a nie w przypadku wiadomości, które już zostały wyświetlone w widoku Windows.

 **Komunikat grup** wybierz grupy komunikat do wyświetlenia. Dostępne grupy obejmują:

- WM_USER: z kodem, jest większa niż lub równa WM_USER

- Zarejestrowany: zarejestrowany **RegisterWindowMessage** wywołania

- Nieznane: nieznany komunikaty w zakresie od 0 do (WM_USER - 1)

  Należy pamiętać, że te **grupy komunikatów** nie zostaną zamapowani na określonych wpisów w obszarze **widoku komunikatów**. Po wybraniu grupy, wybór jest stosowane bezpośrednio do strumienia komunikatów.

  Wygaszone pole wyboru w ramach **grupy komunikatów** wskazuje, że **widoku komunikatów** pole listy został zmodyfikowany dla wiadomości w tej grupie; nie wszystkie typy komunikatów w tej grupie są zaznaczone.

  **Zapisz ustawienia jako domyślne** zapisać bieżące ustawienia w celu późniejszego użycia jako opcje wyszukiwania komunikatu. Te ustawienia są również zapisywane podczas zamykania programu Spy ++.