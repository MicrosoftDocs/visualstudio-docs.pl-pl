---
title: 'Tworzenie aplikacji sieci web ASP.NET Core w języku C #'
description: Dowiedz się, jak utworzyć prostą aplikację internetową Hello World w programie Visual Studio za pomocą języka C# i ASP.NET Core, krok po kroku.
ms.custom: mvc,seodec18
ms.date: 11/06/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 1873c11d8f2e6243a0dc0f867e579f1927cd1607
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579966"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Szybki start: tworzenie pierwszej aplikacji sieci Web ASP.NET Core za pomocą programu Visual Studio

W tym 5-10 minutowym wprowadzeniu do sposobu korzystania z programu Visual Studio utworzysz prostą aplikację sieci web "Hello World" przy użyciu szablonu projektu ASP.NET i języka programowania języka języka C#.

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="install-visual-studio"></a>Instalacja programu Visual Studio

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie.

::: moniker-end

### <a name="choose-your-theme-optional"></a>Wybierz motyw (opcjonalnie)

Ten samouczek szybki start zawiera zrzuty ekranu, które używają ciemnego motywu. Jeśli nie używasz ciemnego motywu, ale chcesz, zobacz [Personalizuj ide programu Visual Studio i edytora](quickstart-personalize-the-ide.md) strony, aby dowiedzieć się, jak to zrobić.

## <a name="create-a-project"></a>Tworzenie projektu

Aby rozpocząć, utworzysz projekt aplikacji sieci web ASP.NET Core. Typ projektu zawiera wszystkie pliki szablonów, aby utworzyć aplikację internetową, zanim jeszcze coś dodałeś!

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

1. Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

1. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **Visual C#,** a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **ASP.NET Core Web Application**. <br/><br/>Następnie nazwij `HelloWorld` plik i wybierz **przycisk OK**.

   ![Tworzenie nowego projektu ASP.NET Core Web Application dla języka C #](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > Jeśli nie widzisz kategorii szablonu projektu **.NET Core,** wybierz łącze **Otwórz Instalator programu Visual Studio** w lewym okienku. (W zależności od ustawień wyświetlania może być konieczne przewinięcie, aby je wyświetlić).
   >
   > ![Otwieranie instalatora programu Visual Studio w oknie dialogowym nowy projekt](../ide/media/open-visual-studio-installer.png)
   >
   > Uruchamia instalator programu Visual Studio. Wybierz ASP.NET i obciążenia **tworzenia stron internetowych,** a następnie wybierz pozycję **Modyfikuj**.
   >
   > ![ASP.NET obciążenia w instalatorze usługi VS](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Przed kontynuowaniem instalowania nowego obciążenia może być jeszcze trzeba zamknąć program Visual Studio).

1. W oknie dialogowym **Nowa ASP.NET Podstawowa aplikacja sieci Web** wybierz polecenie ASP.NET Core **2.1** z menu rozwijanego. Następnie wybierz pozycję **Aplikacja sieci Web**, a następnie wybierz przycisk **OK**.

   ![Okno dialogowe Nowa ASP.NET Core Aplikacji Sieci Web](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > Jeśli nie widzisz **ASP.NET Core 2.1,** upewnij się, że jest uruchomiona najnowsza wersja programu Visual Studio. Aby uzyskać więcej informacji na temat aktualizowania instalacji, zobacz [Update Visual Studio do najnowszej](../install/update-visual-studio.md) wersji strony.

Wkrótce po programie Visual Studio otwiera plik projektu.

::: moniker-end

::: moniker range="vs-2019"

1. Otwórz program Visual Studio.

1. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetlanie okna "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Utwórz nowy projekt** wprowadź lub wpisz *ASP.NET* w polu wyszukiwania. Następnie wybierz **pozycję C#** z listy Język, a następnie wybierz pozycję **Windows** z listy Platforma.

   Po zastosowaniu filtrów języka i platformy wybierz szablon **ASP.NET Core Web Application,** a następnie wybierz pozycję **Dalej**.

   ![Wybieranie szablonu języka C# dla ASP.NET Core Web Application](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **ASP.NET Core Web Application,** możesz go zainstalować w oknie **Utwórz nowy projekt.** W komunikacie **Nie znajdowanie tego, czego szukasz?** **Install more tools and features**
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "Nie znajdując tego, czego szukasz" w oknie "Utwórz nowy projekt"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w Instalatorze programu Visual Studio wybierz ASP.NET i obciążenia **tworzenia sieci Web.**
   >
   > ![ASP.NET podstawowe obciążenie aplikacji sieci Web w Instalatorze programu Visual Studio](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalatorze programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze["Utwórz projekt".](#create-a-project)

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *helloworld* w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

   ![w oknie "Skonfiguruj nowy projekt" nazwij swój projekt "HelloWorld"](../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png)

1. W oknie **Utwórz nową ASP.NET podstawową aplikację sieci Web** sprawdź, czy **ASP.NET Core 3.0** jest wyświetlany w górnym menu rozwijanym. Następnie wybierz aplikację **sieci Web**, która zawiera przykładowe strony Razor. Następnie wybierz pozycję **Utwórz**.

   ![Okno "Tworzenie nowej ASP.NET podstawowej aplikacji sieci Web"](../get-started/csharp/media/vs-2019/csharp-create-aspnet-razor-pages-app.png)

   Visual Studio otwiera nowy projekt.

::: moniker-end

## <a name="create-and-run-the-app"></a>Tworzenie i uruchamianie aplikacji

::: moniker range="vs-2017"

1. W **Eksploratorze rozwiązań**rozwiń folder **Strony,** a następnie wybierz pozycję **About.cshtml**.

   ![Wybierz plik About.cshtml z Eksploratora rozwiązań](../ide/media/csharp-aspnet-about-page-html-file.png)

   Ten plik odpowiada stronie o nazwie **Informacje** w aplikacji sieci web, która jest uruchamiana w przeglądarce sieci web.

   ![Strona Informacje w aplikacji sieci Web](../ide/media/csharp-aspnet-about-page.png)

   W edytorze zobaczysz kod HTML dla obszaru "dodatkowe informacje" na stronie **Informacje.**

   ![Kod HTML dodatkowego obszaru informacyjnego w edytorze Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Zmień tekst "dodatkowe informacje" na **"Hello World!**".

   ![Zmienianie domyślnego kodu HTML dodatkowego obszaru informacyjnego w edytorze Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. W **Eksploratorze rozwiązań**rozwiń rozwiń pozycję **About.cshtml**, a następnie wybierz pozycję **About.cshtml.cs**. (Ten plik odpowiada również stronie **Informacje** w przeglądarce sieci Web).

   ![Wybierz plik About.cshtml z Eksploratora rozwiązań](../ide/media/csharp-aspnet-about-page-code-file.png)

   W edytorze zobaczysz kod języka C#, który zawiera tekst dla obszaru "opis aplikacji" strony **Informacje.**

   ![Kod języka C# dla obszaru opisu aplikacji w edytorze Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Zmień tekst wiadomości "Opis aplikacji" na **"Jaka jest moja wiadomość?**".

   ![Zmienianie domyślnego tekstu wiadomości dla obszaru opisu aplikacji w edytorze Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Wybierz **pozycję IIS Express** lub naciśnij klawisz **Ctrl**+**F5,** aby uruchomić aplikację i otworzyć ją w przeglądarce internetowej.

   ![Wybieranie przycisku IIS Express w programie Visual Studio](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > Jeśli zostanie wyświetlony komunikat o błędzie **informujący: Nie można połączyć się z serwerem sieci Web "IIS Express"** lub komunikat o błędzie, który wspomina o certyfikacie SSL, zamknij program Visual Studio. Następnie otwórz program Visual Studio przy użyciu opcji **Uruchom jako administrator** z menu kontekstowego po kliknięciu prawym przyciskiem myszy. Następnie uruchom aplikację ponownie.

1. W przeglądarce internetowej sprawdź, czy strona **Informacje** zawiera zaktualizowany tekst.

   ![Wyświetl zaktualizowaną stronę Informacje zawierającą wprowadzone zmiany](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Zamknij przeglądarkę internetową.

### <a name="review-your-work"></a>Przejrzyj swoją pracę

Wyświetl następującą animację, aby sprawdzić pracę wykonany w poprzedniej sekcji.

  ![Wyświetlanie animowanego pliku gif, który pokazuje, jak utworzyć i uruchomić prostą aplikację sieci Web ASP.NET Core w programie Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

Gratulujemy ukończenia tego szybkiego startu! Mamy nadzieję, że dowiedziałeś się trochę o C#, ASP.NET Core i Visual Studio IDE (zintegrowane środowisko programistyczne).

::: moniker-end

::: moniker range="vs-2019"

1. W **Eksploratorze rozwiązań**rozwiń folder **Strony,** a następnie wybierz polecenie **Index.cshtml**.

   ![Wybierz plik Index.cshtml z Eksploratora rozwiązań](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   Ten plik odpowiada stronie o nazwie **Strona główna** w aplikacji sieci web, która jest uruchamiana w przeglądarce sieci Web.

   ![Strona Informacje w aplikacji sieci Web](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   W edytorze zobaczysz kod HTML tekstu wyświetlanego na stronie **głównej.**

   ![Kod HTML w pliku Index.cshtml dla strony głównej w edytorze Visual Studio](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page.png)

1. Zmień tekst "Witamy", aby przeczytać "**Hello World!**".

   ![W edytorze Visual Studio zmień domyślny kod HTML, który oznacza Zapraszamy do powiedzenia Hello World zamiast](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page-hello-world.png)

1. Wybierz **pozycję IIS Express** lub naciśnij klawisz **Ctrl**+**F5,** aby uruchomić aplikację i otworzyć ją w przeglądarce internetowej.

   ![Wybieranie przycisku IIS Express w programie Visual Studio](../ide/media/vs-2019/csharp-aspnet-generic-iisbutton.png)

   > [!NOTE]
   > Jeśli zostanie wyświetlony komunikat o błędzie **informujący: Nie można połączyć się z serwerem sieci Web "IIS Express"** lub komunikat o błędzie, który wspomina o certyfikacie SSL, zamknij program Visual Studio. Następnie otwórz program Visual Studio przy użyciu opcji **Uruchom jako administrator** z menu kontekstowego po kliknięciu prawym przyciskiem myszy. Następnie uruchom aplikację ponownie.

1. W przeglądarce internetowej sprawdź, czy strona **główna** zawiera zaktualizowany tekst.

   ![Wyświetl zaktualizowaną stronę główną zawierającą wprowadzone zmiany](../ide/media/vs-2019/csharp-aspnet-index-page-hello-world.png)

1. Zamknij przeglądarkę internetową.

::: moniker-end

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej, przejdź do następującego samouczka:

> [!div class="nextstepaction"]
> [Wprowadzenie do języka C# i ASP.NET w programie Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Zobacz też

[Publikowanie aplikacji sieci Web w usłudze Azure App Service przy użyciu programu Visual Studio](../deployment/quickstart-deploy-to-azure.md)
