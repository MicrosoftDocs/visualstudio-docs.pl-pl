---
title: 'Krok 7: Dodaj problemy z mnożeniem i podziałem'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92a1744b68ad043dcee21dcb5995fbd1908bd81b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579780"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Krok 7: Dodaj problemy z mnożeniem i podziałem

W siódmej części tego samouczka dodasz problemy z mnożeniem i podziałem, ale najpierw zastanów się, jak to zmienić. Należy wziąć pod uwagę początkowy krok, który obejmuje przechowywanie wartości.

> [!NOTE]
> Ten temat jest częścią serii samouczków na temat podstawowych pojęć kodowania. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie quizu matematycznego z czasem](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-multiplication-and-division-problems"></a>Aby dodać problemy z mnożeniem i dzieleniem

1. Dodaj do formularza jeszcze cztery zmienne całkowite.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

2. Podobnie jak poprzednio, `StartTheQuiz()` zmodyfikuj metodę wypełniania liczb losowych dla problemów z mnożeniem i dzieleniem.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. Zmodyfikuj `CheckTheAnswer()` metodę tak, aby sprawdzała również problemy z mnożeniem i podziałem.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     Nie można łatwo wprowadzić znaku mnożenia (×) i znaku podziału (÷) za pomocą klawiatury, więc C# i Visual Basic akceptują gwiazdkę (*) do mnożenia i ukośnik (/) dla podziału.

4. Zmień ostatnią część programu obsługi <xref:System.Windows.Forms.Timer.Tick> zdarzeń czasomierza, tak aby wypełniała poprawną odpowiedź, gdy skończy się czas.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. Zapisz i uruchom program.

     Osoby biorące w quizie muszą odpowiedzieć na cztery problemy, aby ukończyć quiz, jak pokazuje poniższa ilustracja.

     ![Quiz matematyczny z czterema problemami](../ide/media/express_finishedquiz.png)<br/>
***Quiz matematyczny*** *z czterema problemami*

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[Krok 8: Dostosowywanie quizu](../ide/step-8-customize-the-quiz.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 6: Dodawanie problemu odejmowania](../ide/step-6-add-a-subtraction-problem.md).
