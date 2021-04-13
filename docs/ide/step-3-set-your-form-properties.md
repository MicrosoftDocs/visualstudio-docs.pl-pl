---
title: Krok 3. Ustawianie właściwości formularza
description: Dowiedz się, jak używać okno Właściwości, aby zmienić wygląd formularza.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5741a20def684b517d0eed684e08bfff65a54f6a
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296316"
---
# <a name="step-3-set-your-form-properties"></a>Krok 3. Ustawianie właściwości formularza

Następnie użyj okna **Właściwości** , aby zmienić wygląd formularza.

## <a name="how-to-set-your-form-properties"></a>Jak ustawić właściwości formularza

1. Upewnij się, że szukasz **Projektant formularzy systemu Windows**. W zintegrowanym środowisku programistycznym (IDE) programu Visual Studio wybierz kartę **Form1. cs [Design]** (lub kartę **Form1. vb [design]** w Visual Basic).

1. Wybierz dowolne miejsce wewnątrz formularza **Form1** , aby go zaznaczyć. Sprawdź okno **Właściwości** , które teraz powinno być wyświetlane właściwości formularza. Formularze mają różne właściwości. Na przykład można ustawić kolor pierwszego planu i tła, tekst tytułu, który pojawia się w górnej części formularza, rozmiar formularza i inne właściwości.

   > [!NOTE]
   > Jeśli okno **Właściwości** nie zostanie wyświetlone, Zatrzymaj aplikację, wybierając przycisk **przerywaj debugowania** na pasku narzędzi lub po prostu Zamknij okno. Jeśli aplikacja jest zatrzymana i nadal nie widzisz okna **Właściwości** , na pasku menu wybierz polecenie **Wyświetl**  >  **okno właściwości**.

1. Po wybraniu formularza Znajdź właściwość **tekst** w oknie **Właściwości** . W zależności od tego, jak lista jest sortowana, może być konieczne przewinięcie w dół. Wybierz **tekst**, wpisz **Podgląd obrazów**, a następnie wybierz **klawisz ENTER**.  Formularz powinien teraz mieć **obraz** tekstu na pasku tytułu, a okno **Właściwości** powinno wyglądać podobnie do poniższego zrzutu ekranu.

    ![Okno właściwości](../ide/media/express_edittextproperty.png)<br>
   ***Właściwości** _ _window *

   > [!NOTE]
   > Właściwości mogą być uporządkowane według **kategorii** lub widoku **alfabetycznego** . Można przełączać się między tymi dwoma widokami za pomocą przycisków w oknie **Właściwości** . W tym samouczku łatwiej jest znaleźć właściwości w widoku **alfabetycznym** .

1. Wróć do **Projektant formularzy systemu Windows**. Wybierz prawy dolny uchwyt przeciągania, czyli mały biały kwadrat w prawym dolnym rogu formularza i pojawia się w następujący sposób.

    ![Przeciągnij uchwyt](../ide/media/express_bottomrt_drag.png)<br>
   *Przeciągnij uchwyt*

    Przeciągnij uchwyt, aby zmienić rozmiar formularza, tak aby forma była szersza i nieco większa.

1. Sprawdź okno **Właściwości** i Zauważ, że właściwość **size** została zmieniona. Właściwość **size** zmienia się za każdym razem, gdy zmieniany jest rozmiar formularza. Spróbuj przeciągnąć uchwyt formularza, aby zmienić jego rozmiar na rozmiar formularza około **550, 350** (nie musi być dokładne), który powinien być dobrze przydatny dla tego projektu. Alternatywnie można wprowadzić wartości bezpośrednio we właściwości **size** , a następnie wybrać klawisz **Enter** .

1. Uruchom aplikację ponownie. Pamiętaj, że możesz użyć dowolnej z poniższych metod, aby uruchomić aplikację.

   - Wybierz klawisz **F5** .

   - Na pasku menu wybierz **Debuguj**  >  **Rozpocznij debugowanie**.

   - Na pasku narzędzi wybierz przycisk **Rozpocznij debugowanie** , który pojawia się w następujący sposób.

      ![Przycisk paska narzędzi Rozpocznij debugowanie](../ide/media/express_icondebug.png)<br>
     ***Rozpocznij debugowanie** _ _toolbar przycisk *

     Tak jak wcześniej, środowisko IDE kompiluje i uruchamia aplikację, a zostanie wyświetlone okno.

1. Przed przejściem do następnego kroku Zatrzymaj aplikację, ponieważ środowisko IDE nie pozwoli na zmianę aplikacji podczas jej działania. Pamiętaj, że możesz użyć dowolnej z poniższych metod, aby zatrzymać aplikację.

   - Na pasku narzędzi wybierz przycisk **Zatrzymaj debugowanie** .

   - Na pasku menu wybierz **Debuguj**  >  **Zatrzymaj debugowanie**.

   - Użyj klawiatury i naciśnij klawisz **SHIFT** + **F5**.

   - Wybierz przycisk **X** w górnym rogu okna **przeglądarki obrazów** .

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz **[krok 4. układ formularza przy użyciu formantu TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)**.

* Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 2. Uruchamianie aplikacji Przeglądarka obrazów](../ide/step-2-run-your-program.md).

## <a name="see-also"></a>Zobacz też

* [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](tutorial-2-create-a-timed-math-quiz.md)
* [Samouczek 3: Tworzenie gry w dopasowywanie](tutorial-3-create-a-matching-game.md)
