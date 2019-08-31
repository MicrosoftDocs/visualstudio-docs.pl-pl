---
title: 'Szybki start: Utwórz usługę sieci Web ASP.NET Core w programieF#'
description: Dowiedz się, jak utworzyć ASP.NET Core usługę sieci Web w programie F#Visual Studio z programem, krok po kroku.
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
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180325"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>Szybki start: Użyj programu Visual Studio, aby utworzyć pierwszą ASP.NET Core usługę sieci Web w języku F\#

W tym 5-10 minut wprowadzenie do F# programu Visual Studio zostanie utworzona aplikacja sieci Web F# ASP.NET Core.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) strony, aby zainstalować go za darmo.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads) strony, aby zainstalować go za darmo.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt interfejsu API sieci Web ASP.NET Core. Typ projektu zawiera pliki szablonów, które stanowią działającą usługę sieci Web, przed dodaniem nawet wszystkiego.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

2. Na górnym pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

3. W oknie dialogowym **Nowy projekt** w okienku po lewej stronie rozwiń pozycję **Wizualizacja F#** , a następnie wybierz pozycję **Sieć Web**. W środkowym okienku wybierz pozycję **ASP.NET Core aplikacja sieci Web**, a następnie wybierz przycisk **OK**.

     Jeśli nie widzisz **platformy .NET Core** projektu kategorii szablonu, wybierz **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie. Uruchamia Instalatora programu Visual Studio. Wybierz obciążenie **ASP.NET i projektowanie sieci Web** , a następnie wybierz **Modyfikuj**.

     ![Obciążenie platformy ASP.NET w Instalatorze programu VS](../ide/media/quickstart-aspnet-workload.png)

4.In nowe okno dialogowe **ASP.NET Core aplikacji sieci Web** , wybierz pozycję **ASP.NET Core 2,1** z menu rozwijanego górne. (Jeśli na liście nie widzisz **ASP.NET Core 2,1** , zainstaluj ją, korzystając z linku **pobierania** , który powinien pojawić się na żółtym pasku w górnej części okna dialogowego). Wybierz **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

3. Na stronie **Tworzenie nowego projektu** wpisz **f # Web** w polu wyszukiwania, a następnie wybierz szablon projektu **aplikacji sieci Web ASP.NET Core** . Wybierz **dalej**.

4. Na stronie **Konfiguruj nowy projekt** wprowadź nazwę, a następnie wybierz pozycję **Utwórz**.

5. Na stronie **Tworzenie nowej ASP.NET Core aplikacji sieci Web** wybierz pozycję **ASP.NET Core 2,1** z menu rozwijanego górne, a następnie wybierz pozycję **Utwórz**.

::: moniker-end

## <a name="explore-the-ide"></a>Eksploruj IDE

1. Na pasku narzędzi **Eksplorator rozwiązań** rozwiń folder **controllers** , a następnie wybierz **ValuesController. FS** , aby otworzyć go w edytorze.

   ![Eksplorator rozwiązań z rozwiniętym folderem F# controllers w projekcie interfejsu API sieci Web](../ide/media/hello-world-fs-sln-explorer.png)

2. Następnie zmodyfikuj `Get()` składową, tak aby była następująca:

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

Kod jest prosty. F# Tablica wartości jest powiązana z `values` nazwą, a następnie przenoszona do platformy ASP.NET Core `ActionResult`MVC jako. ASP.NET Core zajmie się resztą.

Powinien on wyglądać następująco w edytorze:

![Zmodyfikowany członek Get](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **Ctrl**+**F5** , aby uruchomić aplikację i otworzyć ją w przeglądarce sieci Web.

2. Strona powinna przechodzić do `/api/values` trasy, ale jeśli nie, wpisz `https://localhost:44396/api/values` ją w przeglądarce.

W przeglądarce sieci Web zostanie teraz wyświetlone dopasowanie JSON zgodne z wpisanymi wcześniej.

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenie tego przewodnika Szybki Start! Mamy nadzieję, że uczysz się nieco o F#tym, ASP.NET Core i IDE programu Visual Studio. Aby wyświetlić aplikację uruchomioną na serwerze publicznym, wybierz poniższy przycisk.

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w usłudze Azure App Service](../deployment/quickstart-deploy-to-azure.md)

Aby dowiedzieć się F#więcej na temat, zapoznaj się z oficjalnym [ F# przewodnikiem](/dotnet/fsharp/index).