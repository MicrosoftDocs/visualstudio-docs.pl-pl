---
title: 'Instrukcje: Wyszukiwanie wątku w widoku wątków | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e7987b4da158572d22d609b095877f6d125512c9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776225"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Instrukcje: Wyszukiwanie wątku w widoku wątków
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
