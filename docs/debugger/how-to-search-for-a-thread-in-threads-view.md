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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85d82897144a0ed366d95dfa590a09224a875f55
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845064"
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