---
title: 'Samouczek: wprowadzenie do języka C# i ASP.NET Core'
titleSuffix: ''
description: Dowiedz się, jak utworzyć aplikację ASP.NET Core w języku Visual Studio c# krok po kroku.
ms.custom: seodec18, get-started
ms.date: 02/12/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 58f9604cbecdbe6414e91079a9e0e4691a32b768
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308548"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Samouczek: rozpoczynanie pracy z językami C# i ASP.NET Core w Visual Studio

W tym samouczku na temat tworzenia aplikacji w języku C# za pomocą programu ASP.NET Core przy użyciu programu Visual Studio utworzysz aplikację internetową języka C# ASP.NET Core, dokonasz w nim zmian, poznasz niektóre funkcje środowiska IDE, a następnie uruchomesz aplikację.

## <a name="before-you-begin"></a>Zanim rozpoczniesz

### <a name="install-visual-studio"></a>Instalowanie programu Visual Studio

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/downloads) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2022"

Jeśli jeszcze nie zainstalowano programu Visual Studio 2022 (wersja zapoznawcza), przejdź do strony pobierania programu [Visual Studio 2022 Preview,](https://visualstudio.microsoft.com/vs/preview/vs2022) aby zainstalować ją bezpłatnie.

::: moniker-end

### <a name="update-visual-studio"></a>Aktualizowanie programu Visual Studio

Jeśli masz już zainstalowane Visual Studio, upewnij się, że używasz najnowszej wersji. Aby uzyskać więcej informacji na temat aktualizowania instalacji, zobacz stronę Visual Studio [aktualizacji do najnowszej wersji.](../../install/update-visual-studio.md)

### <a name="choose-your-theme-optional"></a>Wybierz motyw (opcjonalnie)

Ten samouczek zawiera zrzuty ekranu, które używają ciemnego motywu. Jeśli nie używasz ciemnego motywu, ale chcesz, zobacz stronę [Personalizowanie](../../ide/quickstart-personalize-the-ide.md) środowiska IDE i edytora Visual Studio, aby dowiedzieć się, jak to zrobić.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt ASP.NET Core. Typ projektu zawiera wszystkie pliki szablonów potrzebne do w pełni funkcjonalnej witryny internetowej przed dodaniu czegokolwiek!

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **File** New Project > **(Plik nowy** > **projekt).**

3. W **oknie dialogowym Nowy** projekt w okienku po lewej stronie rozwiń pozycję **Visual C#,** rozwiń pozycję **Internet,** a następnie wybierz **pozycję .NET Core.** W środkowym okienku wybierz **pozycję ASP.NET Core Web Application**. Następnie nadaj plikowi *nazwę MyCoreApp* i wybierz przycisk **OK.**

   ![ASP.NET projektu Core Web Application w oknie dialogowym Nowy projekt w Visual Studio IDE](media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

### <a name="add-a-workload-optional"></a>Dodawanie obciążenia (opcjonalnie)

Jeśli nie widzisz szablonu projektu **aplikacji internetowej ASP.NET Core,** możesz go uzyskać, dodając obciążenie tworzenie aplikacji internetowych **ASP.NET aplikacji** internetowych. To obciążenie można dodać na jeden z dwóch następujących sposobów, w zależności od tego, Visual Studio zainstalowano aktualizacje programu 2017 na komputerze.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opcja 1. Użyj okna dialogowego Nowy projekt

1. Wybierz link **Otwórz Instalator programu Visual Studio** w lewym okienku okna **dialogowego Nowy** projekt. (W zależności od ustawień wyświetlania może być konieczne przewinięcie w celu wyświetlenia).

   ![Wybierz link Otwórz Instalator programu Visual Studio w oknie dialogowym Nowy projekt](../media/open-visual-studio-installer-mycoreapp.png)

1. Uruchomienie Instalator programu Visual Studio. Wybierz obciążenie **tworzenie aplikacji ASP.NET sieci Web,** a następnie wybierz pozycję **Modyfikuj.**

   ![Międzyplatformowe obciążenie programowe platformy .NET Core w Instalator programu Visual Studio](../media/tutorial-aspnet-workload.png)

   (Może być konieczne zamknięcie Visual Studio, zanim będzie można kontynuować instalowanie nowego obciążenia).

#### <a name="option-2-use-the-tools-menu-bar"></a>Opcja 2. Korzystanie z paska menu Narzędzia

1. Anuluj poza **oknie dialogowym Nowy** projekt. Następnie na górnym pasku menu wybierz pozycję **Narzędzia** Pobierz  >  **narzędzia i funkcje.**

1. Uruchomienie Instalator programu Visual Studio. Wybierz obciążenie **tworzenie aplikacji ASP.NET sieci Web,** a następnie wybierz pozycję **Modyfikuj.**

   (Może być konieczne zamknięcie Visual Studio, zanim będzie można kontynuować instalowanie nowego obciążenia).

### <a name="add-a-project-template"></a>Dodawanie szablonu projektu

1. W **oknie dialogowym Nowa ASP.NET Core Web Application** wybierz szablon projektu **Aplikacja** internetowa.

1. Sprawdź, **ASP.NET Core 2.1** pojawia się w górnym menu rozwijanych. Następnie wybierz przycisk **OK.**

   ![Okno dialogowe ASP.NET Core Web Application](media/new-project-csharp-aspnet-razor-web-app.png)

   > [!NOTE]
   > Jeśli nie widzisz aplikacji **ASP.NET Core 2.1** z górnego menu rozwijanego, upewnij się, że używasz najnowszej wersji Visual Studio. Aby uzyskać więcej informacji na temat aktualizowania instalacji, zobacz stronę Visual Studio [aktualizacji do najnowszej wersji.](../../install/update-visual-studio.md)

::: moniker-end

::: moniker range=">=vs-2019"

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt.**

   :::image type="content" source="../../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="Wyświetlanie okna &quot;Tworzenie nowego projektu&quot;":::

1. W **oknie Tworzenie nowego projektu** wybierz pozycję **C#** z listy Język. Następnie wybierz pozycję **Windows** z listy Platforma i pozycję **Internet** z listy typów projektów.

      Po zastosowaniu filtrów języka, platformy i typu projektu wybierz szablon ASP.NET **Core Web App,** a następnie wybierz pozycję **Dalej.**

   :::image type="content" source="./media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="Wybieranie szablonu języka C# dla aplikacji internetowej ASP.NET Core":::

   > [!NOTE]
   > Jeśli nie widzisz szablonu aplikacji **internetowej ASP.NET Core,** możesz go zainstalować w oknie **Tworzenie nowego** projektu. W **komunikacie Nie można znaleźć tego,** czego szukasz? wybierz link Zainstaluj więcej narzędzi **i** funkcji.
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" w komunikacie "Nie można znaleźć tego, czego szukasz" w oknie "Tworzenie nowego projektu"](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w witrynie Instalator programu Visual Studio wybierz obciążenie **tworzenie aplikacji ASP.NET sieci Web.**
   >
   > ![Międzyplatformowe obciążenie programowe platformy .NET Core w Instalator programu Visual Studio](../../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Jeśli zostanie wyświetlony monit o zapisanie pracy, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze["Tworzenie projektu".](#create-a-project)

1. W **oknie Konfigurowanie nowego** projektu wpisz lub wprowadź *MyCoreApp* w **polu Nazwa** projektu. Następnie wybierz pozycję **Dalej.**

   :::image type="content" source="./media/vs-2019/csharp-name-your-aspnet-app.png" alt-text="W oknie &quot;Konfigurowanie nowego projektu&quot; nadaj projektowi nazwę &quot;MyCoreApp&quot;":::

1. W **oknie Dodatkowe informacje** sprawdź, **czy program .NET Core 3.1** jest wyświetlany w górnym menu rozwijanych. Pamiętaj, że możesz włączyć obsługę platformy Docker, zaznaczając to pole wyboru. Możesz również dodać obsługę uwierzytelniania, klikając przycisk Zmień uwierzytelnianie. W tym miejscu można wybrać jedną z opcji:
    - Brak: brak uwierzytelniania.
    - Indywidualne konta: są one przechowywane w lokalnej bazie danych lub bazie danych opartej na platformie Azure.
    - Platforma tożsamości firmy Microsoft: ta opcja używa usługi Active Directory, Azure AD Microsoft 365 do uwierzytelniania.
    - Windows: odpowiednie dla aplikacji intranetowych.
    
    Pozostaw **pole Włącz platformę Docker** niezaznaczone, a następnie wybierz opcję **Brak w** polu Typ uwierzytelniania. Następnie wybierz przycisk **Utwórz**.

   :::image type="content" source="./media/vs-2019/aspnet-core-additional-information.png" alt-text="W oknie &quot;Dodatkowe informacje&quot; upewnij się, że wybrano opcję .NET Core 3.1 i pozostaw wszystkie wartości domyślne":::

   Visual Studio spowoduje otwarcie nowego projektu.

::: moniker-end

### <a name="about-your-solution"></a>Informacje o rozwiązaniu

To rozwiązanie jest zgodna ze **wzorcem projektowym strony Razor.** Różni się on od wzorca projektowego [Model-View-Controller (MVC)](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x&preserve-view=true) tym, że usprawnione jest dołączanie kodu modelu i kontrolera do samej strony Razor.

::: moniker range="vs-2017"
## <a name="tour-your-solution"></a>Przewodnik po rozwiązaniu

 1. Szablon projektu tworzy rozwiązanie z pojedynczym projektem ASP.NET Core o nazwie _MyCoreApp._ Wybierz **kartę Eksplorator rozwiązań,** aby wyświetlić jej zawartość.

    ![ASP.NET Eksplorator rozwiązań w Visual Studio for Razor Pages o nazwie MyCoreApp](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Rozwiń folder **Strony,** a następnie rozwiń *pozycję About.cshtml.*

     ![Plik About.cshtml w Eksplorator rozwiązań w Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. Wyświetl plik **About.cshtml** w edytorze kodu.

     ![Zrzut ekranu przedstawiający pierwsze dziesięć wierszy pliku About.cshtml w Visual Studio edytorze kodu.](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. Wybierz plik **About.cshtml.cs.**

     ![Wybierz plik About.cshtml.cs w Visual Studio edytorze kodu](media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. Wyświetl plik **About.cshtml.cs** w edytorze kodu.

     ![Zrzut ekranu przedstawiający pierwsze 18 wierszy pliku About.cshtml.cs w Visual Studio edytorze kodu. ](media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. Projekt zawiera folder **wwwroot,** który jest katalogiem głównym witryny internetowej. Rozwiń folder, aby wyświetlić jego zawartość.

     ![folder wwwroot w Eksplorator rozwiązań w Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    Zawartość witryny statycznej, taką jak CSS, obrazy i biblioteki Języka JavaScript, można umieszczać bezpośrednio w ścieżkach, &mdash; &mdash; w których mają być.

 1. Projekt zawiera również pliki konfiguracji, które zarządzają aplikacją internetową w czasie uruchamiania. Domyślna konfiguracja [aplikacji jest](/aspnet/core/fundamentals/configuration) przechowywana wappsettings.js *na stronie*. Te ustawienia można jednak przesłonić przy użyciu *appsettings.Development.jsna .* Rozwiń **appsettings.jspliku,** aby wyświetlić **appsettings.Development.jspliku.**

     ![Pliki konfiguracji w Eksplorator rozwiązań w Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Uruchamianie, debugowanie i wprowadzanie zmian

1. Wybierz przycisk **IIS Express** w idee, aby skompilować i uruchomić aplikację w trybie debugowania. (Ewentualnie naciśnij klawisz **F5** lub wybierz pozycję **Debuguj.**  >  **Rozpocznij debugowanie** na pasku menu).

     ![Wybierz przycisk IIS Express w Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Jeśli zostanie wyświetlony komunikat o błędzie Nie można nawiązać połączenia z serwerem internetowym **"IIS Express",** zamknij program Visual Studio, a następnie otwórz go przy użyciu opcji Uruchom jako **administrator** z menu kontekstowego lub kliknij prawym przyciskiem myszy. Następnie ponownie uruchom aplikację.
     >
     > Może również zostać wyświetlony komunikat z pytaniem, czy chcesz zaakceptować certyfikat SSL Express usług IIS. Aby wyświetlić kod w przeglądarce internetowej, wybierz pozycję **Tak,** a następnie wybierz pozycję **Tak,** jeśli zostanie wyświetlony komunikat z ostrzeżeniem o zabezpieczeniach.

1. Visual Studio zostanie otwarte okno przeglądarki. Na pasku menu powinny zostać  **wtedy wyświetlony strony Strona** **główna,** Informacje i Kontakt. (Jeśli nie, wybierz element menu "hamburger", aby je wyświetlić).

    ![Wybierz element menu "hamburger" na pasku menu w aplikacji internetowej](media/csharp-aspnet-razor-browser-page.png)

1. Wybierz **pozycję Informacje** na pasku menu.

   ![Wybierz pozycję Informacje na pasku menu okna przeglądarki dla aplikacji](media/csharp-aspnet-razor-browser-page-about-menu.png)

   Między innymi strona **Informacje** w przeglądarce renderuje tekst ustawiony w pliku *About.cshtml.*

   ![Wyświetlanie tekstu na stronie Informacje](media/csharp-aspnet-razor-browser-page-about.png)

1. Wróć do Visual Studio, a następnie naciśnij **klawisze Shift+F5,** aby zatrzymać tryb debugowania. To również zamyka projekt w oknie przeglądarki.

1. W Visual Studio wybierz pozycję **About.cshtml.** Następnie usuń wyraz _additional i_ w jego miejscu dodaj _wyrazy plik i katalog_.

    ![Zmienianie tekstu w pliku About.cshtml](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code-changed.png)

1. Wybierz **pozycję About.cshtml.cs.** Następnie wyczyść dyrektywy `using` w górnej części pliku przy użyciu następującego skrótu:

   Wybierz dowolną wyszarzone `using` dyrektywy, [](../../ide/quick-actions.md) a żarówka Szybkie akcje pojawi się tuż pod lewą Wybierz żarówkę, a następnie wybierz **pozycję Usuń niepotrzebne usings**.

   ![Usuń niepotrzebne usings w pliku About.cshtml.cs](media/csharp-aspnet-razor-remove-unnecessary-usings.png)

     Visual Studio usuwa niepotrzebne dyrektywy `using` z pliku.

1. Następnie w metodzie zmień treść na `OnGet()` następujący kod:

     ```csharp
     public void OnGet()
     {
         string directory = Environment.CurrentDirectory;
         Message = String.Format("Your directory is {0}.", directory);
     }
    ```

1. Zwróć uwagę, że dwa podkreślenia faliste są wyświetlane w obszarze **Environment (Środowisko)** i **String (Ciąg).** Zostaną wyświetlone faliste podkreślenia, ponieważ te typy nie są w zakresie.

   ![Błędy oznaczone falistym podkreśleniem w metodzie OnGet](media/csharp-aspnet-razor-add-new-on-get-method.png)

    Otwórz pasek **narzędzi Lista błędów,** aby zobaczyć tam te same błędy. (Jeśli nie widzisz paska narzędzi Lista **błędów,** wybierz pozycję **Widok**  >  **Lista błędów** na górnym pasku menu).

   ![Lista błędów w Visual Studio](media/csharp-aspnet-razor-error-list.png)

1. Naprawmy to. W edytorze kodu umieść kursor w każdym wierszu zawierającym błąd, a następnie wybierz żarówkę Szybkie akcje na lewym marginesie. Następnie z menu rozwijanego wybierz pozycję **using System;** aby dodać tę dyrektywę na początku pliku i usunąć błędy.

   ![Dodawanie dyrektywy "using System;"](media/csharp-aspnet-razor-add-usings.png)

1. Naciśnij **klawisze Ctrl** + **S,** aby zapisać zmiany, a następnie naciśnij **klawisz F5,** aby otworzyć projekt w przeglądarce internetowej.

1. W górnej części witryny internetowej wybierz pozycję Informacje, **aby** wyświetlić zmiany.

   ![Wyświetl zaktualizowaną stronę Informacje, która zawiera wprowadzone zmiany](media/csharp-aspnet-razor-browser-page-about-changed.png)

1. Zamknij przeglądarkę internetową, naciśnij klawisz + **Shift F5,** aby zatrzymać tryb debugowania, a następnie zamknij Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="tour-your-solution"></a>Przewodnik po rozwiązaniu

 1. Szablon projektu tworzy rozwiązanie z pojedynczym projektem ASP.NET Core o nazwie _MyCoreApp._ Wybierz **kartę Eksplorator rozwiązań,** aby wyświetlić jej zawartość.

    ![ASP.NET Eksplorator rozwiązań w Visual Studio rozwiązania Razor Pages o nazwie MyCoreApp](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Rozwiń folder **Strony.**

     ![Folder Strony w Eksplorator rozwiązań](media/vs-2019/csharp-aspnet-solution-explorer-pages.png)

 1. Wyświetl plik **Index.cshtml** w edytorze kodu.

     ![Wyświetlanie pliku Index.cshtml w edytorze Visual Studio kodu](media/vs-2019/csharp-aspnet-index-cshtml.png)

 1. Każdy plik cshtml ma skojarzony plik kodu. Aby otworzyć plik kodu w edytorze, rozwiń węzeł **Index.cshtml** w Eksplorator rozwiązań i wybierz plik **Index.cshtml.cs.**

     ![Wybierz plik Index.cshtml.cs w edytorze Visual Studio kodu](media/vs-2019/csharp-aspnet-choose-index-cshtml.png)

 1. Wyświetl plik **Index.cshtml.cs** w edytorze kodu.

     ![Wyświetlanie pliku About.cshtml w edytorze Visual Studio kodu](media/vs-2019/csharp-aspnet-index-cshtml-editing.png)

 1. Projekt zawiera folder **wwwroot,** który jest katalogiem głównym witryny internetowej. Rozwiń folder, aby wyświetlić jego zawartość.

     ![folder wwwroot w Eksplorator rozwiązań w Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    Zawartość statyczną witryny, taką jak CSS, obrazy i biblioteki Języka JavaScript, można umieszczać bezpośrednio w ścieżkach, &mdash; &mdash; w których mają być.

 1. Projekt zawiera również pliki konfiguracji, które zarządzają aplikacją internetową w czasie uruchamiania. Domyślna konfiguracja [aplikacji jest](/aspnet/core/fundamentals/configuration) przechowywana wappsettings.js *w programie*. Te ustawienia można jednak przesłonić przy użyciuappsettings.Development.js *na .* Rozwiń **appsettings.jspliku,** aby wyświetlić **appsettings.Development.jspliku.**

     ![Pliki konfiguracji w Eksplorator rozwiązań w Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Uruchamianie, debugowanie i wprowadzanie zmian

1. Wybierz przycisk **IIS Express** w idee, aby skompilować i uruchomić aplikację w trybie debugowania. (Ewentualnie naciśnij klawisz **F5** lub wybierz pozycję **Debuguj.**  >  **Rozpocznij debugowanie** na pasku menu).

     ![Wybierz przycisk IIS Express w Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Jeśli zostanie wyświetlony komunikat o błędzie Nie można nawiązać połączenia z serwerem internetowym **"IIS Express",** zamknij program Visual Studio, a następnie otwórz go przy użyciu opcji Uruchom jako **administrator** z menu kontekstowego lub kliknij prawym przyciskiem myszy. Następnie ponownie uruchom aplikację.
     >
     > Może również zostać wyświetlony komunikat z pytaniem, czy chcesz zaakceptować certyfikat SSL Express usług IIS. Aby wyświetlić kod w przeglądarce internetowej, wybierz pozycję **Tak,** a następnie wybierz pozycję **Tak,** jeśli zostanie wyświetlony komunikat z ostrzeżeniem o zabezpieczeniach.

1. Visual Studio zostanie otwarte okno przeglądarki. Na pasku menu powinny **zostać** **wtedy wyświetlony** strony Strona główna i Prywatność.

1. Wybierz **pozycję Prywatność** na pasku menu.

   Strona **Prywatność** w przeglądarce renderuje tekst ustawiony w pliku *Privacy.cshtml.*

   ![Wyświetlanie tekstu na stronie Prywatność](media/vs-2019/csharp-aspnet-browser-page-privacy.png)

1. Wróć do Visual Studio, a następnie naciśnij **klawisze Shift+F5,** aby zatrzymać tryb debugowania. To również zamyka projekt w oknie przeglądarki.

1. W Visual Studio otwórz do edycji **pliku Privacy.cshtml.** Następnie usuń wyrazy Użyj tej strony, aby szczegółowo opisano zasady ochrony prywatności witryny i w jej miejscu dodać wyrazy Ta strona jest w trakcie budowy _@ViewData ["Sygnatura czasowa"]_. 

    ![Zmienianie tekstu w pliku Privacy.cshtml](media/vs-2019/csharp-aspnet-privacy-cshtml-code-changed.png)

1. Teraz dokonajmy zmiany kodu. Wybierz **pozycję Privacy.cshtml.cs.** Następnie wyczyść dyrektywy `using` w górnej części pliku przy użyciu następującego skrótu:

   Wybierz dowolną wyszarzone `using` dyrektywy, [](../../ide/quick-actions.md) a żarówka Szybkie akcje pojawi się tuż pod lewą Wybierz żarówkę, a następnie najedź kursorem na pozycję **Usuń niepotrzebne usings**.

   ![Usuń niepotrzebne usings w pliku Privacy.cshtml.cs](media/vs-2019/csharp-aspnet-remove-unnecessary-usings.png)

   Teraz wybierz **pozycję Podgląd zmian,** aby zobaczyć, co się zmieni.

   ![Podgląd zmian](media/vs-2019/csharp-aspnet-preview-changes.png)

   Wybierz pozycję **Zastosuj**. Visual Studio usuwa niepotrzebne dyrektywy `using` z pliku.

1. Następnie w metodzie zmień treść na `OnGet()` następujący kod:

     ```csharp
     public void OnGet()
     {
        string dateTime = DateTime.Now.ToShortDateString();
        ViewData["TimeStamp"] = dateTime;
     }
    ```

1. Zwróć uwagę, że dwa podkreślenia faliste pojawiają się w obszarze **DateTime**. Zostaną wyświetlone faliste podkreślenia, ponieważ ten typ nie znajduje się w zakresie.

   ![Błędy oznaczone falistym podkreśleniem w metodzie OnGet](media/vs-2019/csharp-aspnet-add-new-onget-method.png)

    Otwórz pasek **narzędzi Lista błędów,** aby zobaczyć tam te same błędy. (Jeśli nie widzisz paska narzędzi Lista **błędów,** wybierz pozycję **Widok**  >  **Lista błędów** na górnym pasku menu).

   ![Lista błędów w Visual Studio](media/vs-2019/csharp-aspnet-error-list.png)

1. Naprawmy to. W edytorze kodu umieść kursor w każdym wierszu zawierającym błąd, a następnie wybierz żarówkę Szybkie akcje na lewym marginesie. Następnie z menu rozwijanego wybierz pozycję **using System;** aby dodać tę dyrektywę na początku pliku i usunąć błędy.

   ![Dodawanie dyrektywy "using System;"](media/vs-2019/csharp-aspnet-add-usings.png)

1. Naciśnij **klawisz F5,** aby otworzyć projekt w przeglądarce internetowej.

1. W górnej części witryny internetowej wybierz pozycję **Prywatność,** aby wyświetlić zmiany.

   ![Wyświetl zaktualizowaną stronę Prywatność, która zawiera wprowadzone zmiany](media/vs-2019/csharp-aspnet-browser-page-privacy-changed.png)

1. Zamknij przeglądarkę internetową, naciśnij klawisz + **Shift F5,** aby zatrzymać tryb debugowania, a następnie zamknij Visual Studio.
::: moniker-end

## <a name="quick-answers-faq"></a>Szybkie odpowiedzi — często zadawane pytania

Poniżej znajdziesz krótkie często zadawane pytania dotyczące niektórych kluczowych pojęć.

### <a name="what-is-c"></a>Co to jest język C#?

[C#](https://docs.microsoft.com/dotnet/csharp/tour-of-csharp/) to bezpieczny pod kątem typów i zorientowany obiektowo język programowania zaprojektowany tak, aby był niezawodny i łatwy do nauczenia się.

### <a name="what-is-aspnet-core"></a>Co to jest ASP.NET Core?

ASP.NET Core to międzyplatformowa platforma typu open source do tworzenia aplikacji połączonych z Internetem, takich jak aplikacje i usługi internetowe. ASP.NET Core można uruchamiać na .NET Core lub w .NET Framework. Możesz tworzyć i uruchamiać aplikacje ASP.NET Core na wiele platform w systemach Windows, Mac i Linux. ASP.NET Core jest open source w [witrynie GitHub.](https://github.com/aspnet/home)

### <a name="what-is-visual-studio"></a>Co to jest Visual Studio?

Visual Studio to zintegrowany pakiet programistów narzędzi zwiększających produktywność dla deweloperów. Pomyśl o nim jak o programie, który umożliwia tworzenie programów i aplikacji.

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego samouczka! Mamy nadzieję, że wiesz już trochę o języku C#, ASP.NET Core i Visual Studio IDE. Aby dowiedzieć się więcej na temat tworzenia aplikacji internetowej lub witryny internetowej w języku C# i ASP.NET, przejdź do następujących samouczków:

> [!div class="nextstepaction"]
> [Tworzenie aplikacji Razor Pages za pomocą programu ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1&preserve-view=true)

## <a name="see-also"></a>Zobacz też

[Publikowanie aplikacji internetowej w witrynie Azure App Service przy użyciu Visual Studio](../../deployment/quickstart-deploy-to-azure.md)
