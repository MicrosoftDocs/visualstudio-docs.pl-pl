---
title: Tworzenie aplikacji Windows Forms z Visual Basic
description: Dowiedz się, jak tworzenie aplikacji Windows Forms w programie Visual Studio za pomocą Visual Basic, który krok po kroku.
ms.date: 09/27/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8be3edaaab970dab7ef41bd8bce75c84bac54a2e
ms.sourcegitcommit: 13decf878b33fc0c5d665a88067170c2861b261b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71681585"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Utwórz Windows Forms aplikacji w programie Visual Studio za pomocą Visual Basic

W tym krótkie wprowadzenie do programu Visual Studio zintegrowane środowisko programistyczne (IDE) utworzysz prostą aplikację języka Visual Basic, która ma interfejs użytkownika oparty na Windows (UI).

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) strony, aby zainstalować go za darmo.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads) strony, aby zainstalować go za darmo.

> [!NOTE]
> Niektóre zrzuty ekranu w tym samouczku używają ciemnego motywu. Jeśli nie używasz motyw ciemny, ale aby zobaczyć [Personalizowanie programu Visual Studio IDE i edytorem](../ide/quickstart-personalize-the-ide.md) strony, aby dowiedzieć się, jak.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji w języku Visual Basic. Typ projektu zawiera wszystkie pliki szablonu, które będą potrzebne, zanim dodaniu jeszcze nic.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

1. Na górnym pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

1. W **nowy projekt** okno dialogowe w okienku po lewej stronie rozwiń **języka Visual Basic**, a następnie wybierz **pulpitu Windows**. W środkowym okienku wybierz **aplikacji programu Windows Forms (.NET Framework)** . Następnie Nazwij plik `HelloWorld`.

     Jeśli nie widzisz **aplikacji programu Windows Forms (.NET Framework)** projektu szablonu, Anuluj poza **nowy projekt** okna dialogowego pole, a następnie na pasku menu u góry wybierz **narzędzia**  >  **Pobierz narzędzia i funkcje**. Uruchamia Instalatora programu Visual Studio. Wybierz **programowanie aplikacji klasycznych dla platformy .NET** obciążenia, wybierz **Modyfikuj**.

     ![Obciążenie platformy .NET core w Instalatorze programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Open Visual Studio 2019.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetl okno "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Tworzenie nowego projektu** wybierz szablon **Windows Forms aplikacji (.NET Framework)** dla Visual Basic.

   (Jeśli wolisz, możesz udoskonalić wyszukiwanie, aby szybko przejść do żądanego szablonu. Na przykład wpisz lub wpisz *Windows Forms App* w polu wyszukiwania. Następnie wybierz **Visual Basic** z listy język, a następnie wybierz pozycję **Windows** z listy platform.)  

   ![Wybierz szablon Visual Basic dla aplikacji Windows Forms (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

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

   ![w oknie "Konfigurowanie nowego projektu" Nazwij swój projekt "HelloWorld"](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

   Program Visual Studio otwiera nowy projekt.

::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

Po wybraniu szablonu projektu języka Visual Basic i nazwę pliku, programu Visual Studio otwiera formularz. Formularz jest interfejs użytkownika Windows. Utworzymy aplikację "Hello world", dodając formanty do formularza, a następnie uruchomimy aplikację.

### <a name="add-a-button-to-the-form"></a>Dodawanie przycisku do formularza

1. Kliknij przycisk **przybornika** można otworzyć okna wysuwanego przybornika.

     ![Kliknij przycisk przybornika, aby otworzyć okno przybornika](../ide/media/vb-toolbox-toolwindow.png)

     (Jeśli nie widzisz **przybornika** staną się opcji, możesz go otworzyć z paska menu. Aby to zrobić, **wyświetl** > **Przybornik**. Lub naciśnij **Ctrl**+**Alt**+**X**.)

1. Kliknij przycisk **numeru Pin** ikonę, aby zadokować **przybornika** okna.

     ![Kliknij ikonę pinezki, aby przypiąć okno przybornika środowiska IDE](../ide/media/vb-pin-the-toolbox-window.png)

1. Kliknij przycisk **przycisk** sterowania, a następnie przeciągnij go do formularza.

     ![Dodawanie przycisku do formularza](../ide/media/vb-add-a-button-to-form1.png)

1. W sekcji **wygląd** (lub w sekcji **czcionki** ) okna **Właściwości** wpisz `Click this`, a następnie naciśnij klawisz **Enter**.

     ![Dodawanie tekstu do przycisku w formularzu](../ide/media/vb-button-control-text.png)

     (Jeśli nie widzisz **właściwości** okna, możesz go otworzyć z paska menu. Aby to zrobić, kliknij przycisk **widoku** > **okno właściwości**. Lub naciśnij **F4**.)

1. W **projektowania** części **właściwości** okna, zmiana nazwy na podstawie **Button1** do `btnClickThis`, a następnie naciśnij klawisz **Enter**.

     ![Dodawanie funkcji do przycisku w formularzu](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Jeśli w oknie **Właściwości** została umieszczona Alfabetyczna lista, **Button1** pojawi się w sekcji **(DataBindings)** .

### <a name="add-a-label-to-the-form"></a>Dodaj etykietę do formularza

Teraz, po dodaniu kontrolki przycisku, aby utworzyć akcję, możemy dodać kontrolkę typu etykieta do tekstu do wysłania.

1. Wybierz **etykiety** kontrolować z **przybornika** okna, a następnie przeciągnij go do formularza i upuść go pod **kliknij ten element** przycisku.

1. W sekcji **projektu** lub w sekcji **(DataBindings)** okna **właściwości** Zmień nazwę **Label1** na `lblHelloWorld`, a następnie naciśnij klawisz **Enter**.

### <a name="add-code-to-the-form"></a>Dodaj kod do formularza

1. W **Form1.vb &#91;projektowania&#93;**  okna, kliknij dwukrotnie **kliknij** przycisk, aby otworzyć **Form1.vb** okna.

      (Ewentualnie możesz rozwinąć **Form1.vb** w **Eksploratora rozwiązań**, a następnie kliknij przycisk **Form1**.)

1. W oknie **Form1. vb** między liniami podrzędnymi **podrzędnymi** i **końcowymi** wpisz lub wprowadź `lblHelloWorld.Text = "Hello World!"` jak pokazano na poniższym zrzucie ekranu:

     ![Dodaj kod do formularza](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Kliknij przycisk **Start** przycisk, aby uruchomić aplikację.

     ![Kliknij przycisk Uruchom, aby debugować i uruchamianie aplikacji](../ide/media/vb-click-start-hello-world.png)

   Wykonanych kilka działań. W programie Visual Studio IDE **narzędzia diagnostyczne** okno i **dane wyjściowe** okno zbyt. Ale poza IDE **Form1** pojawi się okno dialogowe. Będzie on zawierał swoje **kliknij** przycisk i tekst, który jest wyświetlany komunikat **Label1**.

1. Kliknij przycisk **kliknij** znajdujący się w **Form1** okno dialogowe. Należy zauważyć, że **Label1** tekst zmienia się na **Hello World!** .

    ![Formularz Form1 okno dialogowe, które zawiera tekst Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

1. Zamknij okno dialogowe **Form1** , aby zatrzymać działanie aplikacji.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej, przejdź do następującego samouczka:

> [!div class="nextstepaction"]
> [Samouczek: Tworzenie przeglądarki obrazów](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Zobacz także

* [Więcej samouczków Visual Basic](/visualstudio/get-started/visual-basic/)
* [C#Podręcznik](/visualstudio/get-started/csharp/)
* [C++Podręcznik](/cpp/get-started/tutorial-console-cpp)
