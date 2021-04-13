---
title: Uruchom aplikację przeglądarka obrazów i wypróbuj inne funkcje
description: Uruchom aplikację przeglądarka obrazów i wypróbuj inne funkcje w samouczku Tworzenie obrazu przeglądarki.
ms.date: 09/11/2019
ms.custom: SEO-VS-2020
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 91488b72559b2e6deff23a5cae389cd9b4001443
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296511"
---
# <a name="step-11-run-your-picture-viewer-app-and-try-other-features"></a>Krok 11. Uruchamianie aplikacji Przeglądarka obrazów i wypróbuj inne funkcje

Twoja aplikacja dla przeglądarki obrazów została zakończona i jest gotowa do uruchomienia. Możesz uruchomić aplikację i ustawić kolor tła <xref:System.Windows.Forms.PictureBox> . Aby dowiedzieć się więcej, spróbuj poprawić aplikację, zmieniając kolor formularza, dostosowując przyciski i pole wyboru i zmieniając właściwości formularza.

## <a name="how-to-run-your-app-and-set-the-background-color"></a>Jak uruchomić aplikację i ustawić kolor tła

1. Wybierz **F5** lub na pasku menu wybierz **Debuguj**  >  **Rozpocznij debugowanie**.

1. Przed otwarciem obrazu wybierz przycisk **Ustaw kolor tła** . Zostanie otwarte okno dialogowe **koloru** .

     ![Okno dialogowe koloru](../ide/media/express_colordialog.png)<br/>
***Kolor** _ _dialog pole *

1. Wybierz kolor, aby ustawić kolor tła PictureBox. Dokładnie obejrzyj `backgroundButton_Click()` metodę (lub, `BackgroundButton_Click()` ), aby zrozumieć, jak działa.

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
> [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md)

Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 10. Pisanie kodu dla dodatkowych przycisków i pola wyboru](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

## <a name="see-also"></a>Zobacz też

* [Więcej samouczków dotyczących języka C#](../get-started/csharp/index.yml)
* [Więcej samouczków Visual Basic](../get-started/visual-basic/index.yml)
* [Samouczek języka C++](/cpp/get-started/tutorial-console-cpp)