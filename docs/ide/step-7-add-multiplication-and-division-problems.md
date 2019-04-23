---
title: Krok 7. Dodawanie problemów mnożenia i dzielenia
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e60cb6c289fa582eb27137483f44b7557d4e426d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068525"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Krok 7. Dodawanie problemów mnożenia i dzielenia
W siódmej części tego samouczka będziesz dodawać problemy mnożenia i dzielenia, ale najpierw zastanów się, jak dokonać tej zmiany. Należy wziąć pod uwagę etap początkowy, który obejmuje zapisanie wartości.

## <a name="to-add-multiplication-and-division-problems"></a>Aby dodać problemy mnożenia i dzielenia

1. Dodaj cztery więcej zmiennych całkowitych do formularza.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

2. Jak poprzednio, zmodyfikuj `StartTheQuiz()` metodę, aby wprowadzić liczby losowe dla problemów mnożenia i dzielenia.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. Modyfikowanie `CheckTheAnswer()` metodę, tak aby sprawdzała również problemy mnożenia i dzielenia.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     Nie można łatwo wprowadzić znak mnożenia (x) i znak dzielenia (÷) za pomocą klawiatury, więc Visual C# i Visual Basic Zaakceptuj znak gwiazdki (*) dla mnożenia i znak kreski ukośnej (/) dla działu.

4. Zmień ostatnią część czasomierza <xref:System.Windows.Forms.Timer.Tick> program obsługi zdarzeń, tak że wypełnia poprawną odpowiedź, gdy skończy się czas.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. Zapisz i uruchom program.

     Quizu muszą rozwiązać cztery problemy, aby zakończyć quiz, jak pokazano na następującym rysunku.

     ![Quiz matematyczny z czterema problemami](../ide/media/express_finishedquiz.png)
**kwizu matematycznego z limitem** z czterema problemami

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 8: Dostosowywanie kwizu](../ide/step-8-customize-the-quiz.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 6: Dodawanie problemu odejmowania](../ide/step-6-add-a-subtraction-problem.md).
