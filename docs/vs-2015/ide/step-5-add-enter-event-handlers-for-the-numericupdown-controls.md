---
title: Krok 5. Dodawanie obsługi zdarzeń wprowadzania dla formantów NumericUpDown | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 45a99a5d-c881-4298-b74d-adb481dec5ee
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 970f0d592eca22b6f07bc4f938edcd0370ecf9d5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434024"
---
# <a name="step-5-add-enter-event-handlers-for-the-numericupdown-controls"></a>Krok 5. Dodawanie obsługi zdarzeń wprowadzania dla kontrolek NumericUpDown
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W piątej części tego samouczka dodasz programy obsługi zdarzeń Enter, aby trochę ułatwić wprowadzanie odpowiedzi na pytania quizu. Ten kod zaznaczy i wyczyści bieżącą wartość w każdym formancie NumericUpDown, jak najszybciej quizu ją wybierze i zacznie wpisywać inną wartość.  
  
> [!NOTE]
> Ten temat jest częścią serii samouczków na temat podstawowych pojęć kodowania. Aby uzyskać omówienie samouczka, zobacz [samouczek 2: Utwórz Quiz matematyczny](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
### <a name="to-verify-the-default-behavior"></a>Aby sprawdzić zachowanie domyślne  
  
1. Uruchom program i uruchom quiz.  
  
     W formancie NumericUpDown dla problemu dodawania, kursor miga obok **0** (zero).  
  
2. Wprowadź `3`i zwróć uwagę, że formant pokazuje **30**.  
  
3. Wprowadź `5`i zwróć uwagę, że **350** pojawia się, ale zmienia się na **100** po sekundzie.  
  
     Przed rozwiązaniem tego problemu zastanów się, co się dzieje. Zastanów się, dlaczego **0** nie zniknęła po wprowadzeniu `3` i dlaczego **350** zmieniony na **100** , ale nie od razu.  
  
     To zachowanie może się wydawać dziwne, ale dobrym pomysłem biorąc pod uwagę logikę kodu. Po wybraniu **Start** przycisku jego **włączone** właściwość jest ustawiona na **False**, a przycisk jest wyszarzony i niedostępny. Program zmienia bieżące zaznaczenie (focus) do formantu, który ma następną najniższą wartość TabIndex, który jest formantem NumericUpDown dla problemu dodawania. Gdy używasz klawisza Tab, aby przejść do formantu NumericUpDown, kursor zostanie automatycznie umieszczony na początku formantu, dlatego wprowadzane liczby są wyświetlane po lewej stronie i nie po prawej stronie. Po określeniu numeru jest wyższa niż wartość **MaximumValue** właściwość, która jest równa 100, wprowadzona liczba jest zastępowana wartością tej właściwości.  
  
### <a name="to-add-an-enter-event-handler-for-a-numericupdown-control"></a>Aby dodać moduł obsługi zdarzeń Enter w formancie NumericUpDown  
  
1. Wybierz pierwszy formant NumericUpDown (o nazwie "sum") na formularzu, a następnie w **właściwości** okna dialogowego wybierz **zdarzenia** ikonę na pasku narzędzi.  
  
     **Zdarzenia** karcie **właściwości** okno dialogowe wyświetla wszystkie zdarzenia, które można odpowiedzieć (obsłużyć) dla elementu wybranego w formularzu. Ponieważ wybrano formant NumericUpDown, wszystkie wymienione wydarzenia odnoszą się do niego.  
  
2. Wybierz **Enter** zdarzenia wprowadź `answer_Enter`, a następnie naciśnij klawisz Enter.  
  
     ![Okno dialogowe właściwości](../ide/media/express-answerenter.png "Express_AnswerEnter")  
Okno dialogowe właściwości  
  
     Właśnie dodałeś program obsługi zdarzeń Enter dla formantu sumy NumericUpDown i możesz nadałeś **answer_Enter**.  
  
3. W metodzie dla **answer_Enter** procedura obsługi zdarzeń, Dodaj następujący kod.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#11](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#11)]
     [!code-vb[VbExpressTutorial3Step5_6#11](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#11)]  
  
     Ten kod może wyglądać na złożony, ale można go zrozumieć, jeśli spojrzysz na niego krok po kroku. Po pierwsze, spójrz na górę metody: `object sender` w języku C# lub `sender As System.Object` w języku Visual Basic. Ten parametr odwołuje się do obiektu, którego zdarzenie jest uruchamiane, który jest znany jako nadawca. W tym przypadku obiekt nadawcy jest formant NumericUpDown. Tak w pierwszym wierszu metody należy określić że nadawca to nie po prostu każdy obiekt rodzajowy, ale konkretnie formant NumericUpDown. (Każdy formant NumericUpDown jest obiektem, ale nie każdy obiekt jest formantem NumericUpDown). Formant NumericUpDown nosi nazwę **answerBox** w przypadku tej metody, ponieważ będzie używany dla wszystkich formantów NumericUpDown na formularzu, nie tylko dla formantu NumericUpDown sumy. Ponieważ należy zadeklarować zmienną answerBox w tej metodzie, jej zakres dotyczy tylko tej metody. Innymi słowy zmienna może być używana tylko w ramach tej metody.  
  
     Następny wiersz sprawdza, czy answerBox został pomyślnie przekonwertowany (rzutowany) z obiektu do formantu NumericUpDown. Jeśli konwersja nie powiodła, zmienna będzie miała wartość `null` (C#) lub `Nothing` (Visual Basic). Trzeci wiersz pobiera długość odpowiedzi, która jest wyświetlana w formancie NumericUpDown, a czwarty wiersz wybiera bieżącą wartość w formancie na podstawie tej długości. Teraz gdy uczestnik quizu wybierze formant, Visual Studio uruchamia zdarzenie, co powoduje, że bieżącej odpowiedzi do wybrania. Tak szybko, jak osoba wypełniająca quiz zaczyna wprowadzać inną odpowiedź, poprzednia odpowiedź jest czyszczona i zastąpiona nową odpowiedzią.  
  
4. W programie Windows Forms Designer wybierz formant różnicy NumericUpDown.  
  
5. W **zdarzenia** strony **właściwości** okno dialogowe, przewiń w dół do **Enter** zdarzenia, wybierz strzałkę listy rozwijanej na końcu wiersza, a następnie wybierz `answer_Enter`program obsługi zdarzeń, który właśnie został dodany.  
  
6. Powtórz poprzedni krok dla formantów NumericUpDown iloczynu i ilorazu.  
  
7. Zapisz swój program, a następnie uruchom go.  
  
     Po wybraniu formantu NumericUpDown, istniejąca wartość jest automatycznie wybierane i następnie czyszczona, gdy rozpoczniesz wprowadzać inną wartość.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
- Aby przejść do następnego kroku samouczka, zobacz [krok 6: Dodawanie problemu odejmowania](../ide/step-6-add-a-subtraction-problem.md).  
  
- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 4: Dodawanie metody CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md).
