---
title: 'Tworzenie aplikacji Windows Forms przy użyciu języka C #'
description: Dowiedz się, jak utworzyć aplikację Windows Forms w programie Visual Studio przy użyciu języka C#, krok po kroku.
ms.date: 09/26/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 79fb60f05d12b1105febc12a218b1f36ee498deb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88248728"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>Tworzenie aplikacji Windows Forms w programie Visual Studio przy użyciu języka C\#

W tym krótkim wprowadzeniu do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio utworzysz prostą aplikację w języku C#, która ma interfejs użytkownika oparty na systemie Windows.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

> [!NOTE]
> Niektóre zrzuty ekranu w tym samouczku używają ciemnego motywu. Jeśli nie używasz ciemnego motywu, ale chcesz, zobacz stronę [personalizowanie środowiska IDE i edytora programu Visual Studio](../ide/quickstart-personalize-the-ide.md) , aby dowiedzieć się, jak.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji w języku C#. Typ projektu jest dostarczany ze wszystkimi plikami szablonów, które będą potrzebne, zanim będzie można nawet dodać dowolne.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

1. Na górnym pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

1. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń pozycję **Visual C#**, a następnie wybierz pozycję **Windows Desktop**. W środkowym okienku wybierz pozycję **aplikacja Windows Forms (.NET Framework)**. Następnie Nazwij plik `HelloWorld` .

     Jeśli szablon projektu **aplikacji Windows Forms (.NET Framework)** nie jest widoczny, Anuluj wychodzący z okna dialogowego **Nowy projekt** , a następnie z górnego paska menu wybierz kolejno pozycje **Narzędzia**  >  **Pobierz narzędzia i funkcje**. Zostanie uruchomiona Instalator programu Visual Studio. Wybierz obciążenie **Programowanie aplikacji klasycznych platformy .NET** , a następnie wybierz **Modyfikuj**.

     ![Obciążenie .NET Core w Instalator programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Otwórz program Visual Studio 2019.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetl okno "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Tworzenie nowego projektu** wybierz szablon **aplikacja Windows Forms (.NET Framework)** dla języka C#.

   (Jeśli wolisz, możesz udoskonalić wyszukiwanie, aby szybko przejść do żądanego szablonu. Na przykład wpisz lub wpisz *Windows Forms App* w polu wyszukiwania. Następnie wybierz pozycję **C#** z listy język, a następnie wybierz pozycję **Windows** z listy platform.  

   ![Wybierz szablon C# dla aplikacji Windows Forms (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

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

   ![w oknie "Konfigurowanie nowego projektu" Nazwij swój projekt "HelloWorld"](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Program Visual Studio otwiera nowy projekt.

::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

Po wybraniu szablonu projektu C# i Nazwij swój plik, Visual Studio otwiera formularz. Formularz jest interfejsem użytkownika systemu Windows. Utworzymy aplikację "Hello world", dodając formanty do formularza, a następnie uruchomimy aplikację.

### <a name="add-a-button-to-the-form"></a>Dodaj przycisk do formularza

1. Wybierz **Przybornik** , aby otworzyć okno wyskakujące Przybornik.

     ![Wybierz Przybornik, aby otworzyć okno przybornika](../ide/media/csharp-toolbox-toolwindow.png)

     (Jeśli nie widzisz opcji "przylot" **przybornika** , możesz otworzyć ją z paska menu. Aby to zrobić, **Wyświetl**  >  **Przybornik**. Lub naciśnij **klawisze CTRL** + **Alt** + **X**.)

1. Wybierz ikonę **pinezki** , aby zadokować okno **Przybornik** .

     ![Wybierz ikonę pinezki, aby przypiąć okno przybornika do IDE](../ide/media/vb-pin-the-toolbox-window.png)

1. Wybierz kontrolkę **przycisk** , a następnie przeciągnij ją na formularz.

     ![Dodaj przycisk do formularza](../ide/media/csharp-add-button-form1.png)

1. W oknie **Właściwości** Znajdź **tekst**, Zmień nazwę z **Button1** na `Click this` , a następnie naciśnij klawisz **Enter**.

     ![Dodaj tekst do przycisku w formularzu](../ide/media/vb-button-control-text.png)

     (Jeśli nie widzisz okna **Właściwości** , możesz otworzyć je na pasku menu. Aby to zrobić, wybierz pozycję **Wyświetl**  >  **okno właściwości**. Lub naciśnij klawisz **F4**.)

1. W sekcji **projekt** okna **Właściwości** Zmień nazwę z **Button1** na `btnClickThis` , a następnie naciśnij klawisz **Enter**.

     ![Dodaj funkcję do przycisku w formularzu](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Jeśli w oknie **Właściwości** została umieszczona Alfabetyczna lista, **Button1** pojawi się w sekcji **(DataBindings)** .

### <a name="add-a-label-to-the-form"></a>Dodawanie etykiety do formularza

Po dodaniu kontrolki przycisku do tworzenia akcji Dodajmy kontrolkę etykieta, aby wysłać tekst do.

1. Wybierz kontrolkę **etykieta** z okna **przybornika** , a następnie przeciągnij ją na formularz i upuść ją pod **przyciskiem kliknij ten** przycisk.

1. W sekcji **projektu** lub w sekcji **(DataBindings)** okna **Właściwości** Zmień nazwę **Label1** na `lblHelloWorld` , a następnie naciśnij klawisz **Enter**.

### <a name="add-code-to-the-form"></a>Dodawanie kodu do formularza

1. W oknie **&#93;projekt Form1.cs &#91;** kliknij dwukrotnie **ten** przycisk, aby otworzyć okno **Form1.cs** .

      (Alternatywnie można rozwinąć **Form1.cs** w **Eksplorator rozwiązań**, a następnie wybrać **formularz Form1**).

1. W oknie **Form1.cs** , po prywatnym wierszu **void** wpisz lub ENTER, `lblHelloWorld.Text = "Hello World!";` jak pokazano na poniższym zrzucie ekranu:

     ![Dodawanie kodu do formularza](../get-started/csharp/media/csharp-winforms-add-code.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Wybierz przycisk **Start** , aby uruchomić aplikację.

     ![Wybierz pozycję Rozpocznij, aby debugować i uruchomić aplikację](../ide/media/vb-click-start-hello-world.png)

   Zostanie wykonanych kilka rzeczy. W środowisku IDE programu Visual Studio zostanie otwarte okno **Narzędzia diagnostyczne** , a okno **dane wyjściowe** zostanie otwarte. Ale poza IDE pojawia się okno dialogowe **Form1** . Zostanie on uwzględniony w **kliknięciu tego** przycisku i tekstu **Label1**.

1. Wybierz przycisk **kliknij ten** przycisk w oknie dialogowym **Form1** . Zauważ, że tekst **Label1** zmieni się na **Hello World!**.

    ![Okno dialogowe Form1 zawierające tekst Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

1. Zamknij okno dialogowe **Form1** , aby zatrzymać działanie aplikacji.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej, przejdź do następującego samouczka:

> [!div class="nextstepaction"]
> [Samouczek: Tworzenie przeglądarki obrazów](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Zobacz też

* [Więcej samouczków dotyczących języka C#](/visualstudio/get-started/csharp/)
* [Samouczki Visual Basic](/visualstudio/get-started/visual-basic/)
* [Samouczki języka C++](/cpp/get-started/tutorial-console-cpp)
