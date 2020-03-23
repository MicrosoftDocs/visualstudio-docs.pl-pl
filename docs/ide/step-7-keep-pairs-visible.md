---
title: 'Krok 7: Utrzymuj widoczne pary'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eeca594849625b548857a23b9d5c8e278dcdf07c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579293"
---
# <a name="step-7-keep-pairs-visible"></a>Krok 7: Utrzymuj widoczne pary
Gra działa dobrze, dopóki gracz wybiera tylko pary ikon, które nie są zgodne. Rozważmy jednak, co się powinno zdarzyć, gdy gracz wybierze pasującą parę. Zamiast sprawiać, że ikony znikają, włączając <xref:System.Windows.Forms.Timer.Start> timer (przy użyciu metody), gra powinna zresetować się tak, aby nie śledziła już żadnych etykiet przy użyciu zmiennych `firstClicked` referencyjnych i `secondClicked` referencyjnych, bez resetowania kolorów dla dwóch wybranych etykiet.

## <a name="to-keep-pairs-visible"></a>Aby zachować widoczność par

1. Dodaj następującą `if` instrukcję do metody obsługi `label_Click()` zdarzeń, na końcu kodu tuż nad instrukcją, w której uruchomisz czasomierz. Przyjrzyj się kodowi podczas dodawania go do programu. Zastanów się, jak działa kod.

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]

       > [!IMPORTANT]
       > Use the programming language control at the top right of this page to view either the C# code snippet or the Visual Basic code snippet.<br><br>![Programming language control for Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Pierwszy wiersz `if` instrukcji, który właśnie dodał, sprawdza, czy ikona w pierwszej etykiecie, którą wybierze gracz, jest taka sama jak ikona w drugiej etykiecie. Jeśli ikony są identyczne, program wykonuje trzy instrukcje między nawiasami klamrowymi w `if` języku C# lub trzy instrukcje w instrukcji w języku Visual Basic. Pierwsze dwie instrukcje `firstClicked` `secondClicked` resetują zmienne i odwołania, tak aby nie śledziły już żadnej z etykiet. (Możesz rozpoznać te dwie instrukcje <xref:System.Windows.Forms.Timer.Tick> z obsługi zdarzeń czasomierza). Trzecia instrukcja `return` jest instrukcja, która mówi programowi, aby pominąć pozostałe instrukcje w metodzie bez ich wykonywania.

     Jeśli programowanie w języku C#, można zauważyć, że niektóre z`=`kodu używa jednego znaku równości`==`( ), podczas gdy inne instrukcje używają dwóch znaków równości ( ). Zastanów `=` się, dlaczego jest `==` używany w niektórych miejscach, ale jest używany w innych miejscach.

     To jest dobry przykład, który pokazuje różnicę. Należy uważnie przyjrzeć się kod między nawiasami `if` w instrukcji.

    ```vb
    firstClicked.Text = secondClicked.Text
    ```

    ```csharp
    firstClicked.Text == secondClicked.Text
    ```

     Następnie przyjrzyj się uważnie pierwszej instrukcji `if` w bloku kodu po instrukcji.

    ```vb
    firstClicked = Nothing
    ```

    ```csharp
    firstClicked = null;
    ```

     Pierwsza z tych dwóch instrukcji sprawdza, czy dwie ikony są takie same. Ponieważ dwie wartości są porównywane, program `==` C# używa operatora równości. Druga instrukcja faktycznie zmienia wartość (nazywaną *przypisaniem),* ustawiając zmienną referencyjną równą `firstClicked` jej `null` zresetowaniu. Dlatego zamiast tego używa `=` operatora przypisania. C# używa `=` do ustawiania `==` wartości i porównywania ich. Visual Basic `=` używa zarówno do przypisywania zmiennych, jak i do porównywania.

2. Zapisz i uruchom program, a następnie zacznij wybierać ikony na formularzu. Jeśli wybierzesz parę, która nie pasuje, wyzwala się zdarzenie czasomierza Takt i obie ikony znikają. Jeśli wybierzesz parę pasującą, nowa `if` instrukcja jest wykonywana, a instrukcja return powoduje, że metoda pominąć kod, który uruchamia czasomierz, więc ikony pozostają widoczne, jak pokazano na poniższej ilustracji.

     ![Gra tworzona w ramach tego samouczka](../ide/media/express_finishedgame.png)<br/>
***Pasująca gra*** *z widocznymi parami ikon*

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[Krok 8: Dodawanie metody weryfikacji, czy gracz wygrał.](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)**

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 6: Dodawanie czasomierza](../ide/step-6-add-a-timer.md).
