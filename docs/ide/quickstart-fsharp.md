---
title: 'Szybki Start: Tworzenie usługi sieci Web ASP.NET Core w języku F #'
description: 'Dowiedz się, jak utworzyć ASP.NET Core usługę sieci Web w programie Visual Studio przy użyciu języka F #, krok po kroku.'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "70180325"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>Szybki Start: Użyj programu Visual Studio, aby utworzyć pierwszą ASP.NET Core usługę sieci Web w języku F\#

W tym 5-10 minutowym wprowadzeniu do języka F # w programie Visual Studio utworzysz aplikację sieci Web w języku F # ASP.NET Core.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt interfejsu API sieci Web ASP.NET Core. Typ projektu zawiera pliki szablonów, które stanowią działającą usługę sieci Web, przed dodaniem nawet wszystkiego.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

2. Na górnym pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

3. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń węzeł **Visual F#**, a następnie wybierz pozycję **Sieć Web**. W środkowym okienku wybierz pozycję **ASP.NET Core aplikacja sieci Web**, a następnie wybierz przycisk **OK**.

     Jeśli nie widzisz kategorii szablonu projektu **.NET Core** , wybierz link **Otwórz Instalator programu Visual Studio** w lewym okienku. Zostanie uruchomiona Instalator programu Visual Studio. Wybierz obciążenie **ASP.NET i projektowanie sieci Web** , a następnie wybierz **Modyfikuj**.

     ![ASP.NET obciążenie w instalatorze VS](../ide/media/quickstart-aspnet-workload.png)

4.In nowe okno dialogowe **ASP.NET Core aplikacji sieci Web** , wybierz pozycję **ASP.NET Core 2,1** z menu rozwijanego górne. (Jeśli na liście nie widzisz **ASP.NET Core 2,1** , zainstaluj ją, korzystając z linku **pobierania** , który powinien pojawić się na żółtym pasku w górnej części okna dialogowego). Wybierz **przycisk OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

3. Na stronie **Tworzenie nowego projektu** wpisz **f # Web** w polu wyszukiwania, a następnie wybierz szablon projektu **aplikacji sieci Web ASP.NET Core** . Wybierz pozycję **Next** (Dalej).

4. Na stronie **Konfiguruj nowy projekt** wprowadź nazwę, a następnie wybierz pozycję **Utwórz**.

5. Na stronie **Tworzenie nowej ASP.NET Core aplikacji sieci Web** wybierz pozycję **ASP.NET Core 2,1** z menu rozwijanego górne, a następnie wybierz pozycję **Utwórz**.

::: moniker-end

## <a name="explore-the-ide"></a>Eksplorowanie środowiska IDE

1. Na pasku narzędzi **Eksplorator rozwiązań** rozwiń folder **controllers** , a następnie wybierz **ValuesController. FS** , aby otworzyć go w edytorze.

   ![Eksplorator rozwiązań z rozwiniętym folderem controllers w projekcie interfejsu API sieci Web w języku F #](../ide/media/hello-world-fs-sln-explorer.png)

2. Następnie zmodyfikuj `Get()` składową, tak aby była następująca:

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

Kod jest prosty. Tablica wartości języka F # jest powiązana z `values` nazwą, a następnie przenoszona do ASP.NET Coreej platformy MVC jako `ActionResult` . ASP.NET Core zajmie się resztą.

Powinien on wyglądać następująco w edytorze:

![Zmodyfikowany członek Get](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **Ctrl** + **F5** , aby uruchomić aplikację i otworzyć ją w przeglądarce sieci Web.

2. Strona powinna przechodzić do `/api/values` trasy, ale jeśli nie, wpisz ją `https://localhost:44396/api/values` w przeglądarce.

W przeglądarce sieci Web zostanie teraz wyświetlone dopasowanie JSON zgodne z wpisanymi wcześniej.

## <a name="next-steps"></a>Następne kroki

Gratulujemy zakończenia tego przewodnika Szybki Start! Mamy nadzieję, że uczysz się nieco na temat języka F #, ASP.NET Core i środowiska IDE programu Visual Studio. Aby wyświetlić aplikację uruchomioną na serwerze publicznym, wybierz poniższy przycisk.

> [!div class="nextstepaction"]
> [Wdróż aplikację w Azure App Service](../deployment/quickstart-deploy-to-azure.md)

Aby dowiedzieć się więcej na temat języka F #, zapoznaj się z oficjalną [instrukcją języka f #](/dotnet/fsharp/index).