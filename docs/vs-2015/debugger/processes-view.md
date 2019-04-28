---
title: Widok procesów | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d8b9c04d1cabd44418c70725ef331c9c4b5ec67e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62580512"
---
# <a name="processes-view"></a>Widok procesów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok procesów przedstawia drzewo wszystkich aktywnych procesów w Twoim systemie. Nazwa procesu modułu i identyfikator są wyświetlane. Użyj widoku procesów, jeśli chcesz sprawdzić procesu określonym systemie zazwyczaj odnosi się do wykonywania programu. Procesy są identyfikowane przez nazwy modułów lub zostały one oznaczone "procesy systemowe".  
  
 Program Microsoft Windows obsługuje wiele procesów. Każdy proces może mieć jeden lub więcej wątków i każdy wątek może zawierać jeden lub kilka skojarzonych okien najwyższego poziomu. Każde okno najwyższego poziomu może posiadać kilka okien. A + symbol informuje, że poziom jest zwinięta. W widoku zwiniętym składa się z jeden wiersz dla każdego procesu. Kliknij pozycję + symbolu, aby rozwinąć poziomu.  
  
 Użyj widoku procesów, jeśli chcesz sprawdzić procesu określonym systemie zazwyczaj odnosi się do wykonywania programu. Procesy są identyfikowane przez nazwy modułów lub zostały one oznaczone "procesy systemowe". Aby znaleźć proces, Zwiń drzewo i listę można przeszukiwać.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-open-the-processes-view"></a>Aby otworzyć widok procesów  
  
1. Z **Spy** menu, wybierz **procesy**.  
  
   ![Spy&#43;&#43; Processes View](../debugger/media/spy-processes.png "Spy++_Processes")  
   Widok procesów programu Spy ++  
  
   Powyższy rysunek przedstawia widok procesów z węzłami procesu i wątku, rozwinięty.  
  
### <a name="in-this-section"></a>W tej sekcji  
 [Trwa wyszukiwanie procesu w widoku procesów](../debugger/how-to-search-for-a-process-in-processes-view.md)  
 Wyjaśnia, jak można znaleźć określonego procesu w widoku procesów.  
  
 [Wyświetlanie właściwości procesu](../debugger/how-to-display-process-properties.md)  
 Wyjaśnia, jak wyświetlić więcej informacji na temat wiadomości.  
  
### <a name="related-sections"></a>Sekcje pokrewne  
 [Widoki w programie Spy++](../debugger/spy-increment-views.md)  
 W tym artykule wyjaśniono widoków programu Spy ++ drzewa systemu windows, wiadomości, procesów i wątków.  
  
 [Korzystanie z programu Spy++](../debugger/using-spy-increment.md)  
 Wprowadza narzędzie Spy ++ i wyjaśnia, jak mogą być używane.  
  
 [Wyszukiwanie procesów, okno dialogowe](../debugger/process-search-dialog-box.md)  
 Umożliwia znalezienie węzła dla określonego procesu w widoku procesów.  
  
 [Właściwości procesu, okno dialogowe](../debugger/process-properties-dialog-box.md)  
 Wyświetla właściwości wybranego w widoku procesów procesu.  
  
 [Spy++ — dokumentacja](../debugger/spy-increment-reference.md)  
 Zawiera sekcje, zawierająca opis każdego Spy ++ menu i okno dialogowe.
