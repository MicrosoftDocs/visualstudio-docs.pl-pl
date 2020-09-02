---
title: Karta komunikaty, okno dialogowe Opcje komunikatów | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62905535"
---
# <a name="messages-tab-message-options-dialog-box"></a>Karta Komunikaty, okno dialogowe opcji komunikatów
Karta **komunikaty** służy do wybierania typów komunikatów, które mają być [wyświetlane w widoku komunikatów](../debugger/messages-view.md)oraz do określania kryteriów wyszukiwania komunikatów. Aby wyświetlić okno [dialogowe Opcje wiadomości](../debugger/message-options-dialog-box.md), wybierz pozycję **komunikaty dziennika** z menu **Spy** .

 Zazwyczaj najpierw wybiera się **grupy komunikatów**, a następnie precyzyjnie dostosowuje zaznaczenie, wybierając poszczególne **wiadomości do wyświetlenia**. Przycisk **wszystko** wybiera wszystkie typy komunikatów, a przycisk **Brak** czyści wszystkie typy.

 Na karcie **komunikaty** dostępne są następujące ustawienia:

 **Komunikaty do wyświetlenia** Wybierz konkretne komunikaty do wyświetlenia. Po utworzeniu okna nowe komunikaty można wyświetlić wszystkie komunikaty. Filtrowanie komunikatów z karty **komunikaty** dotyczy tylko nowych komunikatów, a nie komunikatów, które zostały już wyświetlone w widoku systemu Windows.

 **Grupy komunikatów** Wybierz grupy wiadomości do wyświetlenia. Dostępne są następujące grupy:

- WM_USER: przy użyciu kodu o wartości większej lub równej WM_USER

- Zarejestrowano: zarejestrowano w wywołaniu **RegisterWindowMessage**

- Nieznane: nieznane komunikaty z zakresu od 0 do (WM_USER-1)

  Należy zauważyć, że te **grupy komunikatów** nie mapują na określone wpisy w obszarze **komunikaty do wyświetlenia**. Po wybraniu grupy zaznaczenie jest stosowane bezpośrednio do strumienia komunikatów.

  Szare pole wyboru w **grupach komunikatów** wskazuje, że pola listy **wiadomości do wyświetlenia** zostały zmodyfikowane dla wiadomości w tej grupie; nie wszystkie typy komunikatów w tej grupie są zaznaczone.

  **Zapisz ustawienia jako domyślne** Zapisz bieżące ustawienia do późniejszego użycia jako opcje wyszukiwania wiadomości. Te ustawienia są również zapisywane podczas kończenia działania Spy + +.