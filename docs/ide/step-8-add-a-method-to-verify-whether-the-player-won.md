---
title: 'Krok 8: Dodaj metodę, aby sprawdzić, czy gracz wygrał'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 881fa0d90390a059bea28cb19584381f814396d3
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579765"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Krok 8: Dodaj metodę, aby sprawdzić, czy gracz wygrał
Utworzyłeś zabawną grę, ale wymaga ona jeszcze jednej rzeczy. Gra powinna się zakończyć, gdy gracz wygra, więc musisz dodać `CheckForWinner()` metodę, aby sprawdzić, czy gracz wygrał.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Aby dodać metodę w celu sprawdzenia, czy gracz wygrał

1. Dodaj `CheckForWinner()` metodę do dołu kodu, `timer1_Tick()` poniżej programu obsługi zdarzeń, jak pokazano w poniższym kodzie.

     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]

      > [!IMPORTANT]
      > Użyj formantu języka programowania w prawym górnym rogu tej strony, aby wyświetlić fragment kodu języka C# lub fragment kodu języka Visual Basic.<br><br>![Sterowanie językiem programowania dla Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)     

     Metoda używa innej `foreach` pętli w `For Each` języku C# lub pętli w <xref:System.Windows.Forms.TableLayoutPanel>języku Visual Basic, aby przejść przez każdą etykietę w . Używa operatora równości (w`==` języku `=` C# i Visual Basic), aby sprawdzić kolor ikony każdej etykiety, aby sprawdzić, czy pasuje do tła. Jeśli kolory są zgodne, ikona pozostaje niewidoczna, a gracz nie dopasował wszystkich pozostałych ikon. W takim przypadku program używa `return` instrukcji, aby pominąć pozostałą część metody. Jeśli pętla przechodzi przez wszystkie etykiety `return` bez wykonywania instrukcji, oznacza to, że wszystkie ikony w formularzu zostały dopasowane. Program pokazuje MessageBox pogratulować graczowi na wygraną, a `Close()` następnie wywołuje metodę formularza, aby zakończyć grę.

2. Następnie należy wywołać <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń `CheckForWinner()` etykiety nowej metody. Pamiętaj, że program sprawdza zwycięzcę natychmiast po pokazaniu drugiej ikony, którą wybierze gracz. Poszukaj wiersza, w którym ustawisz kolor drugiej `CheckForWinner()` wybranej ikony, a następnie wywołaj metodę zaraz po tym, jak pokazano w poniższym kodzie.

     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]

3. Zapisz i uruchom program. Zagraj w grę i dopasuj wszystkie ikony. Po wygraniu program wyświetla gratulacyjny **MessageBox** (jak pokazano na poniższym zrzucie ekranu), a następnie zamyka pole.

     ![Gra w dopasowywanie z MessageBox](../ide/media/express_tut4step8.png)<br/>
***Pasująca gra*** *z* ***MessageBox***

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[Krok 9: Wypróbuj inne funkcje](../ide/step-9-try-other-features.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 7: Zachowaj widoczne pary](../ide/step-7-keep-pairs-visible.md).
