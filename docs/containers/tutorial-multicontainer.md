---
title: Samouczek wielokontenerowy korzystający z Docker Compose & ASP.NET Core
author: ghogen
description: Dowiedz się, jak używać wielu kontenerów z Docker Compose
ms.author: ghogen
ms.date: 02/21/2019
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: ce6e98e2d068cd569247c4c4ea869c4280101d47
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70179838"
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
::: moniker-end

## <a name="create-a-web-application-project"></a>Tworzenie projektu aplikacji sieci Web

W programie Visual Studio Utwórz projekt **ASP.NET Core aplikacji sieci Web** o nazwie `WebFrontEnd`. Wybierz pozycję **aplikacja sieci Web** , aby utworzyć aplikację sieci Web przy użyciu stron Razor. 
  
::: moniker range="vs-2017"

Nie wybieraj opcji **Włącz obsługę platformy Docker**. Później dodasz obsługę platformy Docker.

![Zrzut ekranu przedstawiający tworzenie projektu sieci Web](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![Zrzut ekranu przedstawiający tworzenie projektu sieci Web](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project1.png)

Nie wybieraj opcji **Włącz obsługę platformy Docker**. Później dodasz obsługę platformy Docker.

![Zrzut ekranu przedstawiający tworzenie projektu sieci Web](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Tworzenie projektu interfejsu API sieci Web

Dodaj projekt do tego samego rozwiązania i Wywołaj go *MyWebAPI*. Wybierz pozycję **interfejs API** jako typ projektu i usuń zaznaczenie pola wyboru **Konfiguruj dla protokołu HTTPS**. W tym projekcie korzystamy z protokołu SSL do komunikacji z klientem, a nie do komunikacji między kontenerami w tej samej aplikacji sieci Web. Wymaga `WebFrontEnd` tylko protokołu HTTPS.

::: moniker range="vs-2017"
   ![Zrzut ekranu przedstawiający tworzenie projektu interfejsu API sieci Web](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Zrzut ekranu przedstawiający tworzenie projektu interfejsu API sieci Web](./media/tutorial-multicontainer/vs-2019/web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Dodawanie kodu do wywoływania interfejsu API sieci Web

1. W projekcie Otwórz plik *index.cshtml.cs* i Zastąp `OnGet` metodę poniższym kodem. `WebFrontEnd`

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://mywebapi/api/values/1");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```

1. W pliku *index. cshtml* Dodaj wiersz do wyświetlenia `ViewData["Message"]` , aby plik wyglądał jak poniższy kod:
    
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

1. Teraz w projekcie interfejsu API sieci Web Dodaj kod do kontrolera wartości, aby dostosować komunikat zwracany przez interfejs API dla wywołania, które zostało dodane zelementu webfrontonu.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

1. W projekcie wybierz pozycję **Dodaj > kontener usługi Orchestrator support.** `WebFrontEnd` Zostanie wyświetlone okno dialogowe **Opcje obsługi platformy Docker** .

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

1. W projekcie interfejsu API sieci Web ponownie kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Dodaj** > **obsługę programu Orchestrator kontenera**. Wybierz **Docker Compose**, a następnie wybierz ten sam docelowy system operacyjny.  

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

1. Uruchom witrynę lokalnie teraz (F5 lub CTRL + F5), aby sprawdzić, czy działa zgodnie z oczekiwaniami. Jeśli wszystko jest prawidłowo skonfigurowane, zobaczysz komunikat "Hello z webfrontonu i WebAPI (z wartością 1)".

   Pierwszy projekt używany podczas dodawania aranżacji kontenera jest ustawiany do uruchamiania lub debugowania. Akcję uruchamiania można skonfigurować we **właściwościach projektu** dla projektu Docker-Zredaguj.  W węźle Docker-redagowanie projektu kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe, a następnie wybierz polecenie **Właściwości**lub użyj klawiszy Alt + Enter.  Poniższy zrzut ekranu przedstawia właściwości, które mają być używane w tym miejscu.  Na przykład można zmienić stronę, która jest ładowana, dostosowując Właściwość **adresu URL usługi** .

   ![Zrzut ekranu przedstawiający właściwości projektu platformy Docker](media/tutorial-multicontainer/launch-action.png)

   Oto co widzisz po uruchomieniu:

   ![Zrzut ekranu przedstawiający uruchomioną aplikację sieci Web](media/tutorial-multicontainer/webfrontend.png)

## <a name="next-steps"></a>Następne kroki

Zapoznaj się z opcjami wdrażania [kontenerów na platformie Azure](/azure/containers).

## <a name="see-also"></a>Zobacz także
  
[Docker Compose](https://docs.docker.com/compose/)  
[Narzędzia kontenera](/visualstudio/containers/)
