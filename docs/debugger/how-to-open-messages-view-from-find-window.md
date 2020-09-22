---
title: Otwórz widok komunikatów z okna wyszukiwania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Messages View in Spy++, opening
- opening Messages View in Spy++
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b6240807eb82313182278251b353894545b957d
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852273"
---
# <a name="how-to-open-messages-view-from-find-window"></a>Porady: otwieranie widoku komunikatów w Znajdź okno
Może się okazać, że można użyć okna dialogowego **Znajdowanie okna** , aby wybrać okno docelowe, a następnie otworzyć widok komunikatów tego okna.

### <a name="to-open-a-messages-view-window-using-the-find-window-dialog-box"></a>Aby otworzyć okno wyświetlania komunikatów przy użyciu okna dialogowego Znajdź okno

1. Rozmieść okna w taki sposób, aby były widoczne zarówno program Spy + +, jak i okno docelowe.

2. Z menu **Spy** wybierz pozycję **Znajdź okno**.

    Zostanie otwarte okno [dialogowe Znajdowanie okna](../debugger/find-window-dialog-box.md) .

3. Na karcie **Windows** przeciągnij **Narzędzie wyszukiwania** nad oknem docelowym. Podczas przeciągania narzędzia okno dialogowe **Znajdowanie okna** wyświetla szczegóły w wybranym oknie.

   - oraz

     Jeśli masz dojście do okna, które chcesz przejrzeć (na przykład skopiowane z debugera), możesz wpisać je w polu tekstowym **uchwyt** .

4. W obszarze **Pokaż**wybierz pozycję **komunikaty**.

5. Naciśnij przycisk **OK**.

    Zostanie otwarte okno [Wyświetl puste wiadomości](../debugger/messages-view.md) , a do paska narzędzi Spy + + zostanie dodane menu **komunikatów** .

6. Z menu **wiadomości** wybierz pozycję **Opcje rejestrowania**.

    Zostanie otwarte okno [dialogowe Opcje komunikatów](../debugger/message-options-dialog-box.md) .

7. Wybierz opcje dla komunikatów, które chcesz wyświetlić.

8. Naciśnij przycisk **OK** , aby rozpocząć rejestrowanie komunikatów.

    W zależności od wybranych opcji komunikaty rozpoczynają przesyłanie strumieniowe do okna widok aktywnych komunikatów.

9. Gdy masz wystarczającą liczbę komunikatów, wybierz pozycję **Zatrzymaj rejestrowanie** z menu **wiadomości** .
