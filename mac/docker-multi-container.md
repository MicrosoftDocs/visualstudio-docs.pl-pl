---
title: Aplikacja wielokontenera z Docker Compose
description: Dowiedz się, jak zarządzać więcej niż jednym kontenerem i komunikować się między nimi w Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/03/2020
ms.topic: tutorial
ms.openlocfilehash: 4dd8695ccf8f1fcf13b9b52387d28c68f8812aec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800726"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>Tworzenie aplikacji z wieloma kontenerami przy użyciu narzędzia Docker Compose

W tym samouczku dowiesz się, jak zarządzać więcej niż jednym kontenerem i komunikować się między nimi przy użyciu Docker Compose w Visual Studio dla komputerów Mac.

## <a name="prerequisites"></a>Wymagania wstępne

* [Pulpit Docker](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio dla komputerów Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>Tworzenie aplikacji sieci Web ASP.NET Core i Dodawanie obsługi platformy Docker

1. Utwórz nowe rozwiązanie, przechodząc do **pliku > nowe rozwiązanie**.
1. W obszarze **aplikacja sieci Web i konsola >** wybierz szablon **aplikacji sieci Web** : ![ Utwórz nową aplikację ASP.NET](media/docker-quickstart-1.png)
1. Wybierz platformę docelową. W tym przykładzie będziemy używać platformy .NET Core 3,1: ![ Ustaw platformę docelową](media/docker-quickstart-2.png)
1. Wprowadź szczegóły projektu, takie jak nazwa projektu (_DockerDemoFrontEnd_ w tym przykładzie) i nazwa rozwiązania (_DockerDemo_). Utworzony projekt zawiera wszystkie podstawowe informacje niezbędne do kompilowania i uruchamiania witryny sieci Web ASP.NET Core.
1. W okienko rozwiązania kliknij prawym przyciskiem myszy projekt DockerDemoFrontEnd i wybierz polecenie **dodaj > Dodawanie obsługi platformy Docker**: ![ Dodawanie obsługi platformy Docker](media/docker-quickstart-3.png)

Visual Studio dla komputerów Mac automatycznie doda nowy projekt do rozwiązania o nazwie **Docker-Zredaguj** i Dodaj **pliku dockerfile** do istniejącego projektu.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>Tworzenie ASP.NET Core internetowego interfejsu API i Dodawanie obsługi platformy Docker

Następnie utworzymy drugi projekt, który będzie pełnić rolę interfejsu API zaplecza. Szablon **interfejsu API programu .NET Core** zawiera kontroler, który pozwala nam obsługiwać żądania RESTful.

1. Dodaj nowy projekt do istniejącego rozwiązania, klikając rozwiązanie prawym przyciskiem myszy i wybierając polecenie **dodaj > Dodaj nowy projekt**.
1. W obszarze **Sieć Web i konsola > aplikacji** wybierz szablon **interfejsu API** .
1. Wybierz platformę docelową. W tym przykładzie będziemy używać platformy .NET Core 3,1.
1. Wprowadź szczegóły projektu, takie jak nazwa projektu (_MyWebAPI_ w tym przykładzie).
1. Po utworzeniu przejdź do okienko rozwiązania i kliknij prawym przyciskiem myszy projekt MyWebAPI i wybierz polecenie **dodaj > Dodaj obsługę platformy Docker**.

Plik **Docker-Compose. yml** w projekcie programu **Docker — redagowanie** zostanie automatycznie zaktualizowany w taki sposób, aby obejmował projekt interfejsu API wraz z istniejącym projektem aplikacji sieci Web. Po skompilowaniu i uruchomieniu projektu **platformy Docker —** każdy z tych projektów zostanie wdrożony w osobnym kontenerze platformy Docker.

```yaml
version: '3.4'

services:
  dockerdemofrontend:
    image: ${DOCKER_REGISTRY-}dockerdemofrontend
    build:
      context: .
      dockerfile: DockerDemoFrontEnd/Dockerfile

  mywebapi:
    image: ${DOCKER_REGISTRY-}mywebapi
    build:
      context: .
      dockerfile: MyWebAPI/Dockerfile
```

## <a name="integrate-the-two-containers"></a>Integruj dwa kontenery

Mamy teraz dwa projekty ASP.NET w naszym rozwiązaniu, a oba są skonfigurowane z obsługą platformy Docker. Następnie musimy dodać kod!

1. W `DockerDemoFrontEnd` projekcie Otwórz plik *Pages/index.* , a następnie zastąp `OnGet` metodę następującym kodem:

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://mywebapi/WeatherForecast");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > W kodzie produkcyjnym nie należy zbyć się `HttpClient` po każdym żądaniu. Aby uzyskać najlepsze rozwiązania, zobacz [Używanie HttpClientFactory do implementowania odpornych żądań HTTP](https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

1. W pliku *index. cshtml* Dodaj wiersz do wyświetlenia, aby `ViewData["Message"]` plik wyglądał jak poniższy kod:

      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }

      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```
  
1. W projektach frontonu i interfejsu API sieci Web Dodaj komentarz do wywołania [Microsoft. AspNetCore. Builder. HttpsPolicyBuilderExtensions. UseHttpsRedirection](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.builder.httpspolicybuilderextensions.usehttpsredirection) w `Configure` metodzie w *Startup.cs*, ponieważ ten przykładowy kod używa protokołu HTTP, a nie https, aby wywołać internetowy interfejs API.

      ```csharp
                  //app.UseHttpsRedirection();
      ```

1. Ustaw `docker-compose` projekt jako projekt startowy, a następnie przejdź do pozycji **Uruchom > Rozpocznij debugowanie**. Jeśli wszystko jest prawidłowo skonfigurowane, zobaczysz komunikat "Hello z webfrontonu i WebAPI (z wartością 1)":

![Rozwiązanie do obsługi kontenera platformy Docker uruchomione](media/docker-multicontainer-debug.png)
