---
title: Jak wyszukiwać proces w widoku procesów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e823ecb1f7523c1a6f094d5669f4a37a72e84f60
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349292"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Porady: wyszukiwanie procesu w widoku procesów
Konkretny proces można wyszukać w widoku procesy przy użyciu identyfikatora procesu lub ciągu modułu jako kryterium wyszukiwania. Możesz również określić początkowy kierunek wyszukiwania. Pola w oknie dialogowym będą zawierać atrybuty wybranego procesu w drzewie procesów.

### <a name="to-search-for-a-process-in-processes-view"></a>Aby wyszukać proces w widoku procesów

1. Rozmieść okna w taki sposób, aby były widoczne okno [Widok](../debugger/processes-view.md) programu Spy + + i aktywne procesy.

2. Z menu **Wyszukaj** wybierz pozycję **Znajdź proces**

    Zostanie otwarte okno [dialogowe Wyszukiwanie procesów](../debugger/process-search-dialog-box.md) .

3. Wpisz identyfikator procesu lub ciąg modułu jako kryterium wyszukiwania.

4. Wyczyść wszystkie pola, dla których nie chcesz określać wartości.

   > [!TIP]
   > Aby znaleźć wszystkie procesy należące do modułu, wyczyść pole **proces** i wpisz nazwę modułu w polu **moduł** . Następnie użyj **Znajdź dalej** , aby kontynuować wyszukiwanie procesów.

5. Wybierz pozycję w **górę** lub **w dół** , aby określić początkowy kierunek wyszukiwania.

6. Kliknij przycisk **OK**.

   W przypadku znalezienia zgodnego procesu zostanie on wyróżniony w oknie **Widok procesu** .