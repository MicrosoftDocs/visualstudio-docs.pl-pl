---
title: 'Krok 5: Dodaj programy obsługi zdarzeń Enter dla formantów NumericUpDown'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 45a99a5d-c881-4298-b74d-adb481dec5ee
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17fb9ba8e82739ddb0a420f52b6f7f945a6454b8
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579831"
---
# <a name="step-5-add-enter-event-handlers-for-the-numericupdown-controls"></a>Krok 5: Dodaj programy obsługi zdarzeń Enter dla formantów NumericUpDown

W piątej części tego samouczka <xref:System.Windows.Forms.Control.Enter> dodasz programy obsługi zdarzeń, aby ułatwić wprowadzanie odpowiedzi na problemy z quizem. Ten kod wybierze i wyczyści <xref:System.Windows.Forms.NumericUpDown> bieżącą wartość w każdej formancie, gdy tylko osoba biorąca udział w quizie wybierze ją i zacznie wprowadzać inną wartość.

> [!NOTE]
> Ten temat jest częścią serii samouczków na temat podstawowych pojęć kodowania. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie quizu matematycznego z czasem](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-verify-the-default-behavior"></a>Aby zweryfikować zachowanie domyślne

1. Uruchom program i rozpocznij quiz.

     W **kontrolce NumericUpDown** dla problemu z dodawaniem kursor miga obok **0** (zero).

2. Wprowadź **3**i zwróć uwagę, że formant pokazuje **30**.

3. Wprowadź **5**i zwróć uwagę, że pojawia się **350,** ale po sekundzie zmienia się na **100.**

     Zanim rozwiążesz ten problem, zastanów się, co się dzieje. Zastanów się, dlaczego **0** nie zniknęło po wprowadzeniu **3** i dlaczego **350** zmienił się na **100,** ale nie od razu.

     To zachowanie może wydawać się dziwne, ale ma sens, biorąc pod uwagę logikę kodu. Po wybraniu przycisku **Start** jego właściwość **Enabled** jest ustawiona na **Fałsz,** a przycisk jest wygaszony i jest niedostępny. Program zmienia bieżące zaznaczenie (fokus) na formant, który ma następną najniższą wartość TabIndex, która jest formantem NumericUpDown dla problemu z dodawaniem. Gdy używasz **klawisza Tab,** aby przejść do kontrolki NumericUpDown, kursor jest automatycznie umieszczany na początku formantu, dlatego wprowadzone liczby pojawiają się z lewej, a nie po prawej stronie. Po określeniu liczby, która jest wyższa niż wartość **właściwości MaximumValue,** która jest ustawiona na 100, wprowadzona liczba jest zastępowana wartością tej właściwości.

## <a name="to-add-an-enter-event-handler-for-a-numericupdown-control"></a>Aby dodać program obsługi zdarzeń Enter dla formantu NumericUpDown

1. Wybierz pierwszy **formant NumericUpDown** (o nazwie "suma") w formularzu, a następnie w oknie dialogowym **Właściwości** wybierz ikonę **Zdarzenia** na pasku narzędzi.

   ![Przycisk Zdarzenia na pasku narzędzi właściwości](media/control-properties-events.png)

   Na karcie **Zdarzenia** w oknie dialogowym **Właściwości** są wyświetlane wszystkie zdarzenia, na które można odpowiedzieć (dojście) dla elementu wybranego w formularzu. Ponieważ wybrano formant NumericUpDown, wszystkie wymienione zdarzenia odnoszą się do niego.

2. Wybierz zdarzenie **Enter,** wpisz `answer_Enter`, a następnie naciśnij klawisz **Enter.**

   ![Wprowadź nazwę metody obsługi zdarzeń](media/enter-event.png)

   Właśnie dodano program obsługi zdarzeń Enter dla sumy Formant NumericUpDown i został nazwany program obsługi **answer_Enter**.

3. W metodzie obsługi zdarzeń **answer_Enter** dodaj następujący kod:

     [!code-vb[VbExpressTutorial3Step5_6#11](../ide/codesnippet/VisualBasic/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#11](../ide/codesnippet/CSharp/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Ten kod może wyglądać skomplikowane, ale można go zrozumieć, jeśli spojrzeć na niego krok po kroku. Najpierw przyjrzyj się górnej `object sender` części metody: w języku C# lub `sender As System.Object` visual basic. Ten parametr odnosi się do obiektu, którego zdarzenie jest wypalania, który jest znany jako nadawca. W takim przypadku obiekt nadawcy jest kontrolką NumericUpDown. Tak więc w pierwszym wierszu metody można określić, że nadawca nie jest tylko dowolny obiekt ogólny, ale w szczególności NumericUpDown kontroli. (Każdy formant NumericUpDown jest obiektem, ale nie każdy obiekt jest formantem NumericUpDown). Formant NumericUpDown nosi nazwę **answerBox** w tej metodzie, ponieważ będzie używany dla wszystkich formantów NumericUpDown w formularzu, a nie tylko dla formantu SumicUpDown. Ponieważ deklarujesz answerBox zmiennej w tej metodzie, jej zakres ma zastosowanie tylko do tej metody. Innymi słowy zmienna może być używana tylko w ramach tej metody.

     Następny wiersz sprawdza, czy answerBox został pomyślnie przekonwertowany (oddanych) z obiektu do kontrolki NumericUpDown. Jeśli konwersja nie powiodła się, `null` zmienna będzie `Nothing` miała wartość (C#) lub (Visual Basic). Trzeci wiersz pobiera długość odpowiedzi, która pojawia się w NumericUpDown kontroli, a czwarty wiersz wybiera bieżącą wartość w formancie na podstawie tej długości. Teraz, gdy osoba biorąca udział w quizie wybierze formant, visual studio uruchamia to zdarzenie, co powoduje, że bieżąca odpowiedź ma być zaznaczona. Gdy tylko osoba biorąca udział w quizie zacznie wprowadzać inną odpowiedź, poprzednia odpowiedź zostanie wyczyszczona i zastąpiona nową odpowiedzią.

4. W **programie Windows Forms Designer**wybierz różnicę w **formancie NumericUpDown.**

5. Na stronie **Zdarzenia** w oknie dialogowym **Właściwości** przewiń w dół do zdarzenia **Enter,** wybierz strzałkę `answer_Enter` rozwijaną na końcu wiersza, a następnie wybierz program obsługi zdarzeń, który właśnie został dodany.

6. Powtórz poprzedni krok dla elementów sterujących ilorazem NumericUpDown.

7. Zapisz program, a następnie uruchom go.

     Po wybraniu formantu **NumericUpDown** istniejąca wartość jest automatycznie zaznaczona, a następnie czyszczona po rozpoczęciu wprowadzania innej wartości.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[Krok 6: Dodawanie problemu odejmowania](../ide/step-6-add-a-subtraction-problem.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 4: Dodawanie metody CheckTheAnswer().](../ide/step-4-add-the-checktheanswer-parens-method.md)
