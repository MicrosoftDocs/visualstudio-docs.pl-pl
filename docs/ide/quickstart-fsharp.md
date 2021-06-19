---
title: 'Szybki start: tworzenie usługi internetowej ASP.NET Core w programie F #'
description: Dowiedz się, jak utworzyć usługę ASP.NET Core w usłudze Visual Studio użyciu języka F#, krok po kroku.
ms.date: 08/24/2018
ms.topic: quickstart
ms.custom: vs-acquisition
author: cartermp
ms.author: phcart
manager: andrehal
dev_langs:
- FSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 298b55120a5e4d0efea1ec5eeeacc2dfa3da274f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386439"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>Szybki start: tworzenie pierwszej Visual Studio internetowej w ASP.NET Core w programie F przy użyciu usługi Visual Studio.\#

W tym 5–10-minutowym wprowadzeniu do języka F# Visual Studio aplikacji internetowej F# ASP.NET Core.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/downloads) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2022"

Jeśli jeszcze nie zainstalowano programu Visual Studio 2022 (wersja zapoznawcza), przejdź do strony pobierania programu [Visual Studio 2022 Preview,](https://visualstudio.microsoft.com/vs/preview/vs2022) aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt internetowego interfejsu API ASP.NET Core. Typ projektu zawiera pliki szablonów, które stanowią funkcjonalną usługę internetową, zanim jeszcze cokolwiek do ciebie dodano.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

2. Na górnym pasku menu wybierz pozycję **File** New Project > **(Plik nowy** > **projekt).**

3. W **oknie dialogowym Nowy** projekt w okienku po lewej stronie rozwiń pozycję Visual F# , **a** następnie wybierz pozycję **Internet.** W środkowym okienku wybierz pozycję **ASP.NET Core Web Application**, a następnie wybierz przycisk **OK.**

     Jeśli nie widzisz kategorii **szablonu projektu .NET Core,** wybierz link Otwórz Instalator programu Visual Studio w okienku po lewej stronie.  Uruchomienie Instalator programu Visual Studio. Wybierz obciążenie **tworzenie aplikacji ASP.NET sieci Web,** a następnie wybierz pozycję **Modyfikuj.**

     ![ASP.NET obciążenia w Instalatorze programu VS](../ide/media/quickstart-aspnet-workload.png)

4.In **oknie dialogowym Nowa ASP.NET Core Web Application** wybierz pozycję ASP.NET Core **2.1** z menu rozwijanego u góry. (Jeśli nie widzisz programu **ASP.NET Core 2.1** na liście, zainstaluj  go, korzystając z linku Pobierz, który powinien pojawić się na żółtym pasku w górnej części okna dialogowego). Wybierz **przycisk OK.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt.**

3. Na stronie **Tworzenie nowego projektu** wpisz **f# Web** w polu wyszukiwania, a następnie wybierz szablon projektu ASP.NET **Core Web** Application. Wybierz pozycję **Next** (Dalej).

4. Na **stronie Konfigurowanie nowego projektu** wprowadź nazwę, a następnie wybierz pozycję **Utwórz.**

5. Na stronie **Tworzenie nowej aplikacji internetowej ASP.NET Core** wybierz pozycję ASP.NET Core **2.1** z górnego menu rozwijanego, a następnie wybierz pozycję **Utwórz.**

::: moniker-end

## <a name="explore-the-ide"></a>Eksplorowanie środowiska IDE

1. Na pasku **Eksplorator rozwiązań** rozwiń folder **Kontrolery,** a następnie wybierz pozycję **ValuesController.fs,** aby otworzyć go w edytorze.

   ![Eksplorator rozwiązań z folderem Controllers rozwiniętym w projekcie internetowego interfejsu API języka F#](../ide/media/hello-world-fs-sln-explorer.png)

2. Następnie `Get()` zmodyfikuj członka tak, aby był następujący:

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

2. Strona powinna przejść do trasy, ale jeśli tak nie `/api/values` jest, wprowadź `https://localhost:44396/api/values` w przeglądarce.

W przeglądarce internetowej będzie teraz wyświetlany tekst JSON zgodny z wpisaną wcześniej wartością.

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego przewodnika Szybki start! Mamy nadzieję, że nieco wiesz o językach F#, ASP.NET Core i Visual Studio IDE. Aby wyświetlić aplikację uruchamianą na serwerze publicznym, wybierz następujący przycisk.

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w Azure App Service](../deployment/quickstart-deploy-to-azure.md)

Aby dowiedzieć się więcej na temat języka F#, zapoznaj się z oficjalnym [przewodnikiem języka F#.](/dotnet/fsharp/index)
