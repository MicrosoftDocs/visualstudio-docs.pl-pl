---
title: Krok 8. Dodanie metody w celu sprawdzenia, czy gracz kupił | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2481693961dd03815381e9f71ee67cb73464bdf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646938"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Krok 8. Dodanie metody sprawdzania, czy gracz wygrał
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Utworzyłeś zabawną grę, ale wymaga ona jeszcze jednej rzeczy. Gra powinna zakończyć się, gdy gracz usługi WINS, więc musisz dodać metodę `CheckForWinner()`, aby sprawdzić, czy odtwarzacz wykupił.

### <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Aby dodać metodę w celu sprawdzenia, czy gracz wygrał

1. Dodaj metodę `CheckForWinner()` w dolnej części kodu poniżej procedury obsługi zdarzeń `timer1_Tick()`, jak pokazano w poniższym kodzie.

     [!code-csharp[VbExpressTutorial4Step8#10](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs#10)]
     [!code-vb[VbExpressTutorial4Step8#10](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb#10)]

     Metoda używa innej pętli `foreach` w pętli wizualizacji C# lub `For Each` w Visual Basic do przechodzenia przez każdą etykietę w TableLayoutPanel. Używa operatora równości (`==` w wizualizacji C# i `=` w Visual Basic), aby sprawdzić kolor ikon każdej etykiety, aby sprawdzić, czy jest on zgodny z tłem. Jeśli kolory są zgodne, ikona pozostaje niewidoczna, a gracz nie dopasował wszystkich pozostałych ikon. W takim przypadku program używa instrukcji `return`, aby pominąć resztę metody. Jeśli pętla przechodzi przez wszystkie etykiety bez wykonywania instrukcji `return`, oznacza to, że wszystkie ikony w formularzu zostały dopasowane. Program wyświetli element MessageBox, który congratulate gracz na wygranie, a następnie wywoła metodę `Close()` formularza, aby zakończyć grę.

2. Następnie, aby program obsługi zdarzeń kliknięcia etykiety wywołał nową metodę `CheckForWinner()`. Pamiętaj, że program sprawdza zwycięzcę natychmiast po pokazaniu drugiej ikony, którą wybierze gracz. Wyszukaj wiersz, w którym ustawisz kolor drugiej wybranej ikony, a następnie Wywołaj metodę `CheckForWinner()` bezpośrednio po tym, jak pokazano w poniższym kodzie.

     [!code-csharp[VbExpressTutorial4Step8#11](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs#11)]
     [!code-vb[VbExpressTutorial4Step8#11](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb#11)]

3. Zapisz i uruchom program. Zagraj w grę i dopasuj wszystkie ikony. Kiedy wygrasz, program wyświetli komunikat MessageBox z gratulacjami (jak pokazano na rysunku poniżej), a następnie zamknie okno.

     ![Dopasowywanie gry przy użyciu MessageBox](../ide/media/express-tut4step8.png "Express_Tut4Step8") Dopasowywanie gry przy użyciu MessageBox

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 9: Wypróbuj inne funkcje](../ide/step-9-try-other-features.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 7. Zachowaj widoczne pary](../ide/step-7-keep-pairs-visible.md).
