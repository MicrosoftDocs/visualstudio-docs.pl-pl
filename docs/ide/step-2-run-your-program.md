---
title: Krok 2. Uruchamianie programu
ms.date: 09/06/2019
ms.assetid: 9a8fe90e-c97b-4e98-b6c8-0c6b3962c49d
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
ms.openlocfilehash: 12ae2a50b114c34f72f4e25ec52db40fc77943d3
ms.sourcegitcommit: bd4e45f1697a8fbfdbc0a7c6b531c8f7b9fb8a48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2019
ms.locfileid: "70808785"
---
# <a name="step-2-run-your-pictureviewer-app"></a>Krok 2. Uruchamianie aplikacji PictureViewer

Podczas tworzenia projektu aplikacji Windows Forms, w rzeczywistości kompilujesz program, który jest uruchamiany. W tym samouczku aplikacja *PictureViewer* nie wykonuje jeszcze&mdash;tej czynności, mimo że będzie. Na razie po prostu wyświetla puste okno, które wyświetla **formularz Form1** na pasku tytułu.

Poniżej przedstawiono sposób uruchamiania programu. 

1. Wybierz jedną z następujących metod:

    - Wybierz klawisz **F5** .

    - Na pasku menu wybierz **Debuguj** > **Rozpocznij debugowanie**.

    - Na pasku narzędzi wybierz przycisk **Rozpocznij debugowanie** , który jest wyświetlany w następujący sposób:

      ![Przycisk paska narzędzi Rozpocznij debugowanie](../ide/media/express_icondebug.png)<br>
      ***Rozpocznij debugowanie*** *przycisk paska narzędzi*

1. Visual Studio uruchamia Twój program i pojawia się okno o nazwie **Form1** . Poniższy zrzut ekranu przedstawia program, który właśnie został skompilowany. Program jest uruchomiony i wkrótce dodasz do niego.

     ![Uruchomiony program aplikacji formularza systemu Windows](../ide/media/express_firstrun.png)<br>
***Windows Forms*** *program aplikacji, uruchomiony*

1. Wróć do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio, a następnie spójrz na nowy pasek narzędzi. Po uruchomieniu programu na pasku narzędzi są wyświetlane dodatkowe przyciski. Te przyciski umożliwiają wykonywanie takich czynności, jak zatrzymywanie i uruchamianie programu oraz śledzenie wszelkich błędów (usterek), które może on mieć. Na potrzeby tego przykładu używamy go do uruchamiania i zatrzymywania programu.

     ![Pasek narzędzi debugowania](../ide/media/express_debugtoolbar.png)<br>
***Debugowanie*** *pasek narzędzi*

1. Aby zatrzymać program, należy użyć jednej z następujących metod:

    - Na pasku narzędzi wybierz przycisk **Zatrzymaj debugowanie** .

    - Na pasku menu wybierz **Debuguj** > **Zatrzymaj debugowanie**.

    - Użyj klawiatury i naciśnij klawisz **SHIFT**+**F5**.

    - Wybierz przycisk **X** w górnym rogu okna **Form1** .

    > [!NOTE]
    > Gdy uruchamiasz program z wewnątrz IDE, nazywa się to debugowanie, ponieważ zazwyczaj jest to konieczne do lokalizowania i naprawiania usterek (błędów) w programie. Mimo że ten program jest mały i nie wykonuje jeszcze żadnych czynności, nadal jest to rzeczywisty program. Wykonaj tę samą procedurę, aby uruchamiać i debugować inne programy. Aby dowiedzieć się więcej o debugowaniu, zobacz [pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz [krok 3: Ustaw właściwości](../ide/step-3-set-your-form-properties.md)formularza.

* Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 1: Utwórz projekt](../ide/step-1-create-a-windows-forms-application-project.md)aplikacji Windows Forms.

## <a name="see-also"></a>Zobacz także

* [Samouczek 2: Tworzenie quizu matematycznego z limitem czasu](tutorial-2-create-a-timed-math-quiz.md)
* [Samouczek 3: Tworzenie gry zgodnej](tutorial-3-create-a-matching-game.md)
