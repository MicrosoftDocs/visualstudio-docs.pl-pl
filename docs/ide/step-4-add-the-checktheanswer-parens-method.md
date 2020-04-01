---
title: Krok 4. Dodawanie metody CheckTheAnswer()
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 199cee66013392a253139abf8ef1b88b502abac2
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472612"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Krok 4. Dodawanie metody CheckTheAnswer()

W czwartej części tego samouczka napiszesz `CheckTheAnswer()`metodę, która określa, czy odpowiedzi na problemy matematyczne są poprawne. Ten temat jest częścią serii samouczków na temat podstawowych pojęć kodowania. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie quizu matematycznego z czasem](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Ten temat jest częścią serii samouczków na temat podstawowych pojęć kodowania. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie quizu matematycznego z czasem](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-verify-whether-the-answers-are-correct"></a>Aby sprawdzić, czy odpowiedzi są poprawne

> [!NOTE]
> Jeśli obserwujesz w języku Visual Basic, użyjesz `Function` słowa kluczowego zamiast zwykłego `Sub` słowa kluczowego, ponieważ ta metoda zwraca wartość. To naprawdę takie proste: sub nie zwraca wartości, ale funkcja nie.

1. Dodaj `CheckTheAnswer()` metodę. Ta metoda powinna być zgodna z innymi metodami, które zostały wprowadzone, takimi jak `StartTheQuiz()`.

     Gdy ta metoda jest wywoływana, dodaje wartości addend1 i addend2 i porównuje <xref:System.Windows.Forms.NumericUpDown> wynik do wartości w formancie sumy. Jeśli wartości są równe, metoda zwraca `true`wartość . W przeciwnym razie metoda `false`zwraca wartość . Kod powinien wyglądać następująco.

     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Następnie sprawdź odpowiedź, aktualizując kod w metodzie dla programu <xref:System.Windows.Forms.Timer.Tick> obsługi zdarzeń czasomierza, aby wywołać nową `CheckTheAnswer()` metodę.

2. Dodaj następujący kod `if else` do instrukcji `Timer1_Tick()` w metodzie, tak aby czasomierz zatrzymuje się, gdy użytkownik pobiera odpowiedź prawo.

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]

     Jeśli odpowiedź jest `CheckTheAnswer()` poprawna, zwraca `true`. Program obsługi zdarzeń zatrzymuje czasomierz, pokazuje komunikat gratulacyjny, a następnie ponownie udostępnia przycisk **Start.** W przeciwnym razie quiz będzie kontynuowany.

3. Zapisz program, uruchom go, rozpocznij quiz i podaj poprawną odpowiedź na problem z dodawaniem.

    > [!NOTE]
    > Po wprowadzeniu odpowiedzi należy wybrać wartość domyślną przed rozpoczęciem wprowadzania odpowiedzi lub ręcznie usunąć wartość zero. To zachowanie zostanie poprawione w dalszej części tego samouczka.

     Po podaniu poprawnej odpowiedzi zostanie otwarte okno komunikatu, przycisk **Start** stanie się dostępny, a stoper zatrzyma się.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[Krok 5: Dodawanie programów obsługi zdarzeń Enter dla formantów NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 3: Dodawanie minutnika](../ide/step-3-add-a-countdown-timer.md).
