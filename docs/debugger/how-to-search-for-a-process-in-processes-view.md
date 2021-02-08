---
title: Wyszukiwanie procesu w widoku procesów | Microsoft Docs
description: Wyszukiwanie określonego procesu w widoku procesów narzędzia Spy + + przy użyciu identyfikatora procesu lub ciągu modułu jako kryterium wyszukiwania podczas debugowania w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85b2c2bab29316846620c7dbec935b41eec1d9df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845077"
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