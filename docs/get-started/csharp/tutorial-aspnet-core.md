---
title: 'Samouczek: Wprowadzenie do języka C# i ASP.NET Core'
titleSuffix: ''
description: Dowiedz się, jak utworzyć ASP.NET podstawową aplikację sieci web w programie Visual Studio w języku C#, krok po kroku.
ms.custom: seodec18, get-started
ms.date: 05/29/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: ef41e28d994f27f66f616623d1b2c9798b65ede4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580049"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Samouczek: Wprowadzenie do języka C# i ASP.NET Core w programie Visual Studio

W tym samouczku na temat rozwoju języka C# z ASP.NET Core za pomocą programu Visual Studio utworzysz aplikację sieci web ASP.NET Języka C# ASP.NET, wprowadzisz do niej zmiany, eksplorujesz niektóre funkcje IDE, a następnie uruchomisz aplikację.

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="install-visual-studio"></a>Instalacja programu Visual Studio

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie.

::: moniker-end

### <a name="update-visual-studio"></a>Aktualizowanie programu Visual Studio

Jeśli program Visual Studio został już zainstalowany, upewnij się, że jest uruchomiona najnowsza wersja. Aby uzyskać więcej informacji na temat aktualizowania instalacji, zobacz [Update Visual Studio do najnowszej](../../install/update-visual-studio.md) wersji strony.

### <a name="choose-your-theme-optional"></a>Wybierz motyw (opcjonalnie)

Ten samouczek zawiera zrzuty ekranu, które używają ciemnego motywu. Jeśli nie używasz ciemnego motywu, ale chcesz, zobacz [Personalizuj ide programu Visual Studio i edytora](../../ide/quickstart-personalize-the-ide.md) strony, aby dowiedzieć się, jak to zrobić.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt ASP.NET Core. Typ projektu zawiera wszystkie pliki szablonów potrzebne do w pełni funkcjonalnej strony internetowej, zanim jeszcze cokolwiek dodasz!

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

3. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń rozwiń pozycję **Visual C#**, rozwiń pozycję **Sieć Web**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **ASP.NET Core Web Application**. Następnie nazwij plik *MyCoreApp* i wybierz **przycisk OK**.

   ![ASP.NET szablon projektu podstawowej aplikacji sieci Web w oknie dialogowym Nowy projekt w programie Visual Studio IDE](media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

### <a name="add-a-workload-optional"></a>Dodawanie obciążenia (opcjonalnie)

Jeśli nie widzisz szablonu projektu **ASP.NET Core Web Application,** możesz go uzyskać, dodając ASP.NET i obciążenia **tworzenia sieci Web.** To obciążenie można dodać w jeden z dwóch następujących sposobów, w zależności od tego, które aktualizacje programu Visual Studio 2017 są zainstalowane na komputerze.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opcja 1: Korzystanie z okna dialogowego Nowy projekt

1. Wybierz łącze **Otwórz Instalatora programu Visual Studio** w lewym okienku okna dialogowego Nowy **projekt.** (W zależności od ustawień wyświetlania może być konieczne przewinięcie, aby je wyświetlić).

   ![Wybieranie łącza Instalator programu Visual Studio w oknie dialogowym Nowy projekt](../media/open-visual-studio-installer-mycoreapp.png)

1. Uruchamia instalator programu Visual Studio. Wybierz ASP.NET i obciążenia **tworzenia stron internetowych,** a następnie wybierz pozycję **Modyfikuj**.

   ![Wieloplatformowe obciążenie programowe programu .NET Core w Instalatorze programu Visual Studio](../media/tutorial-aspnet-workload.png)

   (Przed kontynuowaniem instalowania nowego obciążenia może być jeszcze trzeba zamknąć program Visual Studio).

#### <a name="option-2-use-the-tools-menu-bar"></a>Opcja 2: Użyj paska menu Narzędzia

1. Anulowanie z okna dialogowego **Nowy projekt.** Następnie na górnym pasku menu wybierz pozycję **Narzędzia** > **Pobierz narzędzia i funkcje**.

1. Uruchamia instalator programu Visual Studio. Wybierz ASP.NET i obciążenia **tworzenia stron internetowych,** a następnie wybierz pozycję **Modyfikuj**.

   (Przed kontynuowaniem instalowania nowego obciążenia może być jeszcze trzeba zamknąć program Visual Studio).

### <a name="add-a-project-template"></a>Dodawanie szablonu projektu

1. W oknie dialogowym **Nowa ASP.NET Podstawowa aplikacja sieci Web** wybierz szablon projektu aplikacji sieci **Web.**

1. Sprawdź, czy **ASP.NET Core 2.1** pojawia się w górnym menu rozwijanym. Następnie wybierz przycisk **OK**.

   ![Okno dialogowe Nowa ASP.NET Core Aplikacji Sieci Web](media/new-project-csharp-aspnet-razor-web-app.png)

   > [!NOTE]
   > Jeśli nie widzisz **ASP.NET Core 2.1** z menu rozwijanego, upewnij się, że jest uruchomiona najnowsza wersja programu Visual Studio. Aby uzyskać więcej informacji na temat aktualizowania instalacji, zobacz [Update Visual Studio do najnowszej](../../install/update-visual-studio.md) wersji strony.

::: moniker-end

::: moniker range="vs-2019"

1. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetlanie okna "Tworzenie nowego projektu"](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Utwórz nowy projekt** wprowadź lub wpisz *ASP.NET* w polu wyszukiwania. Następnie wybierz **pozycję C#** z listy Język, a następnie wybierz pozycję **Windows** z listy Platforma.

   Po zastosowaniu filtrów języka i platformy wybierz szablon **ASP.NET Core Web Application,** a następnie wybierz pozycję **Dalej**.

   ![Wybieranie szablonu języka C# dla ASP.NET Core Web Application](./media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **ASP.NET Core Web Application,** możesz go zainstalować w oknie **Utwórz nowy projekt.** W komunikacie **Nie znajdowanie tego, czego szukasz?** **Install more tools and features**
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "Nie znajdując tego, czego szukasz" w oknie "Utwórz nowy projekt"](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w Instalatorze programu Visual Studio wybierz ASP.NET i obciążenia **tworzenia sieci Web.**
   >
   > ![Wieloplatformowe obciążenie programowe programu .NET Core w Instalatorze programu Visual Studio](../../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalatorze programu Visual Studio. Jeśli zostanie wyświetlony monit o zapisanie pracy, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze["Utwórz projekt".](#create-a-project)

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *myCoreApp* w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

   ![w oknie "Skonfiguruj nowy projekt" nazwij swój projekt "MyCoreApp"](./media/vs-2019/csharp-name-your-aspnet-mycoreapp-project.png)

1. W oknie **Utwórz nową ASP.NET podstawową aplikację sieci Web** sprawdź, czy **ASP.NET Core 3.0** jest wyświetlany w górnym menu rozwijanym. Następnie wybierz aplikację **sieci Web**, która zawiera przykładowe strony Razor. Następnie wybierz pozycję **Utwórz**.

   ![Okno "Tworzenie nowej ASP.NET podstawowej aplikacji sieci Web"](./media/vs-2019/csharp-create-aspnet-razor-pages-app.png)

   Visual Studio otwiera nowy projekt.

::: moniker-end

### <a name="about-your-solution"></a>Informacje o rozwiązaniu

To rozwiązanie jest zgodne ze wzorcem projektowym **strony Razor.** Jest inny niż wzorzec projektu [Model-View-Controller (MVC),](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x) ponieważ jest usprawniony w celu uwzględnienia modelu i kodu kontrolera w samej stronie Razor.

::: moniker range="vs-2017"
## <a name="tour-your-solution"></a>Poekslij swoje rozwiązanie

 1. Szablon projektu tworzy rozwiązanie z jednym projektem ASP.NET Core o nazwie _MyCoreApp_. Wybierz kartę **Eksplorator rozwiązań,** aby wyświetlić jej zawartość.

    ![ASP.NET Eksploratora rozwiązań w programie Visual Studio dla stron razor o nazwie MyCoreApp](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Rozwiń folder **Strony,** a następnie rozwiń pozycję *About.cshtml*.

     ![Plik About.cshtml w Eksploratorze rozwiązań w programie Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. Wyświetl plik **About.cshtml** w edytorze kodu.

     ![Wyświetlanie pliku About.cshtml w edytorze kodu programu Visual Studio](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. Wybierz plik **About.cshtml.cs.**

     ![Wybieranie pliku About.cshtml.cs w edytorze kodu programu Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. Wyświetl plik **About.cshtml.cs** w edytorze kodu.

     ![Wyświetlanie pliku About.cshtml w edytorze kodu programu Visual Studio](media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. Projekt zawiera folder **wwwroot,** który jest głównym źródłem twojej witryny. Rozwiń folder, aby wyświetlić jego zawartość.

     ![folder wwwroot w Eksploratorze rozwiązań w programie Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    Statyczną zawartość&mdash;witryny, taką jak CSS, obrazy&mdash;i biblioteki JavaScript, można umieszczać bezpośrednio w ścieżkach w miejscu, w którym chcesz.

 1. Projekt zawiera również pliki konfiguracyjne, które zarządzają aplikacją sieci web w czasie wykonywania. Domyślna [konfiguracja](/aspnet/core/fundamentals/configuration) aplikacji jest przechowywana w *pliku appsettings.json*. Można jednak zastąpić te ustawienia za pomocą *ustawień aplikacji. Development.json*. Rozwiń plik **appsettings.json,** aby wyświetlić **appsettings. Development.json.**

     ![Pliki konfiguracyjne w Eksploratorze rozwiązań w programie Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Uruchamianie, debugowanie i wprowadzanie zmian

1. Wybierz przycisk **IIS Express** w IDE do tworzenia i uruchamiania aplikacji w trybie debugowania. (Alternatywnie naciśnij **klawisz F5**lub wybierz z paska menu polecenie**Debug start debugowania).** **Debug** > 

     ![Wybieranie przycisku IIS Express w programie Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Jeśli zostanie wyświetlony komunikat o błędzie z informacją Nie można połączyć się z **serwerem sieci Web "IIS Express",** zamknij program Visual Studio, a następnie otwórz go za pomocą opcji **Uruchom jako administrator** z menu po kliknięciu prawym przyciskiem myszy lub w menu kontekstowym. Następnie uruchom aplikację ponownie.
     >
     > Może również pojawić się komunikat z pytaniem, czy chcesz zaakceptować certyfikat IIS SSL Express. Aby wyświetlić kod w przeglądarce internetowej, wybierz pozycję **Tak**, a następnie wybierz pozycję **Tak,** jeśli zostanie wyświetlony komunikat ostrzegawczy o zabezpieczeniach uzupełniających.

1. Program Visual Studio uruchamia okno przeglądarki. Następnie na pasku menu powinny zostać wyświetlne strony **Narzędzia główne,** **Informacje**i **Kontakt.** (Jeśli tego nie zrobisz, wybierz pozycję menu "hamburger", aby je wyświetlić).

    ![Wybierz pozycję menu "hamburger" z paska menu w aplikacji internetowej](media/csharp-aspnet-razor-browser-page.png)

1. Z paska menu wybierz **opcję Informacje.**

   ![Wybieranie opcji Informacje na pasku menu okna przeglądarki dla aplikacji](media/csharp-aspnet-razor-browser-page-about-menu.png)

   Między innymi strona **Informacje** w przeglądarce renderuje tekst ustawiony w pliku *About.cshtml.*

   ![Wyświetlanie tekstu na stronie Informacje](media/csharp-aspnet-razor-browser-page-about.png)

1. Wróć do programu Visual Studio, a następnie naciśnij **klawisze Shift+F5,** aby zatrzymać tryb debugowania. Spowoduje to również zamknięcie projektu w oknie przeglądarki.

1. W programie Visual Studio wybierz pozycję **About.cshtml**. Następnie usuń słowo _dodatkowe_ i na jego miejscu dodaj _słowo plik i katalog_.

    ![Zmienianie tekstu w pliku About.cshtml](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code-changed.png)

1. Wybierz **About.cshtml.cs**. Następnie wyczyść `using` dyrektywy w górnej części pliku za pomocą następującego skrótu:

   Wybierz dowolną z `using` wyszarzonych dyrektyw, a żarówka Szybkie [akcje](../../ide/quick-actions.md) pojawi się tuż pod cieszką lub na lewym marginesie. Wybierz żarówkę, a następnie wybierz pozycję **Usuń niepotrzebne użycie**.

   ![Usuwanie niepotrzebnych użycia w pliku About.cshtml.cs](media/csharp-aspnet-razor-remove-unnecessary-usings.png)

     Visual Studio usuwa `using` niepotrzebne dyrektywy z pliku.

1. Następnie w `OnGet()` metodzie zmień treść na następujący kod:

     ```csharp
     public void OnGet()
     {
         string directory = Environment.CurrentDirectory;
         Message = String.Format("Your directory is {0}.", directory);
     }
    ```

1. Zwróć uwagę, że w obszarze **Środowisko** i **Ciąg**pojawią się dwa faliste podkreślenia . Faliste podkreślenia pojawiają się, ponieważ te typy nie są w zakresie.

   ![Błędy oznaczone falistymi podkreśleniami w metodzie OnGet](media/csharp-aspnet-razor-add-new-on-get-method.png)

    Otwórz pasek **narzędzi Lista błędów,** aby wyświetlić te same błędy wymienione na liście. (Jeśli nie widzisz **paska narzędzi Lista błędów,** wybierz pozycję **Wyświetl** > **listę błędów** z górnego paska menu).

   ![Lista błędów w programie Visual Studio](media/csharp-aspnet-razor-error-list.png)

1. Naprawmy to. W edytorze kodu umieść kursor w każdym wierszu zawierającym błąd, a następnie wybierz żarówkę Szybkie akcje na lewym marginesie. Następnie z menu rozwijanego wybierz **pozycję System;** aby dodać tę dyrektywę do górnej części pliku i rozwiązać błędy.

   ![Dodaj dyrektywę "using System;"](media/csharp-aspnet-razor-add-usings.png)

1. Naciśnij **klawisz Ctrl**+**S,** aby zapisać zmiany, a następnie naciśnij **klawisz F5,** aby otworzyć projekt w przeglądarce internetowej.

1. W górnej części witryny sieci Web wybierz pozycję **Informacje,** aby wyświetlić zmiany.

   ![Wyświetl zaktualizowaną stronę Informacje zawierającą wprowadzone zmiany](media/csharp-aspnet-razor-browser-page-about-changed.png)

1. Zamknij przeglądarkę internetową, naciśnij **klawisz Shift**+**F5,** aby zatrzymać tryb debugowania, a następnie zamknij program Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="tour-your-solution"></a>Poekslij swoje rozwiązanie

 1. Szablon projektu tworzy rozwiązanie z jednym projektem ASP.NET Core o nazwie _MyCoreApp_. Wybierz kartę **Eksplorator rozwiązań,** aby wyświetlić jej zawartość.

    ![ASP.NET Eksploratora rozwiązań w programie Visual Studio dla stron razor o nazwie MyCoreApp](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Rozwiń folder **Strony.**

     ![Folder Strony w Eksploratorze rozwiązań](media/vs-2019/csharp-aspnet-solution-explorer-pages.png)

 1. Wyświetl plik **Index.cshtml** w edytorze kodu.

     ![Wyświetlanie pliku Index.cshtml w edytorze kodu programu Visual Studio](media/vs-2019/csharp-aspnet-index-cshtml.png)

 1. Każdy plik cshtml ma skojarzony plik kodu. Aby otworzyć plik kodu w edytorze, rozwiń węzeł **Index.cshtml** w Eksploratorze rozwiązań i wybierz **Index.cshtml.cs** plik.

     ![Wybieranie pliku Index.cshtml.cs w edytorze kodu programu Visual Studio](media/vs-2019/csharp-aspnet-choose-index-cshtml.png)

 1. Wyświetl plik **Index.cshtml.cs** w edytorze kodu.

     ![Wyświetlanie pliku About.cshtml w edytorze kodu programu Visual Studio](media/vs-2019/csharp-aspnet-index-cshtml-editing.png)

 1. Projekt zawiera folder **wwwroot,** który jest głównym źródłem twojej witryny. Rozwiń folder, aby wyświetlić jego zawartość.

     ![folder wwwroot w Eksploratorze rozwiązań w programie Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    Statyczną zawartość&mdash;witryny, taką jak CSS, obrazy&mdash;i biblioteki JavaScript, można umieszczać bezpośrednio w ścieżkach w miejscu, w którym chcesz.

 1. Projekt zawiera również pliki konfiguracyjne, które zarządzają aplikacją sieci web w czasie wykonywania. Domyślna [konfiguracja](/aspnet/core/fundamentals/configuration) aplikacji jest przechowywana w *pliku appsettings.json*. Można jednak zastąpić te ustawienia za pomocą *ustawień aplikacji. Development.json*. Rozwiń plik **appsettings.json,** aby wyświetlić **appsettings. Development.json.**

     ![Pliki konfiguracyjne w Eksploratorze rozwiązań w programie Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Uruchamianie, debugowanie i wprowadzanie zmian

1. Wybierz przycisk **IIS Express** w IDE do tworzenia i uruchamiania aplikacji w trybie debugowania. (Alternatywnie naciśnij **klawisz F5**lub wybierz z paska menu polecenie**Debug start debugowania).** **Debug** > 

     ![Wybieranie przycisku IIS Express w programie Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Jeśli zostanie wyświetlony komunikat o błędzie z informacją Nie można połączyć się z **serwerem sieci Web "IIS Express",** zamknij program Visual Studio, a następnie otwórz go za pomocą opcji **Uruchom jako administrator** z menu po kliknięciu prawym przyciskiem myszy lub w menu kontekstowym. Następnie uruchom aplikację ponownie.
     >
     > Może również pojawić się komunikat z pytaniem, czy chcesz zaakceptować certyfikat IIS SSL Express. Aby wyświetlić kod w przeglądarce internetowej, wybierz pozycję **Tak**, a następnie wybierz pozycję **Tak,** jeśli zostanie wyświetlony komunikat ostrzegawczy o zabezpieczeniach uzupełniających.

1. Program Visual Studio uruchamia okno przeglądarki. Następnie na pasku menu powinny zostać wyświetlne strony **Główne**i **Prywatność.**

1. Wybierz **pozycję Prywatność** z paska menu.

   **Strona Prywatność** w przeglądarce renderuje tekst ustawiony w pliku *Privacy.cshtml.*

   ![Wyświetlanie tekstu na stronie Prywatność](media/vs-2019/csharp-aspnet-browser-page-privacy.png)

1. Wróć do programu Visual Studio, a następnie naciśnij **klawisze Shift+F5,** aby zatrzymać tryb debugowania. Spowoduje to również zamknięcie projektu w oknie przeglądarki.

1. W programie Visual Studio otwórz **plik Privacy.cshtml** do edycji. Następnie usuń słowa _Użyj tej strony, aby szczegółowo wyszczególniać politykę prywatności witryny_ i w jej miejsce dodaj _wyrazy Ta strona jest w budowie od @ViewData["TimeStamp"]_.

    ![Zmienianie tekstu w pliku Privacy.cshtml](media/vs-2019/csharp-aspnet-privacy-cshtml-code-changed.png)

1. Teraz dokonajmy zmiany kodu. Wybierz **Privacy.cshtml.cs**. Następnie wyczyść `using` dyrektywy w górnej części pliku za pomocą następującego skrótu:

   Wybierz dowolną z `using` wyszarzonych dyrektyw, a żarówka Szybkie [akcje](../../ide/quick-actions.md) pojawi się tuż pod cieszką lub na lewym marginesie. Wybierz żarówkę, a następnie najedź kursorem na **Usuń niepotrzebne użycie**.

   ![Usuwanie niepotrzebnych użycia w pliku Privacy.cshtml.cs](media/vs-2019/csharp-aspnet-remove-unnecessary-usings.png)

   Teraz wybierz **opcję Podgląd zmian,** aby zobaczyć, co się zmieni.

   ![Podgląd zmian](media/vs-2019/csharp-aspnet-preview-changes.png)

   Wybierz pozycję **Zastosuj**. Visual Studio usuwa `using` niepotrzebne dyrektywy z pliku.

1. Następnie w `OnGet()` metodzie zmień treść na następujący kod:

     ```csharp
     public void OnGet()
     {
        string dateTime = DateTime.Now.ToShortDateString();
        ViewData["TimeStamp"] = dateTime;
     }
    ```

1. Zwróć uwagę, że w obszarze **DateTime**pojawiają się dwa faliste podkreślenia . Faliste podkreślenia pojawiają się, ponieważ te typy nie jest w zakresie.

   ![Błędy oznaczone falistymi podkreśleniami w metodzie OnGet](media/vs-2019/csharp-aspnet-add-new-onget-method.png)

    Otwórz pasek **narzędzi Lista błędów,** aby wyświetlić te same błędy wymienione na liście. (Jeśli nie widzisz **paska narzędzi Lista błędów,** wybierz pozycję **Wyświetl** > **listę błędów** z górnego paska menu).

   ![Lista błędów w programie Visual Studio](media/vs-2019/csharp-aspnet-error-list.png)

1. Naprawmy to. W edytorze kodu umieść kursor w każdym wierszu zawierającym błąd, a następnie wybierz żarówkę Szybkie akcje na lewym marginesie. Następnie z menu rozwijanego wybierz **pozycję System;** aby dodać tę dyrektywę do górnej części pliku i rozwiązać błędy.

   ![Dodaj dyrektywę "using System;"](media/vs-2019/csharp-aspnet-add-usings.png)

1. Naciśnij **klawisz F5,** aby otworzyć projekt w przeglądarce internetowej.

1. W górnej części witryny sieci Web wybierz **pozycję Prywatność,** aby wyświetlić zmiany.

   ![Wyświetl zaktualizowaną stronę Prywatność zawierającą wprowadzone zmiany](media/vs-2019/csharp-aspnet-browser-page-privacy-changed.png)

1. Zamknij przeglądarkę internetową, naciśnij **klawisz Shift**+**F5,** aby zatrzymać tryb debugowania, a następnie zamknij program Visual Studio.
::: moniker-end

## <a name="quick-answers-faq"></a>Szybkie odpowiedzi często zadawane pytania

Oto krótkie często zadawane pytania, aby wyróżnić kilka kluczowych pojęć.

### <a name="what-is-c"></a>Co to jest C#?

[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) to bezpieczny dla typu i obiektowy język programowania, który został zaprojektowany tak, aby był zarówno niezawodny, jak i łatwy do nauczenia się.

### <a name="what-is-aspnet-core"></a>Co to jest ASP.NET Core?

ASP.NET Core to platforma typu open source i wieloplatformowa do tworzenia aplikacji połączonych z Internetem, takich jak aplikacje i usługi internetowe. ASP.NET aplikacje Core można uruchomić na programie .NET Core lub programie .NET Framework. Aplikacje ASP.NET Core można tworzyć i uruchamiać na wielu platformach w systemach Windows, Mac i Linux. ASP.NET Core jest open source w [GitHub](https://github.com/aspnet/home).

### <a name="what-is-visual-studio"></a>Co to jest program Visual Studio?

Visual Studio to zintegrowany pakiet narzędzi deweloperskich dla deweloperów. Pomyśl o tym jako o programie, którego można używać do tworzenia programów i aplikacji.

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego samouczka! Mamy nadzieję, że dowiedziałeś się trochę o C#, ASP.NET Core i IDE programu Visual Studio. Aby dowiedzieć się więcej na temat tworzenia aplikacji sieci Web lub witryny sieci Web w językach C# i ASP.NET, przejdź do następujących samouczków:

> [!div class="nextstepaction"]
> [Tworzenie aplikacji internetowej Razor Pages za pomocą ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)

## <a name="see-also"></a>Zobacz też

[Publikowanie aplikacji sieci Web w usłudze Azure App Service przy użyciu programu Visual Studio](../../deployment/quickstart-deploy-to-azure.md)
