---
title: Krok 7. Dodawanie zadań z mnożeniem i dzieleniem
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- csharp
- vb
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 182ab3c06ef0956d6c0d97c4276a44c3f3239875
ms.sourcegitcommit: 0e482cfc15f809b564c3de61646f29ecd7bfcba6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70987860"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Krok 7. Dodawanie zadań z mnożeniem i dzieleniem

W siódmej części tego samouczka dodasz problemy mnożenia i dzielenia, ale najpierw zauważasz, jak wprowadzić tę zmianę. Rozważmy Etap początkowy, który obejmuje przechowywanie wartości.

> [!NOTE]
> Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem. 
> - Aby zapoznać się z omówieniem samouczka, [zobacz Samouczek 2: Utwórz Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md)matematyczny z limitem czasu. 
> - Aby pobrać kompletną wersję kodu, zobacz [kompletny przykładowy samouczek quizu Matematycznego](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-add-multiplication-and-division-problems"></a>Aby dodać problemy mnożenia i dzielenia

1. Dodaj cztery więcej zmiennych całkowitych do formularza.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     > [!IMPORTANT]
     > Użyj kontrolki język programowania w prawym górnym rogu tej strony, aby wyświetlić fragment C# kodu lub Visual Basic fragment kodu.<br><br>![Kontrolka języka programowania dla Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

2. Tak jak wcześniej, zmodyfikuj `StartTheQuiz()` metodę, aby wprowadzić liczby losowe dla problemów mnożenia i dzielenia.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. `CheckTheAnswer()` Zmodyfikuj metodę, tak aby sprawdzali również problemy z mnożeniem i dzieleniem.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     Nie można łatwo wprowadzić znaku mnożenia (x) i znaku dzielenia (÷) przy użyciu klawiatury, dlatego Wizualizacja C# i Visual Basic akceptują gwiazdkę (*) dla mnożenia i ukośnika (/) dla dzielenia.

4. Zmień ostatnią część obsługi <xref:System.Windows.Forms.Timer.Tick> zdarzeń czasomierza, tak aby wypełnił poprawną odpowiedź, gdy skończy się czas.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. Zapisz i uruchom program.

     Aby ukończyć quiz, uczestnikom quiz musi odpowiedzieć na cztery problemy, jak pokazano na poniższej ilustracji.

     ![Quiz matematyczny z czterema problemami](../ide/media/express_finishedquiz.png)<br/>
***Quiz matematyczny*** *z czterema problemami*

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz  **[krok 8: Dostosuj Quiz](../ide/step-8-customize-the-quiz.md)** S.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 6. Dodawanie problemu](../ide/step-6-add-a-subtraction-problem.md)odejmowania.
