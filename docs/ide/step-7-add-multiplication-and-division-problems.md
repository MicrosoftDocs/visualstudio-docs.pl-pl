---
title: Krok 7. Dodawanie problemów mnożenia i dzielenia
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 342a27571c9ad7b6ed1586fc762b2952ba86c3db
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575161"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Krok 7. Dodawanie problemów mnożenia i dzielenia

W siódmej części tego samouczka dodasz problemy mnożenia i dzielenia, ale najpierw zauważasz, jak wprowadzić tę zmianę. Rozważmy Etap początkowy, który obejmuje przechowywanie wartości.

> [!NOTE]
> Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem.
> - Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md).
> - Aby pobrać kompletną wersję kodu, zobacz [kompletny przykładowy samouczek quizu Matematycznego](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-add-multiplication-and-division-problems"></a>Aby dodać problemy mnożenia i dzielenia

1. Dodaj cztery więcej zmiennych całkowitych do formularza.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

2. Tak jak wcześniej, zmodyfikuj metodę `StartTheQuiz()`, aby wprowadzić liczby losowe dla problemów mnożenia i dzielenia.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. Zmodyfikuj metodę `CheckTheAnswer()` tak, aby sprawdzał również problemy z mnożeniem i dzieleniem.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     Nie można łatwo wprowadzić znaku mnożenia (×) i znaku dzielenia (÷) przy użyciu klawiatury, a więc C# Visual Basic Zaakceptuj gwiazdkę (*) dla mnożenia i ukośnika (/) dla dzielenia.

4. Zmień ostatnią część programu obsługi zdarzeń <xref:System.Windows.Forms.Timer.Tick> czasomierza, aby wypełnił poprawną odpowiedź, gdy skończy się czas.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. Zapisz i uruchom program.

     Aby ukończyć quiz, uczestnikom quiz musi odpowiedzieć na cztery problemy, jak pokazano na poniższej ilustracji.

     ![Math Quiz zawierający cztery problemy ](../ide/media/express_finishedquiz.png)<br/>
***Quiz matematyczny*** *z czterema problemami*

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[krok 8: Dostosowywanie quizu](../ide/step-8-customize-the-quiz.md)** .

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 6: Dodawanie problemu odejmowania](../ide/step-6-add-a-subtraction-problem.md).
