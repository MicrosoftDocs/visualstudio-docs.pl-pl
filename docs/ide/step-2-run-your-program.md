---
title: Krok 2. Uruchamianie aplikacji Przeglądarka obrazów
ms.date: 09/06/2019
ms.assetid: 9a8fe90e-c97b-4e98-b6c8-0c6b3962c49d
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 772b80452c20d84b1145a5b8762365f2fe3a8e69
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118840"
---
# <a name="step-2-run-your-picture-viewer-app"></a>Krok 2. Uruchamianie aplikacji Przeglądarka obrazów

Podczas tworzenia projektu aplikacji Windows Forms, w rzeczywistości kompilujesz program, który jest uruchamiany. W tym samouczku aplikacja przeglądarka obrazów nie działa znacznie&mdash;, mimo że zostanie wykorzystana. Na razie wyświetla puste okno, które wyświetla **formularz Form1** na pasku tytułu.

Oto jak uruchomić aplikację. 

1. Wybierz jedną z następujących metod:

    - Wybierz klawisz **F5** .

    - Na pasku menu wybierz **Debuguj** > **Rozpocznij debugowanie**.

    - Na pasku narzędzi wybierz przycisk **Rozpocznij debugowanie** , który jest wyświetlany w następujący sposób:

      ![Przycisk paska narzędzi Rozpocznij debugowanie](../ide/media/express_icondebug.png)<br>
      ***Rozpocznij debugowanie*** *przycisk paska narzędzi*

1. Program Visual Studio uruchamia aplikację i zostanie wyświetlone okno o nazwie **Form1** . Poniższy zrzut ekranu przedstawia utworzoną aplikację. Aplikacja jest uruchomiona i wkrótce zostanie dodana do niej.

     ![Windows Forms uruchomiona aplikacja](../ide/media/express_firstrun.png)<br>
***Aplikacja Windows Forms*** *uruchomiona*

1. Wróć do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio, a następnie spójrz na nowy pasek narzędzi. Po uruchomieniu aplikacji na pasku narzędzi są wyświetlane dodatkowe przyciski. Te przyciski umożliwiają wykonywanie takich czynności, jak zatrzymywanie i uruchamianie aplikacji oraz śledzenie wszelkich błędów (usterek), które może on mieć. Na potrzeby tego przykładu używamy go do uruchamiania i zatrzymywania aplikacji.

     ![Pasek narzędzi debugowania](../ide/media/express_debugtoolbar.png)<br>
***Debugowanie*** *pasek narzędzi*

1. Aby zatrzymać aplikację, użyj jednej z następujących metod:

    - Na pasku narzędzi wybierz przycisk **Zatrzymaj debugowanie** .

    - Na pasku menu wybierz **Debuguj** > **Zatrzymaj debugowanie**.

    - Użyj klawiatury i naciśnij klawisz **SHIFT**+**F5**.

    - Wybierz przycisk **X** w górnym rogu okna **Form1** .

    > [!NOTE]
    > Po uruchomieniu aplikacji z wnętrza IDE, nazywa się to debugowaniem, ponieważ zazwyczaj należy to zrobić, aby zlokalizować i naprawić usterki (błędy) w aplikacji. Mimo że ta aplikacja jest mała i nie wykonuje jeszcze żadnych działań, nadal jest to rzeczywisty program. Wykonaj tę samą procedurę, aby uruchamiać i debugować inne programy. Aby dowiedzieć się więcej o debugowaniu, zobacz [pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz  **[krok 3: Ustaw właściwości](../ide/step-3-set-your-form-properties.md)** formularza.

* Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 1: Utwórz projekt](../ide/step-1-create-a-windows-forms-application-project.md)aplikacji Windows Forms.

## <a name="see-also"></a>Zobacz także

* [Samouczek 2: Tworzenie quizu matematycznego z limitem czasu](tutorial-2-create-a-timed-math-quiz.md)
* [Samouczek 3: Tworzenie gry zgodnej](tutorial-3-create-a-matching-game.md)
