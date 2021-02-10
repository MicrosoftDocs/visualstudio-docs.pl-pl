---
title: Tworzenie aplikacji Windows Forms z Visual Basic
description: Dowiedz się, jak utworzyć aplikację Windows Forms w programie Visual Studio z Visual Basic, krok po kroku.
ms.date: 09/27/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jmartens
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7a5ee86c98a7e66ac43cbcfb1abbcab6bf970b08
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970923"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Tworzenie aplikacji Windows Forms w programie Visual Studio z Visual Basic

W tym krótkim wprowadzeniu do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio utworzysz prostą aplikację Visual Basic, która ma interfejs użytkownika oparty na systemie Windows.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

> [!NOTE]
> Niektóre zrzuty ekranu w tym samouczku używają ciemnego motywu. Jeśli nie używasz ciemnego motywu, ale chcesz, zobacz stronę [personalizowanie środowiska IDE i edytora programu Visual Studio](../ide/quickstart-personalize-the-ide.md) , aby dowiedzieć się, jak.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji Visual Basic. Typ projektu jest dostarczany ze wszystkimi plikami szablonów, które będą potrzebne, zanim będzie można nawet dodać dowolne.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

1. Na górnym pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

1. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń węzeł **Visual Basic**, a następnie wybierz pozycję **Windows Desktop**. W środkowym okienku wybierz pozycję **aplikacja Windows Forms (.NET Framework)**. Następnie Nazwij plik `HelloWorld` .

     Jeśli szablon projektu **aplikacji Windows Forms (.NET Framework)** nie jest widoczny, Anuluj wychodzący z okna dialogowego **Nowy projekt** , a następnie z górnego paska menu wybierz kolejno pozycje **Narzędzia**  >  **Pobierz narzędzia i funkcje**. Zostanie uruchomiona Instalator programu Visual Studio. Wybierz obciążenie **Programowanie aplikacji klasycznych platformy .NET** , a następnie wybierz **Modyfikuj**.

     ![Obciążenie .NET Core w Instalator programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Otwórz program Visual Studio 2019.

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
   > ![Obciążenie .NET Core w Instalator programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj** , aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze "[Create a Project](#create-a-project)".

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *HelloWorld* w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

   ![w oknie "Konfigurowanie nowego projektu" Nazwij swój projekt "HelloWorld"](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

   Program Visual Studio otwiera nowy projekt.

::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

Po wybraniu szablonu projektu Visual Basic i Nazwij swój plik program Visual Studio otworzy formularz. Formularz jest interfejsem użytkownika systemu Windows. Utworzymy aplikację "Hello world", dodając formanty do formularza, a następnie uruchomimy aplikację.

### <a name="add-a-button-to-the-form"></a>Dodaj przycisk do formularza

1. Kliknij przycisk **Przybornik** , aby otworzyć okno dialogowe okna podręcznego.

     ![Kliknij Przybornik, aby otworzyć okno przybornika](../ide/media/vb-toolbox-toolwindow.png)

     (Jeśli nie widzisz opcji "przylot" **przybornika** , możesz otworzyć ją z paska menu. Aby to zrobić, **Wyświetl**  >  **Przybornik**. Lub naciśnij **klawisze CTRL** + **Alt** + **X**.)

1. Kliknij ikonę **pinezki** , aby zadokować okno **Przybornik** .

     ![Kliknij ikonę pinezki, aby przypiąć okno przybornika do IDE](../ide/media/vb-pin-the-toolbox-window.png)

1. Kliknij kontrolkę **przycisk** , a następnie przeciągnij ją na formularz.

     ![Dodaj przycisk do formularza](../ide/media/vb-add-a-button-to-form1.png)

1. W sekcji **wygląd** (lub w sekcji **czcionki** ) okna **Właściwości** wpisz `Click this` , a następnie naciśnij klawisz **Enter**.

     ![Dodaj tekst do przycisku w formularzu](../ide/media/vb-button-control-text.png)

     (Jeśli nie widzisz okna **Właściwości** , możesz otworzyć je na pasku menu. Aby to zrobić, kliknij przycisk **Wyświetl**  >  **Właściwości okno**. Lub naciśnij klawisz **F4**.)

1. W sekcji **projekt** okna **Właściwości** Zmień nazwę z **Button1** na `btnClickThis` , a następnie naciśnij klawisz **Enter**.

     ![Dodaj funkcję do przycisku w formularzu](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Jeśli w oknie **Właściwości** została umieszczona Alfabetyczna lista, **Button1** pojawi się w sekcji **(DataBindings)** .

### <a name="add-a-label-to-the-form"></a>Dodawanie etykiety do formularza

Po dodaniu kontrolki przycisku do tworzenia akcji Dodajmy kontrolkę etykieta, aby wysłać tekst do.

1. Wybierz kontrolkę **etykieta** z okna **przybornika** , a następnie przeciągnij ją na formularz i upuść ją pod **przyciskiem kliknij ten** przycisk.

1. W sekcji **projektu** lub w sekcji **(DataBindings)** okna **Właściwości** Zmień nazwę **Label1** na `lblHelloWorld` , a następnie naciśnij klawisz **Enter**.

### <a name="add-code-to-the-form"></a>Dodawanie kodu do formularza

1. W oknie **&#93;projektu Form1. vb &#91;** kliknij dwukrotnie **ten** przycisk, aby otworzyć okno **Form1. vb** .

      (Możesz też rozwinąć **formularz Form1. vb** w **Eksplorator rozwiązań**, a następnie kliknąć przycisk **Form1**).

1. W oknie **Form1. vb** **między podrzędnymi a** **końcowymi** podliniami wpisz lub wprowadź, `lblHelloWorld.Text = "Hello World!"` jak pokazano na poniższym zrzucie ekranu:

     ![Dodawanie kodu do formularza](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Kliknij przycisk **Uruchom** , aby uruchomić aplikację.

     ![Kliknij przycisk Rozpocznij, aby debugować i uruchamiać aplikację](../ide/media/vb-click-start-hello-world.png)

   Zostanie wykonanych kilka rzeczy. W środowisku IDE programu Visual Studio zostanie otwarte okno **Narzędzia diagnostyczne** , a okno **dane wyjściowe** zostanie otwarte. Ale poza IDE pojawia się okno dialogowe **Form1** . Zostanie on uwzględniony w **kliknięciu tego** przycisku i tekstu **Label1**.

1. Kliknij **ten** przycisk w oknie dialogowym **Form1** . Zauważ, że tekst **Label1** zmieni się na **Hello World!**.

    ![Okno dialogowe Form1 zawierające tekst Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

1. Zamknij okno dialogowe **Form1** , aby zatrzymać działanie aplikacji.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej, przejdź do następującego samouczka:

> [!div class="nextstepaction"]
> [Samouczek: Tworzenie przeglądarki obrazów](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Zobacz też

* [Więcej samouczków Visual Basic](../get-started/visual-basic/index.yml)
* [Samouczki języka C#](../get-started/csharp/index.yml)
* [Samouczki języka C++](/cpp/get-started/tutorial-console-cpp)