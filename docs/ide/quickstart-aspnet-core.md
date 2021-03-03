---
title: 'Tworzenie aplikacji sieci Web ASP.NET Core w języku C #'
description: Dowiedz się, jak utworzyć prostą aplikację sieci Web Hello world w programie Visual Studio przy użyciu języka C# i ASP.NET Core, krok po kroku.
ms.custom: mvc,seodec18
ms.date: 11/06/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
author: ornellaalt
ms.author: ornella
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 68ccba785643b8f4f29143e5e72dc65cfedcd512
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101684050"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Szybki Start: Tworzenie ASP.NET Core pierwszej aplikacji sieci Web za pomocą programu Visual Studio

W tym 5-10 minucie dowiesz się, jak korzystać z programu Visual Studio, utworzyć prostą aplikację sieci Web "Hello world" przy użyciu szablonu projektu ASP.NET i języka programowania w języku C#.

## <a name="before-you-begin"></a>Zanim rozpoczniesz

### <a name="install-visual-studio"></a>Instalowanie programu Visual Studio

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

### <a name="choose-your-theme-optional"></a>Wybieranie motywu (opcjonalnie)

Ten samouczek szybki start obejmuje zrzuty ekranu, które używają ciemnego motywu. Jeśli nie używasz ciemnego motywu, ale chcesz, zobacz stronę [personalizowanie środowiska IDE i edytora programu Visual Studio](quickstart-personalize-the-ide.md) , aby dowiedzieć się, jak.

## <a name="create-a-project"></a>Tworzenie projektu

Aby rozpocząć, utworzysz projekt aplikacji sieci Web ASP.NET Core. Typ projektu zawiera wszystkie pliki szablonów do utworzenia aplikacji sieci Web, zanim Dodaliśmy jeszcze wszystko!

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

1. Na górnym pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

1. W lewym okienku okna dialogowego **Nowy projekt** rozwiń pozycję **Visual C#**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz **ASP.NET Core aplikacji sieci Web**. <br/><br/>Następnie Nazwij plik `HelloWorld` i wybierz **przycisk OK**.

   ![Tworzenie nowego projektu aplikacji sieci Web ASP.NET Core dla języka C #](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > Jeśli nie widzisz kategorii szablonu projektu **.NET Core** , wybierz link **Otwórz Instalator programu Visual Studio** w lewym okienku. (W zależności od ustawień wyświetlania może być konieczne przewinięcie, aby je zobaczyć.)
   >
   > ![Otwórz Instalator programu Visual Studio z okna dialogowego Nowy projekt](../ide/media/open-visual-studio-installer.png)
   >
   > Zostanie uruchomiona Instalator programu Visual Studio. Wybierz obciążenie **ASP.NET i projektowanie sieci Web** , a następnie wybierz **Modyfikuj**.
   >
   > ![ASP.NET obciążenie w instalatorze VS](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Przed kontynuowaniem instalacji nowego obciążenia może być konieczne zamknięcie programu Visual Studio).

1. W oknie dialogowym **Nowa aplikacja sieci Web ASP.NET Core** wybierz pozycję **ASP.NET Core 2,1** z menu rozwijanego górne. Następnie wybierz pozycję **aplikacja sieci Web**, a następnie wybierz przycisk **OK**.

   ![Okno dialogowe Nowa aplikacja sieci Web ASP.NET Core](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > Jeśli nie widzisz **ASP.NET Core 2,1**, upewnij się, że korzystasz z najnowszej wersji programu Visual Studio. Aby uzyskać więcej informacji o sposobie aktualizowania instalacji, zobacz sekcję [Aktualizowanie programu Visual Studio do najnowszej wersji](../install/update-visual-studio.md) .

Wkrótce po program Visual Studio otworzy plik projektu.

::: moniker-end

::: moniker range="vs-2019"

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   :::image type="content" source="../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="Wyświetl okno &quot;Tworzenie nowego projektu&quot;":::

1. W oknie **Tworzenie nowego projektu** wybierz pozycję **C#** z listy język. Następnie wybierz pozycję **Windows** z listy platform i **sieci Web** z listy typów projektów.

      Po zastosowaniu filtrów języka, platformy i typu projektu wybierz szablon **ASP.NET Core Web App** , a następnie wybierz **dalej**.

   :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="Wybierz szablon C# dla aplikacji sieci Web ASP.NET Core":::

   > [!NOTE]
   > Jeśli nie widzisz szablonu **ASP.NET Core aplikacji sieci Web** , możesz go zainstalować z okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** .
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "nie można odnaleźć szukanego elementu" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w Instalator programu Visual Studio wybierz obciążenie **ASP.NET i programowanie dla sieci Web** .
   >
   > ![Obciążenie Międzyplatformowe dla platformy .NET Core w Instalator programu Visual Studio](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Jeśli zostanie wyświetlony monit o zapisanie pracy, zrób to. Następnie wybierz pozycję **Kontynuuj** , aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze "[Create a Project](#create-a-project)".

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *HelloWorld* w polu **Nazwa projektu** . Następnie wybierz przycisk **dalej**.

    :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png" alt-text="w oknie &quot;Konfigurowanie nowego projektu&quot; nazwij projekt &quot;MyCoreApp&quot;":::

1. W oknie **Informacje dodatkowe** Sprawdź, czy program **.NET Core 3,1** pojawia się w górnym menu rozwijanym. Pamiętaj, że możesz włączyć obsługę platformy Docker, zaznaczając pole wyboru. Możesz również dodać obsługę uwierzytelniania, klikając przycisk Zmień uwierzytelnianie. Z tego miejsca możesz wybrać jedną z opcji:
    - Brak: brak uwierzytelniania.
    - Pojedyncze konta: są one przechowywane w lokalnej lub opartej na platformie Azure bazie danych.
    - Platforma tożsamości firmy Microsoft: Ta opcja używa Active Directory, Azure AD lub Microsoft 365 do uwierzytelniania.
    - Windows: odpowiednie dla aplikacji intranetowych.
    
    Pozostaw zaznaczenie pola wyboru **Włącz platformę Docker** i wybierz opcję **Brak** dla opcji Typ uwierzytelniania. Następnie wybierz przycisk **Utwórz**.

   :::image type="content" source="../get-started/csharp/media/vs-2019/aspnet-core-additional-information.png" alt-text="w oknie &quot;dodatkowe informacje&quot; Upewnij się, że wybrano opcję .NET Core 3,1 i pozostaw wszystkie wartości domyślne":::

   Program Visual Studio otworzy nowy projekt.

::: moniker-end

## <a name="create-and-run-the-app"></a>Utwórz i uruchom aplikację

::: moniker range="vs-2017"

1. W **Eksplorator rozwiązań** rozwiń folder **strony** , a następnie wybierz pozycję **about. cshtml**.

   ![Zrzut ekranu programu Visual Studio Eksplorator rozwiązań pokazujący pliki w projekcie HelloWorld. Folder strony jest rozwinięty i wybrano około. cshtml.](../ide/media/csharp-aspnet-about-page-html-file.png)

   Ten plik odpowiada stronie o nazwie **informacje** w aplikacji sieci Web, która działa w przeglądarce sieci Web.

   ![Strona informacje w aplikacji sieci Web](../ide/media/csharp-aspnet-about-page.png)

   W edytorze zobaczysz kod HTML dla obszaru "informacje dodatkowe" na stronie **informacje** .

   ![Kod HTML dla obszaru informacji dodatkowych w edytorze programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Zmień tekst "informacje dodatkowe", aby odczytać "**Hello World!**".

   ![Zmiana domyślnego kodu HTML dla obszaru informacji dodatkowych w edytorze programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. W **Eksplorator rozwiązań** rozwiń pozycję **about. cshtml**, a następnie wybierz pozycję **about.cshtml.cs**. (Ten plik odpowiada również stronie **informacje** w przeglądarce internetowej).

   ![Zrzut ekranu programu Visual Studio Eksplorator rozwiązań pokazujący pliki w projekcie HelloWorld. About. cshtml jest rozwinięta, a wybrano About.cshtml.cs.](../ide/media/csharp-aspnet-about-page-code-file.png)

   W edytorze zobaczysz kod C#, który zawiera tekst dla obszaru "Opis aplikacji" na stronie **informacje** .

   ![Kod C# obszaru opisu aplikacji w edytorze programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Zmień tekst komunikatu "Opis aplikacji", aby przeczytać "**co to jest mój komunikat?**".

   ![Zmień domyślny tekst komunikatu dla obszaru opisu aplikacji w edytorze programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Wybierz **IIS Express** lub naciśnij klawisz **Ctrl** + **F5** , aby uruchomić aplikację i otworzyć ją w przeglądarce sieci Web.

   ![Wybierz przycisk IIS Express w programie Visual Studio](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > Jeśli zostanie wyświetlony komunikat o błędzie z informacją, że **nie można nawiązać połączenia z serwerem sieci Web "IIS Express"** lub komunikat o błędzie z informacją o certyfikacie SSL, Zamknij program Visual Studio. Następnie otwórz program Visual Studio przy użyciu opcji **Uruchom jako administrator** w menu kontekstowym po kliknięciu prawym przyciskiem myszy. Następnie ponownie uruchom aplikację.

1. W przeglądarce sieci Web sprawdź, czy strona **informacje** zawiera zaktualizowany tekst.

   ![Wyświetl zaktualizowane informacje o stronie zawierającej wprowadzone zmiany](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Zamknij przeglądarkę internetową.

### <a name="review-your-work"></a>Przejrzyj swoją służbę

Wyświetl poniższą animację, aby sprawdzić pracę zakończono w poprzedniej sekcji.

  ![Wyświetl animowany plik GIF, który pokazuje, jak utworzyć i uruchomić prostą aplikację sieci Web w języku C# ASP.NET Core w programie Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

Gratulujemy zakończenia tego przewodnika Szybki Start! Mamy nadzieję, że uczysz się nieco na temat języka C#, ASP.NET Core i programu Visual Studio IDE (zintegrowanego środowiska programistycznego).

::: moniker-end

::: moniker range="vs-2019"

1. W **Eksplorator rozwiązań** rozwiń folder **strony** , a następnie wybierz polecenie **index. cshtml**.

   ![Wybierz plik index. cshtml z Eksplorator rozwiązań](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   Ten plik odpowiada stronie o nazwie **Home** w aplikacji sieci Web, która działa w przeglądarce sieci Web.

   ![Strona informacje w aplikacji sieci Web](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   W edytorze zobaczysz kod HTML dla tekstu wyświetlanego na stronie **głównej** .

   ![Kod HTML w pliku index. cshtml dla strony głównej w edytorze programu Visual Studio](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page.png)

1. Zmień tekst "Welcome", aby odczytał "**Hello World!**".

   ![W edytorze programu Visual Studio zmień domyślny kod HTML, który mówi, że Hello world zamiast tego.](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page-hello-world.png)

1. Wybierz **IIS Express** lub naciśnij klawisz **Ctrl** + **F5** , aby uruchomić aplikację i otworzyć ją w przeglądarce sieci Web.

   ![Wybierz przycisk IIS Express w programie Visual Studio](../ide/media/vs-2019/csharp-aspnet-generic-iisbutton.png)

   > [!NOTE]
   > Jeśli zostanie wyświetlony komunikat o błędzie z informacją, że **nie można nawiązać połączenia z serwerem sieci Web "IIS Express"** lub komunikat o błędzie z informacją o certyfikacie SSL, Zamknij program Visual Studio. Następnie otwórz program Visual Studio przy użyciu opcji **Uruchom jako administrator** w menu kontekstowym po kliknięciu prawym przyciskiem myszy. Następnie ponownie uruchom aplikację.

1. W przeglądarce sieci Web sprawdź, czy strona **główna** zawiera zaktualizowany tekst.

   ![Wyświetlanie zaktualizowanej strony głównej zawierającej wprowadzone zmiany](../ide/media/vs-2019/csharp-aspnet-index-page-hello-world.png)

1. Zamknij przeglądarkę internetową.

::: moniker-end

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej, przejdź do następującego samouczka:

> [!div class="nextstepaction"]
> [Wprowadzenie do języka C# i ASP.NET w programie Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Zobacz też

[Publikowanie aplikacji sieci Web w Azure App Service przy użyciu programu Visual Studio](../deployment/quickstart-deploy-to-azure.md)
