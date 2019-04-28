---
title: 'Instrukcje: Wyszukiwanie procesu w widoku procesów | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a6b57226b14963759bb4d78afff3beb5559a63e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387595"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Instrukcje: Wyszukiwanie procesu w widoku procesów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz wyszukać określonego procesu w widoku procesów za pomocą ciągu Identyfikatora lub moduł jego procesu jako kryterium wyszukiwania. Można również określić początkową kierunek wyszukiwania. Pola w oknie dialogowym zostaną wyświetlone atrybuty wybranego procesu w drzewo procesów.  
  
### <a name="to-search-for-a-process-in-processes-view"></a>Wyszukiwanie procesu w widoku procesów  
  
1. Rozmieść aplikacji dla systemu windows, więc tego programu Spy ++ i aktywne [widok procesy](../debugger/processes-view.md) okna są widoczne.  
  
2. Z **wyszukiwania** menu, wybierz **Znajdź proces**  
  
    [Okno dialogowe Wyszukiwanie procesów](../debugger/process-search-dialog-box.md) zostanie otwarty.  
  
3. Wpisz identyfikator procesu lub ciąg modułu jako kryterium wyszukiwania.  
  
4. Wyczyść wszystkie pola, dla których nie chcesz określać wartości.  
  
   > [!TIP]
   > Aby znaleźć wszystkie procesy, które są własnością modułu, należy wyczyścić **procesu** pole, a następnie wpisz nazwę modułu w **modułu** pole. Następnie użyj **Znajdź następny** kontynuować wyszukiwanie procesów.  
  
5. Wybierz **się** lub **dół** dla początkowej kierunek wyszukiwania.  
  
6. Kliknij przycisk **OK**.  
  
   Jeśli proces dopasowywania zostanie znaleziony, jest wyróżniona na **widok procesu** okna.
