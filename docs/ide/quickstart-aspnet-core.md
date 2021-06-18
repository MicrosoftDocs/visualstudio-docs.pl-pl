---
title: 'Tworzenie aplikacji ASP.NET Core w języku C #'
description: Dowiedz się, jak utworzyć prostą aplikację Hello world internetową w języku Visual Studio c# i ASP.NET Core, krok po kroku.
ms.custom: acquisition, mvc,seodec18
ms.date: 11/06/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 61fc3f0cf1e23dcf0f9e22ed7e10050fb84c9ba6
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308067"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Szybki start: tworzenie pierwszej Visual Studio Core przy użyciu ASP.NET Core

W tym 5-10-minutowym wprowadzeniu do korzystania z usługi Visual Studio utworzysz prostą aplikację internetową "Hello world" przy użyciu szablonu projektu ASP.NET i języka programowania C#.

## <a name="before-you-begin"></a>Zanim rozpoczniesz

### <a name="install-visual-studio"></a>Instalowanie programu Visual Studio

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/downloads) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2022"

Jeśli jeszcze nie zainstalowano programu Visual Studio 2022 (wersja zapoznawcza), przejdź do strony pobierania programu [Visual Studio 2022 Preview,](https://visualstudio.microsoft.com/vs/preview/vs2022) aby zainstalować ją bezpłatnie.

::: moniker-end

### <a name="choose-your-theme-optional"></a>Wybierz motyw (opcjonalnie)

Ten samouczek Szybki start zawiera zrzuty ekranu, które używają ciemnego motywu. Jeśli nie używasz motywu ciemnego, ale chcesz, zobacz stronę Personalizowanie środowiska [IDE](quickstart-personalize-the-ide.md) i edytora Visual Studio, aby dowiedzieć się, jak to zrobić.

## <a name="create-a-project"></a>Tworzenie projektu

Aby rozpocząć, utworzysz projekt aplikacji ASP.NET Core. Typ projektu zawiera wszystkie pliki szablonów do utworzenia aplikacji internetowej, zanim jeszcze cokolwiek dodano.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

1. Na górnym pasku menu wybierz pozycję **File** New Project > **(Plik nowy** > **projekt).**

1. W lewym okienku okna **dialogowego Nowy** projekt rozwiń pozycję **Visual C#,** a następnie wybierz **pozycję .NET Core.** W środkowym okienku wybierz **pozycję ASP.NET Core Web Application.** <br/><br/>Następnie nadaj plikowi nazwę `HelloWorld` i wybierz **przycisk OK.**

   ![Tworzenie nowego projektu aplikacji ASP.NET Core dla języka C #](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > Jeśli nie widzisz kategorii **szablonu projektu .NET Core,** wybierz link Otwórz Instalator programu Visual Studio w okienku po lewej stronie.  (W zależności od ustawień wyświetlania może być konieczne przewinięcie w celu wyświetlenia).
   >
   > ![Otwieranie Instalator programu Visual Studio z okna dialogowego nowego projektu](../ide/media/open-visual-studio-installer.png)
   >
   > Ta Instalator programu Visual Studio uruchamia się. Wybierz obciążenie **tworzenie aplikacji ASP.NET sieci Web,** a następnie wybierz pozycję **Modyfikuj.**
   >
   > ![ASP.NET obciążenia w instalatorze programu VS](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Może być konieczne zamknięcie Visual Studio, zanim będzie można kontynuować instalowanie nowego obciążenia).

1. W **oknie dialogowym Nowa ASP.NET Core Web Application** wybierz pozycję ASP.NET Core **2.1** z górnego menu rozwijanego. Następnie wybierz pozycję **Aplikacja internetowa,** a następnie wybierz przycisk **OK.**

   ![Okno dialogowe ASP.NET New ASP.NET Core Web Application (Nowa podstawowa aplikacja internetowa)](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > Jeśli nie widzisz wersji **ASP.NET Core 2.1,** upewnij się, że używasz najnowszej wersji Visual Studio. Aby uzyskać więcej informacji na temat aktualizowania instalacji, zobacz stronę Visual Studio [aktualizacji do najnowszej wersji.](../install/update-visual-studio.md)

Wkrótce Visual Studio plik projektu.

::: moniker-end

::: moniker range=">=vs-2019"

1. W oknie uruchamiania wybierz **pozycję Utwórz nowy projekt.**

   :::image type="content" source="../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="Wyświetlanie okna &quot;Tworzenie nowego projektu&quot;":::

1. W **oknie Tworzenie nowego projektu** wybierz pozycję **C#** z listy Język. Następnie wybierz **pozycję Windows** z listy Platforma i pozycję **Internet** z listy typów projektów.

      Po zastosowaniu filtrów języka, platformy i typu  projektu wybierz szablon Podstawowa aplikacja internetowa ASP.NET, a następnie wybierz pozycję **Dalej.**

   :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="Wybieranie szablonu języka C# dla aplikacji internetowej ASP.NET Core":::

   > [!NOTE]
   > Jeśli nie widzisz szablonu aplikacji **internetowej ASP.NET Core,** możesz go zainstalować w oknie **Tworzenie nowego** projektu. W **komunikacie Nie** można znaleźć tego, czego szukasz? wybierz link Zainstaluj więcej narzędzi **i** funkcji.
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" w komunikacie "Nie można znaleźć tego, czego szukasz" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w witrynie Instalator programu Visual Studio wybierz obciążenie **Tworzenie aplikacji ASP.NET sieci Web.**
   >
   > ![Międzyplatformowe obciążenie programowe platformy .NET Core w chmurze Instalator programu Visual Studio](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Jeśli zostanie wyświetlony monit o zapisanie pracy, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze["Tworzenie projektu".](#create-a-project)

1. W **oknie Configure your new project (Konfigurowanie** nowego projektu) wpisz lub wprowadź *HelloWorld* w **polu Project name (Nazwa** projektu). Następnie wybierz pozycję **Dalej.**

    :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png" alt-text="W oknie &quot;Konfigurowanie nowego projektu&quot; nadaj projektowi nazwę &quot;MyCoreApp&quot;":::

1. W **oknie Dodatkowe informacje** sprawdź, czy program **.NET Core 3.1** jest wyświetlany w górnym menu rozwijaym. Pamiętaj, że możesz włączyć obsługę platformy Docker, zaznaczając to pole wyboru. Obsługę uwierzytelniania można również dodać, klikając przycisk Zmiany uwierzytelniania. W tym miejscu można wybrać jedną z opcji:
    - Brak: brak uwierzytelniania.
    - Indywidualne konta: są one przechowywane w lokalnej bazie danych lub bazie danych opartej na platformie Azure.
    - Platforma tożsamości firmy Microsoft: ta opcja używa usługi Active Directory, Azure AD Microsoft 365 do uwierzytelniania.
    - Windows: odpowiednie dla aplikacji intranetowych.
    
    Pozostaw **niezaznaczone pole Włącz platformę Docker** i wybierz opcję **Brak w** polu Typ uwierzytelniania. Następnie wybierz przycisk **Utwórz**.

   :::image type="content" source="../get-started/csharp/media/vs-2019/aspnet-core-additional-information.png" alt-text="W oknie &quot;Dodatkowe informacje&quot; upewnij się, że wybrano opcję .NET Core 3.1 i pozostaw wszystkie wartości domyślne":::

   Visual Studio spowoduje otwarcie nowego projektu.

::: moniker-end

## <a name="create-and-run-the-app"></a>Tworzenie i uruchamianie aplikacji

::: moniker range="vs-2017"

1. W **Eksplorator rozwiązań** rozwiń folder **Strony,** a następnie wybierz **plik About.cshtml.**

   ![Zrzut ekranu Visual Studio Eksplorator rozwiązań przedstawiający pliki w projekcie HelloWorld. Folder Strony jest rozwinięty i wybrano plik About.cshtml.](../ide/media/csharp-aspnet-about-page-html-file.png)

   Ten plik odpowiada stronie o  nazwie Informacje w aplikacji internetowej, która jest uruchamiana w przeglądarce internetowej.

   ![Strona Informacje w aplikacji internetowej](../ide/media/csharp-aspnet-about-page.png)

   W edytorze zobaczysz kod HTML dla obszaru "dodatkowe informacje" na **stronie** Informacje.

   ![Kod HTML obszaru dodatkowych informacji w edytorze Visual Studio kodu](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Zmień tekst "dodatkowe informacje" na **"Hello world!**".

   ![Zmień wartość domyślną Kod HTML dla obszaru dodatkowych informacji w Visual Studio edytorze](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. W **Eksplorator rozwiązań** rozwiń pozycję **About.cshtml,** a następnie wybierz **pozycję About.cshtml.cs.** (Ten plik odpowiada również stronie **Informacje** w przeglądarce internetowej).

   ![Zrzut ekranu Visual Studio Eksplorator rozwiązań przedstawiający pliki w projekcie HelloWorld. Po rozwinięciu pliku About.cshtml i wybraniu pliku About.cshtml.cs.](../ide/media/csharp-aspnet-about-page-code-file.png)

   W edytorze zobaczysz kod języka C#, który zawiera tekst w obszarze "opis aplikacji" na **stronie** Informacje.

   ![Kod języka C# dla obszaru opisu aplikacji w edytorze Visual Studio aplikacji](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Zmień tekst komunikatu "application description" na **"What's my message?**".

   ![Zmień domyślny tekst komunikatu dla obszaru opisu aplikacji w edytorze Visual Studio aplikacji](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Wybierz **IIS Express** lub naciśnij **klawisz Ctrl** + **F5,** aby uruchomić aplikację i otworzyć ją w przeglądarce internetowej.

   ![Wybierz przycisk IIS Express w Visual Studio](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > Jeśli zostanie wyświetlony komunikat o błędzie z komunikatem Nie można nawiązać połączenia z serwerem sieci **Web "IIS Express"** lub komunikat o błędzie informujący o certyfikacie SSL, zamknij Visual Studio. Następnie otwórz Visual Studio przy użyciu opcji Uruchom jako **administrator** z menu kontekstowego dostępnego po kliknięciu prawym przyciskiem myszy. Następnie ponownie uruchom aplikację.

1. W przeglądarce internetowej sprawdź, czy strona **Informacje** zawiera zaktualizowany tekst.

   ![Wyświetl zaktualizowaną stronę Informacje, która zawiera wprowadzone zmiany](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Zamknij przeglądarkę internetową.

### <a name="review-your-work"></a>Przeglądanie pracy

Wyświetl następującą animację, aby sprawdzić pracę, która została ukończona w poprzedniej sekcji.

  ![Wyświetl animowany plik .gif, który pokazuje, jak utworzyć i uruchomić prostą aplikację internetową W# ASP.NET Core w programie Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

Gratulujemy ukończenia tego przewodnika Szybki start! Mamy nadzieję, że wiesz już nieco o języku C#, środowisku ASP.NET Core i Visual Studio IDE (zintegrowanym środowisku projektowym).

::: moniker-end

::: moniker range=">=vs-2019"

1. W **Eksplorator rozwiązań** rozwiń folder **Strony,** a następnie wybierz **plik Index.cshtml.**

   ![Wybierz plik Index.cshtml z Eksplorator rozwiązań](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   Ten plik odpowiada stronie o nazwie **Strona** główna w aplikacji internetowej, która jest uruchamiana w przeglądarce internetowej.

   ![Strona Informacje w aplikacji internetowej](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   W edytorze zobaczysz kod HTML dla tekstu wyświetlanego na **stronie głównej.**

   ![Kod HTML w pliku Index.cshtml dla strony głównej w edytorze Visual Studio plików](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page.png)

1. Zmień tekst "Welcome" (Powitanie) na **"Hello world!**".

   ![W edytorze Visual Studio zmień domyślny kod HTML z wartością Witaj, aby zamiast tego Hello world](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page-hello-world.png)

1. Wybierz **IIS Express** lub naciśnij **klawisz Ctrl** + **F5,** aby uruchomić aplikację i otworzyć ją w przeglądarce internetowej.

   ![Wybierz przycisk IIS Express w Visual Studio](../ide/media/vs-2019/csharp-aspnet-generic-iisbutton.png)

   > [!NOTE]
   > Jeśli zostanie wyświetlony komunikat o błędzie z komunikatem Nie można nawiązać połączenia z serwerem sieci **Web "IIS Express"** lub komunikat o błędzie informujący o certyfikacie SSL, zamknij Visual Studio. Następnie otwórz Visual Studio przy użyciu opcji Uruchom jako **administrator** z menu kontekstowego dostępnego po kliknięciu prawym przyciskiem myszy. Następnie ponownie uruchom aplikację.

1. W przeglądarce internetowej sprawdź, czy strona **główna** zawiera zaktualizowany tekst.

   ![Wyświetl zaktualizowaną stronę główną, która zawiera wprowadzone zmiany](../ide/media/vs-2019/csharp-aspnet-index-page-hello-world.png)

1. Zamknij przeglądarkę internetową.

::: moniker-end

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej, przejdź do następującego samouczka:

> [!div class="nextstepaction"]
> [Wprowadzenie do języka C# i ASP.NET w Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Zobacz też

[Publikowanie aplikacji internetowej w witrynie Azure App Service przy użyciu Visual Studio](../deployment/quickstart-deploy-to-azure.md)
