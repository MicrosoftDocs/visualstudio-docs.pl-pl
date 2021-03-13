---
title: 'Samouczek: wprowadzenie do języka C# i ASP.NET Core'
titleSuffix: ''
description: Dowiedz się, jak utworzyć aplikację internetową ASP.NET Core w programie Visual Studio przy użyciu języka C#, krok po kroku.
ms.custom: seodec18, get-started
ms.date: 02/12/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: b9c7f41fd2977ca00294eabd941bc371d8a3220e
ms.sourcegitcommit: 99b66b0f4ced46ead0b2506a103f974f40cc0076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103295796"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Samouczek: wprowadzenie do języka C# i ASP.NET Core w programie Visual Studio

W ramach tego samouczka dotyczącego programowania w języku C# ASP.NET Core za pomocą programu Visual Studio utworzysz aplikację internetową w języku C# ASP.NET Core, wprowadzisz w niej zmiany, Dowiedz się więcej o funkcjach środowiska IDE, a następnie uruchom aplikację.

## <a name="before-you-begin"></a>Zanim rozpoczniesz

### <a name="install-visual-studio"></a>Instalowanie programu Visual Studio

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

### <a name="update-visual-studio"></a>Aktualizowanie programu Visual Studio

Jeśli masz już zainstalowany program Visual Studio, upewnij się, że korzystasz z najnowszej wersji. Aby uzyskać więcej informacji o sposobie aktualizowania instalacji, zobacz sekcję [Aktualizowanie programu Visual Studio do najnowszej wersji](../../install/update-visual-studio.md) .

### <a name="choose-your-theme-optional"></a>Wybieranie motywu (opcjonalnie)

Ten samouczek zawiera zrzuty ekranu używające ciemnego motywu. Jeśli nie używasz ciemnego motywu, ale chcesz, zobacz stronę [personalizowanie środowiska IDE i edytora programu Visual Studio](../../ide/quickstart-personalize-the-ide.md) , aby dowiedzieć się, jak.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt ASP.NET Core. Typ projektu zawiera wszystkie pliki szablonów, które będą potrzebne dla w pełni funkcjonalnej witryny sieci Web, przed dodaniem nawet wszystkiego.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

3. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń pozycję **Visual C#**, rozwiń węzeł **Sieć Web**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz **ASP.NET Core aplikacji sieci Web**. Następnie Nazwij plik *MyCoreApp* i wybierz **przycisk OK**.

   ![Szablon projektu aplikacji sieci Web ASP.NET Core w oknie dialogowym Nowy projekt w programie Visual Studio IDE](media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

### <a name="add-a-workload-optional"></a>Dodaj obciążenie (opcjonalnie)

Jeśli nie widzisz szablonu projektu **ASP.NET Core aplikacji sieci Web** , możesz uzyskać go, dodając obciążenie **ASP.NET i programowanie dla sieci Web** . Możesz dodać to obciążenie jeden z dwóch poniższych sposobów, w zależności od tego, które aktualizacje programu Visual Studio 2017 są zainstalowane na maszynie.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opcja 1: korzystanie z okna dialogowego Nowy projekt

1. Wybierz łącze **otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** . (W zależności od ustawień wyświetlania może być konieczne przewinięcie, aby je zobaczyć.)

   ![Wybierz łącze Otwórz Instalator programu Visual Studio w oknie dialogowym Nowy projekt](../media/open-visual-studio-installer-mycoreapp.png)

1. Zostanie uruchomiona Instalator programu Visual Studio. Wybierz obciążenie **ASP.NET i projektowanie sieci Web** , a następnie wybierz **Modyfikuj**.

   ![Obciążenie Międzyplatformowe dla platformy .NET Core w Instalator programu Visual Studio](../media/tutorial-aspnet-workload.png)

   (Przed kontynuowaniem instalacji nowego obciążenia może być konieczne zamknięcie programu Visual Studio).

#### <a name="option-2-use-the-tools-menu-bar"></a>Opcja 2. Korzystanie z paska menu narzędzi

1. Anuluj okno dialogowe **Nowy projekt** . Następnie na górnym pasku menu wybierz kolejno pozycje **Narzędzia**  >  **Pobierz narzędzia i funkcje**.

1. Zostanie uruchomiona Instalator programu Visual Studio. Wybierz obciążenie **ASP.NET i projektowanie sieci Web** , a następnie wybierz **Modyfikuj**.

   (Przed kontynuowaniem instalacji nowego obciążenia może być konieczne zamknięcie programu Visual Studio).

### <a name="add-a-project-template"></a>Dodaj szablon projektu

1. W oknie dialogowym **Nowa aplikacja sieci web ASP.NET Core** wybierz szablon projektu **aplikacji sieci Web** .

1. Sprawdź, czy **ASP.NET Core 2,1** pojawia się w górnym menu rozwijanym. Następnie wybierz przycisk **OK**.

   ![Okno dialogowe Nowa aplikacja sieci Web ASP.NET Core](media/new-project-csharp-aspnet-razor-web-app.png)

   > [!NOTE]
   > Jeśli nie widzisz **ASP.NET Core 2,1** z górnego menu rozwijanego, upewnij się, że korzystasz z najnowszej wersji programu Visual Studio. Aby uzyskać więcej informacji o sposobie aktualizowania instalacji, zobacz sekcję [Aktualizowanie programu Visual Studio do najnowszej wersji](../../install/update-visual-studio.md) .

::: moniker-end

::: moniker range="vs-2019"

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   :::image type="content" source="../../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="Wyświetl okno &quot;Tworzenie nowego projektu&quot;":::

1. W oknie **Tworzenie nowego projektu** wybierz pozycję **C#** z listy język. Następnie wybierz pozycję **Windows** z listy platform i **sieci Web** z listy typów projektów.

      Po zastosowaniu filtrów języka, platformy i typu projektu wybierz szablon **ASP.NET Core Web App** , a następnie wybierz **dalej**.

   :::image type="content" source="./media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="Wybierz szablon C# dla aplikacji sieci Web ASP.NET Core":::

   > [!NOTE]
   > Jeśli nie widzisz szablonu **ASP.NET Core aplikacji sieci Web** , możesz go zainstalować z okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** .
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "nie można odnaleźć szukanego elementu" w oknie "Tworzenie nowego projektu"](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w Instalator programu Visual Studio wybierz obciążenie **ASP.NET i programowanie dla sieci Web** .
   >
   > ![Obciążenie Międzyplatformowe dla platformy .NET Core w Instalator programu Visual Studio](../../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Jeśli zostanie wyświetlony monit o zapisanie pracy, zrób to. Następnie wybierz pozycję **Kontynuuj** , aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze "[Create a Project](#create-a-project)".

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *MyCoreApp* w polu **Nazwa projektu** . Następnie wybierz przycisk **dalej**.

   :::image type="content" source="./media/vs-2019/csharp-name-your-aspnet-app.png" alt-text="w oknie &quot;Konfigurowanie nowego projektu&quot; nazwij projekt &quot;MyCoreApp&quot;":::

1. W oknie **Informacje dodatkowe** Sprawdź, czy program **.NET Core 3,1** pojawia się w górnym menu rozwijanym. Pamiętaj, że możesz włączyć obsługę platformy Docker, zaznaczając pole wyboru. Możesz również dodać obsługę uwierzytelniania, klikając przycisk Zmień uwierzytelnianie. Z tego miejsca możesz wybrać jedną z opcji:
    - Brak: brak uwierzytelniania.
    - Pojedyncze konta: są one przechowywane w lokalnej lub opartej na platformie Azure bazie danych.
    - Platforma tożsamości firmy Microsoft: Ta opcja używa Active Directory, Azure AD lub Microsoft 365 do uwierzytelniania.
    - Windows: odpowiednie dla aplikacji intranetowych.
    
    Pozostaw zaznaczenie pola wyboru **Włącz platformę Docker** i wybierz opcję **Brak** dla opcji Typ uwierzytelniania. Następnie wybierz przycisk **Utwórz**.

   :::image type="content" source="./media/vs-2019/aspnet-core-additional-information.png" alt-text="w oknie &quot;dodatkowe informacje&quot; Upewnij się, że wybrano opcję .NET Core 3,1 i pozostaw wszystkie wartości domyślne":::

   Program Visual Studio otworzy nowy projekt.

::: moniker-end

### <a name="about-your-solution"></a>Informacje o rozwiązaniu

To rozwiązanie jest zgodne ze wzorcem projektowania **strony Razor** . Jest to inny niż Wzorzec projektowy [modelu-View-Controller (MVC)](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x&preserve-view=true) , który jest zoptymalizowany do uwzględnienia kodu modelu i kontrolera na stronie Razor.

::: moniker range="vs-2017"
## <a name="tour-your-solution"></a>Zapoznaj się z rozwiązaniem

 1. Szablon projektu tworzy rozwiązanie o pojedynczym ASP.NET Core projekcie o nazwie _MyCoreApp_. Wybierz kartę **Eksplorator rozwiązań** , aby wyświetlić jej zawartość.

    ![ASP.NET Eksplorator rozwiązań w programie Visual Studio dla Razor Pages rozwiązanie o nazwie MyCoreApp](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Rozwiń folder **strony** , a następnie rozwiń pozycję *about. cshtml*.

     ![Plik about. cshtml w Eksplorator rozwiązań w programie Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. Wyświetl plik **about. cshtml** w edytorze kodu.

     ![Zrzut ekranu przedstawiający pierwsze dziesięć wierszy pliku about. cshtml w edytorze kodu programu Visual Studio.](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. Wybierz plik **about.cshtml.cs** .

     ![Wybierz plik About.cshtml.cs w edytorze kodu programu Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. Wyświetl plik **about.cshtml.cs** w edytorze kodu.

     ![Zrzut ekranu przedstawiający pierwsze 18 wierszy pliku About.cshtml.cs w edytorze kodu programu Visual Studio. ](media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. Projekt zawiera folder **wwwroot** , który jest katalogiem głównym witryny sieci Web. Rozwiń folder, aby wyświetlić jego zawartość.

     ![folder wwwroot w Eksplorator rozwiązań w programie Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    Możesz umieścić statyczną zawartość witryny, &mdash; taką jak CSS, obrazy i biblioteki JavaScript, &mdash; bezpośrednio w ścieżkach, w których chcesz.

 1. Projekt zawiera również pliki konfiguracyjne, które zarządzają aplikacją sieci Web w czasie wykonywania. Domyślna [Konfiguracja](/aspnet/core/fundamentals/configuration) aplikacji jest przechowywana w *appsettings.jsna*. Można jednak zastąpić te ustawienia przy użyciu *appsettings.Development.json*. Rozwiń **appsettings.jsna** pliku, aby wyświetlić **appsettings.Development.jsna** pliku.

     ![Pliki konfiguracji w Eksplorator rozwiązań w programie Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Uruchamianie, debugowanie i wprowadzanie zmian

1. Wybierz przycisk **IIS Express** w IDE, aby skompilować i uruchomić aplikację w trybie debugowania. (Alternatywnie naciśnij klawisz **F5** lub wybierz polecenie **Debuguj**  >  **Rozpocznij debugowanie** z paska menu.

     ![Wybierz przycisk IIS Express w programie Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Jeśli zostanie wyświetlony komunikat o błędzie z informacją, że **nie można nawiązać połączenia z serwerem sieci Web "IIS Express"**, Zamknij program Visual Studio, a następnie otwórz go przy użyciu opcji **Uruchom jako administrator** w prawym przyciskiem myszy lub w menu kontekstowym. Następnie ponownie uruchom aplikację.
     >
     > Może również zostać wyświetlony komunikat z pytaniem, czy chcesz zaakceptować certyfikat Express SSL protokołu IIS. Aby wyświetlić kod w przeglądarce sieci Web, wybierz opcję **tak**, a następnie wybierz opcję **tak** , jeśli zostanie wyświetlony komunikat ostrzegawczy o zabezpieczeniach.

1. Program Visual Studio uruchamia okno przeglądarki. Na pasku menu powinna zostać wyświetlona **Strona główna**, **informacje** i **kontakty** . (Jeśli nie, wybierz element menu "Hamburger", aby je wyświetlić).

    ![Wybierz element menu "Hamburger" z paska menu w aplikacji sieci Web.](media/csharp-aspnet-razor-browser-page.png)

1. Wybierz pozycję **informacje** na pasku menu.

   ![Wybierz informacje na pasku menu okna przeglądarki dla aplikacji](media/csharp-aspnet-razor-browser-page-about-menu.png)

   Na stronie **informacje** w przeglądarce jest renderowany tekst ustawiony w pliku *about. cshtml* .

   ![Wyświetlanie tekstu na stronie informacje](media/csharp-aspnet-razor-browser-page-about.png)

1. Wróć do programu Visual Studio, a następnie naciśnij klawisze **Shift + F5** , aby zatrzymać tryb debugowania. Spowoduje to również zamknięcie projektu w oknie przeglądarki.

1. W programie Visual Studio wybierz pozycję **about. cshtml**. Następnie Usuń słowo _dodatkowe_ i w tym miejscu Dodaj _plik i katalog_ wyrazów.

    ![Zmień tekst w pliku about. cshtml](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code-changed.png)

1. Wybierz **about.cshtml.cs**. Następnie wyczyść `using` dyrektywy w górnej części pliku, używając następującego skrótu:

   Wybierz dowolną z szarych `using` dyrektyw, a żarówka [Quick Actions](../../ide/quick-actions.md) zostanie wyświetlona tuż pod karetką lub na lewym marginesie. Wybierz żarówkę, a następnie wybierz **Usuń niepotrzebne użycie**.

   ![Usuń niepotrzebne użycie w pliku About.cshtml.cs](media/csharp-aspnet-razor-remove-unnecessary-usings.png)

     Program Visual Studio usuwa niepotrzebne `using` dyrektywy z pliku.

1. Następnie w `OnGet()` metodzie Zmień treść na następujący kod:

     ```csharp
     public void OnGet()
     {
         string directory = Environment.CurrentDirectory;
         Message = String.Format("Your directory is {0}.", directory);
     }
    ```

1. Zauważ, że dwie faliste podkreślenia są wyświetlane w obszarze **środowisko** i **ciąg**. Linie faliste są wyświetlane, ponieważ te typy nie należą do zakresu.

   ![Błędy oznaczone falistą linią w metodzie OnGet](media/csharp-aspnet-razor-add-new-on-get-method.png)

    Otwórz **Lista błędów** pasku narzędzi, aby zobaczyć te same błędy wymienione w tym miejscu. (Jeśli nie widzisz paska narzędzi **Lista błędów** , wybierz pozycję **Widok**  >  **Lista błędów** z górnego paska menu).

   ![Lista błędów w programie Visual Studio](media/csharp-aspnet-razor-error-list.png)

1. Naprawimy to. W edytorze kodu Umieść kursor w dowolnym wierszu zawierającym błąd, a następnie wybierz żarówkę Quick Actions na lewym marginesie. Następnie z menu rozwijanego wybierz pozycję **using System;** , aby dodać tę dyrektywę na początku pliku i usunąć błędy.

   ![Dodaj dyrektywę "using System;"](media/csharp-aspnet-razor-add-usings.png)

1. Naciśnij **kombinację klawiszy CTRL** + **S** , aby zapisać zmiany, a następnie naciśnij klawisz **F5** , aby otworzyć projekt w przeglądarce sieci Web.

1. W górnej części witryny sieci Web wybierz pozycję **informacje** , aby wyświetlić zmiany.

   ![Wyświetl zaktualizowane informacje o stronie zawierającej wprowadzone zmiany](media/csharp-aspnet-razor-browser-page-about-changed.png)

1. Zamknij przeglądarkę sieci Web, naciśnij klawisz **SHIFT** + **F5** , aby zatrzymać tryb debugowania, a następnie zamknij program Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="tour-your-solution"></a>Zapoznaj się z rozwiązaniem

 1. Szablon projektu tworzy rozwiązanie o pojedynczym ASP.NET Core projekcie o nazwie _MyCoreApp_. Wybierz kartę **Eksplorator rozwiązań** , aby wyświetlić jej zawartość.

    ![ASP.NET Eksplorator rozwiązań w programie Visual Studio dla Razor Pages rozwiązanie o nazwie MyCoreApp](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Rozwiń folder **strony** .

     ![Folder strony w Eksplorator rozwiązań](media/vs-2019/csharp-aspnet-solution-explorer-pages.png)

 1. Wyświetl plik **index. cshtml** w edytorze kodu.

     ![Wyświetlanie pliku index. cshtml w edytorze kodu programu Visual Studio](media/vs-2019/csharp-aspnet-index-cshtml.png)

 1. Każdy plik. cshtml ma skojarzony plik kodu. Aby otworzyć plik kodu w edytorze, rozwiń węzeł **index. cshtml** w Eksplorator rozwiązań i wybierz plik **index.cshtml.cs** .

     ![Wybierz plik Index.cshtml.cs w edytorze kodu programu Visual Studio](media/vs-2019/csharp-aspnet-choose-index-cshtml.png)

 1. Wyświetl plik **index.cshtml.cs** w edytorze kodu.

     ![Wyświetlanie pliku about. cshtml w edytorze kodu programu Visual Studio](media/vs-2019/csharp-aspnet-index-cshtml-editing.png)

 1. Projekt zawiera folder **wwwroot** , który jest katalogiem głównym witryny sieci Web. Rozwiń folder, aby wyświetlić jego zawartość.

     ![folder wwwroot w Eksplorator rozwiązań w programie Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    Możesz umieścić statyczną zawartość witryny, &mdash; taką jak CSS, obrazy i biblioteki JavaScript, &mdash; bezpośrednio w ścieżkach, w których chcesz.

 1. Projekt zawiera również pliki konfiguracyjne, które zarządzają aplikacją sieci Web w czasie wykonywania. Domyślna [Konfiguracja](/aspnet/core/fundamentals/configuration) aplikacji jest przechowywana w *appsettings.jsna*. Można jednak zastąpić te ustawienia przy użyciu *appsettings.Development.json*. Rozwiń **appsettings.jsna** pliku, aby wyświetlić **appsettings.Development.jsna** pliku.

     ![Pliki konfiguracji w Eksplorator rozwiązań w programie Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Uruchamianie, debugowanie i wprowadzanie zmian

1. Wybierz przycisk **IIS Express** w IDE, aby skompilować i uruchomić aplikację w trybie debugowania. (Alternatywnie naciśnij klawisz **F5** lub wybierz polecenie **Debuguj**  >  **Rozpocznij debugowanie** z paska menu.

     ![Wybierz przycisk IIS Express w programie Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Jeśli zostanie wyświetlony komunikat o błędzie z informacją, że **nie można nawiązać połączenia z serwerem sieci Web "IIS Express"**, Zamknij program Visual Studio, a następnie otwórz go przy użyciu opcji **Uruchom jako administrator** w prawym przyciskiem myszy lub w menu kontekstowym. Następnie ponownie uruchom aplikację.
     >
     > Może również zostać wyświetlony komunikat z pytaniem, czy chcesz zaakceptować certyfikat Express SSL protokołu IIS. Aby wyświetlić kod w przeglądarce sieci Web, wybierz opcję **tak**, a następnie wybierz opcję **tak** , jeśli zostanie wyświetlony komunikat ostrzegawczy o zabezpieczeniach.

1. Program Visual Studio uruchamia okno przeglądarki. Na pasku menu powinna zostać wyświetlona **Strona główna** i **prywatność** .

1. Wybierz opcję **prywatność** z paska menu.

   Na stronie **prywatność** w przeglądarce jest renderowany tekst ustawiony w pliku *privacy. cshtml* .

   ![Wyświetlanie tekstu na stronie prywatność](media/vs-2019/csharp-aspnet-browser-page-privacy.png)

1. Wróć do programu Visual Studio, a następnie naciśnij klawisze **Shift + F5** , aby zatrzymać tryb debugowania. Spowoduje to również zamknięcie projektu w oknie przeglądarki.

1. W programie Visual Studio Otwórz pozycję **privacy. cshtml** do edycji. Następnie usuń wyrazy _Użyj tej strony, aby zobaczyć szczegóły zasad zachowania poufności informacji w witrynie_ i w ich miejscu Dodaj wyrazy, które _Ta strona jest w przygotowaniu do @ViewData ["timestamp"]_.

    ![Zmień tekst w pliku privacy. cshtml](media/vs-2019/csharp-aspnet-privacy-cshtml-code-changed.png)

1. Teraz Wprowadźmy zmianę kodu. Wybierz **privacy.cshtml.cs**. Następnie wyczyść `using` dyrektywy w górnej części pliku, używając następującego skrótu:

   Wybierz dowolną z szarych `using` dyrektyw, a żarówka [Quick Actions](../../ide/quick-actions.md) zostanie wyświetlona tuż pod karetką lub na lewym marginesie. Wybierz żarówkę, a następnie umieść wskaźnik myszy nad **Usuń niepotrzebne użycie**.

   ![Usuń niepotrzebne użycie w pliku Privacy.cshtml.cs](media/vs-2019/csharp-aspnet-remove-unnecessary-usings.png)

   Teraz wybierz pozycję **Podgląd zmian** , aby zobaczyć, co zmieni się.

   ![Podgląd zmian](media/vs-2019/csharp-aspnet-preview-changes.png)

   Wybierz pozycję **Zastosuj**. Program Visual Studio usuwa niepotrzebne `using` dyrektywy z pliku.

1. Następnie w `OnGet()` metodzie Zmień treść na następujący kod:

     ```csharp
     public void OnGet()
     {
        string dateTime = DateTime.Now.ToShortDateString();
        ViewData["TimeStamp"] = dateTime;
     }
    ```

1. Zauważ, że dwie faliste podkreślenia są wyświetlane w obszarze **DateTime**. Linie faliste są wyświetlane, ponieważ ten typ nie znajduje się w zakresie.

   ![Błędy oznaczone falistą linią w metodzie OnGet](media/vs-2019/csharp-aspnet-add-new-onget-method.png)

    Otwórz **Lista błędów** pasku narzędzi, aby zobaczyć te same błędy wymienione w tym miejscu. (Jeśli nie widzisz paska narzędzi **Lista błędów** , wybierz pozycję **Widok**  >  **Lista błędów** z górnego paska menu).

   ![Lista błędów w programie Visual Studio](media/vs-2019/csharp-aspnet-error-list.png)

1. Naprawimy to. W edytorze kodu Umieść kursor w dowolnym wierszu zawierającym błąd, a następnie wybierz żarówkę Quick Actions na lewym marginesie. Następnie z menu rozwijanego wybierz pozycję **using System;** , aby dodać tę dyrektywę na początku pliku i usunąć błędy.

   ![Dodaj dyrektywę "using System;"](media/vs-2019/csharp-aspnet-add-usings.png)

1. Naciśnij klawisz **F5** , aby otworzyć projekt w przeglądarce sieci Web.

1. W górnej części witryny sieci Web wybierz pozycję **Ochrona prywatności** , aby wyświetlić zmiany.

   ![Wyświetlanie zaktualizowanej strony prywatności zawierającej wprowadzone zmiany](media/vs-2019/csharp-aspnet-browser-page-privacy-changed.png)

1. Zamknij przeglądarkę sieci Web, naciśnij klawisz **SHIFT** + **F5** , aby zatrzymać tryb debugowania, a następnie zamknij program Visual Studio.
::: moniker-end

## <a name="quick-answers-faq"></a>Szybkie odpowiedzi — często zadawane pytania

Oto krótkie często zadawane pytania, aby wyróżnić niektóre kluczowe pojęcia.

### <a name="what-is-c"></a>Co to jest język C#?

[C#](https://docs.microsoft.com/dotnet/csharp/tour-of-csharp/) to bezpieczny dla typu język programowania i zorientowany obiektowo, zaprojektowany tak, aby był niezawodny i łatwy w nauce.

### <a name="what-is-aspnet-core"></a>Co to jest ASP.NET Core?

ASP.NET Core to platforma typu "open source" i międzyplatformowa do tworzenia aplikacji połączonych z Internetem, takich jak aplikacje i usługi sieci Web. Aplikacje ASP.NET Core mogą być uruchamiane na platformie .NET Core lub .NET Framework. Możesz tworzyć i uruchamiać aplikacje ASP.NET Core na wielu platformach w systemach Windows, Mac i Linux. ASP.NET Core to Open Source w serwisie [GitHub](https://github.com/aspnet/home).

### <a name="what-is-visual-studio"></a>Co to jest Visual Studio?

Program Visual Studio to zintegrowany pakiet programistyczny narzędzi do tworzenia produktywności dla deweloperów. Zastanów się, że program służy do tworzenia programów i aplikacji.

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego samouczka. Mamy nadzieję, że uczysz się nieco na temat języka C#, ASP.NET Core i środowiska IDE programu Visual Studio. Aby dowiedzieć się więcej na temat tworzenia aplikacji lub witryny sieci Web za pomocą języka C# i ASP.NET, przejdź do następujących samouczków:

> [!div class="nextstepaction"]
> [Tworzenie aplikacji sieci Web Razor Pages za pomocą ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1&preserve-view=true)

## <a name="see-also"></a>Zobacz też

[Publikowanie aplikacji sieci Web w Azure App Service przy użyciu programu Visual Studio](../../deployment/quickstart-deploy-to-azure.md)
