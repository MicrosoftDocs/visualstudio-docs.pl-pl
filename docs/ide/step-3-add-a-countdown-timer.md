---
title: Krok 3. Dodawanie czasomierza odliczania
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a11e9c75b463aeb4de14dc4bc66f2c7e6d1dae50
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55853251"
---
# <a name="step-3-add-a-countdown-timer"></a>Krok 3. Dodawanie czasomierza odliczania
W trzeciej części tego samouczka dodasz licznik czasu, aby śledzić liczbę sekund, które pozostają uczestnikowi quizu do zakończenia.

> [!NOTE]
>  Ten temat jest częścią serii samouczków na temat podstawowych pojęć kodowania. Aby uzyskać omówienie samouczka, zobacz [samouczek 2: Utwórz quiz matematyczny](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-a-countdown-timer"></a>Aby dodać minutnik

1.  Dodaj zmienną całkowitą o nazwie **timeLeft**, podobnie jak w poprzedniej procedurze. Kod powinien wyglądać następująco.

     [!code-vb[VbExpressTutorial3Step3#5](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_1.vb)]
     [!code-csharp[VbExpressTutorial3Step3#5](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_1.cs)]

     Teraz potrzebujesz metody, która faktycznie zlicza sekundy, takiej jak timer, który wywołuje zdarzenie po upływie czasu, który określisz.

2.  W oknie projektu, Przenieś <xref:System.Windows.Forms.Timer> z kontrolować **składniki** kategorii **przybornika** do formularza.

     Ten formant jest widoczny w szarym obszarze w dolnej części okna projektu.

3.  W formularzu Wybierz **timer1** ikonę, która właśnie dodany i ustaw jego **interwał** właściwości **1000**.

     Ponieważ wartość interwału jest w milisekundach, wartość 1000 powoduje, że <xref:System.Windows.Forms.Timer.Tick> zdarzenia co sekundę.

4.  W formularzu, kliknij dwukrotnie **czasomierza** kontrolować, lub wybierz go, a następnie wybierz **Enter** klucza.

     Edytor kodu pojawi się i wyświetli metodę dla programu obsługi zdarzeń Tick, który właśnie został dodany.

5.  Dodaj następujące instrukcje do nowej metody obsługi zdarzeń.

     [!code-vb[VbExpressTutorial3Step3#6](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_2.vb)]
     [!code-csharp[VbExpressTutorial3Step3#6](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_2.cs)]

     Oparte na elementy dodane przez Ciebie, czasomierz sprawdza co sekundę, czy czas się skończył się poprzez określenie czy **timeLeft** zmienną całkowitą jest większa niż 0. Jeśli tak jest, czas jest nadal pozostaje. Timer najpierw odejmuje 1 od timeLeft, a następnie aktualizuje **tekstu** właściwość **timeLabel** formantu, aby pokazać uczestnikowi quizu, ile sekund pozostało.

     Jeżeli czas się skończy, timer się zatrzyma i zmieni tekst **timeLabel** kontrolować tak, aby pokazywał **czasu!** Okno komunikatu informuje, że quiz się skończył, i odpowiedź jest odsłonięta — w tym przypadku przez dodanie elementów addend1 i addend2. **Włączone** właściwość **startButton** kontrolki jest ustawiona na **true** tak, aby uczestnik mógł uruchomić kolejny quiz.

     Właśnie dodałeś `if else` instrukcję, która wskazuje, jak sprawdzić programy do podejmowania decyzji. `if else` Instrukcji wygląda podobnie do następującej.

    > [!NOTE]
    >  Poniższy przykład jest wyłącznie do celów informacyjnych — nie należy dodawać go do projektu.

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

     Przyjrzyj się bliżej instrukcji, które zostały dodane w `else` bloku, aby wyświetlić odpowiedź na problem dodawania.

     [!code-vb[VbExpressTutorial3Step3#24](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_3.vb)]
     [!code-csharp[VbExpressTutorial3Step3#24](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_3.cs)]

     Wykonywanie instrukcji `addend1 + addend2` razem dodaje wartości w dwóch zmiennych. Pierwsza część (`sum.Value`) używa **wartość** właściwości formantu sumy NumericUpDown, aby wyświetlić poprawną odpowiedź. Umożliwia tę samą właściwość później sprawdzić odpowiedzi do quizu.

     Quizu mogą łatwiej wpisywać liczby przy użyciu <xref:System.Windows.Forms.NumericUpDown> formantu, dlatego używasz takiego odpowiedzi na problemy matematyczne. Wszystkie potencjalne odpowiedzi są liczbami całkowitymi od 0 do 100. Pozostawiając wartości domyślne **Minimum**, **maksymalna**, i **DecimalPlaces** właściwości, należy zapewnić, że quizu nie można wprowadzić liczbę miejsc dziesiętnych, liczby, ujemne lub numery, które są zbyt wysokie. (Jeśli chcesz umożliwić uczestnikom quizu wprowadzanie wartości 3,141, ale nie 3.1415, można ustawić **DecimalPlaces** właściwość 3.)

6.  Dodaj trzy wiersze na końcu `StartTheQuiz()` metody, aby kod wyglądał następująco.

     [!code-vb[VbExpressTutorial3Step3#7](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_4.vb)]
     [!code-csharp[VbExpressTutorial3Step3#7](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_4.cs)]

     Teraz, kiedy quiz się rozpoczyna, **timeLeft** zmienna jest ustawiona na 30 i **tekstu** właściwość **timeLabel** kontrolki jest ustawiona na 30 sekund. A następnie <xref:System.Windows.Forms.Timer.Start> metoda formant Timer rozpoczyna odliczanie do zera. (Quiz nie sprawdza odpowiedzi jeszcze — to przychodzi dalej.)

7.  Zapisz swój program, uruchom go, a następnie wybierz **Start** przycisku w formularzu.

     Timer rozpoczyna odliczanie. Gdy skończy się czas, kończy się quiz i pojawia się odpowiedź. Na poniższej ilustracji przedstawiono quiz w toku.

     ![Quiz matematyczny w toku](../ide/media/express_addcountdown.png) quiz matematyczny w toku

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

-   Aby przejść do następnego kroku samouczka, zobacz [krok 4: Dodawanie metody CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md).

-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 2: Tworzenie losowego problemu dodawania](../ide/step-2-create-a-random-addition-problem.md).
