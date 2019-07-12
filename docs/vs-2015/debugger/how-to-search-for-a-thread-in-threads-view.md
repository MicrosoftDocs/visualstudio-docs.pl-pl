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
ms.openlocfilehash: d5974bc962faf439af8de5d50bf51bad3d824647
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "64827356"
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
   > Aby znaleźć wszystkie wątki, które są własnością modułu, należy wyczyścić **wątku** pole tekstowe i wpisz moduł nazwy **modułu** pole. Następnie użyj **Znajdź następny** kontynuować wyszukiwanie wątków.  
  
5. Wybierz **się** lub **dół** dla początkowej kierunek wyszukiwania.  
  
6. Kliknij przycisk **OK**.  
  
   Jeśli zostanie znalezione pasujące wątku, jest wyróżniona w oknie Widok wątków.
