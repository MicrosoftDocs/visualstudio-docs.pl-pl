---
title: Pisanie kodu dla dodatkowych przycisków i pola wyboru
description: Dowiedz się, jak napisać kod dla dodatkowych przycisków i pola wyboru w samouczku Tworzenie obrazu przeglądarki.
ms.date: 08/30/2019
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c8fa5bcacd4d6086dbe926240ec11743f06e513d
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480333"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Krok 10. Pisanie kodu dla dodatkowych przycisków i pola wyboru

Teraz wszystko jest gotowe do wykonania innych czterech metod. Możesz skopiować i wkleić ten kod, ale jeśli chcesz poznać większość z tego samouczka, wpisz kod i użyj funkcji IntelliSense.

Ten kod dodaje funkcję do przycisków, które zostały dodane wcześniej. Bez tego kodu przyciski nie wykonują żadnych czynności. Przyciski używają kodu w swoich <xref:System.Windows.Forms.Control.Click> zdarzeniach (a pole wyboru używa <xref:System.Windows.Forms.CheckBox.CheckedChanged> zdarzenia) do wykonywania różnych czynności podczas aktywowania kontrolek. Na przykład `clearButton_Click` zdarzenie (lub `ClearButton_Click` ), które aktywuje się po wybraniu przycisku **Wyczyść obraz** , powoduje wymazanie bieżącego obrazu przez ustawienie jego właściwości **Image** na **wartość null** (lub **Nothing**). Każde zdarzenie w kodzie zawiera komentarze objaśniające, jak działa kod.

> [!TIP]
> Najlepszym rozwiązaniem jest zawsze Dodawanie komentarzy do kodu. Komentarze są informacjami dla osoby, które mają być odczytane, i warto pamiętać o tym, aby kod był zrozumiały. Wszystkie elementy w wierszu komentarza są ignorowane przez aplikację. W języku C# można skomentować wiersz, wpisując dwa ukośniki do przodu (//), a w Visual Basic komentarz wiersza, zaczynając od pojedynczego cudzysłowu (').

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Jak napisać kod dla dodatkowych przycisków i pola wyboru

Dodaj następujący kod do pliku kodu **Form1** (*Form1.cs* lub *Form1. vb*).

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

> [!NOTE]
> Kod może nie wyświetlać liter "camelCase".

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz **[krok 11. Uruchamianie aplikacji i wypróbuj inne funkcje](../ide/step-11-run-your-program-and-try-other-features.md)**.

* Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 9: przeglądanie, komentowanie i testowanie kodu](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>Zobacz też

* [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](tutorial-2-create-a-timed-math-quiz.md)
* [Samouczek 3: Tworzenie gry w dopasowywanie](tutorial-3-create-a-matching-game.md)
