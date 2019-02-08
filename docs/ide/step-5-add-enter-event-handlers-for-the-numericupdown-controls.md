---
title: Krok 5. Dodawanie obsługi zdarzeń Enter dla formantów NumericUpDown
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45a99a5d-c881-4298-b74d-adb481dec5ee
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 194988a3d21078ebb712afee52d9106659b65b14
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55952335"
---
# <a name="step-5-add-enter-event-handlers-for-the-numericupdown-controls"></a>Krok 5. Dodawanie obsługi zdarzeń Enter dla formantów NumericUpDown

W piątej części tego samouczka dodasz <xref:System.Windows.Forms.Control.Enter> procedury obsługi zdarzeń, aby upewnić się, wprowadzając odpowiedzi do quizu była nieco łatwiejsza. Ten kod zaznaczy i wyczyści bieżącą wartość w każdym <xref:System.Windows.Forms.NumericUpDown> kontrolować, jak najszybciej quizu ją wybierze i zacznie wpisywać inną wartość.

> [!NOTE]
> Ten temat jest częścią serii samouczków na temat podstawowych pojęć kodowania. Aby uzyskać omówienie samouczka, zobacz [samouczek 2: Utwórz quiz matematyczny](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-verify-the-default-behavior"></a>Aby sprawdzić zachowanie domyślne

1. Uruchom program i uruchom quiz.

     W **NumericUpDown** kontrola dla problemu dodawania, kursor miga obok **0** (zero).

2. Wprowadź **3**i zwróć uwagę, że formant pokazuje **30**.

3. Wprowadź **5**i zwróć uwagę, że **350** pojawia się, ale zmienia się na **100** po sekundzie.

     Przed rozwiązaniem tego problemu zastanów się, co się dzieje. Zastanów się, dlaczego **0** nie zniknęła po wprowadzeniu **3** i dlaczego **350** zmieniony na **100** , ale nie od razu.

     To zachowanie może się wydawać dziwne, ale dobrym pomysłem biorąc pod uwagę logikę kodu. Po wybraniu **Start** przycisku jego **włączone** właściwość jest ustawiona na **False**, a przycisk jest wyszarzony i niedostępny. Program zmienia bieżące zaznaczenie (focus) do formantu, który ma następną najniższą wartość TabIndex, który jest formantem NumericUpDown dla problemu dodawania. Kiedy używasz **kartę** klucza, aby przejść do formantu NumericUpDown, kursor zostanie automatycznie umieszczony na początku formantu, dlatego wprowadzane liczby są wyświetlane po lewej stronie i nie po prawej stronie. Po określeniu numeru jest wyższa niż wartość **MaximumValue** właściwość, która jest równa 100, wprowadzona liczba jest zastępowana wartością tej właściwości.

## <a name="to-add-an-enter-event-handler-for-a-numericupdown-control"></a>Aby dodać moduł obsługi zdarzeń Enter w formancie NumericUpDown

1. Wybierz pierwsze **NumericUpDown** kontroli (o nazwie "sum") na formularzu, a następnie w **właściwości** okna dialogowego wybierz **zdarzenia** ikonę na pasku narzędzi.

   ![Zdarzenia przycisku właściwości w pasku narzędzi](media/control-properties-events.png)

   **Zdarzenia** karcie **właściwości** okno dialogowe wyświetla wszystkie zdarzenia, które można odpowiedzieć (obsłużyć) dla elementu wybranego w formularzu. Ponieważ wybrano formant NumericUpDown, wszystkie wymienione wydarzenia odnoszą się do niego.

2. Wybierz **Enter** zdarzeń, typ `answer_Enter`, a następnie naciśnij klawisz **Enter** klucza.

   ![Wprowadź nazwę metody obsługi zdarzeń](media/enter-event.png)

   Właśnie dodałeś program obsługi zdarzeń Enter dla formantu sumy NumericUpDown i możesz nadałeś **answer_Enter**.

3. W metodzie dla **answer_Enter** procedura obsługi zdarzeń, Dodaj następujący kod:

     [!code-vb[VbExpressTutorial3Step5_6#11](../ide/codesnippet/VisualBasic/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#11](../ide/codesnippet/CSharp/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.cs)]

     Ten kod może wyglądać na złożony, ale można go zrozumieć, jeśli spojrzysz na niego krok po kroku. Po pierwsze, spójrz na górę metody: `object sender` w języku C# lub `sender As System.Object` w języku Visual Basic. Ten parametr odwołuje się do obiektu, którego zdarzenie jest uruchamiane, który jest znany jako nadawca. W tym przypadku obiekt nadawcy jest formant NumericUpDown. Tak w pierwszym wierszu metody należy określić że nadawca to nie po prostu każdy obiekt rodzajowy, ale konkretnie formant NumericUpDown. (Każdy formant NumericUpDown jest obiektem, ale nie każdy obiekt jest formantem NumericUpDown). Formant NumericUpDown nosi nazwę **answerBox** w przypadku tej metody, ponieważ będzie używany dla wszystkich formantów NumericUpDown na formularzu, nie tylko dla formantu NumericUpDown sumy. Ponieważ należy zadeklarować zmienną answerBox w tej metodzie, jej zakres dotyczy tylko tej metody. Innymi słowy zmienna może być używana tylko w ramach tej metody.

     Następny wiersz sprawdza, czy answerBox został pomyślnie przekonwertowany (rzutowany) z obiektu do formantu NumericUpDown. Jeśli konwersja nie powiodła, zmienna będzie miała wartość `null` (C#) lub `Nothing` (Visual Basic). Trzeci wiersz pobiera długość odpowiedzi, która jest wyświetlana w formancie NumericUpDown, a czwarty wiersz wybiera bieżącą wartość w formancie na podstawie tej długości. Teraz gdy uczestnik quizu wybierze formant, Visual Studio uruchamia zdarzenie, co powoduje, że bieżącej odpowiedzi do wybrania. Tak szybko, jak osoba wypełniająca quiz zaczyna wprowadzać inną odpowiedź, poprzednia odpowiedź jest czyszczona i zastąpiona nową odpowiedzią.

4. W **Windows Forms Designer**, wybierz opcję, różnicy **NumericUpDown** kontroli.

5. W **zdarzenia** strony **właściwości** okno dialogowe, przewiń w dół do **Enter** zdarzenia, wybierz strzałkę listy rozwijanej na końcu wiersza, a następnie wybierz `answer_Enter`program obsługi zdarzeń, który właśnie został dodany.

6. Powtórz poprzedni krok dla formantów NumericUpDown iloczynu i ilorazu.

7. Zapisz swój program, a następnie uruchom go.

     Po wybraniu **NumericUpDown** kontrolki, istniejąca wartość jest automatycznie wybierane i następnie czyszczona, gdy rozpoczniesz wprowadzać inną wartość.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 6: Dodawanie problemu odejmowania](../ide/step-6-add-a-subtraction-problem.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 4: Dodawanie metody CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md).
