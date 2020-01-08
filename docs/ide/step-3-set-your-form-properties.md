---
title: Krok 3. Ustawianie właściwości formularza
ms.date: 08/30/2019
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1be9af1badba19932c5d713bb4134448ccf84caf
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591752"
---
# <a name="step-3-set-your-form-properties"></a>Krok 3. Ustawianie właściwości formularza

Następnie użyj okna **Właściwości** , aby zmienić wygląd formularza.

## <a name="how-to-set-your-form-properties"></a>Jak ustawić właściwości formularza

1. Upewnij się, że szukasz **Projektant formularzy systemu Windows**. W zintegrowanym środowisku programistycznym (IDE) programu Visual Studio wybierz kartę **Form1.cs [Design]** (lub kartę **Form1. vb [Design]** w Visual Basic).

1. Wybierz dowolne miejsce wewnątrz formularza **Form1** , aby go zaznaczyć. Sprawdź okno **Właściwości** , które teraz powinno być wyświetlane właściwości formularza. Formularze mają różne właściwości. Na przykład można ustawić kolor pierwszego planu i tła, tekst tytułu, który pojawia się w górnej części formularza, rozmiar formularza i inne właściwości.

   > [!NOTE]
   > Jeśli okno **Właściwości** nie zostanie wyświetlone, Zatrzymaj aplikację, wybierając przycisk **przerywaj debugowania** na pasku narzędzi lub po prostu Zamknij okno. Jeśli aplikacja jest zatrzymana i nadal nie widzisz okna **Właściwości** , na pasku menu wybierz polecenie **Wyświetl** > **okno właściwości**.

1. Po wybraniu formularza Znajdź właściwość **tekst** w oknie **Właściwości** . W zależności od tego, jak lista jest sortowana, może być konieczne przewinięcie w dół. Wybierz **tekst**, wpisz **Podgląd obrazów**, a następnie wybierz **klawisz ENTER**.  Formularz powinien teraz mieć **obraz** tekstu na pasku tytułu, a okno **Właściwości** powinno wyglądać podobnie do poniższego zrzutu ekranu.

    ![okno Właściwości](../ide/media/express_edittextproperty.png)<br>
   *Okno* właściwości

   > [!NOTE]
   > Właściwości mogą być uporządkowane według **kategorii** lub widoku **alfabetycznego** . Można przełączać się między tymi dwoma widokami za pomocą przycisków w oknie **Właściwości** . W tym samouczku łatwiej jest znaleźć właściwości w widoku **alfabetycznym** .

1. Wróć do **Projektant formularzy systemu Windows**. Wybierz prawy dolny uchwyt przeciągania, czyli mały biały kwadrat w prawym dolnym rogu formularza i pojawia się w następujący sposób.

    ![uchwyt przeciągania](../ide/media/express_bottomrt_drag.png)<br>
   *Przeciągnij uchwyt*

    Przeciągnij uchwyt, aby zmienić rozmiar formularza, tak aby forma była szersza i nieco większa.

1. Sprawdź okno **Właściwości** i Zauważ, że właściwość **size** została zmieniona. Właściwość **size** zmienia się za każdym razem, gdy zmieniany jest rozmiar formularza. Spróbuj przeciągnąć uchwyt formularza, aby zmienić jego rozmiar na rozmiar formularza około **550, 350** (nie musi być dokładne), który powinien być dobrze przydatny dla tego projektu. Alternatywnie można wprowadzić wartości bezpośrednio we właściwości **size** , a następnie wybrać klawisz **Enter** .

1. Uruchom aplikację ponownie. Pamiętaj, że możesz użyć dowolnej z poniższych metod, aby uruchomić aplikację.

   - Wybierz klawisz **F5** .

   - Na pasku menu wybierz **debuguj** > **Rozpocznij debugowanie**.

   - Na pasku narzędzi wybierz przycisk **Rozpocznij debugowanie** , który pojawia się w następujący sposób.

      przycisk paska narzędzi ![rozpoczęcia debugowania](../ide/media/express_icondebug.png)<br>
     *Przycisk paska narzędzi* ***Rozpocznij debugowanie***

     Tak jak wcześniej, środowisko IDE kompiluje i uruchamia aplikację, a zostanie wyświetlone okno.

1. Przed przejściem do następnego kroku Zatrzymaj aplikację, ponieważ środowisko IDE nie pozwoli na zmianę aplikacji podczas jej działania. Pamiętaj, że możesz użyć dowolnej z poniższych metod, aby zatrzymać aplikację.

   - Na pasku narzędzi wybierz przycisk **Zatrzymaj debugowanie** .

   - Na pasku menu wybierz **debuguj** > **Zatrzymaj debugowanie**.

   - Użyj klawiatury i naciśnij klawisz **Shift**+**F5**.

   - Wybierz przycisk **X** w górnym rogu okna **przeglądarki obrazów** .

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz **[krok 4. układ formularza przy użyciu formantu TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)** .

* Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 2. Uruchamianie aplikacji Przeglądarka obrazów](../ide/step-2-run-your-program.md).

## <a name="see-also"></a>Zobacz także

* [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](tutorial-2-create-a-timed-math-quiz.md)
* [Samouczek 3: Tworzenie gry w dopasowywanie](tutorial-3-create-a-matching-game.md)
