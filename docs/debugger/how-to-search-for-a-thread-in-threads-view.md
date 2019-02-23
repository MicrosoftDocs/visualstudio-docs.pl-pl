---
title: 'Instrukcje: Wyszukiwanie wątku w widoku wątków | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 665633047a37a9f219306e2baaa874a37c9344ea
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689567"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Instrukcje: Wyszukiwanie wątku w widoku wątków
Możesz wyszukać określonego wątku w widoku wątków, za pomocą ciągu Identyfikatora lub moduł jego wątku jako kryterium wyszukiwania. Można również określić początkową kierunek wyszukiwania. Pola w oknie dialogowym pokaże atrybuty zaznaczonych wątków w drzewie wątku.

### <a name="to-search-for-a-thread-in-threads-view"></a>Wyszukiwanie wątku w widoku wątków

1. Rozmieść aplikacji dla systemu windows, więc tego programu Spy ++ i aktywne [Widok wątków](../debugger/threads-view.md) okna są widoczne.

2. Z **wyszukiwania** menu, wybierz **Znajdź wątek**.

    [Okno dialogowe Wyszukiwanie wątków](../debugger/thread-search-dialog-box.md) zostanie otwarty.

3. Wpisz identyfikator wątku lub ciąg modułu jako kryterium wyszukiwania.

4. Wyczyść wszystkie pola, dla których nie chcesz określać wartości.

   > [!TIP]
   >  Aby znaleźć wszystkie wątki, które są własnością modułu, należy wyczyścić **wątku** pole tekstowe i wpisz moduł nazwy **modułu** pole. Następnie użyj **Znajdź następny** kontynuować wyszukiwanie wątków.

5. Wybierz **się** lub **dół** dla początkowej kierunek wyszukiwania.

6. Kliknij przycisk **OK**.

   Jeśli zostanie znalezione pasujące wątku, jest wyróżniona w oknie Widok wątków.