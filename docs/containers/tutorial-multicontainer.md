---
title: Praca z wieloma kontenerami przy użyciu Docker Compose
author: ghogen
description: Dowiedz się, jak używać wielu kontenerów z Docker Compose
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 03/15/2021
ms.technology: vs-azure
ms.topic: tutorial
ms.openlocfilehash: 78af96eaa8f340129b2b445dd92419f84cf91ab1
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307820"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Samouczek: tworzenie aplikacji z wieloma kontenerami przy użyciu Docker Compose

Z tego samouczka dowiesz się, jak zarządzać więcej niż jednym kontenerem i komunikować się między nimi podczas korzystania z narzędzi kontenerów w Visual Studio.  Zarządzanie wieloma kontenerami *wymaga aranżacji* kontenerów i wymaga orkiestratora, takiego jak Docker Compose, Kubernetes lub Service Fabric. W tym miejscu użyjemy Docker Compose. Docker Compose to doskonałe narzędzie do lokalnego debugowania i testowania w trakcie cyklu projektowania.

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range="vs-2017"

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) r. z zainstalowanym obciążeniem **Tworzenie** aplikacji internetowych, Narzędzia platformy **Azure** lub Międzyplatformowe tworzenie aplikacji **dla platformy .NET Core**
::: moniker-end

::: moniker range="vs-2019"

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) r. z zainstalowanym obciążeniem Tworzenie aplikacji **internetowych,** Narzędzia platformy **Azure** i/lub tworzeniem aplikacji dla wielu platform na platformie **.NET Core**
* [.NET Core 2.2 Development Tools](https://dotnet.microsoft.com/download/dotnet-core/2.2) for development with .NET Core 2.2 (Narzędzia programskie dla platform .NET Core 2.2 na platformie .NET Core 2.2)
* [.NET Core 3 Development Tools](https://dotnet.microsoft.com/download/dotnet-core/3.1) for development with .NET Core 3.1 (Narzędzia programskie dla platform .NET Core 3.
::: moniker-end

::: moniker range=">=vs-2022"

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2022 r. w wersji](https://visualstudio.microsoft.com/vs/preview/vs2022) zapoznawczej z zainstalowanym obciążeniem Tworzenie aplikacji **internetowych,** Narzędzia platformy **Azure** i/lub **międzyplatformowym** obciążeniem programistyki platformy .NET Core
* [.NET Core 3 Development Tools](https://dotnet.microsoft.com/download/dotnet-core/3.1) for development with .NET Core 3.1 (Narzędzia programskie dla platform .NET Core 3.
* [.NET 5 Development Toos for](https://dotnet.microsoft.com/download/dotnet-core/5.0) development with .NET 5 (Toos deweloperski dla platform .NET 5 na platformie .NET 5).
::: moniker-end

## <a name="create-a-web-application-project"></a>Tworzenie projektu aplikacji internetowej

W Visual Studio utwórz projekt **ASP.NET Core Web App** o nazwie , aby utworzyć aplikację internetową ze `WebFrontEnd` stronami Razor.
  
::: moniker range="vs-2017"

Nie wybieraj opcji **Włącz obsługę platformy Docker.** Później dodasz obsługę platformy Docker.

![Zrzut ekranu przedstawiający tworzenie projektu internetowego](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Tworzenie ASP.NET Core Web App](./media/tutorial-multicontainer/vs-2019/create-web-project1.png)

Nie wybieraj opcji **Włącz obsługę platformy Docker.** Później dodasz obsługę platformy Docker.

![Zrzut ekranu przedstawiający ekran Dodatkowe informacje podczas tworzenia projektu internetowego. Opcja Włącz obsługę platformy Docker nie jest zaznaczona.](./media/tutorial-multicontainer/vs-2019/create-web-project-additional-information.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Tworzenie projektu internetowego interfejsu API

Dodaj projekt do tego samego rozwiązania i wywołaj go *MyWebAPI.* Wybierz **typ projektu API,** a następnie wyczyść pole wyboru **Skonfiguruj dla protokołu HTTPS.** W tym projekcie używamy protokołu SSL tylko do komunikacji z klientem, a nie do komunikacji między kontenerami w tej samej aplikacji internetowej. Wymaga tylko protokołu HTTPS, a kod w przykładach zakłada, że to pole wyboru nie `WebFrontEnd` jest zaznaczone. Ogólnie rzecz biorąc, certyfikaty dewelopera .NET używane przez usługę Visual Studio są obsługiwane tylko w przypadku żądań z zewnątrz do kontenera, a nie dla żądań kontenera do kontenera.

::: moniker range="vs-2017"
   ![Zrzut ekranu przedstawiający tworzenie projektu internetowego interfejsu API](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Zrzut ekranu przedstawiający tworzenie projektu internetowego interfejsu API](./media/tutorial-multicontainer/vs-2019/create-webapi-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Dodawanie kodu w celu wywołania internetowego interfejsu API

1. W `WebFrontEnd` projekcie otwórz plik *Index.cshtml.cs* i zastąp `OnGet` metodę następującym kodem.

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
    > W rzeczywistym kodzie nie należy usuwać po `HttpClient` każdym żądaniu. Aby uzyskać najlepsze rozwiązania, zobacz Use HttpClientFactory to implement resilient HTTP requests (Implementowanie odpornych żądań HTTP za pomocą metody [HttpClientFactory).](/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests)

   W przypadku platformy .NET Core 3.1 w programie Visual Studio 2019 lub nowszym szablon internetowego interfejsu API używa interfejsu API WeatherForecast, dlatego należy odkomentować ten wiersz i zakomentować wiersz dla wersji ASP.NET 2.x.

1. W pliku *Index.cshtml* dodaj wiersz do wyświetlenia, aby `ViewData["Message"]` plik wyglądał podobnie do następującego kodu:
    
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

1. (ASP.NET tylko 2.x) Teraz w projekcie internetowego interfejsu API dodaj kod do kontrolera Wartości, aby dostosować komunikat zwrócony przez interfejs API dla wywołania dodanego z *witryny webfrontend*.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    W przypadku platformy .NET Core 3.1 nie jest to konieczne, ponieważ możesz użyć interfejsu API WeatherForecast, który już istnieje. Należy jednak skomentować wywołanie metody w metodzie w witrynie <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> `Configure` *Startup.cs,* ponieważ ten kod używa protokołu HTTP, a nie HTTPS, do wywołania internetowego interfejsu API.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. W `WebFrontEnd` projekcie wybierz pozycję **Dodaj > orkiestratora kontenerów.** Zostanie **wyświetlone okno dialogowe Opcje pomocy** technicznej platformy Docker.

1. Wybierz **Docker Compose**.

1. Wybierz docelowy system operacyjny, na przykład Linux.

   ![Zrzut ekranu przedstawiający wybieranie docelowego systemu operacyjnego](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio tworzy plik *docker-compose.yml* i plik *dockerignore* w węźle **docker-compose** w rozwiązaniu, a projekt jest pogrubiony czcionką, co pokazuje, że jest to projekt startowy.

   ![Zrzut ekranu przedstawiający Eksplorator rozwiązań z dodanym projektem docker-compose](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   *Docker-compose.yml wygląda* następująco:

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   Plik *dockerignore* zawiera typy i rozszerzenia plików, które nie powinny być dołączane do kontenera przez program Docker. Te pliki są zwykle kojarzone ze środowiskiem dewelopera i kontrolą źródła, a nie częścią aplikacji lub usługi, która jest projektowa.

   Szczegółowe informacje o uruchamianych **poleceniach** można znaleźć w sekcji Narzędzia kontenerów okienka danych wyjściowych.  Widać, że narzędzie wiersza polecenia docker-compose służy do konfigurowania i tworzenia kontenerów środowiska uruchomieniowego.

1. W projekcie internetowego interfejsu API ponownie kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz pozycję **Dodaj**  >  **obsługę orkiestratora kontenerów.** Wybierz **Docker Compose**, a następnie wybierz ten sam docelowy system operacyjny.  

    > [!NOTE]
    > W tym kroku Visual Studio do utworzenia pliku Dockerfile. Jeśli to zrobisz w projekcie, który ma już obsługę platformy Docker, zostanie wyświetlony monit o zastąpienie istniejącego pliku Dockerfile. Jeśli w pliku Dockerfile wproszą zmiany, które chcesz zachować, wybierz pozycję nie.

    Visual Studio wprowadza pewne zmiany w pliku YML redagowania platformy Docker. Teraz obie usługi są dołączone.

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

1. Uruchom lokację lokalnie teraz (F5 lub Ctrl+F5), aby sprawdzić, czy działa ona zgodnie z oczekiwaniami. Jeśli wszystko jest poprawnie skonfigurowane przy użyciu wersji 2.x programu .NET Core, zostanie wyświetlony komunikat "Hello from webfrontend and webapi (with value 1)" (Witaj z webfrontend i webapi (z wartością 1)."  Dzięki programowi .NET Core 3 zobaczysz dane prognozy pogody.

   Pierwszy projekt, który jest uruchamiany podczas dodawania aranżacji kontenera, jest uruchamiany podczas uruchamiania lub debugowania. Akcję uruchamiania można skonfigurować w oknie **Właściwości projektu** dla projektu docker-compose.  W węźle projektu docker-compose kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe, a następnie wybierz pozycję **Właściwości** lub naciśnij klawisze Alt+Enter.  Poniższy zrzut ekranu przedstawia właściwości rozwiązania używanego w tym miejscu.  Można na przykład zmienić załadowaną stronę, do dostosowywania właściwości **Adres URL** usługi.

   ![Zrzut ekranu przedstawiający właściwości projektu docker-compose](media/tutorial-multicontainer/launch-action.png)

   Oto, co zobaczysz po jego uruchomionym programie (wersja .NET Core 2.x):

   ![Zrzut ekranu przedstawiający uruchamianie aplikacji internetowej](media/tutorial-multicontainer/webfrontend.png)

   Aplikacja internetowa dla programu .NET 3.1 wyświetla dane o pogodzie w formacie JSON.

## <a name="next-steps"></a>Następne kroki

Przyjrzyj się opcjam wdrażania [kontenerów na platformie Azure.](/azure/containers)

Aby uzyskać większą kontrolę nad usługami uruchamianymi podczas sesji debugowania, dowiedz się, jak używać profilów uruchamiania Docker Compose, aby skonfigurować usługi uruchamiane podczas debugowania. Zobacz [Zarządzanie profilami uruchamiania dla Docker Compose](launch-profiles.md)

## <a name="see-also"></a>Zobacz też
  
[Docker Compose](https://docs.docker.com/compose/)  
[Narzędzia kontenerów](./index.yml)