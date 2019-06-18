---
title: Samouczek — tworzenie wiele kontenerów aplikacji przy użyciu rozwiązania Docker Compose
description: Dowiedz się, jak zarządzać więcej niż jednego kontenera i komunikować się między nimi w programie Visual Studio dla komputerów Mac
author: bytesguy
ms.author: adhartle
ms.date: 06/17/2019
ms.openlocfilehash: df130e86de7f35c43459a70a12c0e9cfafbbe3a4
ms.sourcegitcommit: fd5a5b057df3d733f5224c305096907989811f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2019
ms.locfileid: "67196406"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>Utwórz wiele kontenerów aplikacji przy użyciu rozwiązania Docker Compose

W tym samouczku dowiesz się, jak zarządzać więcej niż jednego kontenera i komunikować się między nimi przy użyciu rozwiązania Docker Compose w programie Visual Studio dla komputerów Mac.

## <a name="prerequisites"></a>Wymagania wstępne

* [Pulpitu platformy docker](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio for Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>Utwórz aplikację sieci Web platformy ASP.NET Core i Dodaj obsługę platformy Docker

1. Utwórz nowe rozwiązanie, przechodząc do **Plik > nowe rozwiązanie**.
1. W obszarze **platformy .NET Core > App** wybierz **aplikacji sieci Web** szablonu: ![Tworzenie nowej aplikacji platformy ASP.NET](media/docker-quickstart-1.png)
1. Wybierz platformę docelową. W tym przykładzie używamy platformy .NET Core 2.2: ![Platforma docelowa zestawu](media/docker-quickstart-2.png)
1. Wprowadź szczegóły projektu, takie jak nazwa projektu (_DockerDemoFrontEnd_ w tym przykładzie) i nazwę rozwiązania (_DockerDemo_). Utworzony projekt zawiera podstawowe, których potrzebujesz, aby skompilować i uruchomić witrynę sieci web platformy ASP.NET Core.
1. W konsoli rozwiązania, kliknij prawym przyciskiem myszy projekt DockerDemoFrontEnd, a następnie wybierz **Dodaj > Dodaj obsługę platformy Docker**: ![Dodaj obsługę platformy docker](media/docker-quickstart-3.png)

Visual Studio dla komputerów Mac automatycznie doda nowy projekt do rozwiązania o nazwie **narzędzia docker compose** i Dodaj **pliku Dockerfile** do istniejącego projektu.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>Tworzenie internetowego interfejsu API platformy ASP.NET Core i Dodaj obsługę platformy Docker

Następnie utworzymy drugi projekt, który będzie pełnił rolę naszego interfejsu API zaplecza. **Interfejsu API platformy .NET Core** szablon zawiera kontroler, który umożliwia obsługę żądań RESTful.

1. Dodaj nowy projekt do istniejącego rozwiązania, kliknięcie prawym przyciskiem myszy rozwiązanie i wybierając pozycję **Dodaj > Dodaj nowy projekt**.
1. W obszarze **platformy .NET Core > App** wybierz **API** szablonu.
1. Wybierz platformę docelową. W tym przykładzie używamy platformy .NET Core 2.2
1. Wprowadź szczegóły projektu, takie jak nazwa projektu (_DockerDemoAPI_ w tym przykładzie).
1. Po utworzeniu przejdź do konsoli rozwiązania i projektu DockerDemoAPI kliknij prawym przyciskiem myszy i wybierz **Dodaj > Dodaj obsługę platformy Docker**.

**Docker-compose.yml** w pliku **narzędzia docker compose** projektu zostanie automatycznie zaktualizowana do uwzględnienia w projekcie interfejsu API wraz z istniejącego projektu aplikacji sieci Web. Gdy do skompilowania i uruchomienia **docker-compose** zostanie wdrożony projekt, każdy z tych projektów do oddzielnego kontenera platformy Docker.

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

## <a name="integrate-the-two-containers"></a>Integrowanie dwóch kontenerów

Obecnie dostępne są dwa projekty ASP.NET w naszym rozwiązaniu i są konfigurowane z obsługą platformy Docker. Następnie należy dodać kod!

1. W `DockerDemoFrontEnd` otwarty projekt *Index.cshtml.cs* plik i zastąpić `OnGet` metoda następującym kodem:

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

1. W *Index.cshtml* Dodaj wiersz, aby wyświetlić `ViewData["Message"]` tak, aby plik będzie wyglądać podobnie do poniższego kodu:
    
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

1. Teraz w projekcie interfejsu API sieci Web, Dodaj kod do kontrolera wartości, aby dostosować komunikat zwrócony przez interfejs API dla wywołania dodane z *webfrontend*:
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```
1. Ustaw `docker-compose` projekt jako projekt startowy, a następnie przejdź do **Uruchom > Rozpocznij debugowanie**. Jeśli wszystko jest poprawnie skonfigurowane, zostanie wyświetlony komunikat "Hello webfrontend i webapi (z wartością 1).":

![Uruchamianie rozwiązania do kontenerów multi platformy docker](media/docker-multicontainer-debug.png)
