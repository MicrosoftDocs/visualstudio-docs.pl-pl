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
ms.openlocfilehash: 0e701fd45230295222ffc6e17c05052e01b47189
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745044"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Szybki start: Tworzenie pierwszej aplikacji sieci web platformy ASP.NET Core przy użyciu programu Visual Studio

W ramach tego wprowadzenia 5 – 10 minut, jak używać programu Visual Studio utworzysz prostą aplikację sieci web "Hello World" przy użyciu szablonu projektu programu ASP.NET i języka programowania C#.

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="install-visual-studio"></a>Instalowanie programu Visual Studio

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) strony, aby zainstalować go za darmo.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) strony, aby zainstalować go za darmo.

::: moniker-end

### <a name="choose-your-theme-optional"></a>Wybierz kompozycję (opcjonalnie)

Ten samouczek Szybki Start zawiera zrzuty ekranu, używanego przez ciemnego motywu. Jeśli nie używasz motyw ciemny, ale aby zobaczyć [Personalizowanie programu Visual Studio IDE i edytorem](quickstart-personalize-the-ide.md) strony, aby dowiedzieć się, jak.

## <a name="create-a-project"></a>Tworzenie projektu

Aby rozpocząć, należy utworzyć projekt aplikacji sieci web platformy ASP.NET Core. Typ projektu jest dostarczany z wszystkich plików szablonów do tworzenia aplikacji sieci web, przed nawet dodano niczego!

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

1. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

1. W okienku po lewej stronie **nowy projekt** okna dialogowego rozwiń **Visual C#** , a następnie wybierz **platformy .NET Core**. W środkowym okienku wybierz **aplikacji sieci Web programu ASP.NET Core**. <br/><br/>Następnie nadaj plikowi nazwę `HelloWorld` i wybierz polecenie **OK**.

   ![Utwórz nowy projekt aplikacji sieci Web programu ASP.NET Core dla języka C#](../ide/media/csharp-aspnet-choose-template-name-file.png)

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

1. W **Nowa aplikacja internetowa ASP.NET Core** okno dialogowe, wybierz opcję **platformy ASP.NET Core 2.1** z górnego menu rozwijanego. Następnie wybierz pozycję **aplikacji sieci Web**, a następnie wybierz **OK**.

   ![Okno dialogowe nowej aplikacji sieci Web programu ASP.NET Core](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > Jeśli nie widzisz **platformy ASP.NET Core 2.1**, upewnij się, że używasz najnowszej wersji programu Visual Studio. Aby uzyskać więcej informacji dotyczących sposobu instalacji aktualizacji, zobacz [aktualizacji programu Visual Studio do najnowszej wersji](../install/update-visual-studio.md) strony.

Wkrótce potem Visual Studio otwiera plik projektu.

::: moniker-end

::: moniker range="vs-2019"

1. Otwórz program Visual Studio.

1. W oknie rozpoczęcia wybierz **Utwórz nowy projekt**.

   ![Wyświetlanie w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Na **Utwórz nowy projekt** oknie wprowadź lub wpisz *ASP.NET* w polu wyszukiwania. Następnie wybierz pozycję **C#** od języka, a następnie wybierz **Windows** z listy Platform.

   Po zastosowaniu filtrów języka i platformy, wybierz **aplikacji sieci Web programu ASP.NET Core** szablonu, a następnie wybierz **dalej**.

   ![Wybierz C# szablonu dla aplikacji sieci Web platformy ASP.NET Core](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > Jeśli nie widzisz **aplikacji sieci Web programu ASP.NET Core** szablonu, można zainstalować go z **Utwórz nowy projekt** okna. W **nie znaleźć, czego szukasz?** komunikatu, wybierz polecenie **zainstalować więcej narzędzi i funkcji** łącza.
   >
   > ![Łącza "Zainstaluj więcej narzędzi i funkcji" komunikat "Nie możesz znaleźć teraz wyszukiwanie" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w Instalatorze programu Visual Studio, wybierz **ASP.NET i tworzenie aplikacji internetowych** obciążenia.
   >
   > ![Obciążenia podstawowej aplikacji sieci Web platformy ASP.NET w Instalatorze programu Visual Studio](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Następnie należy wybrać **Modyfikuj** przycisku w Instalatorze programu Visual Studio. Może zostać wyświetlony monit, aby zapisać swoją pracę; Jeśli tak, należy to zrobić. Następnie wybierz pozycję **Kontynuuj** do zainstalowania z obciążeniem. Następnie wróć do kroku 2, w tym "[Utwórz projekt](#create-a-project)" procedury.

1. W **konfigurowania nowego projektu** oknie wpisz lub wprowadź *HelloWorld* w **Nazwa projektu** pole. Następnie wybierz **Utwórz**.

   ![w oknie "Konfigurowanie nowego projektu" nazwij swój projekt "HelloWorld"](../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png)

1. W **Tworzenie nowej aplikacji sieci Web platformy ASP.NET Core** okna, upewnij się, że **platformy ASP.NET Core 2.1** pojawia się w menu u góry listy rozwijanej. Następnie wybierz **aplikacji sieci Web**, w tym przykładzie stron Razor. Następnie wybierz pozycję **Utwórz**.

   ![W oknie "Tworzenie nowej aplikacji sieci Web platformy ASP.NET Core"](../get-started/csharp/media/vs-2019/csharp-create-aspnet-core-razor-pages-app.png)

   Visual Studio otwiera nowy projekt.

::: moniker-end

## <a name="create-and-run-the-app"></a>Tworzenie i uruchamianie aplikacji

1. W **Eksploratora rozwiązań**, rozwiń węzeł **stron** folder, a następnie wybierz **About.cshtml**.

   ![Wybierz plik About.cshtml z poziomu Eksploratora rozwiązań](../ide/media/csharp-aspnet-about-page-html-file.png)

   Ten plik odnosi się do strony, który nosi nazwę **o** w aplikacji sieci web, które są uruchamiane w przeglądarce sieci web.

   ![Na stronie informacje w aplikacji sieci web](../ide/media/csharp-aspnet-about-page.png)

   W edytorze zostaną wyświetlone HTML kodu dla obszaru "informacje dodatkowe" **o** strony.

   ![Kod HTML dla obszaru dodatkowe informacje w edytorze programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Zmień tekst "informacje dodatkowe" do odczytu "**Hello World!** ".

   ![Zmień domyślny kod HTML dla obszaru dodatkowe informacje w edytorze programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. W **Eksploratora rozwiązań**, rozwiń węzeł **About.cshtml**, a następnie wybierz **About.cshtml.cs**. (Ten plik, ale także odpowiada **o** strony w przeglądarce sieci web.)

   ![Wybierz plik About.cshtml z poziomu Eksploratora rozwiązań](../ide/media/csharp-aspnet-about-page-code-file.png)

   W edytorze zostaną wyświetlone C# kod, który zawiera tekst dla obszaru "application description" **o** strony.

   ![Kod C# obszar opisu aplikacji w edytorze programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Zmień tekst komunikatu "description aplikacji" do odczytu "**co to jest wiadomość?** ".

   ![Zmień domyślny tekst komunikatu dla obszaru Opis aplikacji, w edytorze programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Wybierz **usług IIS Express** lub naciśnij **Ctrl**+**F5** Uruchom aplikację i otworzyć go w przeglądarce sieci web.

   ![Kliknij przycisk usług IIS Express w programie Visual Studio](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > Jeśli otrzymasz komunikat o błędzie informujący, że, **nie można połączyć się z serwerem sieci web usług IIS Express**, lub komunikat o błędzie dotyczący certyfikatu SSL, zamknij program Visual Studio. Następnie otwórz program Visual Studio przy użyciu **Uruchom jako administrator** opcję z menu kontekstowym kliknij prawym przyciskiem myszy. Następnie uruchom ponownie aplikację.

1. W przeglądarce sieci web, upewnij się, że **o** strona zawiera zaktualizowane tekstu.

   ![Wyświetlić zaktualizowany o stronie zawierającej wprowadzone zmiany](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Zamknij przeglądarkę sieci web.

### <a name="review-your-work"></a>Przejrzyj swoją pracę

Wyświetl następujące animacji, aby sprawdzić prac, które można wykonać w poprzedniej sekcji.

  ![Wyświetl plik animowany obraz GIF, pokazujący sposób tworzenia i uruchamiania prostego C# aplikacji internetowej ASP.NET Core w programie Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

Gratulujemy ukończenie tego przewodnika Szybki Start! Mamy nadzieję, że wiesz już nieco C#, ASP.NET Core i programu Visual Studio IDE (zintegrowanym środowiskiem programistycznym).

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej, przejdź do następującego samouczka:

> [!div class="nextstepaction"]
> [Wprowadzenie do języka C# i platformy ASP.NET w programie Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Zobacz także

[Publikowanie aplikacji sieci web w usłudze Azure App Service przy użyciu programu Visual Studio](../deployment/quickstart-deploy-to-azure.md)
