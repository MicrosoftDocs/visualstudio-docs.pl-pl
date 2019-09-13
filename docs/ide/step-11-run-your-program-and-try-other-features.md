---
title: Krok 11. Uruchom aplikację przeglądarka obrazów i wypróbuj inne funkcje
ms.date: 09/11/2019
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 672156f9c1274189e904c79eb74a0c01e10f3a60
ms.sourcegitcommit: b60a00ac3165364ee0e53f7f6faef8e9fe59ec4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70913129"
---
# <a name="step-11-run-your-picture-viewer-app-and-try-other-features"></a>Krok 11. Uruchom aplikację przeglądarka obrazów i wypróbuj inne funkcje

Twoja aplikacja dla przeglądarki obrazów została zakończona i jest gotowa do uruchomienia. Możesz uruchomić aplikację i ustawić kolor <xref:System.Windows.Forms.PictureBox>tła. Aby dowiedzieć się więcej, spróbuj poprawić aplikację, zmieniając kolor formularza, dostosowując przyciski i pole wyboru i zmieniając właściwości formularza.

## <a name="how-to-run-your-app-and-set-the-background-color"></a>Jak uruchomić aplikację i ustawić kolor tła

1. Wybierz **F5**lub na pasku menu wybierz **Debuguj** > **Rozpocznij debugowanie**.

1. Przed otwarciem obrazu wybierz przycisk **Ustaw kolor tła** . Zostanie otwarte okno dialogowe **koloru** .

     ![Okno dialogowe koloru](../ide/media/express_colordialog.png)<br/>
***Kolor*** okno *dialogowe*

1. Wybierz kolor, aby ustawić kolor tła PictureBox. Dokładnie `backgroundButton_Click()` Obejrzyj metodę (lub,) `BackgroundButton_Click()`, aby zrozumieć, jak działa.

    > [!NOTE]
    > Możesz załadować obraz z Internetu, wklejając jego adres URL do okna dialogowego **Otwórz plik** . Spróbuj znaleźć obraz z przezroczystym tłem, aby wyświetlić kolor tła.

1. Wybierz przycisk **Wyczyść obraz** , aby upewnić się, że został wyczyszczony. Następnie zamknij aplikację, wybierając przycisk **Zamknij** .

## <a name="try-other-features"></a>Wypróbowywanie innych funkcji

* Zmień kolor formularza i przycisków przy użyciu właściwości **BackColor** .

* Dostosuj przyciski i pola wyboru przy użyciu właściwości **Font** i **ForeColor** .

* Zmień właściwości **FormBorderStyle** i **ControlBox** formularza.

* Użyj właściwości **AcceptButton** i **CancelButton** formularza, aby przyciski były wybierane automatycznie, gdy użytkownik wybierze klawisz **Enter** lub **ESC** . Utwórz aplikację otwierającą okno dialogowe **Otwórz plik** , gdy użytkownik wybierze **klawisz ENTER** i zamknie pole, gdy użytkownik wybierze **klawisz ESC**.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej, przejdź do następującego samouczka:

> [!div class="nextstepaction"]
> [Samouczek 2: Tworzenie quizu matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md)

Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 10: Napisz kod dla dodatkowych przycisków i pola](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)wyboru.

## <a name="see-also"></a>Zobacz także

* [Więcej C# samouczków](/visualstudio/get-started/csharp/)
* [Więcej samouczków Visual Basic](/visualstudio/get-started/visual-basic/)
* [C++Ręczny](../ide/getting-started-with-cpp-in-visual-studio.md)
