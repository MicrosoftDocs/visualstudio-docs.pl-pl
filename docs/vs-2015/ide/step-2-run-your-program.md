---
title: Krok 2. Uruchamianie programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 9a8fe90e-c97b-4e98-b6c8-0c6b3962c49d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2ddec4c7327aa9799ae8a12a04b3940d690205cb
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851569"
---
# <a name="step-2-run-your-program"></a>Krok 2. Uruchomienie programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po utworzeniu nowego rozwiązania jest tworzony program, który jest uruchamiany. Jeszcze nie działa — po prostu wyświetla puste okno, które wyświetla **formularz Form1** na pasku tytułu. Jest to jednak uruchamiane, ponieważ wkrótce się znajdziesz.

 ![link do wideo](../data-tools/media/playvideo.gif "PlayVideo") Aby uzyskać wersję wideo tego tematu, zobacz [Samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic — wideo 1](https://msdn.microsoft.com/vbasic/gg315352.aspx) lub [Samouczek 1: Tworzenie przeglądarki obrazów w C# wideo 1](https://msdn.microsoft.com/vcsharp/gg278409.aspx). Te filmy wideo korzystają ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

### <a name="to-run-your-program"></a>Aby uruchomić program

1. Użyj jednej z poniższych metod, aby uruchomić program.

    - Wybierz klawisz **F5** .

    - Na pasku menu wybierz **Debuguj**, **Rozpocznij debugowanie**.

    - Na pasku narzędzi wybierz przycisk **Rozpocznij debugowanie** , który pojawia się w następujący sposób.

         ![Przycisk paska narzędzi Rozpocznij debugowanie](../ide/media/express-icondebug.png "Express_IconDebug") Przycisk paska narzędzi Rozpocznij debugowanie

2. Visual Studio uruchamia Twój program i pojawia się okno o nazwie **Form1** . Na poniższym diagramie przedstawiono program, który właśnie został skompilowany. Program jest uruchomiony i wkrótce zostanie dodany do niego.

     ![Uruchomiony program aplikacji formularza systemu Windows](../ide/media/express-firstrun.png "Express_FirstRun") Uruchomiony program aplikacji formularza systemu Windows

3. Wróć do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio i zapoznaj się z nowym paskiem narzędzi. Po uruchomieniu programu na pasku narzędzi są wyświetlane dodatkowe przyciski. Te przyciski umożliwiają wykonywanie takich czynności, jak zatrzymywanie i uruchamianie programu oraz śledzenie wszelkich błędów (usterek), które może on mieć. Na potrzeby tego przykładu używamy go do uruchamiania i zatrzymywania programu.

     ![Pasek narzędzi debugowania](../ide/media/express-debugtoolbar.png "Express_DebugToolbar") Pasek narzędzi debugowania

4. Użyj jednej z poniższych metod, aby zatrzymać program.

    - Na pasku narzędzi wybierz przycisk **Zatrzymaj debugowanie** .

    - Na pasku menu wybierz **Debuguj**, **Zatrzymaj debugowanie**.

    - Wybierz przycisk X w górnym rogu okna **Form1** .

    > [!NOTE]
    > Gdy uruchamiasz program z wewnątrz IDE, nazywa się to *debugowanie* , ponieważ zazwyczaj jest to konieczne do lokalizowania i naprawiania usterek (błędów) w programie. Mimo że ten program jest mały i nie wykonuje jeszcze żadnych czynności, nadal jest to rzeczywisty program. Wykonaj tę samą procedurę, aby uruchamiać i debugować inne programy. Aby dowiedzieć się więcej na temat debugowania, zobacz [podstawy debugera](../debugger/debugger-basics.md).

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 3: Ustawianie właściwości formularza](../ide/step-3-set-your-form-properties.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 1. Tworzenie projektu aplikacji Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md).
