---
title: Wyszukiwanie wątku w widoku wątków | Microsoft Docs
description: Wyszukiwanie określonego wątku w widoku wątków narzędzia Spy + + przy użyciu identyfikatora wątku lub ciągu modułu jako kryterium wyszukiwania podczas debugowania w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92864c9d3c66a7547ef52a2694f6307d57a43304
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148536"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Porady: wyszukiwanie wątku w widoku wątków
Konkretny wątek można wyszukać w widoku wątki przy użyciu identyfikatora wątku lub ciągu modułu jako kryterium wyszukiwania. Możesz również określić początkowy kierunek wyszukiwania. Pola w oknie dialogowym będą zawierać atrybuty wybranego wątku w drzewie wątku.

### <a name="to-search-for-a-thread-in-threads-view"></a>Aby wyszukać wątek w widoku wątki

1. Rozmieść okna w taki sposób, że okno widok programu Spy + + i aktywne [wątki](../debugger/threads-view.md) są widoczne.

2. Z menu **wyszukiwania** wybierz polecenie **Znajdź wątek**.

    Zostanie otwarte okno [dialogowe Wyszukiwanie wątków](../debugger/thread-search-dialog-box.md) .

3. Wpisz identyfikator wątku lub ciąg modułu jako kryterium wyszukiwania.

4. Wyczyść wszystkie pola, dla których nie chcesz określać wartości.

   > [!TIP]
   > Aby znaleźć wszystkie wątki należące do modułu, usuń zaznaczenie pola tekstowego **wątek** i wpisz nazwę modułu w polu **moduł** . Następnie użyj **Znajdź dalej** , aby kontynuować wyszukiwanie wątków.

5. Wybierz pozycję w **górę** lub **w dół** , aby określić początkowy kierunek wyszukiwania.

6. Kliknij przycisk **OK**.

   Jeśli zostanie znaleziony pasujący wątek, zostanie on wyróżniony w oknie Widok wątków.