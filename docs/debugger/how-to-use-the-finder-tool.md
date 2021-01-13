---
title: Korzystanie z narzędzia wyszukiwania | Microsoft Docs
description: Aby wyświetlić właściwości okna lub komunikaty podczas sesji debugowania, użyj narzędzia wyszukiwania w oknie dialogowym okna wyszukiwania w narzędziu Spy + +.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41ca277962f81b3cd1c35ebcf8a940e8168a6803
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150603"
---
# <a name="how-to-use-the-finder-tool"></a>Porady: korzystanie z narzędzia wyszukiwania
Możesz użyć narzędzia wyszukiwania w oknie dialogowym **Znajdowanie okna** do wyświetlania właściwości okna lub komunikatów. Narzędzie wyszukiwania może również lokalizować wyłączone okna podrzędne i rozpoznać, które okno ma zostać wyróżnione, jeśli wyłączone okna podrzędne nakładają się na siebie.

 Okno ![dialogowe "Spy&#43;&#43; Find](../debugger/media/icon_spy--_find.png "Icon_Spy + + _Find") " Narzędzie wyszukiwania w oknie dialogowym Znajdowanie okna

 Powyższy rysunek zawiera okno dialogowe Znajdowanie okna po kroku 3 poniżej.

### <a name="to-display-window-properties-or-messages"></a>Aby wyświetlić właściwości okna lub komunikaty

1. Rozmieść okna w taki sposób, aby były widoczne zarówno program Spy + +, jak i okno docelowe.

2. Z menu **Spy** wybierz pozycję **Znajdź okno**.

    Zostanie otwarte okno [dialogowe Znajdowanie okna](../debugger/find-window-dialog-box.md) .

3. Przeciągnij **Narzędzie wyszukiwania** nad oknem docelowym.

    Podczas przeciągania narzędzia okno dialogowe **Znajdowanie okna** wyświetla szczegóły w wybranym oknie.

   - oraz

     Jeśli masz dojście do okna, które chcesz przejrzeć (na przykład skopiowane z debugera), wpisz je w polu tekstowym **uchwyt** .

   > [!TIP]
   > Aby zmniejszyć czytelność ekranu, wybierz opcję **Ukryj program Spy** . Ta opcja ukrywa główne okno programu Spy + +, pozostawiając tylko okno dialogowe **Znajdowanie okna** widoczne na wierzchu innych aplikacji. Okno główne programu Spy + + jest przywracane po kliknięciu przycisku **OK** lub **Anuluj** lub po wyczyszczeniu opcji **Ukryj program Spy + +** .

4. W obszarze **Pokaż** wybierz opcję **Właściwości** lub **komunikaty**.

5. Naciśnij przycisk **OK**.

    W przypadku wybrania **Właściwości** zostanie otwarte okno [dialogowe Właściwości okna](../debugger/window-properties-dialog-box.md) . W przypadku wybrania **wiadomości** zostanie otwarte okno [Widok komunikatów](../debugger/messages-view.md) .

## <a name="see-also"></a>Zobacz także
- [Spy++ — Widoki](../debugger/spy-increment-views.md)
- [Korzystanie z programu Spy++](../debugger/using-spy-increment.md)
- [Spy++ — Odwołanie](../debugger/spy-increment-reference.md)