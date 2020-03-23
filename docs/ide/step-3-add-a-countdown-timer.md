---
title: 'Krok 3: Dodaj minutnik'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ca2dce7f6f9ddc484b67f250f34d69747c6e46e
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579873"
---
# <a name="step-3-add-a-countdown-timer"></a>Krok 3: Dodaj minutnik

W trzeciej części tego samouczka dodasz minutnik, aby śledzić liczbę sekund, które pozostały do ukończenia quizu.

> [!NOTE]
> Ten temat jest częścią serii samouczków na temat podstawowych pojęć kodowania. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie quizu matematycznego z czasem](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-a-countdown-timer"></a>Aby dodać minutnik

1. Dodaj zmienną całkowitą o nazwie **timeLeft**, podobnie jak w poprzedniej procedurze. Kod powinien wyglądać następująco.

     [!code-vb[VbExpressTutorial3Step3#5](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_1.vb)]
     [!code-csharp[VbExpressTutorial3Step3#5](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Teraz potrzebujesz metody, która faktycznie liczy sekundy, takie jak czasomierz, który podnosi zdarzenie po czasie, który określisz.

2. W oknie projektu przenieś <xref:System.Windows.Forms.Timer> formant z kategorii **Składniki** **przybornika** do formularza.

     Formant pojawi się w szarym obszarze u dołu okna projektu.

3. W formularzu wybierz właśnie dodaną ikonę **timer1** i ustaw jej **właściwość Interval** na **1000**.

     Ponieważ wartość interwału jest milisekund, wartość 1000 <xref:System.Windows.Forms.Timer.Tick> powoduje, że zdarzenie jest uruchamiane co sekundę.

4. W formularzu kliknij dwukrotnie kontrolka **timera** lub wybierz go, a następnie wybierz klawisz **Enter.**

     Edytor kodu pojawia się i wyświetla metodę programu obsługi zdarzeń Tick, który właśnie został dodany.

5. Dodaj następujące instrukcje do nowej metody obsługi zdarzeń.

     [!code-vb[VbExpressTutorial3Step3#6](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_2.vb)]
     [!code-csharp[VbExpressTutorial3Step3#6](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_2.cs)]

     Na podstawie tego, co dodano, czasomierz sprawdza co sekundę, czy czas się wyczerpie, określając, czy **timeLeft** zmienna całkowitej jest większa niż 0. Jeśli tak, czas nadal pozostaje. Czasomierz najpierw odejmuje 1 od timeLeft, a następnie aktualizuje **Text** właściwości **timeLabel** kontroli, aby pokazać uczestnika quizu, ile sekund pozostało.

     Jeśli nie pozostaje czas, czasomierz zatrzymuje się i zmienia tekst **timeLabel** kontroli tak, że pokazuje **czas jest w górę!** Okno komunikatu informuje, że quiz się skończył, a odpowiedź zostanie ujawniona — w tym przypadku przez dodanie addend1 i addend2. **Enabled** właściwość **startButton** kontroli jest ustawiona na **true,** dzięki czemu osoba biorąca quiz można rozpocząć kolejny quiz.

     Właśnie dodałeś `if else` oświadczenie, w jaki sposób mówisz programom o podejmowaniu decyzji. Instrukcja `if else` wygląda następująco.

    > [!NOTE]
    > Poniższy przykład jest tylko do demonstracji - nie dodawaj go do projektu.

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

     Przyjrzyj się uważnie instrukcji, `else` które zostały dodane w bloku, aby wyświetlić odpowiedź na problem z dodawaniem.

     [!code-vb[VbExpressTutorial3Step3#24](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_3.vb)]
     [!code-csharp[VbExpressTutorial3Step3#24](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_3.cs)]

     Instrukcja `addend1 + addend2` dodaje wartości w dwóch zmiennych razem. Pierwsza część`sum.Value`( ) używa **Value** właściwości sumy NumericUpDown kontroli, aby wyświetlić poprawną odpowiedź. Później użyjesz tej samej właściwości, aby sprawdzić odpowiedzi na quiz.

     Osoby biorące udział w quizie <xref:System.Windows.Forms.NumericUpDown> mogą łatwiej wprowadzać liczby za pomocą formantu, dlatego używasz go do odpowiedzi na problemy matematyczne. Wszystkie potencjalne odpowiedzi to liczby pełne od 0 do 100. Pozostawiając wartości domyślne właściwości **Minimum,** **Maximum**i **DecimalPlaces,** należy upewnić się, że osoby biorące udział w quizie nie mogą wprowadzać zbyt wysokich miejsc dziesiętnych, liczb ujemnych ani liczb. (Jeśli chcesz zezwolić osobom biorącym udział w quizie na wprowadzenie wartości 3.141, ale nie 3.1415, możesz ustawić właściwość **DecimalPlaces** na 3).

6. Dodaj trzy wiersze na `StartTheQuiz()` końcu metody, więc kod wygląda następująco.

     [!code-vb[VbExpressTutorial3Step3#7](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_4.vb)]
     [!code-csharp[VbExpressTutorial3Step3#7](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_4.cs)]

     Teraz, po uruchomieniu quizu, **timeLeft** zmienna jest ustawiona na 30 i **Text** właściwość **timeLabel** kontroli jest ustawiona na 30 sekund. Następnie <xref:System.Windows.Forms.Timer.Start> metoda timer kontroli rozpoczyna odliczanie. (Quiz nie sprawdza jeszcze odpowiedzi — to będzie następne).

7. Zapisz program, uruchom go, a następnie wybierz przycisk **Start** w formularzu.

     Zegar zaczyna się odliczać. Gdy skończy się czas, quiz kończy się i pojawia się odpowiedź. Na poniższej ilustracji przedstawiono quiz w toku.

     ![Quiz matematyczny w toku](../ide/media/express_addcountdown.png)<br/>
*Quiz matematyczny w toku*

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[Krok 4: Dodaj metodę CheckTheAnswer().](../ide/step-4-add-the-checktheanswer-parens-method.md)**

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 2: Tworzenie losowego problemu z dodawaniem](../ide/step-2-create-a-random-addition-problem.md).
