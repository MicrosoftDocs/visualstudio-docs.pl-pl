---
title: 'Krok 11: Uruchom aplikację przeglądarki obrazów i wypróbuj inne funkcje'
ms.date: 09/11/2019
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 865064bd85d45ccb24129d289b48143321486ca1
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579904"
---
# <a name="step-11-run-your-picture-viewer-app-and-try-other-features"></a>Krok 11: Uruchom aplikację przeglądarki obrazów i wypróbuj inne funkcje

Aplikacja do przeglądarki obrazów jest gotowa do uruchomienia. Możesz uruchomić aplikację i ustawić kolor <xref:System.Windows.Forms.PictureBox>tła pliku . Aby dowiedzieć się więcej, spróbuj ulepszyć aplikację, zmieniając kolor formularza, dostosowując przyciski i pole wyboru oraz zmieniając właściwości formularza.

## <a name="how-to-run-your-app-and-set-the-background-color"></a>Jak uruchomić aplikację i ustawić kolor tła

1. Wybierz **opcję F5**lub na pasku menu wybierz polecenie **Debugowanie** > **rozpocznij debugowanie**.

1. Przed otwarciem obrazu wybierz przycisk **Ustaw kolor tła.** Zostanie otwarte okno dialogowe **Kolor.**

     ![Okno dialogowe Kolor](../ide/media/express_colordialog.png)<br/>
***Okno*** *dialogowe* Kolor

1. Wybierz kolor, aby ustawić kolor tła PictureBox. Przyjrzyj `backgroundButton_Click()` się uważnie `BackgroundButton_Click()`(lub), aby zrozumieć, jak to działa.

    > [!NOTE]
    > Obraz z Internetu można załadować, wklejając jego adres URL do okna dialogowego **Otwieranie pliku.** Spróbuj znaleźć obraz z przezroczystym tłem, aby kolor tła był wyświetlany.

1. Wybierz przycisk **Wyczyść obraz,** aby upewnić się, że jest czyszczenie. Następnie zamknij aplikację, wybierając przycisk **Zamknij.**

## <a name="try-other-features"></a>Wypróbowywanie innych funkcji

* Zmień kolor formularza i przycisków za pomocą **Właściwości BackColor.**

* Dostosuj przyciski i pole wyboru przy użyciu właściwości **Czcionka** i **Kolor forecolor.**

* Zmień właściwości **FormBorderStyle** i **ControlBox** formularza.

* Użyj właściwości **AcceptButton** i **CancelButton** formularza, aby przyciski były automatycznie wybierane, gdy użytkownik wybierze klawisz **Enter** lub **Esc.** Upewnij się, że aplikacja otworzy okno dialogowe **Otwórz plik,** gdy użytkownik wybierze **pozycję Enter** i zamknij pole, gdy użytkownik wybierze **polecenie Esc**.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej, przejdź do następującego samouczka:

> [!div class="nextstepaction"]
> [Samouczek 2: Tworzenie quizu matematycznego z czasem](../ide/tutorial-2-create-a-timed-math-quiz.md)

Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 10: Pisanie kodu dodatkowych przycisków i pole wyboru](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

## <a name="see-also"></a>Zobacz też

* [Więcej samouczków języka C#](/visualstudio/get-started/csharp/)
* [Więcej samouczków języka Visual Basic](/visualstudio/get-started/visual-basic/)
* [Samouczek języka C++](/cpp/get-started/tutorial-console-cpp)
