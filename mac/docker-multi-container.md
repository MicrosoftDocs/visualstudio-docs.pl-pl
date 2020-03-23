---
title: Samouczek — tworzenie aplikacji z wieloma kontenerami za pomocą aplikacji Docker Compose
description: Dowiedz się, jak zarządzać więcej niż jednym kontenerem i komunikować się między nimi w programie Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/17/2019
ms.openlocfilehash: 487945399252ca3627d625e3572637b5b2af2916
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983956"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>Tworzenie aplikacji z wieloma kontenerami przy użyciu narzędzia Docker Compose

W tym samouczku dowiesz się, jak zarządzać więcej niż jednym kontenerem i komunikować się między nimi podczas korzystania z dokca compose w programie Visual Studio dla komputerów Mac.

## <a name="prerequisites"></a>Wymagania wstępne

* [Pulpit platformy Docker](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio 2019 dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>Tworzenie ASP.NET podstawowej aplikacji sieci Web i dodawanie obsługi platformy Docker

1. Utwórz nowe rozwiązanie, przechodząc do **file > new solution**.
1. W obszarze **.NET Core > App** wybierz ![szablon aplikacji sieci **Web:** Tworzenie nowej aplikacji ASP.NET](media/docker-quickstart-1.png)
1. Wybierz platformę docelową. W tym przykładzie użyjemy .NET Core ![2.2: Set target framework](media/docker-quickstart-2.png)
1. Wprowadź szczegóły projektu, takie jak Nazwa projektu _(DockerDemoFrontEnd_ w tym przykładzie) i Nazwa rozwiązania (_DockerDemo_). Utworzony projekt zawiera wszystkie podstawy potrzebne do utworzenia i uruchomienia witryny sieci Web ASP.NET Core.
1. W panelu rozwiązania kliknij prawym przyciskiem myszy projekt DockerDemoFrontEnd i wybierz polecenie **Dodaj > Dodaj obsługę platformy Docker:** ![Dodaj obsługę platformy docker](media/docker-quickstart-3.png)

Visual Studio dla komputerów Mac automatycznie doda nowy projekt do rozwiązania o nazwie **docker-compose** i dodać **Dockerfile** do istniejącego projektu.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>Tworzenie ASP.NET core web API i dodawanie obsługi platformy Docker

Następnie utworzymy drugi projekt, który będzie działać jako nasz interfejs API wewnętrznej bazy danych. Szablon **interfejsu API .NET Core** zawiera kontroler, który pozwala nam obsługiwać żądania RESTful.

1. Dodaj nowy projekt do istniejącego rozwiązania, klikając prawym przyciskiem myszy rozwiązanie i wybierając **pozycję Dodaj > Dodaj nowy projekt**.
1. W obszarze **.NET Core > App** wybierz szablon **interfejsu API.**
1. Wybierz platformę docelową. W tym przykładzie użyjemy platformy .NET Core 2.2
1. Wprowadź szczegóły projektu, takie jak Nazwa projektu (_DockerDemoAPI_ w tym przykładzie).
1. Po utworzeniu przejdź do panelu rozwiązań i kliknij prawym przyciskiem myszy projekt DockerDemoAPI i wybierz pozycję **Dodaj > Dodaj obsługę platformy Docker**.

Plik **docker-compose.yml** w projekcie **docker-compose** zostanie automatycznie zaktualizowany w celu uwzględnienia projektu interfejsu API wraz z istniejącym projektem aplikacji Web App. Podczas tworzenia i **uruchamiania projektu docker-compose,** każdy z tych projektów zostanie wdrożony w oddzielnym kontenerze platformy Docker.

```
version: '3.4'

services:
  dockerdemofrontend:
    image: ${DOCKER_REGISTRY-}dockerdemofrontend
    build:
      context: .
      dockerfile: DockerDemoFrontEnd/Dockerfile

  dockerdemoapi:
    image: ${DOCKER_REGISTRY-}dockerdemoapi
    build:
      context: .
      dockerfile: DockerDemoAPI/Dockerfile
```

## <a name="integrate-the-two-containers"></a>Integracja dwóch kontenerów

Mamy teraz dwa ASP.NET projektów w naszym rozwiązaniu i oba są skonfigurowane z obsługą platformy Docker. Następnie musimy dodać kod!

1. W `DockerDemoFrontEnd` projekcie otwórz plik *Index.cshtml.cs* i zastąp `OnGet` metodę następującym kodem:

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://dockerdemoapi/api/values/1");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```

1. W pliku *Index.cshtml* dodaj wiersz `ViewData["Message"]` do wyświetlenia, aby plik wyglądał jak następujący kod:

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

1. Teraz w projekcie interfejsu API sieci Web dodaj kod do kontrolera Wartości, aby dostosować wiadomość zwróconą przez interfejs API dla wywołania dodanego z *webfrontend:*

      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

1. Ustaw `docker-compose` projekt jako projekt startowy i przejdź do **uruchom > Rozpocznij debugowanie**. Jeśli wszystko jest poprawnie skonfigurowane, zostanie wyświetlony komunikat "Hello from webfrontend and webapi (with value 1).":

![Uruchamianie rozwiązania docker dla wielu kontenerów](media/docker-multicontainer-debug.png)
