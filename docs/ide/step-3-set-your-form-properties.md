---
title: 'Krok 3: Ustawianie właściwości formularza'
ms.date: 08/30/2019
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82dbef4baee72be8ff96f83e436b2587e9a020ea
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579853"
---
# <a name="step-3-set-your-form-properties"></a>Krok 3: Ustawianie właściwości formularza

Następnie użyj okna **Właściwości,** aby zmienić wygląd formularza.

## <a name="how-to-set-your-form-properties"></a>Jak ustawić właściwości formularza

1. Upewnij się, że korzystasz z **programu Windows Forms Designer**. W zintegrowanym środowisku programistycznym programu Visual Studio (IDE) wybierz kartę **Form1.cs [Projekt]** (lub kartę **Form1.vb [Projekt]** w języku Visual Basic).

1. Wybierz dowolne miejsce w formularzu **Form1,** aby go zaznaczyć. Spójrz na **właściwości** okna, które powinny być teraz wyświetlane właściwości formularza. Formularze mają różne właściwości. Można na przykład ustawić kolor pierwszego planu i tła, tekst tytułu wyświetlany u góry formularza, rozmiar formularza i inne właściwości.

   > [!NOTE]
   > Jeśli okno **Właściwości** nie jest wyświetlane, zatrzymaj aplikację, wybierając kwadratowy przycisk **Zatrzymaj debugowanie** na pasku narzędzi lub po prostu zamknij okno. Jeśli aplikacja została zatrzymana i nadal nie widzisz okna **Właściwości,** na pasku menu wybierz polecenie **Wyświetl** > **okno Właściwości**.

1. Po wybraniu formularza znajdź **właściwość Tekst** w oknie **Właściwości.** W zależności od sposobu sortowania listy może być konieczne przewinięcie w dół. Wybierz **pozycję Tekst**, wpisz Podgląd **obrazów**, a następnie wybierz pozycję **Enter**.  Formularz powinien mieć teraz **podgląd** obrazu tekstu na pasku tytułu, a okno **Właściwości** powinno wyglądać podobnie do poniższego zrzutu ekranu.

    ![Okno Właściwości](../ide/media/express_edittextproperty.png)<br>
   ***Properties*** *Okno* Właściwości

   > [!NOTE]
   > Właściwości można zamówić w widoku **kategoryzowanym** lub **alfabetycznym.** Można przełączać się między tymi dwoma **widokami** za pomocą przycisków w oknie Właściwości. W tym samouczku łatwiej jest znaleźć właściwości w widoku **alfabetycznym.**

1. Wróć do **programu Windows Forms Designer**. Wybierz prawy dolny rączka przeciągania formularza, który jest małym białym kwadratem w prawym dolnym połówek formularza i jest wyświetlany w następujący sposób.

    ![Przeciągnij uchwyt](../ide/media/express_bottomrt_drag.png)<br>
   *Przeciągnij uchwyt*

    Przeciągnij uchwyt, aby zmienić rozmiar formularza, aby formularz był szerszy i nieco wyższy.

1. Spójrz na **właściwości** okna i zauważyć, że **Size** właściwość została zmieniona. Właściwość **Rozmiar** zmienia się przy każdej zmianie rozmiaru formularza. Spróbuj przeciągnąć uchwyt formularza, aby zmienić jego rozmiar do rozmiaru formularza około **550, 350** (nie trzeba dokładnie), co powinno działać dobrze dla tego projektu. Alternatywnie można wprowadzić wartości bezpośrednio we właściwości **Size,** a następnie wybrać klawisz **Enter.**

1. Ponownie uruchom aplikację. Pamiętaj, że możesz użyć dowolnej z następujących metod, aby uruchomić aplikację.

   - Wybierz klawisz **F5.**

   - Na pasku menu wybierz polecenie **Debugowanie** > **start debugowania**.

   - Na pasku narzędzi wybierz przycisk **Rozpocznij debugowanie,** który jest wyświetlany w następujący sposób.

      ![Przycisk Uruchamianie paska narzędzi Debugowania](../ide/media/express_icondebug.png)<br>
     ***Przycisk Uruchamianie paska narzędzi Debugowania*** *toolbar button*

     Podobnie jak wcześniej, IDE tworzy i uruchamia aplikację i pojawi się okno.

1. Przed przejściem do następnego kroku zatrzymaj aplikację, ponieważ ide nie pozwala na zmianę aplikacji, gdy jest uruchomiona. Pamiętaj, że możesz użyć dowolnej z następujących metod, aby zatrzymać aplikację.

   - Na pasku narzędzi wybierz przycisk **Zatrzymaj debugowanie.**

   - Na pasku menu wybierz pozycję **Debugowanie** > **zatrzymaj debugowanie**.

   - Użyj klawiatury i naciśnij klawisz **Shift**+**F5**.

   - Wybierz przycisk **X** w górnym rogu okna **Podgląd obrazu.**

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz **[Krok 4: Rozmieść formularz za pomocą kontrolki TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)**.

* Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 2: Uruchamianie aplikacji przeglądarki obrazów](../ide/step-2-run-your-program.md).

## <a name="see-also"></a>Zobacz też

* [Samouczek 2: Tworzenie quizu matematycznego z czasem](tutorial-2-create-a-timed-math-quiz.md)
* [samouczek 3: Tworzenie pasującej gry](tutorial-3-create-a-matching-game.md)
