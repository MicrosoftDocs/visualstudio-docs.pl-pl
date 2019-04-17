---
title: 'Szybki start: Tworzenie usługi sieci web platformy ASP.NET Core wF#'
description: Dowiedz się, jak tworzyć usługi sieci web platformy ASP.NET Core w programie Visual Studio F#krok po kroku.
ms.date: 08/24/2018
ms.topic: quickstart
author: cartermp
ms.author: phcart
manager: andrehal
dev_langs:
- FSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: c24803f3817aa8461f9445e390fe44853d2d27c5
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59657237"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>Szybki start: Tworzenie pierwszej usługi sieci web platformy ASP.NET Core w F przy użyciu programu Visual Studio\#

W ramach tego wprowadzenia 5 – 10 minut, aby F# w programie Visual Studio, utworzysz F# aplikacji sieci web platformy ASP.NET Core.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) strony, aby zainstalować go za darmo.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) strony, aby zainstalować go za darmo.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt internetowego interfejsu API platformy ASP.NET Core. Typ projektu jest dostarczany z plików szablonów, wchodzących w skład usługi sieci web funkcjonalności, zanim jeszcze dodano niczego!

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

2. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

3. W **nowy projekt** rozwiń w lewym okienku w oknie dialogowym **Visual F#** , następnie wybierz **Web**. W środkowym okienku wybierz **aplikacji sieci Web programu ASP.NET Core**, następnie wybierz **OK**.

     Jeśli nie widzisz **platformy .NET Core** projektu kategorii szablonu, wybierz **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie. Uruchamia Instalatora programu Visual Studio. Wybierz **ASP.NET i tworzenie aplikacji internetowych** obciążenia, wybierz **Modyfikuj**.

     ![Obciążenie platformy ASP.NET w Instalatorze programu VS](../ide/media/quickstart-aspnet-workload.png)

4 w **Nowa aplikacja internetowa ASP.NET Core** okno dialogowe, wybierz opcję **platformy ASP.NET Core 2.1** z górnego menu rozwijanego. (Jeśli nie widzisz **platformy ASP.NET Core 2.1** na liście, zainstaluj ją, wykonując **Pobierz** link, który powinien zostać wyświetlony w żółty pasek w górnej części okna dialogowego.) Wybierz **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. W oknie rozpoczęcia wybierz **Utwórz nowy projekt**.

3. Na **Utwórz nowy projekt** wpisz **f # web** do wyszukiwania, a następnie wybierz **aplikacji sieci Web programu ASP.NET Core** szablonu projektu. Wybierz **dalej**.

4. Na **konfigurowania nowego projektu** strony, wprowadź nazwę, a następnie wybierz **Utwórz**.

5. Na **Tworzenie nowej aplikacji sieci Web platformy ASP.NET Core** wybierz opcję **platformy ASP.NET Core 2.1** z górnego menu rozwijanego, a następnie wybierz **Utwórz**.

::: moniker-end

## <a name="explore-the-ide"></a>Eksploruj IDE

1. W **Eksploratora rozwiązań** narzędzi rozwiń **kontrolerów** folderu, wybierz **ValuesController.fs** aby go otworzyć w edytorze.

   ![Eksplorator rozwiązań z folderem kontrolerów rozwinięty w F# projekt internetowego interfejsu API](../ide/media/hello-world-fs-sln-explorer.png)

2. Następnie zmodyfikuj `Get()` element członkowski może być następujące:

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

Kod jest bardzo proste. F# Tablicy wartości jest powiązany z `values` nazwę, a następnie przekazywane do struktury programu ASP.NET Core MVC jako `ActionResult`. ASP.NET Core zajmie się resztą dla Ciebie.

Powinien wyglądać następująco w edytorze:

![Element członkowski Get zmodyfikowane](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **Ctrl**+**F5** Aby uruchomić aplikację, a następnie otwórz go w przeglądarce sieci web.

2. Strony należy przejść do `/api/values` trasy, ale jeśli nie, wprowadź `https://localhost:44396/api/values` w przeglądarce.

Przeglądarka sieci web będą teraz wyświetlane dopasowania wcześniej wpisane w formacie JSON.

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenie tego przewodnika Szybki Start! Mamy nadzieję, że wiesz już trochę F#, ASP.NET Core i programu Visual Studio IDE. Aby sprawdzić działanie aplikacji na publiczny serwer, przycisk.

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w usłudze Azure App Service](../deployment/quickstart-deploy-to-azure.md)

Aby dowiedzieć się więcej na temat F#, zapoznaj się z oficjalną [ F# przewodnik](/dotnet/fsharp/index).