---
title: Tworzenie aplikacji Windows Forms za pomocąC#
description: Dowiedz się C#, jak utworzyć aplikację Windows Forms w programie Visual Studio, krok po kroku.
ms.date: 09/26/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 4017ee2da040ccef36c58b17d896abab199c3517
ms.sourcegitcommit: 13decf878b33fc0c5d665a88067170c2861b261b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71682145"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>Tworzenie aplikacji Windows Forms w programie Visual Studio przy użyciuC#

W tym krótkim wprowadzeniu do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio utworzysz prostą C# aplikację, która ma interfejs użytkownika oparty na systemie Windows.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) strony, aby zainstalować go za darmo.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads) strony, aby zainstalować go za darmo.

> [!NOTE]
> Niektóre zrzuty ekranu w tym samouczku używają ciemnego motywu. Jeśli nie używasz motyw ciemny, ale aby zobaczyć [Personalizowanie programu Visual Studio IDE i edytorem](../ide/quickstart-personalize-the-ide.md) strony, aby dowiedzieć się, jak.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt C# aplikacji. Typ projektu zawiera wszystkie pliki szablonu, które będą potrzebne, zanim dodaniu jeszcze nic.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

1. Na górnym pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

1. W oknie dialogowym **Nowy projekt** w okienku po lewej stronie rozwiń pozycję **Wizualizacja C#** , a następnie wybierz pozycję **Windows Desktop**. W środkowym okienku wybierz **aplikacji programu Windows Forms (.NET Framework)** . Następnie Nazwij plik `HelloWorld`.

     Jeśli nie widzisz **aplikacji programu Windows Forms (.NET Framework)** projektu szablonu, Anuluj poza **nowy projekt** okna dialogowego pole, a następnie na pasku menu u góry wybierz **narzędzia**  >  **Pobierz narzędzia i funkcje**. Uruchamia Instalatora programu Visual Studio. Wybierz **programowanie aplikacji klasycznych dla platformy .NET** obciążenia, wybierz **Modyfikuj**.

     ![Obciążenie platformy .NET core w Instalatorze programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Open Visual Studio 2019.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetl okno "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Tworzenie nowego projektu** wybierz szablon **aplikacja Windows Forms (.NET Framework)** dla programu C#.

   (Jeśli wolisz, możesz udoskonalić wyszukiwanie, aby szybko przejść do żądanego szablonu. Na przykład wpisz lub wpisz *Windows Forms App* w polu wyszukiwania. Następnie wybierz **C#** pozycję z listy język, a następnie wybierz pozycję **Windows** z listy platform.  

   ![Wybierz C# szablon aplikacji Windows Forms (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

   > [!NOTE]
   > Jeśli szablon **aplikacji Windows Forms (.NET Framework)** nie jest wyświetlany, można go zainstalować za pomocą okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** .
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "nie można odnaleźć szukanego elementu" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w Instalator programu Visual Studio wybierz obciążenie **Programowanie aplikacji klasycznych platformy .NET** .
   >
   > ![Obciążenie platformy .NET core w Instalatorze programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj** , aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze "[Create a Project](#create-a-project)".

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *HelloWorld* w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

   ![w oknie "Konfigurowanie nowego projektu" Nazwij swój projekt "HelloWorld"](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Program Visual Studio otwiera nowy projekt.

::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

Po wybraniu szablonu C# projektu i Nazwij swój plik, program Visual Studio otworzy formularz. Formularz jest interfejs użytkownika Windows. Utworzymy aplikację "Hello world", dodając formanty do formularza, a następnie uruchomimy aplikację.

### <a name="add-a-button-to-the-form"></a>Dodawanie przycisku do formularza

1. Wybierz **Przybornik** , aby otworzyć okno wyskakujące Przybornik.

     ![Wybierz Przybornik, aby otworzyć okno przybornika](../ide/media/csharp-toolbox-toolwindow.png)

     (Jeśli nie widzisz **przybornika** staną się opcji, możesz go otworzyć z paska menu. Aby to zrobić, **wyświetl** > **Przybornik**. Lub naciśnij **Ctrl**+**Alt**+**X**.)

1. Wybierz ikonę **pinezki** , aby zadokować okno **Przybornik** .

     ![Wybierz ikonę pinezki, aby przypiąć okno przybornika do IDE](../ide/media/vb-pin-the-toolbox-window.png)

1. Wybierz kontrolkę **przycisk** , a następnie przeciągnij ją na formularz.

     ![Dodawanie przycisku do formularza](../ide/media/csharp-add-button-form1.png)

1. W oknie **Właściwości** Znajdź **tekst**, Zmień nazwę z **Button1** na `Click this`, a następnie naciśnij klawisz **Enter**.

     ![Dodawanie tekstu do przycisku w formularzu](../ide/media/vb-button-control-text.png)

     (Jeśli nie widzisz **właściwości** okna, możesz go otworzyć z paska menu. Aby to zrobić, wybierz pozycję **wyświetl** > **okno właściwości**. Lub naciśnij **F4**.)

1. W **projektowania** części **właściwości** okna, zmiana nazwy na podstawie **Button1** do `btnClickThis`, a następnie naciśnij klawisz **Enter**.

     ![Dodawanie funkcji do przycisku w formularzu](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Jeśli w oknie **Właściwości** została umieszczona Alfabetyczna lista, **Button1** pojawi się w sekcji **(DataBindings)** .

### <a name="add-a-label-to-the-form"></a>Dodaj etykietę do formularza

Teraz, po dodaniu kontrolki przycisku, aby utworzyć akcję, możemy dodać kontrolkę typu etykieta do tekstu do wysłania.

1. Wybierz **etykiety** kontrolować z **przybornika** okna, a następnie przeciągnij go do formularza i upuść go pod **kliknij ten element** przycisku.

1. W sekcji **projektu** lub w sekcji **(DataBindings)** okna **właściwości** Zmień nazwę **Label1** na `lblHelloWorld`, a następnie naciśnij klawisz **Enter**.

### <a name="add-code-to-the-form"></a>Dodaj kod do formularza

1. W oknie **projekt &#91;&#93; Form1.cs** kliknij dwukrotnie **ten** przycisk, aby otworzyć okno **Form1.cs** .

      (Alternatywnie można rozwinąć **Form1.cs** w **Eksplorator rozwiązań**, a następnie wybrać **formularz Form1**).

1. W oknie **Form1.cs** , po prywatnym wierszu **void** wpisz lub wprowadź `lblHelloWorld.Text = "Hello World!";`, jak pokazano na poniższym zrzucie ekranu:

     ![Dodaj kod do formularza](../get-started/csharp/media/csharp-winforms-add-code.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Wybierz przycisk **Start** , aby uruchomić aplikację.

     ![Wybierz pozycję Rozpocznij, aby debugować i uruchomić aplikację](../ide/media/vb-click-start-hello-world.png)

   Wykonanych kilka działań. W programie Visual Studio IDE **narzędzia diagnostyczne** okno i **dane wyjściowe** okno zbyt. Ale poza IDE **Form1** pojawi się okno dialogowe. Będzie on zawierał swoje **kliknij** przycisk i tekst, który jest wyświetlany komunikat **Label1**.

1. Wybierz przycisk **kliknij ten** przycisk w oknie dialogowym **Form1** . Należy zauważyć, że **Label1** tekst zmienia się na **Hello World!** .

    ![Formularz Form1 okno dialogowe, które zawiera tekst Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

1. Zamknij okno dialogowe **Form1** , aby zatrzymać działanie aplikacji.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej, przejdź do następującego samouczka:

> [!div class="nextstepaction"]
> [Samouczek: Tworzenie przeglądarki obrazów](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Zobacz także

* [Więcej C# samouczków](/visualstudio/get-started/csharp/)
* [Samouczki Visual Basic](/visualstudio/get-started/visual-basic/)
* [C++Podręcznik](/cpp/get-started/tutorial-console-cpp)
