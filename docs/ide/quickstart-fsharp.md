---
title: 'Szybki start: tworzenie usługi internetowej ASP.NET Core w programie F #'
description: Dowiedz się, jak utworzyć ASP.NET Core w usłudze Visual Studio za pomocą języka F# i krok po kroku.
ms.date: 08/24/2018
ms.topic: quickstart
ms.custom: acquisition
author: cartermp
ms.author: phcart
manager: andrehal
dev_langs:
- FSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: cbb85c41a01a03461bc1a73bdb58620e8a0c472f
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113204"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>Szybki start: tworzenie pierwszej usługi Visual Studio Core w ASP.NET Core w programie F przy użyciu usługi Visual Studio\#

W tym 5-10-minutowym wprowadzeniu do języka F# w Visual Studio utworzysz aplikację internetową F# ASP.NET Core.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/downloads) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt internetowego interfejsu API ASP.NET Core. Typ projektu zawiera pliki szablonów, które stanowią funkcjonalną usługę internetową, zanim jeszcze cokolwiek dodano.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

2. Na górnym pasku menu wybierz pozycję **File** New Project > **(Plik nowy** > **projekt).**

3. W **oknie dialogowym Nowy** projekt w okienku po lewej stronie rozwiń pozycję **Visual F#**, a następnie wybierz pozycję **Internet.** W środkowym okienku wybierz **pozycję ASP.NET Core Web Application**, a następnie wybierz przycisk **OK.**

     Jeśli nie widzisz kategorii **szablonu projektu .NET Core,** wybierz link Otwórz Instalator programu Visual Studio w okienku po lewej stronie.  Ta Instalator programu Visual Studio uruchamia się. Wybierz obciążenie **tworzenie aplikacji ASP.NET sieci Web,** a następnie wybierz pozycję **Modyfikuj.**

     ![ASP.NET obciążenia w instalatorze programu VS](../ide/media/quickstart-aspnet-workload.png)

4.In **oknie dialogowym Nowa ASP.NET Core Web Application** wybierz pozycję ASP.NET Core **2.1** z górnego menu rozwijanego. (Jeśli nie widzisz programu **ASP.NET Core 2.1** na liście, zainstaluj  go, korzystając z linku Pobierz, który powinien pojawić się na żółtym pasku w górnej części okna dialogowego). Wybierz **przycisk OK.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. W oknie uruchamiania wybierz **pozycję Utwórz nowy projekt.**

3. Na stronie **Tworzenie nowego projektu** wpisz **f# Web** w polu wyszukiwania, a następnie wybierz szablon projektu ASP.NET **Core Web** Application. Wybierz pozycję **Next** (Dalej).

4. Na **stronie Konfigurowanie nowego projektu** wprowadź nazwę, a następnie wybierz pozycję **Utwórz.**

5. Na stronie **Tworzenie nowej aplikacji ASP.NET Core** wybierz pozycję ASP.NET Core **2.1** z górnego menu rozwijanego, a następnie wybierz pozycję **Utwórz.**

::: moniker-end

## <a name="explore-the-ide"></a>Eksplorowanie środowiska IDE

1. Na pasku **Eksplorator rozwiązań** rozwiń folder **Kontrolery,** a następnie wybierz pozycję **ValuesController.fs,** aby otworzyć go w edytorze.

   ![Eksplorator rozwiązań z folderem Controllers rozwiniętym w projekcie internetowego interfejsu API języka F#](../ide/media/hello-world-fs-sln-explorer.png)

2. Następnie zmodyfikuj `Get()` członka tak, aby był następujący:

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

Kod jest prosty. Tablica wartości języka F# jest powiązana z nazwą, a następnie przekazywana do platformy `values` ASP.NET Core MVC jako `ActionResult` . ASP.NET Core zajmie się resztą za Ciebie.

W edytorze powinien on wyglądać tak:

![Zmodyfikowany członek get](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij **klawisz Ctrl** + **F5,** aby uruchomić aplikację i otworzyć ją w przeglądarce internetowej.

2. Strona powinna przejść do trasy, ale jeśli tak się nie `/api/values` stanie, wprowadź `https://localhost:44396/api/values` ją w przeglądarce.

W przeglądarce internetowej będzie teraz wyświetlany tekst JSON zgodny z wpisaną wcześniej wartością.

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego przewodnika Szybki start! Mamy nadzieję, że wiesz już nieco o F#, ASP.NET Core i Visual Studio IDE. Aby wyświetlić aplikację uruchamianą na serwerze publicznym, wybierz następujący przycisk.

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w Azure App Service](../deployment/quickstart-deploy-to-azure.md)

Aby dowiedzieć się więcej na temat języka F#, zapoznaj się z oficjalnym [przewodnikiem języka F#.](/dotnet/fsharp/index)
