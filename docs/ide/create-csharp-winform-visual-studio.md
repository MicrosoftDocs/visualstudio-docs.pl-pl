---
title: 'Tworzenie aplikacji Windows Forms w języku C #'
description: Dowiedz się, jak utworzyć Windows Forms aplikacji w języku Visual Studio użyciu języka C#, krok po kroku.
ms.date: 09/26/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 0efdb7d35549a32e1151a134ce3a665337bb27ce
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308314"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>Tworzenie aplikacji Windows Forms aplikacji w języku Visual Studio c\#

W tym krótkim wprowadzeniu do Visual Studio zintegrowanego środowiska projektowego (IDE) utworzysz prostą aplikację w języku C# z interfejsem użytkownika (UI) opartym na systemie Windows.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/downloads) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

> [!NOTE]
> Niektóre zrzuty ekranu w tym samouczku używają ciemnego motywu. Jeśli nie używasz motywu ciemnego, ale chcesz, zobacz stronę Personalizowanie środowiska [IDE](../ide/quickstart-personalize-the-ide.md) i edytora Visual Studio, aby dowiedzieć się, jak to zrobić.

::: moniker-end

::: moniker range="vs-2022"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony pobierania Visual Studio [2022 (wersja](https://visualstudio.microsoft.com/vs/preview/vs2022) zapoznawcza), aby zainstalować ją bezpłatnie.

> [!NOTE]
> Niektóre zrzuty ekranu w tym samouczku używają ciemnego motywu. Jeśli nie używasz motywu ciemnego, ale chcesz, zobacz stronę Personalizowanie środowiska [IDE](../ide/quickstart-personalize-the-ide.md) i edytora Visual Studio, aby dowiedzieć się, jak to zrobić.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji w języku C#. Typ projektu zawiera wszystkie potrzebne pliki szablonów, zanim jeszcze cokolwiek dodano.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

1. Na górnym pasku menu wybierz pozycję **File** New Project > **(Plik nowy** > **projekt).**

1. W **oknie dialogowym Nowy** projekt w okienku po lewej stronie rozwiń pozycję **Visual C#,** a następnie wybierz pozycję **Windows Desktop.** W środkowym okienku wybierz **pozycję Windows Forms App (.NET Framework).** Następnie nadaj plikowi nazwę `HelloWorld` .

     Jeśli nie widzisz szablonu projektu **Windows Forms App (.NET Framework),** anuluj opcję z okna  dialogowego Nowy projekt i na górnym pasku menu wybierz pozycję Narzędzia Pobierz narzędzia i  >  funkcje. Ta Instalator programu Visual Studio uruchamia się. Wybierz obciążenie **Tworzenie aplikacji klasycznych dla programu .NET,** a następnie wybierz pozycję **Modyfikuj.**

     ![Obciążenie .NET Core w Instalator programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

1. W oknie uruchamiania wybierz **pozycję Utwórz nowy projekt.**

   ![Wyświetlanie okna "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W **oknie Create a new project (Tworzenie** nowego projektu) wybierz **szablon Windows Forms App (.NET Framework)** dla języka C#.

   (Jeśli wolisz, możesz uściślić wyszukiwanie, aby szybko uzyskać dostęp do szablonu. Na przykład wprowadź lub wpisz *Windows Forms App* w polu wyszukiwania. Następnie wybierz **pozycję C#** z listy Język, a następnie wybierz pozycję **Windows** z listy Platforma).  

   ![Wybierz szablon języka C# dla aplikacji Windows Forms (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

   > [!NOTE]
   > Jeśli szablon aplikacji Windows Forms **(.NET Framework)** nie jest wyświetlony, możesz go zainstalować w oknie **Tworzenie nowego** projektu. W **komunikacie Nie** można znaleźć tego, czego szukasz? wybierz link Zainstaluj więcej narzędzi **i** funkcji.
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" w komunikacie "Nie można znaleźć tego, czego szukasz" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w Instalator programu Visual Studio wybierz obciążenie Wybierz tworzenie aplikacji **klasycznych dla programu .NET.**
   >
   > ![Obciążenie .NET Core w Instalator programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy. Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze["Tworzenie projektu".](#create-a-project)

1. W **oknie Configure your new project (Konfigurowanie** nowego projektu) wpisz lub wprowadź *HelloWorld* w **polu Project name (Nazwa** projektu). Następnie wybierz pozycję **Utwórz**.

   ![W oknie "Konfigurowanie nowego projektu" nadaj projektowi nazwę "HelloWorld"](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Visual Studio otworzy nowy projekt.

::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

Po wybraniu szablonu projektu języka C# i nazwie pliku Visual Studio zostanie otwarty formularz. Formularz jest interfejsem użytkownika systemu Windows. Utworzymy aplikację "Hello world", dodając kontrolki do formularza, a następnie będziemy uruchamiać aplikację.

### <a name="add-a-button-to-the-form"></a>Dodawanie przycisku do formularza

1. Wybierz **pozycję Przybornik,** aby otworzyć okno wysuwu przybornika.

     ![Wybierz przybornik, aby otworzyć okno przybornika](../ide/media/csharp-toolbox-toolwindow.png)

     (Jeśli nie widzisz opcji **wysuwania** przybornika, możesz otworzyć ją na pasku menu. Aby to zrobić, **wyświetl**  >  **przybornik**. Możesz też nacisnąć klawisze **Ctrl** + **Alt** + **X).**

1. Wybierz **ikonę Przypnij,** aby zadokować **okno przybornika.**

     ![Wybierz ikonę Przypnij, aby przypiąć okno przybornika do środowiska IDE](../ide/media/vb-pin-the-toolbox-window.png)

1. Wybierz **kontrolkę Przycisk,** a następnie przeciągnij ją do formularza.

     ![Dodawanie przycisku do formularza](../ide/media/csharp-add-button-form1.png)

1. W **oknie Właściwości** znajdź pozycję **Tekst,** zmień nazwę z **Button1** na `Click this` , a następnie naciśnij klawisz **Enter**.

     ![Dodawanie tekstu do przycisku w formularzu](../ide/media/vb-button-control-text.png)

     (Jeśli nie widzisz okna **Właściwości,** możesz otworzyć je na pasku menu. W tym celu wybierz pozycję **Wyświetl**  >  **okno właściwości.** Możesz też nacisnąć **klawisz F4).**

1. W sekcji **Projekt** okna **Właściwości** zmień nazwę z **Button1** na `btnClickThis` , a następnie naciśnij klawisz **Enter**.

     ![Dodawanie funkcji do przycisku w formularzu](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Jeśli lista jest uporządkowana alfabetycznie w oknie Właściwości, w sekcji **(DataBindings)** pojawi się przycisk **Button1.** 

### <a name="add-a-label-to-the-form"></a>Dodawanie etykiety do formularza

Teraz, gdy dodaliśmy kontrolkę przycisku w celu utworzenia akcji, dodajmy kontrolkę etykiety, do która będzie wysyłać tekst.

1. Wybierz **kontrolkę Etykieta** w **oknie** przybornika, a następnie przeciągnij ją do formularza i upuść poniżej **przycisku Kliknij** ten.

1. W sekcji **Projektowanie** lub **(DataBindings)** okna  Właściwości zmień nazwę **etykiety Label1** na `lblHelloWorld` , a następnie naciśnij klawisz **Enter**.

### <a name="add-code-to-the-form"></a>Dodawanie kodu do formularza

1. W **oknie &#91;Design&#93;Form1.cs** kliknij dwukrotnie  przycisk Kliknij ten, aby otworzyć **okno Form1.cs.**

      (Alternatywnie możesz rozwinąć pozycję **Form1.cs** w Eksplorator rozwiązań , **a** następnie wybrać **form1).**

1. W **oknie Form1.cs** po prywatnym wierszu **void** wpisz lub wprowadź , jak `lblHelloWorld.Text = "Hello World!";` pokazano na poniższym zrzucie ekranu:

     ![Dodawanie kodu do formularza](../get-started/csharp/media/csharp-winforms-add-code.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Wybierz przycisk **Uruchom,** aby uruchomić aplikację.

     ![Wybierz pozycję Rozpocznij, aby debugować i uruchamiać aplikację](../ide/media/vb-click-start-hello-world.png)

   Kilka rzeczy się stanie. W Visual Studio IDE zostanie otwarte okno **Narzędzia** diagnostyczne, **a** także zostanie otwarte okno Dane wyjściowe. Jednak poza ideą zostanie wyświetlone **okno dialogowe Form1.** Będzie on zawierać przycisk **Kliknij ten** i tekst o **etykiecie Label1**.

1. Wybierz przycisk **Kliknij ten** w oknie **dialogowym Form1.** Zwróć uwagę, że tekst **Label1** zmieni się **na Hello world!**.

    ![Okno dialogowe Form1, które zawiera tekst Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

1. Zamknij okno **dialogowe Form1,** aby zatrzymać uruchamianie aplikacji.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej, przejdź do następującego samouczka:

> [!div class="nextstepaction"]
> [Samouczek: tworzenie przeglądarki obrazów](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Zobacz też

* [Więcej samouczków języka C#](../get-started/csharp/index.yml)
* [Visual Basic samouczków](../get-started/visual-basic/index.yml)
* [Samouczki języka C++](/cpp/get-started/tutorial-console-cpp)