---
title: Krok 8. Dodaj metodę, aby sprawdzić, czy gracz wygrał | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d4198d9a575f4ab2add48d08994d5d48392f23a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178630"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Krok 8. Dodawanie metody sprawdzania, czy gracz wygrał
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Utworzyłeś zabawną grę, ale wymaga ona jeszcze jednej rzeczy. Gra powinna się kończyć kiedy gracz wygrywa, więc trzeba dodać `CheckForWinner()` metodę, aby sprawdzić, czy gracz wygrał.  
  
### <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Aby dodać metodę w celu sprawdzenia, czy gracz wygrał  
  
1. Dodaj `CheckForWinner()` metodę do dolnej części kodu, poniżej `timer1_Tick()` program obsługi zdarzeń, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[VbExpressTutorial4Step8#10](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs#10)]
     [!code-vb[VbExpressTutorial4Step8#10](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb#10)]  
  
     Metoda używa innej `foreach` pętli w języku Visual C# lub `For Each` pętli w języku Visual Basic, aby przejść przez każdą etykietę w TableLayoutPanel. Używa operatora równości (`==` w języku Visual C# i `=` w języku Visual Basic) do sprawdzania kolor ikony każdej etykiety, aby sprawdzić, czy pasuje do tła. Jeśli kolory są zgodne, ikona pozostaje niewidoczna, a gracz nie dopasował wszystkich pozostałych ikon. W takim przypadku program używa `return` instrukcję, aby pominąć resztę metody. Jeśli pętla przechodzi przez wszystkie etykiety bez wykonywania `return` instrukcji, oznacza to, że wszystkie ikony w formularzu zostały dopasowane. Program pokazuje komunikat MessageBox, aby pogratulować graczowi wygranej, a następnie wywołuje formularza `Close()` metodę, aby zakończyć grę.  
  
2. Następnie, Spowoduj Click etykiety program obsługi zdarzeń wywoływał nową `CheckForWinner()` metody. Pamiętaj, że program sprawdza zwycięzcę natychmiast po pokazaniu drugiej ikony, którą wybierze gracz. Wyszukaj wiersz, gdzie ustawiasz kolor drugiej wybranej ikony, a następnie wywołaj `CheckForWinner()` metoda zaraz po tym, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[VbExpressTutorial4Step8#11](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs#11)]
     [!code-vb[VbExpressTutorial4Step8#11](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb#11)]  
  
3. Zapisz i uruchom program. Zagraj w grę i dopasuj wszystkie ikony. Kiedy wygrasz, program wyświetli komunikat MessageBox z gratulacjami (jak pokazano na rysunku poniżej), a następnie zamknie okno.  
  
     ![Gra w dopasowywanie z MessageBox](../ide/media/express-tut4step8.png "Express_Tut4Step8")  
Gra w dopasowywanie z MessageBox  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
- Aby przejść do następnego kroku samouczka, zobacz [krok 9: Spróbuj innych funkcji](../ide/step-9-try-other-features.md).  
  
- Aby powrócić do poprzedniego kroku samouczka, zobacz [kroku 7: Zachować widoczność par](../ide/step-7-keep-pairs-visible.md).
