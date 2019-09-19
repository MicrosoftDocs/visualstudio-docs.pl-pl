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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c9ff51d8193ebc8c1ca264a334cdd3f1fb7401b
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118923"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Krok 4. Dodawanie metody CheckTheAnswer()

W czwartej części tego samouczka napiszesz metodę, `CheckTheAnswer()`która określa, czy odpowiedzi na problemy matematyczne są poprawne. Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem. Aby zapoznać się z omówieniem samouczka, [zobacz Samouczek 2: Utwórz Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md)matematyczny z limitem czasu.

> [!NOTE]
> Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem.
> - Aby zapoznać się z omówieniem samouczka, [zobacz Samouczek 2: Utwórz Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md)matematyczny z limitem czasu.
> - Aby pobrać kompletną wersję kodu, zobacz [kompletny przykładowy samouczek quizu Matematycznego](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-verify-whether-the-answers-are-correct"></a>Aby sprawdzić, czy odpowiedzi są poprawne

> [!NOTE]
> Jeśli korzystasz z Visual Basic, użyj `Function` słowa kluczowego zamiast zwykłego `Sub` słowa kluczowego, ponieważ ta metoda zwraca wartość. Jest to naprawdę proste: sub nie zwraca wartości, ale funkcja wykonuje.

1. `CheckTheAnswer()` Dodaj metodę.

     Gdy ta metoda jest wywoływana, dodaje wartości addend1 i addend2 i porównuje wynik z wartością w formancie Sum <xref:System.Windows.Forms.NumericUpDown> . Jeśli wartości są równe, metoda zwraca wartość `true`. W przeciwnym razie metoda zwraca wartość `false`. Kod powinien wyglądać podobnie do poniższego.

     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]

     > [!IMPORTANT]
     > Użyj kontrolki język programowania w prawym górnym rogu tej strony, aby wyświetlić fragment C# kodu lub Visual Basic fragment kodu.<br><br>![Kontrolka języka programowania dla Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

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

- Aby przejść do następnego kroku samouczka, zobacz  **[krok 5: Dodaj programy obsługi zdarzeń Enter dla formantów](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)** NumericUpDown.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 3. Dodawanie czasomierza](../ide/step-3-add-a-countdown-timer.md)odliczania.
