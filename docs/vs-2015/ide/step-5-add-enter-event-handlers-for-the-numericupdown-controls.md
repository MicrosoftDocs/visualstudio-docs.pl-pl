---
title: Krok 5. Dodawanie obsługi zdarzeń Enter dla formantów NumericUpDown | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 45a99a5d-c881-4298-b74d-adb481dec5ee
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 566bcf10d681b9ea81ee78601bf8536e9e6d9985
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671749"
---
# <a name="step-5-add-enter-event-handlers-for-the-numericupdown-controls"></a>Krok 5. Dodawanie obsługi zdarzeń wprowadzania dla formantów NumericUpDown
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W piątej części tego samouczka dodasz programy obsługi zdarzeń, aby wprowadzić odpowiedzi na problemy z quizem nieco łatwiej. Ten kod zostanie wybrany i wyczyści bieżącą wartość w każdej kontrolce NumericUpDown zaraz po jej wybraniu i rozpoczęciu wprowadzania innej wartości.

> [!NOTE]
> Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md).

### <a name="to-verify-the-default-behavior"></a>Aby sprawdzić zachowanie domyślne

1. Uruchom program i uruchom quiz.

     W kontrolce NumericUpDown dla problemu dodawania, kursor będzie się znajdował obok **0** (zero).

2. Wprowadź `3` wartość i zwróć uwagę na to, że kontrolka pokazuje **30**.

3. Wprowadź wartość `5` i pamiętaj, że **350** pojawia się, **100** ale po drugiej.

     Przed usunięciem tego problemu należy zastanowić się, co się dzieje. Zastanów się, dlaczego **0** nie znika po wprowadzeniu `3` i dlaczego **350** zmieniony na **100** , ale nie od razu.

     Takie zachowanie może wydawać się nieparzyste, ale jest zrozumiałe dla logiki kodu. Po wybraniu przycisku **Start** , jego właściwość **Enabled** ma wartość **false**, a przycisk jest wyszarzony i jest niedostępny. Program zmienia bieżące zaznaczenie (fokus) na kontrolkę, która ma następną najmniejszą wartość TabIndex, która jest kontrolką NumericUpDown dla problemu dodawania. Gdy używasz klawisza Tab, aby przejść do kontrolki NumericUpDown, kursor jest automatycznie ustawiany na początku kontrolki, co oznacza, że wprowadzone liczby są wyświetlane po lewej stronie, a nie po prawej stronie. Po określeniu liczby, która jest wyższa niż wartość właściwości **MaximumValue** , która jest ustawiona na 100, wprowadzona liczba jest zastępowana wartością tej właściwości.

### <a name="to-add-an-enter-event-handler-for-a-numericupdown-control"></a>Aby dodać procedurę obsługi zdarzeń Enter dla kontrolki NumericUpDown

1. Wybierz pierwszą kontrolkę NumericUpDown (o nazwie "Sum") w formularzu, a następnie w oknie dialogowym **Właściwości** wybierz ikonę **zdarzenia** na pasku narzędzi.

     Na karcie **zdarzenia** w oknie dialogowym **Właściwości** są wyświetlane wszystkie zdarzenia, na które można odpowiedzieć (dojście) dla elementu wybranego w formularzu. Ze względu na to, że wybrano kontrolkę NumericUpDown, wszystkie zdarzenia na liście odnoszą się do niego.

2. Wybierz zdarzenie **Enter** , ENTER `answer_Enter` , a następnie wybierz klawisz ENTER.

     ![Okno dialogowe właściwości](../ide/media/express-answerenter.png "Express_AnswerEnter") Okno dialogowe właściwości

     Właśnie dodano procedurę obsługi zdarzeń Enter dla kontrolki sum NumericUpDown, a nazwa programu obsługi została określona jako **answer_Enter**.

3. W metodzie dla programu obsługi zdarzeń **answer_Enter** Dodaj następujący kod.

     [!code-csharp[VbExpressTutorial3Step5_6#11](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#11)]
     [!code-vb[VbExpressTutorial3Step5_6#11](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#11)]

     Ten kod może wyglądać skomplikowanie, ale możesz go zrozumieć, Jeśli zobaczysz go na etapie krok po kroku. Najpierw Spójrz na początek metody: `object sender` w języku C# lub `sender As System.Object` w Visual Basic. Ten parametr odnosi się do obiektu, którego zdarzenie jest wyzwalane, co jest znane jako nadawca. W takim przypadku obiektem nadawcy jest formant NumericUpDown. Dlatego w pierwszym wierszu metody należy określić, że nadawca nie jest tylko obiektem ogólnym, ale szczególnie formantem NumericUpDown. (Każda kontrolka NumericUpDown jest obiektem, ale nie każdy obiekt jest kontrolką NumericUpDown). Kontrolka NumericUpDown ma nazwę **answerBox** w tej metodzie, ponieważ będzie używana we wszystkich kontrolkach NumericUpDown w formularzu, a nie tylko w formancie NumericUpDown sum. Ponieważ w tej metodzie deklarujesz zmienną answerBox, jej zakres ma zastosowanie tylko do tej metody. Innymi słowy, zmienna może być używana tylko w ramach tej metody.

     Następny wiersz weryfikuje, czy answerBox został pomyślnie przekonwertowany (rzutowany) z obiektu do kontrolki NumericUpDown. Jeśli konwersja zakończyła się niepowodzeniem, zmienna miałaby wartość `null` (C#) lub `Nothing` (Visual Basic). Trzeci wiersz otrzymuje długość odpowiedzi, która pojawia się w kontrolce NumericUpDown, a czwarta linia wybiera bieżącą wartość w kontrolce na podstawie tej długości. Teraz, gdy program quizu wybierze formant, program Visual Studio wyzwala to zdarzenie, co powoduje wybranie bieżącej odpowiedzi. Zaraz po rozpoczęciu przez program quizu w celu wprowadzenia innej odpowiedzi poprzednia odpowiedź zostanie wyczyszczona i zastąpiona nową odpowiedzią.

4. W Projektant formularzy systemu Windows wybierz formant różnica NumericUpDown.

5. Na stronie **zdarzenia** okna dialogowego **Właściwości** przewiń w dół do zdarzenia **Enter** , wybierz strzałkę listy rozwijanej na końcu wiersza, a następnie wybierz `answer_Enter` właśnie dodany program obsługi zdarzeń.

6. Powtórz poprzedni krok dla kontrolek NumericUpDown produktu i ilorazu.

7. Zapisz swój program, a następnie uruchom go.

     Po wybraniu formantu NumericUpDown, istniejąca wartość jest wybierana automatycznie, a następnie wyczyszczona po rozpoczęciu wprowadzania innej wartości.

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 6: Dodawanie problemu odejmowania](../ide/step-6-add-a-subtraction-problem.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 4: Dodawanie metody metody CheckTheAnswer ()](../ide/step-4-add-the-checktheanswer-parens-method.md).
