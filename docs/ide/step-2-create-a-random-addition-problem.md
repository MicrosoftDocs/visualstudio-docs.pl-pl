---
title: 'Krok 2: Utwórz losowy problem z dodawaniem'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2febef6987cf3440f92f6a6c505840cfe3ca3448
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579890"
---
# <a name="step-2-create-a-random-addition-problem"></a>Krok 2: Utwórz losowy problem z dodawaniem

W drugiej części tego samouczka, aby quiz wyzwanie, dodając problemy matematyczne, które są oparte na losowych liczb. Można również utworzyć metodę, `StartTheQuiz()` która jest nazwany i który wypełnia problemy i uruchamia licznik odliczania. W dalszej części tego samouczka dodasz problemy z odejmowania, mnożenia i dzielenia.

> [!NOTE]
> Ten temat jest częścią serii samouczków na temat podstawowych pojęć kodowania. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie quizu matematycznego z czasem](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-create-a-random-addition-problem"></a>Aby utworzyć losowy problem z dodawaniem

1. W projektancie formularzy wybierz formularz (**Form1**).

2. Na pasku menu wybierz pozycję **Wyświetl** > **kod**.

     *Form1.cs* lub *Form1.vb* pojawia się, w zależności od języka programowania, którego używasz, dzięki czemu można wyświetlić kod za formularzem.

3. Utwórz <xref:System.Random> obiekt, `new` dodając instrukcję w górnej części kodu, jak poniżej.

     [!code-csharp[VbExpressTutorial3Step2#1](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_1.cs)]
     [!code-vb[VbExpressTutorial3Step2#1](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_1.vb)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Dodano obiekt Random do formularza i nazwano obiekt **randomizer**.

     `Random`jest znany jako obiekt. Prawdopodobnie słyszałeś to słowo wcześniej, i dowiedzieć się więcej o tym, co to znaczy dla programowania w następnym samouczku. Na razie wystarczy pamiętać, `new` że można używać instrukcji do tworzenia przycisków, etykiet, paneli, OpenFileDialogs, ColorDialogs, SoundPlayers, Randoms, a nawet formularzy, a te elementy są określane jako obiekty. Po uruchomieniu programu formularz jest uruchamiany, a kod za nim tworzy losowy obiekt i nadaje go **losowo.**

     Wkrótce zbudujesz metodę sprawdzania odpowiedzi, więc twój quiz musi używać zmiennych do przechowywania liczb losowych, które generuje dla każdego problemu. Zobacz [zmienne](/dotnet/visual-basic/programming-guide/language-features/variables/index) lub [typy](/dotnet/csharp/programming-guide/types/index). Aby prawidłowo używać zmiennych, należy je zadeklarować, co oznacza wyświetlanie ich nazw i typów danych.

4. Dodaj dwie zmienne całkowite do formularza i nazwij je **addend1** i **addend2**.

    > [!NOTE]
    > Zmienna całkowitej jest znana jako int w języku C# lub Liczba całkowita w języku Visual Basic. Ten rodzaj zmiennej przechowuje liczbę dodatnią lub ujemną od -2147483648 do 2147483647 i może przechowywać tylko liczby pełne, a nie dziesiętne.

     Aby dodać zmienną całkowitą, należy użyć podobnej składni, tak jak w przypadku dodawania losowego obiektu, zgodnie z poniższym kodem.

     [!code-csharp[VbExpressTutorial3Step2#2](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_2.cs)]
     [!code-vb[VbExpressTutorial3Step2#2](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_2.vb)]

5. Dodaj metodę, która `StartTheQuiz()` jest nazwana i która <xref:System.Random.Next> używa Random obiektu metody, aby wyświetlić liczby losowe w etykietach. `StartTheQuiz()`ostatecznie wypełni wszystkie problemy, a następnie uruchomi czasomierz, więc dodaj komentarz. Funkcja powinna wyglądać następująco.

     [!code-csharp[VbExpressTutorial3Step2#3](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_3.cs)]
     [!code-vb[VbExpressTutorial3Step2#3](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_3.vb)]

     Należy zauważyć, że po wprowadzeniu kropki (.) po `randomizer` w kodzie, okno IntelliSense otwiera się i pokazuje wszystkie random metody obiektu, które można wywołać. Na przykład IntelliSense `Next()` wyświetla następującą listę metody.

     ![Następna metoda](../ide/media/express_randomwhite.png)<br/>
*Następna metoda*

     Po wprowadzeniu kropki za obiektem intelliSense pokazuje listę elementów członkowskich obiektu, takich jak właściwości, metody i zdarzenia.

    > [!NOTE]
    > Podczas korzystania `Next()` z metody `Random` z obiektem, `randomizer.Next(50)`na przykład podczas wywoływania, otrzymasz losową liczbę mniejszą niż 50 (od 0 do 49). W tym przykładzie `randomizer.Next(51)`wywołano . Użyłeś 51, a nie 50, aby dwie losowe liczby sumują się do odpowiedzi od 0 do 100. Jeśli przejdziesz 50 `Next()` do metody, wybierze liczbę od 0 do 49, więc najwyższa możliwa odpowiedź to 98, a nie 100. Po pierwszych dwóch instrukcji w uruchomieniu metody, każda z dwóch zmiennych liczb całkowitych, **addend1** i **addend2**, przytrzymaj liczbę losową od 0 do 50. Ten zrzut ekranu pokazuje kod języka C#, ale IntelliSense działa w ten sam sposób dla języka Visual Basic.

     Przyjrzyj się bliżej tym stwierdzeń.

     [!code-csharp[VbExpressTutorial3Step2#18](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_4.cs)]
     [!code-vb[VbExpressTutorial3Step2#18](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_4.vb)]

     Instrukcje ustawić **Text** właściwości **plusLeftLabel** i **plusRightLabel** tak, aby wyświetlić dwie liczby losowe. Aby przekonwertować liczby `ToString()` na tekst, należy użyć metody liczby całkowitej. (W programowaniu ciąg oznacza tekst. Formanty etykiet wyświetlają tylko tekst, a nie liczby.

6. W oknie projektu kliknij dwukrotnie przycisk **Start** lub wybierz go, a następnie wybierz klawisz **Enter.**

     Gdy osoba biorąca udział w quizie wybierze ten przycisk, quiz powinien się rozpocząć, a właśnie dodano program obsługi zdarzeń Click, aby zaimplementować to zachowanie.

7. Dodaj następujące dwie instrukcje.

     [!code-csharp[VbExpressTutorial3Step2#4](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_5.cs)]
     [!code-vb[VbExpressTutorial3Step2#4](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_5.vb)]

     Pierwsza instrukcja wywołuje `StartTheQuiz()` nową metodę. Druga instrukcja ustawia **Enabled** właściwość **startButton** kontroli **false,** tak aby osoba biorąca quiz nie można wybrać przycisk podczas quizu.

8. Zapisz kod, uruchom go, a następnie wybierz przycisk **Start.**

     Pojawia się losowy problem z dodawaniem, jak pokazano na poniższym zrzucie ekranu.

     ![Losowy problem z dodawaniem](../ide/media/express_additionproblem.png)<br/>
*Losowy problem z dodawaniem*

     W następnym kroku samouczka dodasz sumę.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[Krok 3: Dodawanie minutnika](../ide/step-3-add-a-countdown-timer.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 1: Tworzenie projektu i dodawanie etykiet do formularza](../ide/step-1-create-a-project-and-add-labels-to-your-form.md).
