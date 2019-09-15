---
title: Krok 10. Pisanie kodu dla dodatkowych przycisków i pola wyboru
ms.date: 08/30/2019
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c35ee154dd0656f1eb29fd8a03e8c1b63876ed2
ms.sourcegitcommit: 0e482cfc15f809b564c3de61646f29ecd7bfcba6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70987681"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Krok 10. Pisanie kodu dla dodatkowych przycisków i pola wyboru

Teraz wszystko jest gotowe do wykonania innych czterech metod. Możesz skopiować i wkleić ten kod, ale jeśli chcesz poznać większość z tego samouczka, wpisz kod i użyj funkcji IntelliSense.

Ten kod dodaje funkcję do przycisków, które zostały dodane wcześniej. Bez tego kodu przyciski nie wykonują żadnych czynności. Przyciski używają kodu w swoich <xref:System.Windows.Forms.Control.Click> zdarzeniach (a pole wyboru <xref:System.Windows.Forms.CheckBox.CheckedChanged> używa zdarzenia) do wykonywania różnych czynności podczas aktywowania kontrolek. Na przykład `clearButton_Click` `ClearButton_Click`zdarzenie (lub), które aktywuje się po wybraniu przycisku **Wyczyść obraz** , powoduje wymazanie bieżącego obrazu przez ustawienie jego właściwości **Image** na **wartość null** (lub **Nothing**). Każde zdarzenie w kodzie zawiera komentarze objaśniające, jak działa kod.

> [!TIP]
> Najlepszym rozwiązaniem jest: Zawsze Skomentuj swój kod. Komentarze są informacjami dla osoby, które mają być odczytane, i warto pamiętać o tym, aby kod był zrozumiały. Wszystkie elementy w wierszu komentarza są ignorowane przez aplikację. W C#programie Dodaj komentarz do wiersza, wpisując dwa ukośniki do przodu (//), a w Visual Basic skomentować linię, zaczynając od znaku pojedynczego cudzysłowu (').

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Jak napisać kod dla dodatkowych przycisków i pola wyboru

Dodaj następujący kod do pliku kodu **Form1** (*Form1.cs* lub *Form1. vb*).
> [!IMPORTANT]
> Użyj kontrolki język programowania w prawym górnym rogu tej strony, aby wyświetlić fragment C# kodu lub Visual Basic fragment kodu.<br><br>![Kontrolka języka programowania dla Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

> [!NOTE]
> Kod może nie wyświetlać liter "camelCase". 

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz  **[krok 11: Uruchom aplikację i wypróbuj inne funkcje](../ide/step-11-run-your-program-and-try-other-features.md).**

* Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 9: Przejrzyj, Skomentuj i Przetestuj swój kod](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>Zobacz także

* [Samouczek 2: Tworzenie quizu matematycznego z limitem czasu](tutorial-2-create-a-timed-math-quiz.md)
* [Samouczek 3: Tworzenie gry zgodnej](tutorial-3-create-a-matching-game.md)
