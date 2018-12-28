---
title: Tworzenie aplikacji internetowej platformy ASP.NET Core wC#
description: Dowiedz się, jak utworzyć prostą aplikację sieci web Hello World w programie Visual Studio w języku C# i ASP.NET Core, który krok po kroku.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.custom: mvc,seodec18
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 23ba016d95e96965637ca6742501b09b16a42707
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684369"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Szybki start: Tworzenie pierwszej aplikacji sieci web platformy ASP.NET Core przy użyciu programu Visual Studio

W ramach tego wprowadzenia 5 – 10 minut, jak używać programu Visual Studio utworzysz prostą aplikację sieci web "Hello World" przy użyciu szablonu projektu programu ASP.NET i języka programowania C#.

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="install-visual-studio"></a>Instalowanie programu Visual Studio

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

### <a name="update-visual-studio"></a>Aktualizowanie programu Visual Studio

Jeśli po zainstalowaniu programu Visual Studio, upewnij się, że używasz najnowszej wersji. Aby uzyskać więcej informacji dotyczących sposobu instalacji aktualizacji, zobacz [aktualizacji programu Visual Studio 2017 do najnowszej wersji](../install/update-visual-studio.md) strony.

### <a name="choose-your-theme-optional"></a>Wybierz kompozycję (opcjonalnie)

Ten samouczek Szybki Start zawiera zrzuty ekranu, używanego przez ciemnego motywu. Jeśli nie używasz motyw ciemny, ale aby zobaczyć [Personalizowanie programu Visual Studio IDE i edytorem](quickstart-personalize-the-ide.md) strony, aby dowiedzieć się, jak.

## <a name="create-a-project"></a>Tworzenie projektu

Aby rozpocząć, należy utworzyć projekt aplikacji sieci web platformy ASP.NET Core. Typ projektu jest dostarczany z wszystkich plików szablonów do tworzenia aplikacji sieci web, przed nawet dodano niczego!

1. Otwórz program Visual Studio 2017.

1. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

1. W okienku po lewej stronie **nowy projekt** okna dialogowego rozwiń **Visual C#**, a następnie wybierz **platformy .NET Core**. W środkowym okienku wybierz **aplikacji sieci Web programu ASP.NET Core**. Następnie nadaj plikowi nazwę `HelloWorld` i wybierz polecenie **OK**.

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

1. W **Nowa aplikacja internetowa ASP.NET Core** okno dialogowe, wybierz opcję **ASP.NET Core 2.0** lub nowszych z górnego menu rozwijanego.

   > [!NOTE]
   > Jeśli nie widzisz **ASP.NET Core 2.0** lub nowszym, upewnij się, że używasz najnowszej wersji programu Visual Studio. Aby uzyskać więcej informacji dotyczących sposobu instalacji aktualizacji, zobacz [aktualizacji programu Visual Studio 2017 do najnowszej wersji](../install/update-visual-studio.md) strony.

1. Następnie wybierz pozycję **aplikacji sieci Web**, a następnie wybierz **OK**.

   ![Okno dialogowe nowej aplikacji sieci Web programu ASP.NET Core](../ide/media/quickstart-aspnet-core20.png)

Wkrótce potem Visual Studio otwiera plik projektu.

## <a name="create-the-app"></a>Tworzenie aplikacji

1. W **Eksploratora rozwiązań**, rozwiń węzeł **stron** folder, a następnie wybierz **About.cshtml**.

   ![Wybierz plik About.cshtml z poziomu Eksploratora rozwiązań](../ide/media/csharp-aspnet-about-page-html-file.png)

   Ten plik odnosi się do strony, który nosi nazwę **o** w aplikacji sieci web.

   ![Na stronie informacje w aplikacji sieci web](../ide/media/csharp-aspnet-about-page.png)

   W edytorze zostaną wyświetlone HTML kodu dla obszaru "informacje dodatkowe" **o** strony.

   ![Kod HTML dla obszaru dodatkowe informacje w edytorze programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Zmień tekst "informacje dodatkowe" do odczytu "**Hello World!**".

   ![Zmień domyślny kod HTML dla obszaru dodatkowe informacje w edytorze programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. W **Eksploratora rozwiązań**, rozwiń węzeł **About.cshtml**, a następnie wybierz **About.cshtml.cs**. (Ten plik, ale także odpowiada **o** strony w aplikacji sieci web.)

   ![Wybierz plik About.cshtml z poziomu Eksploratora rozwiązań](../ide/media/csharp-aspnet-about-page-code-file.png)

   W edytorze zostaną wyświetlone C# kod, który zawiera tekst dla obszaru "application description" **o** strony.

   ![Kod C# obszar opisu aplikacji w edytorze programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Zmień tekst komunikatu "description aplikacji" do odczytu "**co to jest wiadomość?**".

   ![Zmień domyślny tekst komunikatu dla obszaru Opis aplikacji, w edytorze programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

## <a name="run-the-app"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **Ctrl**+**F5** Uruchom aplikację i otworzyć go w przeglądarce sieci web.

   > [!NOTE]
   > Jeśli otrzymasz komunikat o błędzie informujący, że, **nie można połączyć się z serwerem sieci web usług IIS Express**, lub komunikat o błędzie dotyczący certyfikatu SSL, zamknij program Visual Studio. Następnie otwórz program Visual Studio przy użyciu **Uruchom jako administrator** opcję z menu kliknij prawym przyciskiem myszy lub kontekstu. Następnie uruchom ponownie aplikację.

1. W górnej części strony sieci web wybierz **o**.

   ![Wybierz informacje ze strony internetowej](../ide/media/csharp-aspnet-home-page-about.png)

1. Zaktualizowany tekst, który został dodany do wyświetlenia **o** strony.

   ![Wyświetl zaktualizowane informacje o stronie, który zawiera tekst, który został dodany](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Zamknij przeglądarkę sieci web.

Gratulujemy ukończenie tego przewodnika Szybki Start! Mamy nadzieję, że wiesz już nieco C#, ASP.NET Core i programu Visual Studio IDE (zintegrowanym środowiskiem programistycznym).

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej, przejdź do następującego samouczka:

> [!div class="nextstepaction"]
> [Wprowadzenie do języka C# i platformy ASP.NET w programie Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Zobacz także

[Publikowanie aplikacji sieci web w usłudze Azure App Service przy użyciu programu Visual Studio](../deployment/quickstart-deploy-to-azure.md)
