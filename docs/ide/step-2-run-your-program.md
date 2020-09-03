---
title: Krok 2. Uruchamianie aplikacji Przeglądarka obrazów
ms.date: 09/06/2019
ms.assetid: 9a8fe90e-c97b-4e98-b6c8-0c6b3962c49d
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8204f2a32a1bb29203c75af55aa383141f17853f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77579404"
---
# <a name="step-2-run-your-picture-viewer-app"></a>Krok 2. Uruchamianie aplikacji Przeglądarka obrazów

Podczas tworzenia projektu aplikacji Windows Forms, w rzeczywistości kompilujesz program, który jest uruchamiany. W tym samouczku aplikacja przeglądarka obrazów nie działa znacznie, &mdash; mimo że zostanie wykorzystana. Na razie wyświetla puste okno, które wyświetla **formularz Form1** na pasku tytułu.

Oto jak uruchomić aplikację. 

1. Wybierz jedną z poniższych metod:

    - Wybierz klawisz **F5** .

    - Na pasku menu wybierz **Debuguj**  >  **Rozpocznij debugowanie**.

    - Na pasku narzędzi wybierz przycisk **Rozpocznij debugowanie** , który jest wyświetlany w następujący sposób:

      ![Przycisk paska narzędzi Rozpocznij debugowanie](../ide/media/express_icondebug.png)<br>
      *Przycisk paska narzędzi* ***Rozpocznij debugowanie***

1. Program Visual Studio uruchamia aplikację i zostanie wyświetlone okno o nazwie **Form1** . Poniższy zrzut ekranu przedstawia utworzoną aplikację. Aplikacja jest uruchomiona i wkrótce zostanie dodana do niej.

     ![Windows Forms uruchomiona aplikacja](../ide/media/express_firstrun.png)<br>
***Aplikacja Windows Forms*** *uruchomiona*

1. Wróć do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio, a następnie spójrz na nowy pasek narzędzi. Po uruchomieniu aplikacji na pasku narzędzi są wyświetlane dodatkowe przyciski. Te przyciski umożliwiają wykonywanie takich czynności, jak zatrzymywanie i uruchamianie aplikacji oraz śledzenie wszelkich błędów (usterek), które może on mieć. Na potrzeby tego przykładu używamy go do uruchamiania i zatrzymywania aplikacji.

     ![Pasek narzędzi debugowania](../ide/media/express_debugtoolbar.png)<br>
***Debugging*** *Pasek narzędzi* debugowania

1. Aby zatrzymać aplikację, użyj jednej z następujących metod:

    - Na pasku narzędzi wybierz przycisk **Zatrzymaj debugowanie** .

    - Na pasku menu wybierz **Debuguj**  >  **Zatrzymaj debugowanie**.

    - Użyj klawiatury i naciśnij klawisz **SHIFT** + **F5**.

    - Wybierz przycisk **X** w górnym rogu okna **Form1** .

    > [!NOTE]
    > Po uruchomieniu aplikacji z wnętrza IDE, nazywa się to debugowaniem, ponieważ zazwyczaj należy to zrobić, aby zlokalizować i naprawić usterki (błędy) w aplikacji. Mimo że ta aplikacja jest mała i jeszcze nie działa, nadal jest rzeczywistym programem. Wykonaj tę samą procedurę, aby uruchamiać i debugować inne programy. Aby dowiedzieć się więcej o debugowaniu, zobacz [pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz **[krok 3: Ustawianie właściwości formularza](../ide/step-3-set-your-form-properties.md)**.

* Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 1. Tworzenie projektu aplikacji Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md).

## <a name="see-also"></a>Zobacz też

* [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](tutorial-2-create-a-timed-math-quiz.md)
* [Samouczek 3: Tworzenie gry w dopasowywanie](tutorial-3-create-a-matching-game.md)
