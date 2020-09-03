---
title: Krok 4. Dodanie metody metody CheckTheAnswer () | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cbfdc15b06d857b7537a4a327f3201c86d4db2d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671780"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Krok 4. Dodawanie metody CheckTheAnswer()
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W czwartej części tego samouczka napiszesz metodę, `CheckTheAnswer()` która określa, czy odpowiedzi na problemy matematyczne są poprawne. Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Jeśli korzystasz z Visual Basic, użyj `Function` słowa kluczowego zamiast zwykłego `Sub` słowa kluczowego, ponieważ ta metoda zwraca wartość. Jest to naprawdę proste: sub nie zwraca wartości, ale funkcja wykonuje.

### <a name="to-verify-whether-the-answers-are-correct"></a>Aby sprawdzić, czy odpowiedzi są poprawne

1. Dodaj `CheckTheAnswer()` metodę.

     Gdy ta metoda jest wywoływana, dodaje wartości addend1 i addend2 i porównuje wynik z wartością w `NumericUpDown` formancie sum. Jeśli wartości są równe, metoda zwraca wartość `true` . W przeciwnym razie metoda zwraca wartość `false` . Kod powinien wyglądać podobnie do poniższego.

     [!code-csharp[VbExpressTutorial3Step4#8](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#8)]
     [!code-vb[VbExpressTutorial3Step4#8](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#8)]

     Następnie sprawdź odpowiedź, aktualizując kod w metodzie dla programu obsługi zdarzeń taktu czasomierza, aby wywołać nową `CheckTheAnswer()` metodę.

2. Dodaj następujący kod do `if else` instrukcji.

     [!code-csharp[VbExpressTutorial3Step4#10](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#10)]
     [!code-vb[VbExpressTutorial3Step4#10](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#10)]

     Jeśli odpowiedź jest poprawna, `CheckTheAnswer()` zwraca `true` . Program obsługi zdarzeń zatrzyma czasomierz, wyświetli komunikat gratulacjami, a następnie ponownie udostępni przycisk **Uruchom** . W przeciwnym razie quiz kontynuuje działanie.

3. Zapisz swój program, uruchom go, uruchom quiz i podaj prawidłową odpowiedź na problem dodawania.

    > [!NOTE]
    > Po wprowadzeniu odpowiedzi musisz wybrać wartość domyślną przed rozpoczęciem wprowadzania odpowiedzi lub należy usunąć zero ręcznie. To zachowanie zostanie poprawione w dalszej części tego samouczka.

     Po podaniu prawidłowej odpowiedzi zostanie otwarte okno komunikatu, przycisk **Start** będzie dostępny i Czasomierz zostanie zatrzymany.

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 5. Dodawanie obsługi zdarzeń wprowadzania dla formantów NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 3: Dodawanie czasomierza odliczania](../ide/step-3-add-a-countdown-timer.md).
