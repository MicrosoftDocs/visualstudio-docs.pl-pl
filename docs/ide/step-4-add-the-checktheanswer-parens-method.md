---
title: Krok 4. Dodawanie metody CheckTheAnswer()
description: Dowiedz się, jak napisać metodę metody CheckTheAnswer (), aby określić, czy odpowiedzi na problemy matematyczne są poprawne.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: a1d9d22363aa26628d122b451c51fb7d1df29fbe
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480593"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Krok 4. Dodawanie metody CheckTheAnswer()

W czwartej części tego samouczka napiszesz metodę, `CheckTheAnswer()` która określa, czy odpowiedzi na problemy matematyczne są poprawne. Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-verify-whether-the-answers-are-correct"></a>Aby sprawdzić, czy odpowiedzi są poprawne

> [!NOTE]
> Jeśli korzystasz z Visual Basic, użyj `Function` słowa kluczowego zamiast zwykłego `Sub` słowa kluczowego, ponieważ ta metoda zwraca wartość. Jest to naprawdę proste: sub nie zwraca wartości, ale funkcja wykonuje.

1. Dodaj `CheckTheAnswer()` metodę. Ta metoda powinna być zgodnie z innymi metodami, takimi jak `StartTheQuiz()` .

     Gdy ta metoda jest wywoływana, dodaje wartości addend1 i addend2 i porównuje wynik z wartością w <xref:System.Windows.Forms.NumericUpDown> formancie sum. Jeśli wartości są równe, metoda zwraca wartość `true` . W przeciwnym razie metoda zwraca wartość `false` . Kod powinien wyglądać podobnie do poniższego.

     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Następnie sprawdź odpowiedź, aktualizując kod w metodzie dla <xref:System.Windows.Forms.Timer.Tick> programu obsługi zdarzeń czasomierza, aby wywołać nową `CheckTheAnswer()` metodę.

2. Dodaj następujący kod do `if else` instrukcji w `Timer1_Tick()` metodzie, aby czasomierz zatrzymał się, gdy użytkownik otrzymuje odpowiedź.

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]

     Jeśli odpowiedź jest poprawna, `CheckTheAnswer()` zwraca `true` . Program obsługi zdarzeń zatrzyma czasomierz, wyświetli komunikat gratulacjami, a następnie ponownie udostępni przycisk **Uruchom** . W przeciwnym razie quiz kontynuuje działanie.

3. Zapisz swój program, uruchom go, uruchom quiz i podaj prawidłową odpowiedź na problem dodawania.

    > [!NOTE]
    > Po wprowadzeniu odpowiedzi musisz wybrać wartość domyślną przed rozpoczęciem wprowadzania odpowiedzi lub należy usunąć zero ręcznie. To zachowanie zostanie poprawione w dalszej części tego samouczka.

     Po podaniu prawidłowej odpowiedzi zostanie otwarte okno komunikatu, przycisk **Start** będzie dostępny i Czasomierz zostanie zatrzymany.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[krok 5. Dodawanie obsługi zdarzeń wprowadzania dla formantów NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 3: Dodawanie czasomierza odliczania](../ide/step-3-add-a-countdown-timer.md).
