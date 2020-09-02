---
title: Krok 7. Dodawanie problemów mnożenia i dzielenia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f7f7efb0acf6611346abe67a7a94e5c221919665
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646975"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Krok 7. Dodawanie problemów mnożenia i dzielenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W siódmej części tego samouczka dodasz problemy mnożenia i dzielenia, ale najpierw zauważasz, jak wprowadzić tę zmianę. Rozważmy Etap początkowy, który obejmuje przechowywanie wartości.

### <a name="to-add-multiplication-and-division-problems"></a>Aby dodać problemy mnożenia i dzielenia

1. Dodaj cztery więcej zmiennych całkowitych do formularza.

     [!code-csharp[VbExpressTutorial3Step7#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial3Step7#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#15)]

2. Tak jak wcześniej, zmodyfikuj metodę, `StartTheQuiz()` Aby wprowadzić liczby losowe dla problemów mnożenia i dzielenia.

     [!code-csharp[VbExpressTutorial3Step7#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial3Step7#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#16)]

3. Zmodyfikuj `CheckTheAnswer()` metodę, tak aby sprawdzali również problemy z mnożeniem i dzieleniem.

     [!code-csharp[VbExpressTutorial3Step7#17](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#17)]
     [!code-vb[VbExpressTutorial3Step7#17](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#17)]

     Nie można łatwo wprowadzić znaku mnożenia (x) i znaku dzielenia (÷) przy użyciu klawiatury, dlatego Visual C# i Visual Basic akceptują gwiazdkę (*) dla mnożenia i ukośnika (/) dla dzielenia.

4. Zmień ostatnią część programu obsługi zdarzeń taktu czasomierza, tak aby wypełnił poprawną odpowiedź, gdy skończy się czas.

     [!code-csharp[VbExpressTutorial3Step7#23](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#23)]
     [!code-vb[VbExpressTutorial3Step7#23](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#23)]

5. Zapisz i uruchom program.

     Aby ukończyć quiz, uczestnikom quiz musi odpowiedzieć na cztery problemy, jak pokazano na poniższej ilustracji.

     ![Quiz matematyczny z czterema problemami](../ide/media/express-finishedquiz.png "Express_FinishedQuiz") Quiz matematyczny z czterema problemami

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 8: Dostosowywanie quizu](../ide/step-8-customize-the-quiz.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 6: Dodawanie problemu odejmowania](../ide/step-6-add-a-subtraction-problem.md).
