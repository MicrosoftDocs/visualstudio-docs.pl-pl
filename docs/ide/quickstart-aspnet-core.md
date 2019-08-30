---
title: Tworzenie aplikacji internetowej platformy ASP.NET Core wC#
description: Dowiedz się, jak utworzyć prostą aplikację sieci web Hello World w programie Visual Studio w języku C# i ASP.NET Core, który krok po kroku.
ms.custom: mvc,seodec18
ms.date: 06/06/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 28994e7f3a4f31a9e3ee8c292a08df1132cf20df
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180384"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Szybki start: Tworzenie pierwszej ASP.NET Core aplikacji sieci Web przy użyciu programu Visual Studio

W ramach tego wprowadzenia 5 – 10 minut, jak używać programu Visual Studio utworzysz prostą aplikację sieci web "Hello World" przy użyciu szablonu projektu programu ASP.NET i języka programowania C#.

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="install-visual-studio"></a>Instalowanie programu Visual Studio

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) strony, aby zainstalować go za darmo.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads) strony, aby zainstalować go za darmo.

::: moniker-end

### <a name="choose-your-theme-optional"></a>Wybierz kompozycję (opcjonalnie)

Ten samouczek Szybki Start zawiera zrzuty ekranu, używanego przez ciemnego motywu. Jeśli nie używasz motyw ciemny, ale aby zobaczyć [Personalizowanie programu Visual Studio IDE i edytorem](quickstart-personalize-the-ide.md) strony, aby dowiedzieć się, jak.

## <a name="create-a-project"></a>Tworzenie projektu

Aby rozpocząć, należy utworzyć projekt aplikacji sieci web platformy ASP.NET Core. Typ projektu zawiera wszystkie pliki szablonów do utworzenia aplikacji sieci Web, zanim Dodaliśmy jeszcze wszystko!

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

1. Na górnym pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

1. W okienku po lewej stronie **nowy projekt** okna dialogowego rozwiń **Visual C#** , a następnie wybierz **platformy .NET Core**. W środkowym okienku wybierz **aplikacji sieci Web programu ASP.NET Core**. <br/><br/>Następnie nadaj plikowi nazwę `HelloWorld` i wybierz polecenie **OK**.

   ![Utwórz nowy projekt aplikacji sieci Web ASP.NET Core dlaC#](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > Jeśli nie widzisz **platformy .NET Core** projektu kategorii szablonu, wybierz **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie. (W zależności od ustawień wyświetlania, trzeba będzie Przewinięcie w celu wyświetlenia go.)
   >
   > ![Instalator programu Visual Studio Otwórz okno dialogowe Nowy projekt](../ide/media/open-visual-studio-installer.png)
   >
   > Uruchamia Instalatora programu Visual Studio. Wybierz **ASP.NET i tworzenie aplikacji internetowych** obciążenia, a następnie wybierz **Modyfikuj**.
   >
   > ![Obciążenie platformy ASP.NET w Instalatorze programu VS](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Może być ma zamknięcie programu Visual Studio, zanim będzie można kontynuować instalowania nowego obciążenia).

1. W oknie dialogowym **Nowa aplikacja sieci Web ASP.NET Core** wybierz pozycję **ASP.NET Core 2,1** z menu rozwijanego górne. Następnie wybierz pozycję **aplikacja sieci Web**, a następnie wybierz przycisk **OK**.

   ![Okno dialogowe Nowa aplikacja sieci Web ASP.NET Core](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > Jeśli nie widzisz **ASP.NET Core 2,1**, upewnij się, że korzystasz z najnowszej wersji programu Visual Studio. Aby uzyskać więcej informacji o sposobie aktualizowania instalacji, zobacz sekcję [Aktualizowanie programu Visual Studio do najnowszej wersji](../install/update-visual-studio.md) .

Wkrótce potem Visual Studio otwiera plik projektu.

::: moniker-end

::: moniker range="vs-2019"

1. Otwórz program Visual Studio.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetl okno "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Tworzenie nowego projektu** wprowadź lub wpisz *ASP.NET* w polu wyszukiwania. Następnie wybierz **C#** z listy język, a następnie wybierz pozycję **Windows** z listy platform.

   Po zastosowaniu filtrów języka i platformy wybierz szablon **ASP.NET Core aplikacji sieci Web** , a następnie wybierz przycisk **dalej**.

   ![Wybierz C# szablon dla ASP.NET Core aplikacji sieci Web](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **ASP.NET Core aplikacji sieci Web** , możesz go zainstalować z okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** .
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "nie można odnaleźć szukanego elementu" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w Instalator programu Visual Studio wybierz obciążenie **ASP.NET i programowanie dla sieci Web** .
   >
   > ![ASP.NET Core obciążenie aplikacji sieci Web w Instalator programu Visual Studio](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj** , aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze "[Create a Project](#create-a-project)".

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *HelloWorld* w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

   ![w oknie "Konfigurowanie nowego projektu" Nazwij swój projekt "HelloWorld"](../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png)

1. W oknie **Tworzenie nowej ASP.NET Core aplikacji sieci Web** Sprawdź, czy w górnym menu rozwijanym znajduje się **ASP.NET Core 2,1** . Następnie wybierz pozycję **aplikacja sieci Web**, która zawiera przykład Razor Pages. Następnie wybierz pozycję **Utwórz**.

   ![Okno "Tworzenie nowej ASP.NET Core aplikacji sieci Web"](../get-started/csharp/media/vs-2019/csharp-create-aspnet-core-razor-pages-app.png)

   Program Visual Studio otwiera nowy projekt.

::: moniker-end

## <a name="create-and-run-the-app"></a>Tworzenie i uruchamianie aplikacji

1. W **Eksplorator rozwiązań**rozwiń folder **strony** , a następnie wybierz pozycję **about. cshtml**.

   ![Wybierz plik About.cshtml z poziomu Eksploratora rozwiązań](../ide/media/csharp-aspnet-about-page-html-file.png)

   Ten plik odnosi się do strony, który nosi nazwę **o** w aplikacji sieci web, które są uruchamiane w przeglądarce sieci web.

   ![Na stronie informacje w aplikacji sieci web](../ide/media/csharp-aspnet-about-page.png)

   W edytorze zobaczysz kod HTML dla obszaru "informacje dodatkowe" na stronie **informacje** .

   ![Kod HTML dla obszaru informacji dodatkowych w edytorze programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Zmień tekst "informacje dodatkowe", aby odczytać "**Hello World!** ".

   ![Zmiana domyślnego kodu HTML dla obszaru informacji dodatkowych w edytorze programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. W **Eksploratora rozwiązań**, rozwiń węzeł **About.cshtml**, a następnie wybierz **About.cshtml.cs**. (Ten plik odpowiada również stronie **informacje** w przeglądarce internetowej).

   ![Wybierz plik About.cshtml z poziomu Eksploratora rozwiązań](../ide/media/csharp-aspnet-about-page-code-file.png)

   W edytorze zobaczysz C# kod, który zawiera tekst dla obszaru "Opis aplikacji" na stronie **informacje** .

   ![C# Kod obszaru opisu aplikacji w edytorze programu Visual Studio.](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Zmień tekst komunikatu "description aplikacji" do odczytu "**co to jest wiadomość?** ".

   ![Zmień domyślny tekst komunikatu dla obszaru opisu aplikacji w edytorze programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Wybierz **usług IIS Express** lub naciśnij **Ctrl**+**F5** Uruchom aplikację i otworzyć go w przeglądarce sieci web.

   ![Wybierz przycisk IIS Express w programie Visual Studio](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > Jeśli otrzymasz komunikat o błędzie informujący, że, **nie można połączyć się z serwerem sieci web usług IIS Express**, lub komunikat o błędzie dotyczący certyfikatu SSL, zamknij program Visual Studio. Następnie otwórz program Visual Studio przy użyciu opcji **Uruchom jako administrator** w menu kontekstowym po kliknięciu prawym przyciskiem myszy. Następnie uruchom ponownie aplikację.

1. W przeglądarce sieci web, upewnij się, że **o** strona zawiera zaktualizowane tekstu.

   ![Wyświetl zaktualizowane informacje o stronie zawierającej wprowadzone zmiany](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Zamknij przeglądarkę sieci web.

### <a name="review-your-work"></a>Przejrzyj swoją służbę

Wyświetl poniższą animację, aby sprawdzić pracę zakończono w poprzedniej sekcji.

  ![Wyświetl animowany plik GIF, który pokazuje, jak utworzyć i uruchomić prostą C# aplikację sieci Web ASP.NET Core w programie Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

Gratulujemy ukończenie tego przewodnika Szybki Start! Mamy nadzieję, że wiesz już nieco C#, ASP.NET Core i programu Visual Studio IDE (zintegrowanym środowiskiem programistycznym).

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej, przejdź do następującego samouczka:

> [!div class="nextstepaction"]
> [Wprowadzenie do języka C# i platformy ASP.NET w programie Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Zobacz także

[Publikowanie aplikacji sieci web w usłudze Azure App Service przy użyciu programu Visual Studio](../deployment/quickstart-deploy-to-azure.md)
