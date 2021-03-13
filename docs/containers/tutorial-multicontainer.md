---
title: Pracuj z wieloma kontenerami przy użyciu Docker Compose
author: ghogen
description: Dowiedz się, jak używać wielu kontenerów z Docker Compose
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 01/10/2020
ms.technology: vs-azure
ms.topic: tutorial
ms.openlocfilehash: eca1d66ddef1a0f89a3971a4867254549118e2a1
ms.sourcegitcommit: 99b66b0f4ced46ead0b2506a103f974f40cc0076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103295721"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Samouczek: Tworzenie aplikacji z obsługą kontenera przy użyciu Docker Compose

W tym samouczku dowiesz się, jak zarządzać więcej niż jednym kontenerem i komunikować się między nimi przy użyciu narzędzi kontenera w programie Visual Studio.  Zarządzanie wieloma kontenerami wymaga *aranżacji kontenera* i wymaga koordynatora, takiego jak Docker Compose, Kubernetes lub Service Fabric. W tym miejscu będziemy używać Docker Compose. Docker Compose doskonale nadaje się do lokalnego debugowania i testowania w trakcie cyklu programowania.

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range="vs-2017"
* [Pulpit Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Program Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z zainstalowaną obsługą tworzenia aplikacji dla **sieci Web**, obciążeń **narzędzi platformy Azure** lub **oprogramowania .NET Core dla wielu platform**
::: moniker-end

::: moniker range=">= vs-2019"
* [Pulpit Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Program Visual Studio 2019](https://visualstudio.microsoft.com/downloads) z zainstalowaną obsługą tworzenia aplikacji dla **sieci Web**, obciążeń **narzędzi platformy Azure** i/lub **oprogramowania .NET Core dla wielu platform**
* [Narzędzia programistyczne programu .net core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) do programowania przy użyciu programu .net Core 2,2
* [Narzędzia programistyczne programu .NET Core 3](https://dotnet.microsoft.com/download/dotnet-core/3.1) na potrzeby programowania przy użyciu programu .net Core 3,1.
::: moniker-end

## <a name="create-a-web-application-project"></a>Tworzenie projektu aplikacji sieci Web

W programie Visual Studio Utwórz projekt **aplikacji sieci web ASP.NET Core** o nazwie `WebFrontEnd` , aby utworzyć aplikację sieci Web za pomocą stron Razor.
  
::: moniker range="vs-2017"

Nie wybieraj opcji **Włącz obsługę platformy Docker**. Później dodasz obsługę platformy Docker.

![Zrzut ekranu przedstawiający tworzenie projektu sieci Web](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![Utwórz projekt aplikacji sieci Web ASP.NET Core](./media/tutorial-multicontainer/vs-2019/create-web-project1.png)

Nie wybieraj opcji **Włącz obsługę platformy Docker**. Później dodasz obsługę platformy Docker.

![Zrzut ekranu przedstawiający ekran informacji dodatkowych podczas tworzenia projektu sieci Web. Opcja włączania obsługi platformy Docker nie jest zaznaczona.](./media/tutorial-multicontainer/vs-2019/create-web-project-additional-information.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Tworzenie projektu interfejsu API sieci Web

Dodaj projekt do tego samego rozwiązania i Wywołaj go *MyWebAPI*. Wybierz pozycję **interfejs API** jako typ projektu i usuń zaznaczenie pola wyboru **Konfiguruj dla protokołu HTTPS**. W tym projekcie korzystamy z protokołu SSL do komunikacji z klientem, a nie do komunikacji między kontenerami w tej samej aplikacji sieci Web. Tylko `WebFrontEnd` należy do protokołu HTTPS i kod w przykładach założono, że pole wyboru zostało wyczyszczone. Ogólnie rzecz biorąc, certyfikaty dewelopera platformy .NET używane przez program Visual Studio są obsługiwane tylko w przypadku żądań zewnętrznych do kontenera, a nie do żądań Container-to-Container.

::: moniker range="vs-2017"
   ![Zrzut ekranu przedstawiający tworzenie projektu interfejsu API sieci Web](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Zrzut ekranu przedstawiający tworzenie projektu interfejsu API sieci Web](./media/tutorial-multicontainer/vs-2019/create-webapi-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Dodawanie kodu do wywoływania interfejsu API sieci Web

1. W `WebFrontEnd` projekcie Otwórz plik *index.cshtml.cs* i Zastąp `OnGet` metodę poniższym kodem.

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          // request.RequestUri = new Uri("http://mywebapi/WeatherForecast"); // ASP.NET 3 (VS 2019 only)
          request.RequestUri = new Uri("http://mywebapi/api/values/1"); // ASP.NET 2.x
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > W kodzie rzeczywistym nie należy zbyć się `HttpClient` po każdym żądaniu. Aby uzyskać najlepsze rozwiązania, zobacz [Używanie HttpClientFactory do implementowania odpornych żądań HTTP](/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

   W przypadku platformy .NET Core 3,1 w programie Visual Studio 2019 lub nowszym szablon internetowego interfejsu API używa interfejsu API WeatherForecast, więc Usuń komentarz tego wiersza i Skomentuj wiersz dla ASP.NET 2. x.

1. W pliku *index. cshtml* Dodaj wiersz do wyświetlenia, aby `ViewData["Message"]` plik wyglądał jak poniższy kod:
    
      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }
    
      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```

1. (Tylko ASP.NET 2. x) Teraz w projekcie interfejsu API sieci Web Dodaj kod do kontrolera wartości, aby dostosować komunikat zwracany przez interfejs API dla wywołania, które zostało dodane z elementu *webfrontonu*.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    W przypadku platformy .NET Core 3,1 nie jest to potrzebne, ponieważ można użyć interfejsu API WeatherForecast, który już istnieje. Należy jednak dodać komentarz do wywołania <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> `Configure` metody w *Startup.cs*, ponieważ ten kod używa protokołu HTTP, a nie https, aby wywołać internetowy interfejs API.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. W `WebFrontEnd` projekcie wybierz pozycję **Dodaj > kontener usługi Orchestrator support**. Zostanie wyświetlone okno dialogowe **Opcje obsługi platformy Docker** .

1. Wybierz **Docker Compose**.

1. Wybierz docelowy system operacyjny, na przykład Linux.

   ![Zrzut ekranu przedstawiający Wybieranie docelowego systemu operacyjnego](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Program Visual Studio tworzy plik *Docker-Compose. yml* i plik *. dockerignore* w węźle **Docker-redagowanie** w rozwiązaniu, a ten projekt pokazuje pogrubioną czcionkę, która pokazuje, że jest to projekt startowy.

   ![Zrzut ekranu przedstawiający Eksplorator rozwiązań z dodanym projektem platformy Docker](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   *Docker-Compose. yml* pojawia się w następujący sposób:

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   Plik *. dockerignore* zawiera typy plików i rozszerzenia, które nie powinny być uwzględniane przez platformę Docker w kontenerze. Te pliki są zwykle powiązane ze środowiskiem deweloperskim i kontrolą źródła, a nie częścią aplikacji lub usługi, która jest opracowywana.

   Aby uzyskać szczegółowe informacje na temat wykonywanych poleceń, zapoznaj się z sekcją **Narzędzia kontenera** w okienku danych wyjściowych.  Aby skonfigurować i utworzyć kontenery środowiska uruchomieniowego, można zobaczyć narzędzie wiersza polecenia Docker-Zredaguj.

1. W projekcie interfejsu API sieci Web ponownie kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Dodaj**  >  **obsługę programu Orchestrator kontenera**. Wybierz **Docker Compose**, a następnie wybierz ten sam docelowy system operacyjny.  

    > [!NOTE]
    > W tym kroku program Visual Studio będzie oferować pliku dockerfile. Jeśli wykonasz tę czynność w projekcie, który ma już obsługę platformy Docker, zostanie wyświetlony monit z pytaniem, czy chcesz zastąpić istniejące pliku dockerfile. Jeśli wprowadzono zmiany w pliku dockerfile, które chcesz zachować, wybierz pozycję nie.

    Program Visual Studio wprowadza pewne zmiany w pliku YML programu Docker. Teraz są uwzględniane obie usługi.

    ```yaml
    version: '3.4'
    
    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
    
      mywebapi:
        image: ${DOCKER_REGISTRY-}mywebapi
        build:
          context: .
          dockerfile: MyWebAPI/Dockerfile
    ```

1. Uruchom witrynę lokalnie teraz (F5 lub CTRL + F5), aby sprawdzić, czy działa zgodnie z oczekiwaniami. Jeśli wszystko jest poprawnie skonfigurowane w wersji .NET Core 2. x, zobaczysz komunikat "Hello z webfrontonu i WebAPI (z wartością 1)".  W przypadku platformy .NET Core 3 widoczne są dane prognozy pogody.

   Pierwszy projekt używany podczas dodawania aranżacji kontenera jest ustawiany do uruchamiania lub debugowania. Akcję uruchamiania można skonfigurować we **właściwościach projektu** dla projektu Docker-Zredaguj.  W węźle Docker-redagowanie projektu kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe, a następnie wybierz polecenie **Właściwości** lub użyj klawiszy Alt + Enter.  Poniższy zrzut ekranu przedstawia właściwości, które mają być używane w tym miejscu.  Na przykład można zmienić stronę, która jest ładowana, dostosowując Właściwość **adresu URL usługi** .

   ![Zrzut ekranu przedstawiający właściwości projektu platformy Docker](media/tutorial-multicontainer/launch-action.png)

   Oto co widać po uruchomieniu programu (wersja programu .NET Core 2. x):

   ![Zrzut ekranu przedstawiający uruchomioną aplikację sieci Web](media/tutorial-multicontainer/webfrontend.png)

   Aplikacja sieci Web dla programu .NET 3,1 pokazuje dane pogodowe w formacie JSON.

## <a name="next-steps"></a>Następne kroki

Zapoznaj się z opcjami wdrażania [kontenerów na platformie Azure](/azure/containers).

## <a name="see-also"></a>Zobacz też
  
[Docker Compose](https://docs.docker.com/compose/)  
[Narzędzia kontenera](./index.yml)