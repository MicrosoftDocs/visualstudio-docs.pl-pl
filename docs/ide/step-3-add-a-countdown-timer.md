---
title: Krok 3. Dodawanie czasomierza odliczającego w dół
description: Dowiedz się, jak dodać czasomierz odliczania, aby śledzić liczbę sekund, które pozostaną na zakończenie dla modułu quizu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 238f6a2b6492fdd4ac04e0b596bbfbc304529786
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950838"
---
# <a name="step-3-add-a-countdown-timer"></a>Krok 3. Dodawanie czasomierza odliczającego w dół

W trzeciej części tego samouczka dodasz czasomierz odliczania, aby śledzić liczbę sekund, które pozostaną na zakończenie przez program quizu.

> [!NOTE]
> Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-a-countdown-timer"></a>Aby dodać czasomierz odliczania

1. Dodaj zmienną całkowitą o nazwie **timeleft**, tak jak w poprzedniej procedurze. Kod powinien wyglądać podobnie do poniższego.

     [!code-vb[VbExpressTutorial3Step3#5](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_1.vb)]
     [!code-csharp[VbExpressTutorial3Step3#5](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Teraz potrzebna jest metoda, która faktycznie zlicza sekundy, takie jak czasomierz, który wywołuje zdarzenie po upływie określonego czasu.

2. W oknie projektowania Przenieś <xref:System.Windows.Forms.Timer> kontrolkę z kategorii **składniki** **przybornika** do formularza.

     Kontrolka pojawia się w szarym obszarze u dołu okna projektowania.

3. Na formularzu Wybierz dodaną ikonę **Timer1** i ustaw jej właściwość **Interval** na **1000**.

     Ponieważ wartość interwału wynosi milisekundy, wartość 1000 powoduje, że <xref:System.Windows.Forms.Timer.Tick> zdarzenie jest uruchamiane co sekundę.

4. W formularzu kliknij dwukrotnie formant **Timer** lub wybierz go, a następnie wybierz klawisz **Enter** .

     Zostanie wyświetlony Edytor kodu i zostanie wyświetlona Metoda programu obsługi zdarzeń Tick, który właśnie został dodany.

5. Dodaj następujące instrukcje do nowej metody obsługi zdarzeń.

     [!code-vb[VbExpressTutorial3Step3#6](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_2.vb)]
     [!code-csharp[VbExpressTutorial3Step3#6](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_2.cs)]

     Na podstawie dodanych przez Ciebie operacji czasomierz sprawdza każdą sekundę, czy czas został uruchomiony przez określenie, czy zmienna **timeleft** Integer jest większa od 0. Jeśli tak jest, czas nadal pozostaje. Czasomierz najpierw odejmuje 1 od timeLeft, a następnie aktualizuje właściwość **Text** formantu **timeLabel** , aby pokazać pozostałą liczbę sekund.

     Jeśli czas nie zostanie przekroczony, czasomierz zatrzyma się i zmieni tekst kontrolki **timeLabel** , aby wyświetlić **czas** pracy. W oknie komunikatu ogłoszono quiz, a odpowiedź jest ujawniana — w tym przypadku przez dodanie addend1 i addend2. Właściwość **Enabled** formantu **startButton** jest ustawiona na **wartość true** , aby można było zacząć korzystać z innego quizu.

     Właśnie dodano `if else` instrukcję, która jest poinformowania programów, aby podejmować decyzje. `if else`Instrukcja wygląda następująco.

    > [!NOTE]
    > Poniższy przykład dotyczy tylko demonstracji — nie należy dodawać go do projektu.

    ```vb
    If (something that your program will check) Then
        ' One or more statements that will run
        ' if what the program checked is true.
    Else
        ' One or more statements that will run
        ' if what the program checked is false.
    End If
    ```

    ```csharp
    if (something that your program will check)
    {
        // One or more statements that will run
        // if what the program checked is true.
    }
    else
    {
        // One or more statements that will run
        // if what the program checked is false.
    }
    ```

     Dokładnie zapoznaj się z instrukcją dodaną w `else` bloku, aby wyświetlić odpowiedź na problem dodawania.

     [!code-vb[VbExpressTutorial3Step3#24](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_3.vb)]
     [!code-csharp[VbExpressTutorial3Step3#24](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_3.cs)]

     Instrukcja `addend1 + addend2` dodaje wartości w obu zmiennych jednocześnie. Pierwsza część ( `sum.Value` ) używa właściwości **wartość** kontrolki sum NumericUpDown, aby wyświetlić poprawną odpowiedź. Użyj tej samej właściwości później, aby sprawdzić odpowiedzi dla quizu.

     Program Quiz uczestnikom może łatwiej wprowadzać liczby przy użyciu <xref:System.Windows.Forms.NumericUpDown> kontrolki, co oznacza, że można ją użyć do odpowiedzi na problemy matematyczne. Wszystkie potencjalne odpowiedzi są liczbami całkowitymi od 0 do 100. Pozostawiając wartości domyślne właściwości **minimum**, **maksimum** i **DecimalPlaces** , upewnij się, że w uczestnikom quizu nie można wprowadzać cyfr dziesiętnych, liczb ujemnych ani liczb, które są zbyt duże. (Jeśli chcesz zezwolić uczestnikomowi quizu na wprowadzenie 3,141, ale nie 3,1415, możesz ustawić właściwość **DecimalPlaces** na 3).

6. Dodaj trzy wiersze na końcu `StartTheQuiz()` metody, tak aby kod wyglądał następująco.

     [!code-vb[VbExpressTutorial3Step3#7](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_4.vb)]
     [!code-csharp[VbExpressTutorial3Step3#7](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_4.cs)]

     Teraz po rozpoczęciu quizu zmienna **timeleft** jest ustawiona na wartość 30, a właściwość **Text** kontrolki **timeLabel** jest ustawiona na 30 sekund. Następnie <xref:System.Windows.Forms.Timer.Start> Metoda formantu Timer zaczyna odliczanie. (Quiz nie sprawdza jeszcze odpowiedzi — jest to kolejne.)

7. Zapisz swój program, uruchom go, a następnie wybierz przycisk **Start** w formularzu.

     Czasomierz zaczyna liczyć w dół. Po uruchomieniu quizu zostanie zakończona i zostanie wyświetlona odpowiedź. Na poniższej ilustracji przedstawiono Quiz w toku.

     ![Quiz matematyczny w toku](../ide/media/express_addcountdown.png)<br/>
*Quiz matematyczny w toku*

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[krok 4: Dodawanie metody metody CheckTheAnswer ()](../ide/step-4-add-the-checktheanswer-parens-method.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 2. Tworzenie losowego problemu z dodaniem](../ide/step-2-create-a-random-addition-problem.md).
