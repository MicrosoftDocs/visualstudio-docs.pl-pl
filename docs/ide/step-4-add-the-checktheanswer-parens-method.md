---
title: Krok 4. Dodawanie metody CheckTheAnswer()
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 694336b0012a8f67e732744cfd34cebf9c6f411a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892563"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Krok 4. Dodawanie metody CheckTheAnswer()
W czwartej części tego samouczka będziesz pisać metodę `CheckTheAnswer()`, która określa, czy odpowiedzi na problemy matematyczne są poprawne. Ten temat jest częścią serii samouczków na temat podstawowych pojęć kodowania. Aby uzyskać omówienie samouczka, zobacz [samouczek 2: Utwórz quiz matematyczny](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
> [!NOTE]
>  Jeśli piszesz w Visual Basic użyjesz `Function` słowa kluczowego zamiast zwykłego `Sub` — słowo kluczowe, ponieważ ta metoda zwraca wartość. Jest naprawdę proste: sub nie zwraca wartości, natomiast funkcja.  

## <a name="to-verify-whether-the-answers-are-correct"></a>Aby sprawdzić, czy odpowiedzi są poprawne  

1.  Dodaj `CheckTheAnswer()` metody.  
  
     Gdy ta metoda jest wywoływana, dodaje wartości addend1 i addend2 i porównuje wynik z wartością w sumie <xref:System.Windows.Forms.NumericUpDown> kontroli. Jeśli wartości są równe, metoda zwraca wartość `true`. W przeciwnym razie metoda zwraca wartość `false`. Kod powinien wyglądać następująco.  
  
     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]  
  
     Następnie sprawdzisz odpowiedź, aktualizując kod w metodzie dla czasomierza <xref:System.Windows.Forms.Timer.Tick> programu obsługi zdarzeń, aby wywołać nową `CheckTheAnswer()` metody.  
  
2.  Dodaj następujący kod do `if else` instrukcji.  

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]  

     Jeśli odpowiedź jest poprawna, `CheckTheAnswer()` zwraca `true`. Program obsługi zdarzeń zatrzymuje timer, pokazuje komunikat z gratulacjami i następnie sprawia, że **Start** przycisk ponownie. W przeciwnym razie quiz trwa nadal.  

3.  Zapisz swój program, uruchom go, uruchom quiz i Podaj poprawną odpowiedź na problem dodawania.  

    > [!NOTE]
    >  Po wprowadzeniu swojej odpowiedzi, musisz wybrać wartość domyślną przed rozpoczęciem wprowadzania odpowiedzi lub musisz usunąć zero ręcznie. W dalszej części tego samouczka skorygujesz to zachowanie.  

     Jeśli podasz poprawną odpowiedź, zostanie otwarte okno komunikatu **Start** przycisk staje się dostępny, a timer się zatrzyma.  

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 5: Dodawanie obsługi zdarzeń Enter dla formantów NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 3: Dodawanie czasomierza odliczania](../ide/step-3-add-a-countdown-timer.md).
