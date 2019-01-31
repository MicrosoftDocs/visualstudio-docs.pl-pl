---
title: 'Samouczek: Rozpoczynanie pracy z usługą C# i ASP.NET Core'
titleSuffix: ''
description: Dowiedz się, jak utworzyć aplikację internetową platformy ASP.NET Core w programie Visual Studio w języku C#, krok po kroku.
ms.custom: seodec18, get-started
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 7ff1b15c42b01894044a01b99f506dc343333c0e
ms.sourcegitcommit: 9866740aec05d1a3a5dc3b4b6d2ceaeecbd3fc29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55424476"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Samouczek: Wprowadzenie do języka C# i ASP.NET Core w programie Visual Studio

W tym samouczku dla rozwoju języka C# za pomocą programu ASP.NET Core przy użyciu programu Visual Studio będzie tworzenie aplikacji internetowej w języku C# ASP.NET Core, wprowadzić zmiany, zapoznaj się z niektórymi funkcjami środowiska IDE i następnie uruchom aplikację.

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="install-visual-studio"></a>Instalowanie programu Visual Studio

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

### <a name="update-visual-studio"></a>Aktualizowanie programu Visual Studio

Jeśli po zainstalowaniu programu Visual Studio, upewnij się, że używasz najnowszej wersji. Aby uzyskać więcej informacji dotyczących sposobu instalacji aktualizacji, zobacz [aktualizacji programu Visual Studio 2017 do najnowszej wersji](../../install/update-visual-studio.md) strony.

### <a name="choose-your-theme-optional"></a>Wybierz kompozycję (opcjonalnie)

Ten samouczek zawiera zrzuty ekranu, używanego przez ciemnego motywu. Jeśli nie używasz motyw ciemny, ale aby zobaczyć [Personalizowanie programu Visual Studio IDE i edytorem](../../ide/quickstart-personalize-the-ide.md) strony, aby dowiedzieć się, jak.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt programu ASP.NET Core. Typ projektu jest dostarczany z wszystkie pliki szablonu potrzebnych dla w pełni funkcjonalnej witryny sieci Web, zanim jeszcze dodano niczego!

1. Otwórz program Visual Studio 2017.

2. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

3. W **nowy projekt** okno dialogowe w okienku po lewej stronie rozwiń **Visual C#**, rozwiń węzeł **Web**, a następnie wybierz **platformy .NET Core**. W środkowym okienku wybierz **aplikacji sieci Web programu ASP.NET Core**. Następnie nadaj plikowi nazwę *MyCoreApp* i wybierz polecenie **OK**.

   ![Szablon projektu aplikacji sieci Web platformy ASP.NET Core w oknie dialogowym Nowy projekt w środowisku IDE programu Visual Studio](media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

### <a name="add-a-workload-optional"></a>Dodaj obciążenie (opcjonalnie)

Jeśli nie widzisz **aplikacji sieci Web programu ASP.NET Core** szablon projektu, możesz ją uzyskać, dodając **ASP.NET i tworzenie aplikacji internetowych** obciążenia. Można dodać tego obciążenia w jednej z dwóch sposobów, zależności od tego, które aktualizacje programu Visual Studio 2017 są instalowane na komputerze.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Option 1: Użyj okna dialogowego Nowy projekt

1. Wybierz **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe. (W zależności od ustawień wyświetlania, trzeba będzie Przewinięcie w celu wyświetlenia go.)

   ![Wybierz link Otwórz Instalator programu Visual Studio z okna dialogowego Nowy projekt](../media/open-visual-studio-installer-mycoreapp.png)

1. Uruchamia Instalatora programu Visual Studio. Wybierz **ASP.NET i tworzenie aplikacji internetowych** obciążenia, a następnie wybierz **Modyfikuj**.

   ![Obciążenia programowanie dla wielu platform .NET core w Instalatorze programu Visual Studio](../media/tutorial-aspnet-workload.png)

   (Może być ma zamknięcie programu Visual Studio, zanim będzie można kontynuować instalowania nowego obciążenia).

#### <a name="option-2-use-the-tools-menu-bar"></a>Option 2: Użyj paska menu Narzędzia

1. Anuluj poza **nowy projekt** okno dialogowe. Następnie na pasku menu u góry wybierz **narzędzia** > **Pobierz narzędzia i funkcje**.

1. Uruchamia Instalatora programu Visual Studio. Wybierz **ASP.NET i tworzenie aplikacji internetowych** obciążenia, a następnie wybierz **Modyfikuj**.

   (Może być ma zamknięcie programu Visual Studio, zanim będzie można kontynuować instalowania nowego obciążenia).

### <a name="add-a-project-template"></a>Dodaj szablon projektu

1. W **Nowa aplikacja internetowa ASP.NET Core** okna dialogowego wybierz **aplikacji sieci Web** szablonu projektu.

1. Upewnij się, że **platformy ASP.NET Core 2.1** pojawia się w menu u góry listy rozwijanej. Następnie wybierz **OK**.

   ![Okno dialogowe nowej aplikacji sieci Web programu ASP.NET Core](media/new-project-csharp-aspnet-razor-web-app.png)

   > [!NOTE]
   > Jeśli nie widzisz **ASP.NET Core 2.0** lub nowszej z górnego menu rozwijanego, upewnij się, że używasz najnowszej wersji programu Visual Studio. Aby uzyskać więcej informacji dotyczących sposobu instalacji aktualizacji, zobacz [aktualizacji programu Visual Studio 2017 do najnowszej wersji](../../install/update-visual-studio.md) strony.

### <a name="about-your-solution"></a>O rozwiązaniu

To rozwiązanie jest zgodna **strona Razor** wzorca projektowego. Jest inny niż [Model-View-Controller (MVC)](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x) wzorzec projektowania w tym usprawnione obejmujący kodu modelu i kontrolera w obrębie strony Razor, sam.

## <a name="tour-your-solution"></a>Poznasz rozwiązania

 1. Szablon projektu tworzy rozwiązanie za pomocą pojedynczego projektu ASP.NET Core, który nosi nazwę _MyCoreApp_. Wybierz **Eksploratora rozwiązań** kartę, aby wyświetlić jego zawartość.

    ![Eksplorator rozwiązań ASP.NET w programie Visual Studio dla rozwiązania stron Razor, który nosi nazwę MyCoreApp](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Rozwiń **stron** folder, a następnie rozwiń węzeł *About.cshtml*.

     ![Plik About.cshtml w Eksploratorze rozwiązań w programie Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. Widok **About.cshtml** plik w edytorze kodu.

     ![Wyświetl plik About.cshtml w edytorze kodu programu Visual Studio](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. Wybierz **About.cshtml.cs** pliku.

     ![Wybierz plik About.cshtml.cs w edytorze kodu programu Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. Widok **About.cshtml.cs** plik w edytorze kodu.

     ![Wyświetl plik About.cshtml w edytorze kodu programu Visual Studio](media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. Projekt zawiera **wwwroot** folderu, który jest głównym witryny sieci Web. Rozwiń folder, aby wyświetlić jego zawartość.

     ![folder Wwwroot w Eksploratorze rozwiązań w programie Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    Możesz umieścić zawartości statycznej witryny&mdash;CSS, obrazów i bibliotek JavaScript&mdash;bezpośrednio w ścieżki, w której chcesz je.

 1. Projekt zawiera również pliki konfiguracji, które Zarządzanie aplikacją sieci web w czasie wykonywania. Domyślna aplikacja [konfiguracji](/aspnet/core/fundamentals/configuration) są przechowywane w *appsettings.json*. Jednak możesz zastąpić te ustawienia przy użyciu *appsettings. Development.JSON*. Rozwiń **appsettings.json** plik, aby wyświetlić **appsettings. Development.JSON** pliku.

     ![Pliki konfiguracji w Eksploratorze rozwiązań w programie Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Uruchamiać, debugować i wprowadzić zmiany

1. Wybierz **usług IIS Express** przycisku w środowisku IDE, aby skompilować i uruchomić aplikację w trybie debugowania. (Też nacisnąć klawisz **F5**, lub wybierz **debugowania** > **Rozpocznij debugowanie** z paska menu.)

     ![Kliknij przycisk usług IIS Express w programie Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Jeśli otrzymasz komunikat o błędzie informujący, że **nie można połączyć się z serwerem sieci web usług IIS Express**, zamknij program Visual Studio, a następnie otwórz go za pomocą **Uruchom jako administrator** opcję z menu kliknij prawym przyciskiem myszy lub kontekstu. Następnie uruchom ponownie aplikację.

1. Visual Studio otworzy w przeglądarce. Powinien zostać wyświetlony **Home**, **o**, i **skontaktuj się z pomocą** strony na pasku menu. (Jeśli tego nie zrobisz, wybierz element menu ""hamburger "", aby je wyświetlić.)

    ![Wybierz element menu "hamburger" na pasku menu w aplikacji sieci web](media/csharp-aspnet-razor-browser-page.png)

1. Wybierz **o** z paska menu.

   ![Wybierz informacje, na pasku menu, okna przeglądarki dla aplikacji](media/csharp-aspnet-razor-browser-page-about-menu.png)

   Między innymi **o** strony w przeglądarce renderuje tekst, który jest ustawiony w *About.cshtml* pliku.

   ![Wyświetlanie tekstu na stronie informacje](media/csharp-aspnet-razor-browser-page-about.png)

1. Zachowaj okna przeglądarki otwartego i z powrotem do programu Visual Studio.

1. W programie Visual Studio, wybierz **About.cshtml**. Następnie usuń słowo _dodatkowe_ i w jego miejsce, należy dodać wyrazy _plików i katalogów_.

    ![Zmień tekst w pliku About.cshtml](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code-changed.png)

1. Wybierz **About.cshtml.cs**. Następnie wyczyść `using` dyrektywę w górnej części pliku przy użyciu następującego skrótu:

   Wybierz dowolną wyszarzona `using` dyrektyw i [szybkie akcje](../../ide/quick-actions.md) żarówki pojawi się na lewym marginesie lub pod karetką. Wybierz żarówki, a następnie wybierz **Usuń niepotrzebne użycia**.

   ![Usuń niepotrzebne użycia w pliku About.cshtml.cs](media/csharp-aspnet-razor-remove-unnecessary-usings.png)

     Program Visual Studio usuwa niepotrzebne `using` dyrektyw z pliku.

1. Następnie w `OnGet()` metody, należy zmienić treść z następującym kodem:

     ```csharp
     public void OnGet()
     {
         string directory = Environment.CurrentDirectory;
     Message = String.Format("Your directory is {0}.", directory);
     }
    ```
1. Należy zauważyć, że dwa faliste podkreślenia są wyświetlane w obszarze **środowiska** i **ciąg**. Faliste podkreślenia są wyświetlane, ponieważ te typy nie są w zakresie.

   ![Błędy oznaczone faliste podkreślenia w metodzie OnGet](media/csharp-aspnet-razor-add-new-on-get-method.png)

    Otwórz **lista błędów** narzędzi, aby wyświetlić błędy w tej samej liście. (Jeśli nie widzisz **lista błędów** narzędzi, wybierz **widoku** > **lista błędów** na pasku menu u góry.)

   ![Lista błędów w programie Visual Studio](media/csharp-aspnet-razor-error-list.png)

1. Możemy to naprawić. W edytorze kodu umieść kursor w dowolnym wierszu, który zawiera błąd, a następnie kliknij żarówkę szybkich akcji na lewym marginesie. Następnie z menu rozwijanego wybierz **przy użyciu systemu;** dodanie tej dyrektywy do początku pliku i naprawić błędy.

   ![Dodaj "za pomocą systemu;" — dyrektywa](media/csharp-aspnet-razor-add-usings.png)

1. Naciśnij klawisz **Ctrl**+**S** Aby zapisać zmiany i odświeżać aplikację w przeglądarce sieci web.

1. W górnej części witryny sieci web wybierz **o** Aby przejrzeć wprowadzone zmiany.

   ![Wyświetlić zaktualizowany o stronie zawierającej wprowadzone zmiany](media/csharp-aspnet-razor-browser-page-about-changed.png)

1. Zamknij przeglądarkę sieci web, naciśnij klawisz **Shift**+**F5** Aby zatrzymać tryb debugowania, a następnie zamknij program Visual Studio.

## <a name="quick-answers-faq"></a>Szybkie odpowiedzi na często zadawane pytania

Poniżej przedstawiono listę często zadawanych PYTAŃ szybkiego aby zaznaczyć kilka podstawowych pojęć.

### <a name="what-is-c"></a>Co to jest C#?

[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) jest zorientowany obiektowo i bezpieczny typowo język programowania, który ma możliwość zarówno niezawodne i łatwe do opanowania.

### <a name="what-is-aspnet-core"></a>Co to jest platforma ASP.NET Core?

Platforma ASP.NET Core to platforma typu open source i dla wielu platform, podczas tworzenia aplikacji połączonej z Internetem, takich jak aplikacje sieci web i usług. Aplikacje platformy ASP.NET Core mogą być uruchamiane na platformy .NET Core lub .NET Framework. Można tworzyć i uruchamiać aplikacje dla wielu platform ASP.NET Core na Windows, Mac i Linux. Platforma ASP.NET Core to "open source" na [GitHub](https://github.com/aspnet/home).

### <a name="what-is-visual-studio"></a>Co to jest program Visual Studio?

Program Visual Studio jest zintegrowanego rozwoju pakietu narzędzi zwiększających produktywność dla deweloperów. Go traktować jako program, który służy do tworzenia aplikacji i programów.

## <a name="next-steps"></a>Następne kroki

Gratulujemy wykonanie kroków tego samouczka! Mamy nadzieję, że wiesz już nieco C#, ASP.NET Core i środowisku IDE programu Visual Studio. Aby dowiedzieć się więcej na temat tworzenia aplikacji sieci web lub witryny sieci Web przy użyciu języka C# i platformy ASP.NET, Kontynuuj z następujących samouczków:

> [!div class="nextstepaction"]
> [Tworzenie aplikacji internetowej strony Razor za pomocą programu ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)

## <a name="see-also"></a>Zobacz także

[Publikowanie aplikacji sieci web w usłudze Azure App Service przy użyciu programu Visual Studio](../../deployment/quickstart-deploy-to-azure.md)
