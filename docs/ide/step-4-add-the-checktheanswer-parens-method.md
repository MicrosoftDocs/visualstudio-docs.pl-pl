---
title: Krok 4. Dodawanie metody CheckTheAnswer()
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- csharp
- vb
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c691b1db57fa1a00ad33441e36ff0f7f79716f11
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416513"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Krok 4. Dodawanie metody CheckTheAnswer()
W czwartej części tego samouczka napiszesz metodę, `CheckTheAnswer()`która określa, czy odpowiedzi na problemy matematyczne są poprawne. Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem. Aby zapoznać się z omówieniem samouczka, [zobacz Samouczek 2: Utwórz Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md)matematyczny z limitem czasu.

> [!NOTE]
> Jeśli korzystasz z Visual Basic, użyj `Function` słowa kluczowego zamiast zwykłego `Sub` słowa kluczowego, ponieważ ta metoda zwraca wartość. Jest to naprawdę proste: sub nie zwraca wartości, ale funkcja wykonuje.

## <a name="to-verify-whether-the-answers-are-correct"></a>Aby sprawdzić, czy odpowiedzi są poprawne

1. `CheckTheAnswer()` Dodaj metodę.

     Gdy ta metoda jest wywoływana, dodaje wartości addend1 i addend2 i porównuje wynik z wartością w formancie Sum <xref:System.Windows.Forms.NumericUpDown> . Jeśli wartości są równe, metoda zwraca wartość `true`. W przeciwnym razie metoda zwraca wartość `false`. Kod powinien wyglądać podobnie do poniższego.

     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]

     Następnie sprawdź odpowiedź, aktualizując kod w metodzie dla programu obsługi <xref:System.Windows.Forms.Timer.Tick> zdarzeń czasomierza, aby wywołać nową `CheckTheAnswer()` metodę.

2. Dodaj następujący kod do `if else` instrukcji.

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]

     Jeśli odpowiedź jest poprawna `CheckTheAnswer()` , `true`zwraca. Program obsługi zdarzeń zatrzyma czasomierz, wyświetli komunikat gratulacjami, a następnie ponownie udostępni przycisk **Uruchom** . W przeciwnym razie quiz kontynuuje działanie.

3. Zapisz swój program, uruchom go, uruchom quiz i podaj prawidłową odpowiedź na problem dodawania.

    > [!NOTE]
    > Po wprowadzeniu odpowiedzi musisz wybrać wartość domyślną przed rozpoczęciem wprowadzania odpowiedzi lub należy usunąć zero ręcznie. To zachowanie zostanie poprawione w dalszej części tego samouczka.

     Po podaniu prawidłowej odpowiedzi zostanie otwarte okno komunikatu, przycisk **Start** będzie dostępny i Czasomierz zostanie zatrzymany.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 5: Dodaj programy obsługi zdarzeń Enter dla formantów](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)NumericUpDown.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 3. Dodawanie czasomierza](../ide/step-3-add-a-countdown-timer.md)odliczania.
