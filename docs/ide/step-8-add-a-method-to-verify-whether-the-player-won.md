---
title: Krok 8. Dodawanie metody sprawdzania, czy gracz wygrał
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eed7a2796f08e85441c174e882c00fa406cb2379
ms.sourcegitcommit: a5a54b147e772dc39e519da74ec41a0c25d99628
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2019
ms.locfileid: "72289662"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Krok 8. Dodawanie metody sprawdzania, czy gracz wygrał
Utworzyłeś zabawną grę, ale wymaga ona jeszcze jednej rzeczy. Gra powinna zakończyć się, gdy gracz usługi WINS, więc musisz dodać metodę `CheckForWinner()`, aby sprawdzić, czy odtwarzacz wykupił.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Aby dodać metodę w celu sprawdzenia, czy gracz wygrał

1. Dodaj metodę `CheckForWinner()` w dolnej części kodu poniżej procedury obsługi zdarzeń `timer1_Tick()`, jak pokazano w poniższym kodzie.

     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]

      > [!IMPORTANT]
      > Użyj kontrolki język programowania w prawym górnym rogu tej strony, aby wyświetlić fragment C# kodu lub Visual Basic fragment kodu.<br><br>0Programming — kontrola języka dla dokumentacji docs. Microsoft. com @ no__t-1 @no__t     

     Metoda używa innej pętli `foreach` w pętli wizualizacji C# lub `For Each` w Visual Basic do przechodzenia przez każdą etykietę w <xref:System.Windows.Forms.TableLayoutPanel>. Używa operatora równości (`==` w wizualizacji C# i `=` w Visual Basic), aby sprawdzić kolor ikon każdej etykiety, aby sprawdzić, czy jest on zgodny z tłem. Jeśli kolory są zgodne, ikona pozostaje niewidoczna, a gracz nie dopasował wszystkich pozostałych ikon. W takim przypadku program używa instrukcji `return`, aby pominąć resztę metody. Jeśli pętla przechodzi przez wszystkie etykiety bez wykonywania instrukcji `return`, oznacza to, że wszystkie ikony w formularzu zostały dopasowane. Program wyświetla element MessageBox, który congratulate gracz na wygranie, a następnie wywołuje metodę `Close()` formularza, aby zakończyć grę.

2. Następnie zadzwoń do programu obsługi zdarzeń <xref:System.Windows.Forms.Control.Click>, aby wywoływać nową metodę `CheckForWinner()`. Pamiętaj, że program sprawdza zwycięzcę natychmiast po pokazaniu drugiej ikony, którą wybierze gracz. Wyszukaj wiersz, w którym ustawisz kolor drugiej wybranej ikony, a następnie Wywołaj metodę `CheckForWinner()` bezpośrednio po tym, jak pokazano w poniższym kodzie.

     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]

3. Zapisz i uruchom program. Zagraj w grę i dopasuj wszystkie ikony. Gdy wygrasz, program wyświetli element **MessageBox** gratulacjami (jak pokazano na poniższej ilustracji), a następnie zamknie to pole.

     @no__t — gra 0Matching z elementem MessageBox @ no__t-1<br/>
**Dopasowywanie gry** przy użyciu **MessageBox**

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [Step 9: Wypróbuj inne funkcje @ no__t-0.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Step 7: Zachowaj widoczne pary @ no__t-0.
