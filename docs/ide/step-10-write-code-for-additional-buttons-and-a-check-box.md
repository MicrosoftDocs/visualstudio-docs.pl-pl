---
title: 'Krok 10: Napisz kod dodatkowych przycisków i pole wyboru'
ms.date: 08/30/2019
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0dc7281b51d0efe0d19020df6a154e332ad9bb0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579439"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Krok 10: Napisz kod dodatkowych przycisków i pole wyboru

Teraz możesz przystąpić do ukończenia pozostałych czterech metod. Możesz skopiować i wkleić ten kod, ale jeśli chcesz dowiedzieć się najwięcej z tego samouczka, wpisz kod i użyj IntelliSense.

Ten kod dodaje funkcjonalność do przycisków dodanych wcześniej. Bez tego kodu przyciski nic nie robią. Przyciski używają kodu <xref:System.Windows.Forms.Control.Click> w swoich zdarzeniach (a pole wyboru używa <xref:System.Windows.Forms.CheckBox.CheckedChanged> zdarzenia) do wykonywania różnych czynności po aktywowaniu formantów. Na przykład `clearButton_Click` zdarzenie `ClearButton_Click`(lub), które aktywuje się po wybraniu przycisku **Wyczyść obraz,** powoduje wymazanie bieżącego obrazu przez ustawienie jego właściwości **Image** na **wartość null** (lub, **nic).** Każde zdarzenie w kodzie zawiera komentarze, które wyjaśniają, co robi kod.

> [!TIP]
> Najlepszym rozwiązaniem: zawsze skomentuj swój kod. Komentarze są informacjami dla osoby do przeczytania i warto poświęcić czas, aby twój kod był zrozumiały. Wszystko w wierszu komentarza jest ignorowane przez aplikację. W języku C#, komentarz wiersza, wpisując dwa ukośniki do przodu na początku (//), a w języku Visual Basic komentujesz wiersz, zaczynając od pojedynczego cudzysłowu (').

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Jak napisać kod dodatkowych przycisków i pole wyboru

Dodaj następujący kod do pliku kodu **formularza Form1** *(Form1.cs* lub *Form1.vb*).

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

> [!NOTE]
> Kod może nie wyświetlać liter "camelCase".

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz **[Krok 11: Uruchamianie aplikacji i wypróbowanie innych funkcji](../ide/step-11-run-your-program-and-try-other-features.md)**.

* Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 9: Przeglądanie, komentowanie i testowanie kodu](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>Zobacz też

* [Samouczek 2: Tworzenie quizu matematycznego z czasem](tutorial-2-create-a-timed-math-quiz.md)
* [samouczek 3: Tworzenie pasującej gry](tutorial-3-create-a-matching-game.md)
