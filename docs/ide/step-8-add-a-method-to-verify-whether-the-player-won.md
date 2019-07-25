---
title: Krok 8. Dodawanie metody sprawdzania, czy gracz wygrał
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- csharp
- vb
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9daa4d939eb1cd5c03d3811337f258fc3ef3c70c
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68415635"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Krok 8. Dodawanie metody sprawdzania, czy gracz wygrał
Utworzyłeś zabawną grę, ale wymaga ona jeszcze jednej rzeczy. Gra powinna zakończyć się, gdy gracz usługi WINS, więc musisz dodać `CheckForWinner()` metodę, aby sprawdzić, czy odtwarzacz wykupił.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Aby dodać metodę w celu sprawdzenia, czy gracz wygrał

1. Dodaj metodę do dolnej części kodu `timer1_Tick()` poniżej procedury obsługi zdarzeń, jak pokazano w poniższym kodzie. `CheckForWinner()`

     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]

     Metoda używa `foreach` innej pętli w wizualizacji C# lub `For Each` pętli w Visual Basic <xref:System.Windows.Forms.TableLayoutPanel>do przechodzenia przez każdą etykietę w. Używa operatora równości (`==` w wizualizacji C# i `=` w Visual Basic), aby sprawdzić kolor ikon każdej etykiety, aby sprawdzić, czy jest on zgodny z tłem. Jeśli kolory są zgodne, ikona pozostaje niewidoczna, a gracz nie dopasował wszystkich pozostałych ikon. W takim przypadku program używa `return` instrukcji, aby pominąć resztę metody. Jeśli pętla przechodzi przez wszystkie etykiety bez wykonywania `return` instrukcji, oznacza to, że wszystkie ikony w formularzu zostały dopasowane. Program wyświetli element MessageBox, który congratulate gracz na wygranie, a następnie wywoła `Close()` metodę formularza, aby zakończyć grę.

2. Następnie należy wywołać nową <xref:System.Windows.Forms.Control.Click> `CheckForWinner()` metodę obsługi zdarzeń etykiety. Pamiętaj, że program sprawdza zwycięzcę natychmiast po pokazaniu drugiej ikony, którą wybierze gracz. Wyszukaj wiersz, w którym ustawisz kolor drugiej wybranej ikony, a następnie Wywołaj `CheckForWinner()` metodę bezpośrednio po tym, jak pokazano w poniższym kodzie.

     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]

3. Zapisz i uruchom program. Zagraj w grę i dopasuj wszystkie ikony. Gdy wygrasz, program wyświetli element **MessageBox** gratulacjami (jak pokazano na poniższej ilustracji), a następnie zamknie to pole.

     ![Dopasowywanie gry przy](../ide/media/express_tut4step8.png)
użyciu**gry** MessageBox z funkcją **MessageBox**

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 9: Wypróbuj inne funkcje](../ide/step-9-try-other-features.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 7: Zachowaj widoczne](../ide/step-7-keep-pairs-visible.md)pary.
