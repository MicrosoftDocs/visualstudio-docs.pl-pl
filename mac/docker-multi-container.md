---
title: Samouczek — Tworzenie aplikacji z obsługą kontenera przy użyciu Docker Compose
description: Dowiedz się, jak zarządzać więcej niż jednym kontenerem i komunikować się między nimi w Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/17/2019
ms.openlocfilehash: 487945399252ca3627d625e3572637b5b2af2916
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74983956"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>Tworzenie aplikacji z obsługą kontenera przy użyciu Docker Compose

W tym samouczku dowiesz się, jak zarządzać więcej niż jednym kontenerem i komunikować się między nimi przy użyciu Docker Compose w Visual Studio dla komputerów Mac.

## <a name="prerequisites"></a>Wymagania wstępne

* [Pulpit Docker](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio for Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>Tworzenie aplikacji sieci Web ASP.NET Core i Dodawanie obsługi platformy Docker

1. Utwórz nowe rozwiązanie, przechodząc do **pliku > nowe rozwiązanie**.
1. W obszarze **aplikacja .NET Core >** wybierz szablon **aplikacja sieci Web** : ![utwórz nową aplikację ASP.NET](media/docker-quickstart-1.png)
1. Wybierz platformę docelową. W tym przykładzie będziemy używać platformy .NET Core 2,2: ![ustawić platformę docelową](media/docker-quickstart-2.png)
1. Wprowadź szczegóły projektu, takie jak nazwa projektu (_DockerDemoFrontEnd_ w tym przykładzie) i nazwa rozwiązania (_DockerDemo_). Utworzony projekt zawiera wszystkie podstawowe informacje niezbędne do kompilowania i uruchamiania witryny sieci Web ASP.NET Core.
1. W okienko rozwiązania kliknij prawym przyciskiem myszy projekt DockerDemoFrontEnd i wybierz polecenie **dodaj > Dodaj obsługę platformy Docker**: ![dodać obsługę platformy docker](media/docker-quickstart-3.png)

Visual Studio dla komputerów Mac automatycznie doda nowy projekt do rozwiązania o nazwie **Docker-Zredaguj** i Dodaj **pliku dockerfile** do istniejącego projektu.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>Tworzenie ASP.NET Core internetowego interfejsu API i Dodawanie obsługi platformy Docker

Następnie utworzymy drugi projekt, który będzie pełnić rolę interfejsu API zaplecza. Szablon **interfejsu API programu .NET Core** zawiera kontroler, który pozwala nam obsługiwać żądania RESTful.

1. Dodaj nowy projekt do istniejącego rozwiązania, klikając rozwiązanie prawym przyciskiem myszy i wybierając polecenie **dodaj > Dodaj nowy projekt**.
1. W obszarze **aplikacja .NET Core >** wybierz szablon **interfejsu API** .
1. Wybierz platformę docelową. W tym przykładzie będziemy używać platformy .NET Core 2,2
1. Wprowadź szczegóły projektu, takie jak nazwa projektu (_DockerDemoAPI_ w tym przykładzie).
1. Po utworzeniu przejdź do okienko rozwiązania i kliknij prawym przyciskiem myszy projekt DockerDemoAPI i wybierz polecenie **dodaj > Dodaj obsługę platformy Docker**.

Plik **Docker-Compose. yml** w projekcie programu **Docker — redagowanie** zostanie automatycznie zaktualizowany w taki sposób, aby obejmował projekt interfejsu API wraz z istniejącym projektem aplikacji sieci Web. Po skompilowaniu i uruchomieniu projektu **platformy Docker —** każdy z tych projektów zostanie wdrożony w osobnym kontenerze platformy Docker.

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

## <a name="integrate-the-two-containers"></a>Integruj dwa kontenery

Mamy teraz dwa projekty ASP.NET w naszym rozwiązaniu, a oba są skonfigurowane z obsługą platformy Docker. Następnie musimy dodać kod!

1. W projekcie `DockerDemoFrontEnd` Otwórz plik *index.cshtml.cs* i Zastąp metodę `OnGet` następującym kodem:

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

1. W pliku *index. cshtml* Dodaj wiersz, aby wyświetlić `ViewData["Message"]`, tak aby plik wyglądał jak poniższy kod:

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

1. Teraz w projekcie interfejsu API sieci Web Dodaj kod do kontrolera wartości, aby dostosować komunikat zwracany przez interfejs API dla wywołania, które zostało dodane z elementu *webfrontonu*:

      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

1. Ustaw projekt `docker-compose` jako projekt startowy, a następnie wybierz pozycję **> Uruchom, aby rozpocząć debugowanie**. Jeśli wszystko jest prawidłowo skonfigurowane, zobaczysz komunikat "Hello z webfrontonu i WebAPI (z wartością 1)":

![Rozwiązanie do obsługi kontenera platformy Docker uruchomione](media/docker-multicontainer-debug.png)
