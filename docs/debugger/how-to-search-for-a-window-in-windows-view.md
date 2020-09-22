---
title: Wyszukiwanie okna w widoku systemu Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 880f6ec3ea0882d92f5376859ed629e23781f5f9
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851973"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Porady: wyszukiwanie okna w widoku okien
Można wyszukać określone okno w widoku systemu Windows przy użyciu uchwytu, podpisu, klasy lub kombinacji jego podpisu i klasy jako kryterium wyszukiwania. Możesz również określić początkowy kierunek wyszukiwania. Pola w oknie dialogowym będą zawierać atrybuty wybranego okna w drzewie okien.

 Rozpocznij od drzewa rozwiniętego do drugiego poziomu (wszystkie okna, które są elementami podrzędnymi pulpitu), aby można było identyfikować okna na poziomie pulpitu według ich nazwy i tytułu klasy. Po wybraniu okna poziomu pulpitu można rozwinąć ten poziom, aby znaleźć określone okno podrzędne.

### <a name="to-search-for-a-window-in-windows-view"></a>Aby wyszukać okno w widoku systemu Windows

1. Rozmieść swoje okna tak, aby program Spy + +, okno [Widok systemu Windows](../debugger/windows-view.md) i okno docelowe były widoczne.

2. Z menu **Wyszukaj** wybierz pozycję **Znajdź okno**.

    Zostanie otwarte okno [dialogowe Wyszukiwanie okna](../debugger/window-search-dialog-box.md) .

   > [!TIP]
   > Aby zmniejszyć czytelność ekranu, wybierz opcję **Ukryj program Spy** . Ta opcja ukrywa główne okno programu Spy + + i pozostawia tylko okno dialogowe **wyszukiwania okna** widoczne na innych aplikacjach. Okno główne programu Spy + + jest przywracane po kliknięciu przycisku **OK** lub **Anuluj**lub po wyczyszczeniu opcji **Ukryj program Spy + +** .

3. Przeciągnij **Narzędzie wyszukiwania** nad oknem docelowym. Podczas przeciągania narzędzia okno dialogowe **wyszukiwania okna** wyświetla szczegóły w wybranym oknie.

   - oraz

     Jeśli wiesz, jak dojście do żądanego okna (na przykład z debugera), możesz wpisać je w polu **uchwyt** .

   - oraz

     Jeśli znasz podpis i/lub klasę żądanego okna, możesz wpisać je w polach tekstowych **podpis** i **Klasa** i wyczyścić pole tekstowe **uchwyt** .

4. Wybierz pozycję w **górę** lub **w dół** , aby określić początkowy kierunek wyszukiwania.

5. Kliknij przycisk **OK**.

    Jeśli zostanie znalezione pasujące okno, zostanie ono wyróżnione w oknie [Widok systemu Windows](../debugger/windows-view.md) .