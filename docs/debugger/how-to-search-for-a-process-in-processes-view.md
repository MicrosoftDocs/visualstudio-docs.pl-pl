---
title: 'Instrukcje: Wyszukiwanie procesu w widoku procesów | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c9cd618768268b5c0bc4e3e99fbffd4fd65e874
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715092"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Instrukcje: Wyszukiwanie procesu w widoku procesów
Możesz wyszukać określonego procesu w widoku procesów za pomocą ciągu Identyfikatora lub moduł jego procesu jako kryterium wyszukiwania. Można również określić początkową kierunek wyszukiwania. Pola w oknie dialogowym zostaną wyświetlone atrybuty wybranego procesu w drzewo procesów.

### <a name="to-search-for-a-process-in-processes-view"></a>Wyszukiwanie procesu w widoku procesów

1. Rozmieść aplikacji dla systemu windows, więc tego programu Spy ++ i aktywne [widok procesy](../debugger/processes-view.md) okna są widoczne.

2. Z **wyszukiwania** menu, wybierz **Znajdź proces**

    [Okno dialogowe Wyszukiwanie procesów](../debugger/process-search-dialog-box.md) zostanie otwarty.

3. Wpisz identyfikator procesu lub ciąg modułu jako kryterium wyszukiwania.

4. Wyczyść wszystkie pola, dla których nie chcesz określać wartości.

   > [!TIP]
   >  Aby znaleźć wszystkie procesy, które są własnością modułu, należy wyczyścić **procesu** pole, a następnie wpisz nazwę modułu w **modułu** pole. Następnie użyj **Znajdź następny** kontynuować wyszukiwanie procesów.

5. Wybierz **się** lub **dół** dla początkowej kierunek wyszukiwania.

6. Kliknij przycisk **OK**.

   Jeśli proces dopasowywania zostanie znaleziony, jest wyróżniona na **widok procesu** okna.