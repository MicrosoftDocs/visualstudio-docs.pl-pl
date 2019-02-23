---
title: Widok procesów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99ba60021410f1965e05f7c5479231013d53cb71
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697627"
---
# <a name="processes-view"></a>Widok procesów
Widok procesów przedstawia drzewo wszystkich aktywnych procesów w Twoim systemie. Nazwa procesu modułu i identyfikator są wyświetlane. Użyj widoku procesów, jeśli chcesz sprawdzić procesu określonym systemie zazwyczaj odnosi się do wykonywania programu. Procesy są identyfikowane przez nazwy modułów lub zostały one oznaczone "procesy systemowe".

 Program Microsoft Windows obsługuje wiele procesów. Każdy proces może mieć jeden lub więcej wątków i każdy wątek może zawierać jeden lub kilka skojarzonych okien najwyższego poziomu. Każde okno najwyższego poziomu może posiadać kilka okien. A + symbol informuje, że poziom jest zwinięta. W widoku zwiniętym składa się z jeden wiersz dla każdego procesu. Kliknij pozycję + symbolu, aby rozwinąć poziomu.

 Użyj widoku procesów, jeśli chcesz sprawdzić procesu określonym systemie zazwyczaj odnosi się do wykonywania programu. Procesy są identyfikowane przez nazwy modułów lub zostały one oznaczone "procesy systemowe". Aby znaleźć proces, Zwiń drzewo i listę można przeszukiwać.

## <a name="procedures"></a>Procedury

#### <a name="to-open-the-processes-view"></a>Aby otworzyć widok procesów

1. Z **Spy** menu, wybierz **procesy**.

   ![Szpieguj&#43; &#43; widok procesów](../debugger/media/spy--_processes.png "Spy ++ _Processes") Spy ++ widok procesów

   Powyższy rysunek przedstawia widok procesów z węzłami procesu i wątku, rozwinięty.

### <a name="in-this-section"></a>W tej sekcji
 [Trwa wyszukiwanie procesu w widoku procesów](../debugger/how-to-search-for-a-process-in-processes-view.md) wyjaśnia, jak można znaleźć określonego procesu w widoku procesów.

 [Wyświetlanie właściwości procesu](../debugger/how-to-display-process-properties.md) wyjaśniono sposób wyświetlić więcej informacji na temat wiadomości.

### <a name="related-sections"></a>Sekcje pokrewne
 [Widoków programu Spy ++](../debugger/spy-increment-views.md) wyjaśnia widoków programu Spy ++ drzewa systemu windows, wiadomości, procesów i wątków.

 [Korzystanie z programu Spy ++](../debugger/using-spy-increment.md) wprowadzono narzędzie Spy ++ i opisano, jak mogą być używane.

 [Okno dialogowe Wyszukiwanie procesów](../debugger/process-search-dialog-box.md) umożliwia znalezienie węzła dla określonego procesu w widoku procesów.

 [Okno dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md) zostaną wyświetlone właściwości procesem, który został wybrany w widoku procesów.

 [Spy ++ — odwołanie](../debugger/spy-increment-reference.md) zawiera sekcje opisujące każdy Spy ++ menu i okno dialogowe.