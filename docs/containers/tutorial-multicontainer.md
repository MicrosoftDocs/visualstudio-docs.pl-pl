---
title: Samouczek wielokontenerowy przy użyciu dokowane compose & ASP.NET Core
author: ghogen
description: Dowiedz się, jak używać wielu kontenerów z docker Compose
ms.author: ghogen
ms.date: 01/10/2020
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: b9e1a2fc7c9027c34aeb8a0e0d1d44fdb0211e65
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027333"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Samouczek: Tworzenie aplikacji z wieloma kontenerami za pomocą aplikacji Docker Compose

W tym samouczku dowiesz się, jak zarządzać więcej niż jednym kontenerem i komunikować się między nimi podczas korzystania z narzędzi kontenera w programie Visual Studio.  Zarządzanie wieloma kontenerami wymaga *aranżacji kontenera* i wymaga koordynatora, takiego jak Docker Compose, Kubernetes lub Service Fabric. W tym miejscu użyjemy docker compose. Docker Compose doskonale nadaje się do lokalnego debugowania i testowania w trakcie cyklu rozwoju.

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range="vs-2017"
* [Pulpit platformy Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z zainstalowanym **programem Web Development,** **obciążeniem narzędzi platformy Azure** lub **międzyplatformowym** obciążeniem .NET Core
::: moniker-end

::: moniker range=">= vs-2019"
* [Pulpit platformy Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) z zainstalowanym **programem Web Development,** **obciążeniem narzędzi platformy Azure** i/lub **międzyplatformowym** obciążeniem programistycznym .NET Core
* [.NET Core 2.2 Narzędzia programistyczne](https://dotnet.microsoft.com/download/dotnet-core/2.2) do tworzenia z .NET Core 2.2
* [.NET Core 3 Development Tools](https://dotnet.microsoft.com/download/dotnet-core/3.1) do tworzenia z .NET Core 3.1.
::: moniker-end

## <a name="create-a-web-application-project"></a>Tworzenie projektu aplikacji sieci Web

W programie Visual Studio utwórz projekt ASP.NET Core `WebFrontEnd`Web **Application** o nazwie . Wybierz **aplikację sieci Web,** aby utworzyć aplikację sieci Web ze stronami Razor. 
  
::: moniker range="vs-2017"

Nie należy **wybierać opcji Włącz obsługę platformy Docker**. Dasz obsługę platformy Docker później.

![Zrzut ekranu przedstawiający tworzenie projektu sieci Web](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![Zrzut ekranu przedstawiający tworzenie projektu sieci Web](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project1.png)

Nie należy **wybierać opcji Włącz obsługę platformy Docker**. Dasz obsługę platformy Docker później.

![Zrzut ekranu przedstawiający tworzenie projektu sieci Web](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Tworzenie projektu interfejsu API sieci Web

Dodaj projekt do tego samego rozwiązania i nazwij go *MyWebAPI*. Wybierz **interfejs API** jako typ projektu i wyczyść pole wyboru **Konfigurowanie dla protokołu HTTPS**. W tym projekcie używamy tylko SSL do komunikacji z klientem, a nie do komunikacji między kontenerami w tej samej aplikacji sieci web. Tylko `WebFrontEnd` musi HTTPS i kod w przykładach zakłada, że wyczyszczone to pole wyboru.

::: moniker range="vs-2017"
   ![Zrzut ekranu przedstawiający tworzenie projektu interfejsu API sieci Web](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Zrzut ekranu przedstawiający tworzenie projektu interfejsu API sieci Web](./media/tutorial-multicontainer/vs-2019/web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Dodawanie kodu do wywoływania interfejsu API sieci Web

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
    > W rzeczywistym kodzie nie należy wyrzucać `HttpClient` po każdym żądaniu. Aby uzyskać najlepsze rozwiązania, zobacz [Używanie protokołu HttpClientFactory do implementowania odpornych żądań HTTP.](https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests)

   W przypadku platformy .NET Core 3.1 w programie Visual Studio 2019 lub nowszym szablon interfejsu API sieci Web używa interfejsu API WeatherForecast, więc odkomentuj ten wiersz i wykomentuj wiersz dla ASP.NET 2.x.

1. W pliku *Index.cshtml* dodaj wiersz `ViewData["Message"]` do wyświetlenia, aby plik wyglądał jak następujący kod:
    
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

1. (tylko ASP.NET 2.x) Teraz w projekcie interfejsu API sieci Web dodaj kod do kontrolera Wartości, aby dostosować wiadomość zwróconą przez interfejs API dla wywołania dodanego z *webfrontend*.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    Z .NET Core 3.1, nie trzeba tego, ponieważ można użyć WeatherForecast INTERFEJSU API, który już istnieje. Jednak należy skomentować wywołanie <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> w `Configure` metodzie w *Startup.cs*, ponieważ ten kod używa HTTP, a nie HTTPS, do wywołania interfejsu API sieci Web.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. W `WebFrontEnd` projekcie wybierz pozycję **Dodaj > obsługę koordynatora kontenerów**. Zostanie wyświetlone okno dialogowe **Opcje obsługi platformy Docker.**

1. Wybierz pozycję **Docker Compose**.

1. Wybierz swój system operacyjny docelowy, na przykład Linux.

   ![Zrzut ekranu przedstawiający wybór systemu operacyjnego docelowego](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Program Visual Studio tworzy plik *docker-compose.yml* i plik *.dockerignore* w węźle **docker-compose** w rozwiązaniu, a ten projekt jest wyświetlany czcionką pogrubioną czcionką, która pokazuje, że jest to projekt startowy.

   ![Zrzut ekranu przedstawiający Eksploratora rozwiązań z dodanym projektem docker-compose](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   *Docker-compose.yml* jest wyświetlany w następujący sposób:

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   Plik *.dockerignore* zawiera typy plików i rozszerzenia, których program Docker nie ma uwzględniać w kontenerze. Te pliki są zazwyczaj skojarzone ze środowiskiem programistycznym i kontrolą źródła, a nie częścią aplikacji lub usługi, którą tworzysz.

   Zapoznaj się z sekcją **Narzędzia kontenerów** w okienku danych wyjściowych, aby uzyskać szczegółowe informacje na temat uruchamianych poleceń.  Widać, że narzędzie wiersza polecenia docker-compose służy do konfigurowania i tworzenia kontenerów środowiska wykonawczego.

1. W projekcie interfejsu API sieci Web ponownie kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **obsługę koordynatora kontenerów**. Wybierz pozycję **Docker Compose**, a następnie wybierz ten sam docelowy system operacyjny.  

    > [!NOTE]
    > W tym kroku visual studio zaoferuje do utworzenia Dockerfile. Jeśli to zrobisz w projekcie, który ma już obsługę platformy Docker, zostanie wyświetlony monit, czy chcesz zastąpić istniejący plik Dockerfile. Jeśli wprowadzono zmiany w pliku dockerfile, które chcesz zachować, wybierz nie.

    Visual Studio wprowadza pewne zmiany do pliku docker compose YML. Teraz obie usługi są wliczone w cenę.

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

1. Uruchom witrynę lokalnie teraz (F5 lub Ctrl + F5), aby sprawdzić, czy działa zgodnie z oczekiwaniami. Jeśli wszystko jest poprawnie skonfigurowane w wersji .NET Core 2.x, zostanie wyświetlony komunikat "Hello from webfrontend and webapi (z wartością 1)."  W pliku .NET Core 3 zobaczysz dane prognozy pogody.

   Pierwszy projekt, który jest używany podczas dodawania aranżacji kontenera jest skonfigurowany do uruchomienia po uruchomieniu lub debugowania. Akcję uruchamiania można skonfigurować we **właściwościach projektu** dla projektu docker-compose.  W węźle projektu docker-compose kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe, a następnie wybierz polecenie Właściwości lub użyj **klawiszy**Alt+Enter.  Poniższy zrzut ekranu przedstawia właściwości, które chcesz dla rozwiązania używanego w tym miejscu.  Na przykład można zmienić stronę, która jest ładowana przez dostosowanie **usługi adres URL** właściwości.

   ![Zrzut ekranu przedstawiający właściwości projektu docker-compose](media/tutorial-multicontainer/launch-action.png)

   Oto, co widzisz po uruchomieniu (wersja .NET Core 2.x):

   ![Zrzut ekranu przedstawiający uruchamianie aplikacji sieci Web](media/tutorial-multicontainer/webfrontend.png)

   Aplikacja sieci web dla platformy .NET 3.1 wyświetla dane pogodowe w formacie JSON.

## <a name="next-steps"></a>Następne kroki

Zapoznaj się z opcjami wdrażania kontenerów na [platformie Azure.](/azure/containers)

## <a name="see-also"></a>Zobacz też
  
[Docker Compose](https://docs.docker.com/compose/)  
[Narzędzia kontenerowe](/visualstudio/containers/)
