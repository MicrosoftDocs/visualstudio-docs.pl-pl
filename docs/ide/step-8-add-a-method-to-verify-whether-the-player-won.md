---
title: Krok 8. Dodaj metodę, aby sprawdzić, czy gracz wygrał
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e21caa6b73d6cf23a41bd7691fa19b1f7ff8e2f2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60047754"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Krok 8. Dodaj metodę, aby sprawdzić, czy gracz wygrał
Utworzyłeś zabawną grę, ale wymaga ona jeszcze jednej rzeczy. Gra powinna się kończyć kiedy gracz wygrywa, więc trzeba dodać `CheckForWinner()` metodę, aby sprawdzić, czy gracz wygrał.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Aby dodać metodę w celu sprawdzenia, czy gracz wygrał

1. Dodaj `CheckForWinner()` metodę do dolnej części kodu, poniżej `timer1_Tick()` program obsługi zdarzeń, jak pokazano w poniższym kodzie.

     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]

     Metoda używa innej `foreach` pętli w elemencie wizualnym C# lub `For Each` pętli w języku Visual Basic, aby przejść przez każdą etykietę w <xref:System.Windows.Forms.TableLayoutPanel>. Używa operatora równości (`==` w języku Visual C# i `=` w języku Visual Basic) do sprawdzania kolor ikony każdej etykiety, aby sprawdzić, czy pasuje do tła. Jeśli kolory są zgodne, ikona pozostaje niewidoczna, a gracz nie dopasował wszystkich pozostałych ikon. W takim przypadku program używa `return` instrukcję, aby pominąć resztę metody. Jeśli pętla przechodzi przez wszystkie etykiety bez wykonywania `return` instrukcji, oznacza to, że wszystkie ikony w formularzu zostały dopasowane. Program pokazuje komunikat MessageBox, aby pogratulować graczowi wygranej, a następnie wywołuje formularza `Close()` metodę, aby zakończyć grę.

2. Następnie, Spowoduj etykiety <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń wywoływał nową `CheckForWinner()` metody. Pamiętaj, że program sprawdza zwycięzcę natychmiast po pokazaniu drugiej ikony, którą wybierze gracz. Wyszukaj wiersz, gdzie ustawiasz kolor drugiej wybranej ikony, a następnie wywołaj `CheckForWinner()` metoda zaraz po tym, jak pokazano w poniższym kodzie.

     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]

3. Zapisz i uruchom program. Zagraj w grę i dopasuj wszystkie ikony. Kiedy wygrasz, program wyświetla gratulacjami **MessageBox** (jak pokazano na poniższej ilustracji), a następnie zamknie okno.

     ![Gra w dopasowywanie z MessageBox](../ide/media/express_tut4step8.png)
**gra w dopasowywanie** z **MessageBox**

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 9: Spróbuj innych funkcji](../ide/step-9-try-other-features.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [kroku 7: Zachować widoczność par](../ide/step-7-keep-pairs-visible.md).
