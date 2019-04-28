---
title: 'Instrukcje: Wyszukiwanie komunikatu w widoku komunikatów | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6c89a763389abe364fe70166e63b41f932581837
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430911"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Instrukcje: Wyszukiwanie komunikatu w widoku komunikatów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz wyszukać szczegółowy komunikat o błędzie w widoku komunikatów za pomocą jego uchwytu, typ lub identyfikator komunikatu jako kryterium wyszukiwania. Jeden z nich — lub kombinacji — będą prawidłowe kryteria. Można również określić początkową kierunek wyszukiwania. Pola w oknie dialogowym są wstępnie ładowane z atrybutami komunikatów aktualnie wybrany.  
  
### <a name="to-search-for-a-message-in-messages-view"></a>Aby wyszukać komunikatu w widoku komunikatów  
  
1. Rozmieść aplikacji dla systemu windows, więc tego programu Spy ++ i aktywne [widoku komunikatów](../debugger/messages-view.md) okna są widoczne.  
  
2. Z **wyszukiwania** menu, wybierz **Znajdź komunikat**.  
  
    [Wyszukiwanie komunikatów — okno dialogowe](../debugger/message-search-dialog-box.md) zostanie otwarty.  
  
3. Przeciągnij **Wyszukiwarka** przedziale żądaną. Przeciągnij narzędzie **Wyszukiwarka komunikatów** okno dialogowe wyświetla szczegóły wybranego okna.  
  
    — lub —  
  
    Jeśli uchwyt okna komunikatów, którego chcesz zbadać, wpisz go w **obsługi** pola tekstowego.  
  
    — lub —  
  
    Jeśli znasz typ komunikatu i/lub identyfikator wiadomości, które chcesz, aby wybrać je z **typu** i **komunikat** menu rozwijanych i wyczyść **obsługi** pola tekstowego.  
  
4. Wyczyść wszystkie pola, dla których nie chcesz określać wartości.  
  
   > [!TIP]
   > Aby zwiększyć czytelność ekranu, wybierz pozycję **Ukryj Spy** opcji. Ta opcja zawiera narzędzie Spy ++ oknie głównym, pozostawiając tylko **Znajdź okno** okno dialogowe widoczne na podstawie innych aplikacji. Okno główne programu Spy ++ jest przywracany po kliknięciu **OK** lub **anulować**, lub po usunięciu zaznaczenia **Ukryj Spy ++** opcji.  
  
5. Wybierz **się** lub **dół** dla początkowej kierunek wyszukiwania.  
  
6. Kliknij przycisk **OK**.  
  
   Jeśli zostanie znaleziona pasująca wiadomość, jest wyróżniona w oknie Widok komunikatów. Zobacz [widoku komunikatów](../debugger/messages-view.md).
