---
title: Krok 3. Dodawanie czasomierza odliczania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4440370453db96fa207c283e9c4a03b28d7ef6b7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54775971"
---
# <a name="step-3-add-a-countdown-timer"></a>Krok 3. Dodawanie czasomierza odliczającego w dół
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W trzeciej części tego samouczka dodasz licznik czasu, aby śledzić liczbę sekund, które pozostają uczestnikowi quizu do zakończenia.  
  
> [!NOTE]
>  Ten temat jest częścią serii samouczków na temat podstawowych pojęć kodowania. Aby uzyskać omówienie samouczka, zobacz [samouczek 2: Utwórz Quiz matematyczny](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
### <a name="to-add-a-countdown-timer"></a>Aby dodać minutnik  
  
1.  Dodaj zmienną całkowitą o nazwie **timeLeft**, podobnie jak w poprzedniej procedurze. Kod powinien wyglądać następująco.  
  
     [!code-csharp[VbExpressTutorial3Step3#5](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#5)]
     [!code-vb[VbExpressTutorial3Step3#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#5)]  
  
     Teraz potrzebujesz metody, która faktycznie zlicza sekundy, takiej jak timer, który wywołuje zdarzenie po upływie czasu, który określisz.  
  
2.  W oknie projektu, Przenieś `Timer` z kontrolować **składniki** kategorii przybornika do formularza.  
  
     Ten formant jest widoczny w szarym obszarze w dolnej części okna projektu.  
  
3.  W formularzu Wybierz **timer1** ikonę, która właśnie dodany i ustaw jego **interwał** właściwości **1000**.  
  
     Ponieważ wartość interwału jest w milisekundach, wartość 1000 powoduje, że zdarzenie Tick jest inicjowane co sekundę.  
  
4.  W formularzu kliknij dwukrotnie formant Timer lub wybierz go, a następnie naciśnij klawisz Enter.  
  
     Edytor kodu pojawi się i wyświetli metodę dla programu obsługi zdarzeń Tick, który właśnie został dodany.  
  
5.  Dodaj następujące instrukcje do nowej metody obsługi zdarzeń.  
  
     [!code-csharp[VbExpressTutorial3Step3#6](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#6)]
     [!code-vb[VbExpressTutorial3Step3#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#6)]  
  
     Oparte na elementy dodane przez Ciebie, czasomierz sprawdza co sekundę, czy czas się skończył się poprzez określenie czy **timeLeft** zmienną całkowitą jest większa niż 0. Jeśli tak jest, czas jest nadal pozostaje. Timer najpierw odejmuje 1 od timeLeft, a następnie aktualizuje **tekstu** właściwość `timeLabel` formantu, aby pokazać uczestnikowi quizu, ile sekund pozostało.  
  
     Jeżeli czas się skończy, timer się zatrzyma i zmieni tekst `timeLabel` kontrolować tak, aby pokazywał **czasu!** Okno komunikatu informuje, że quiz się skończył, i odpowiedź jest odsłonięta — w tym przypadku przez dodanie elementów addend1 i addend2. **Włączone** właściwość `startButton` kontrolki jest ustawiona na `true` tak, aby uczestnik mógł uruchomić kolejny quiz.  
  
     Właśnie dodałeś `if else` instrukcję, która wskazuje, jak sprawdzić programy do podejmowania decyzji. `if else` Instrukcji wygląda podobnie do następującej.  
  
    > [!NOTE]
    >  Poniższy przykład jest wyłącznie do celów informacyjnych – nie dodawaj go do projektu.  
  
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
  
     [!code-csharp[VbExpressTutorial3Step3#24](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#24)]
     [!code-vb[VbExpressTutorial3Step3#24](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#24)]  
  
     Wykonywanie instrukcji `addend1 + addend2` razem dodaje wartości w dwóch zmiennych. Pierwsza część (`sum.Value`) używa **wartość** właściwość sumy `NumericUpDown` formantu, aby wyświetlić poprawną odpowiedź. Umożliwia tę samą właściwość później sprawdzić odpowiedzi do quizu.  
  
     Quizu mogą łatwiej wpisywać liczby przy użyciu `NumericUpDown` formantu, dlatego używasz takiego odpowiedzi na problemy matematyczne. Wszystkie potencjalne odpowiedzi są liczbami całkowitymi od 0 do 100. Pozostawiając wartości domyślne **Minimum**, **maksymalna**, i **DecimalPlaces** właściwości, należy zapewnić, że quizu nie można wprowadzić liczbę miejsc dziesiętnych, liczby, ujemne lub numery, które są zbyt wysokie. (Jeśli chcesz umożliwić uczestnikom quizu wprowadzanie wartości 3,141, ale nie 3.1415, można ustawić **DecimalPlaces** właściwość 3.)  
  
6.  Dodaj trzy wiersze na końcu `StartTheQuiz()` metody, aby kod wyglądał następująco.  
  
     [!code-csharp[VbExpressTutorial3Step3#7](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#7)]
     [!code-vb[VbExpressTutorial3Step3#7](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#7)]  
  
     Teraz, kiedy quiz się rozpoczyna, **timeLeft** zmienna jest ustawiona na 30 i **tekstu** właściwość `timeLabel` kontrolki jest ustawiona na 30 sekund. A następnie `Start()` metody `Timer` kontroli zaczyna odliczanie do zera. (Quiz nie sprawdza odpowiedzi jeszcze — to przychodzi dalej.)  
  
7.  Zapisz swój program, uruchom go, a następnie wybierz **Start** przycisku w formularzu.  
  
     Timer rozpoczyna odliczanie. Gdy skończy się czas, kończy się quiz i pojawia się odpowiedź. Na poniższej ilustracji przedstawiono quiz w toku.  
  
     ![Quiz matematyczny w toku](../ide/media/express-addcountdown.png "Express_AddCountdown")  
Quiz matematyczny w toku  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 4: Dodawanie metody CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 2: Tworzenie losowego problemu dodawania](../ide/step-2-create-a-random-addition-problem.md).
