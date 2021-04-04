---
title: Krok 7. Dodawanie zadań z mnożeniem i dzieleniem
description: Dowiedz się, jak dodać problemy mnożenia i dzielenia.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8027b248fd675a112d64c9889686b9ef9a9c8514
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214190"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Krok 7. Dodawanie zadań z mnożeniem i dzieleniem

W siódmej części tego samouczka dodasz problemy mnożenia i dzielenia, ale najpierw zauważasz, jak wprowadzić tę zmianę. Rozważmy Etap początkowy, który obejmuje przechowywanie wartości.

> [!NOTE]
> Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-multiplication-and-division-problems"></a>Aby dodać problemy mnożenia i dzielenia

1. Dodaj cztery więcej zmiennych całkowitych do formularza.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs" id="Snippet15":::

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

2. Tak jak wcześniej, zmodyfikuj metodę, `StartTheQuiz()` Aby wprowadzić liczby losowe dla problemów mnożenia i dzielenia.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb" id="Snippet16":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs" id="Snippet16":::

3. Zmodyfikuj `CheckTheAnswer()` metodę, tak aby sprawdzali również problemy z mnożeniem i dzieleniem.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb" id="Snippet17":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs" id="Snippet17":::

     Nie można łatwo wprowadzić znaku mnożenia (x) i znaku dzielenia (÷) przy użyciu klawiatury, dlatego w języku C# i Visual Basic akceptuje gwiazdki (*) dla mnożenia i ukośnika (/) dla dzielenia.

4. Zmień ostatnią część obsługi zdarzeń czasomierza, <xref:System.Windows.Forms.Timer.Tick> tak aby wypełnił poprawną odpowiedź, gdy skończy się czas.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb" id="Snippet23":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs" id="Snippet23":::

5. Zapisz i uruchom program.

     Aby ukończyć quiz, uczestnikom quiz musi odpowiedzieć na cztery problemy, jak pokazano na poniższej ilustracji.

     ![Quiz matematyczny z czterema problemami](../ide/media/express_finishedquiz.png)<br/>
***Quiz matematyczny** _ _with cztery problemy *

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[krok 8: Dostosowywanie quizu](../ide/step-8-customize-the-quiz.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 6: Dodawanie problemu odejmowania](../ide/step-6-add-a-subtraction-problem.md).
