---
title: 'Szybki start: tworzenie usługi sieci web ASP.NET Core w f #'
description: Dowiedz się, jak utworzyć usługę sieci web ASP.NET Core w programie Visual Studio za pomocą programu F#, krok po kroku.
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
ms.openlocfilehash: 990106f7f3ca97ae38a20170ca6ed2e1d699d4e4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "70180325"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>Szybki start: tworzenie pierwszej usługi sieci web ASP.NET Core w języku F za pomocą programu Visual Studio\#

W tym 5-10 minut wprowadzenie do języka F# w programie Visual Studio, utworzysz F# ASP.NET Core aplikacji sieci web.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt ASP.NET Core Web API. Typ projektu zawiera pliki szablonów, które stanowią funkcjonalną usługę internetową, zanim jeszcze coś dodasz!

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

2. Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

3. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń węzeł **Visual F#**, a następnie wybierz pozycję **Sieć Web**. W środkowym okienku wybierz pozycję **ASP.NET Core Web Application**, a następnie wybierz przycisk **OK**.

     Jeśli nie widzisz kategorii szablonu projektu **.NET Core,** wybierz łącze **Otwórz Instalator programu Visual Studio** w lewym okienku. Uruchamia instalator programu Visual Studio. Wybierz ASP.NET i obciążenia **tworzenia stron internetowych,** a następnie wybierz pozycję **Modyfikuj**.

     ![ASP.NET obciążenia w instalatorze usługi VS](../ide/media/quickstart-aspnet-workload.png)

4.In okna dialogowego **Nowa ASP.NET Podstawowa aplikacja sieci Web** wybierz polecenie ASP.NET Core **2.1** z menu rozwijanego. (Jeśli na liście nie widzisz **ASP.NET Core 2.1,** zainstaluj go, klikając link **Pobierz,** który powinien pojawić się na żółtym pasku u góry okna dialogowego). Wybierz **przycisk OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

3. Na stronie **Tworzenie nowego projektu** wpisz w polu wyszukiwania sieć web **f#,** a następnie wybierz szablon projektu **ASP.NET Core Web Application.** Wybierz pozycję **Dalej**.

4. Na stronie **Konfigurowanie nowego projektu** wprowadź nazwę, a następnie wybierz pozycję **Utwórz**.

5. Na stronie **Tworzenie nowej ASP.NET podstawowej aplikacji sieci Web** wybierz polecenie ASP.NET Core **2.1** z górnego menu, a następnie wybierz polecenie **Utwórz**.

::: moniker-end

## <a name="explore-the-ide"></a>Poznaj IDE

1. Na **pasku narzędzi Eksploratora rozwiązań** rozwiń folder **Kontrolery,** a następnie wybierz pozycję **ValuesController.fs,** aby otworzyć go w edytorze.

   ![Eksplorator rozwiązań z folderem Kontrolery rozwiniętym w projekcie interfejsu API sieci Web języka F#](../ide/media/hello-world-fs-sln-explorer.png)

2. Następnie zmodyfikuj `Get()` element członkowski, aby był następujący:

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

Kod jest prosty. Tablica wartości języka F# `values` jest powiązana z nazwą, a następnie przekazywana `ActionResult`do ASP.NET core mvc framework jako . ASP.NET Core dba o resztę za Ciebie.

Powinno to wyglądać tak w edytorze:

![Zmodyfikowany element członkowski Get](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij **klawisz Ctrl**+**F5,** aby uruchomić aplikację i otworzyć ją w przeglądarce internetowej.

2. Strona powinna przejść `/api/values` do trasy, ale jeśli `https://localhost:44396/api/values` tak nie jest, wprowadź ją do przeglądarki.

Przeglądarka internetowa będzie teraz wyświetlać JSON pasujące do tego, co wpisano wcześniej.

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego szybkiego startu! Mamy nadzieję, że dowiedziałeś się trochę o F#, ASP.NET Core i IDE programu Visual Studio. Aby wyświetlić aplikację uruchomione na serwerze publicznym, wybierz następujący przycisk.

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w usłudze Azure App Service](../deployment/quickstart-deploy-to-azure.md)

Aby dowiedzieć się więcej o F#, zapoznaj się z oficjalnym [przewodnikiem F#](/dotnet/fsharp/index).