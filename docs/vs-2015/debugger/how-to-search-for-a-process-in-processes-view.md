---
title: 'Instrukcje: wyszukiwanie procesu w widoku procesów | Microsoft Docs'
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
ms.openlocfilehash: e39168e36e9540ec8c5e23a9030d996b81c4097c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64799501"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Porady: wyszukiwanie procesu w widoku procesów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
