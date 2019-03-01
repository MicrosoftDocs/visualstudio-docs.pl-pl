---
title: Visual Studio, narzędzia kontenerów wieloma kontenerami w celu samouczek przy użyciu narzędzia Docker Compose i ASP.NET Core
author: ghogen
description: Dowiedz się, jak używać wielu kontenerów za pomocą narzędzia Docker Compose
ms.author: ghogen
ms.date: 02/21/2019
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.topic: include
monikerRange: '>= vs-2017'
ms.openlocfilehash: 168afe9d5188b445260f9143967cc022771917d9
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57223896"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Samouczek: Utwórz aplikację obsługującą wiele kontenerów przy użyciu narzędzia Docker Compose

W tym samouczku dowiesz się, jak zarządzać więcej niż jednego kontenera i komunikować się między nimi przy użyciu narzędzia kontenerów programu Visual Studio.  Zarządzanie wieloma kontenerami wymaga *aranżacji kontenerów* i wymaga orkiestratora, takiego jak Docker Compose, Kubernetes lub usługi Service Fabric. W tym miejscu użyjemy narzędzia Docker Compose. Docker Compose to idealne narzędzie do debugowania i testowania w ramach cyklu tworzenia oprogramowania lokalnego.

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range="vs-2017"
* [Pulpitu platformy docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Program Visual Studio 2017](https://visualstudio.microsoft.com/) z **programowania dla sieci Web**, **narzędzi Azure** obciążenia, lub **programowanie dla wielu platform .NET Core** zainstalowanym obciążeniem

::: moniker-end

::: moniker range=">= vs-2019"
* [Pulpitu platformy docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019 Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+preview) z **programowania dla sieci Web**, **narzędzi Azure** obciążenia i/lub **programowanie dla wielu platform .NET Core** zainstalowanym obciążeniem
* [Narzędzia programistyczne programu .NET core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) podczas tworzenia aplikacji z platformy .NET Core 2.2
::: moniker-end

## <a name="create-a-web-application-project"></a>Tworzenie projektu aplikacji sieci Web

W programie Visual Studio, należy utworzyć **aplikacji sieci Web programu ASP.NET Core** projektu o nazwie `WebFrontEnd`. Wybierz **aplikacji sieci Web** do tworzenia aplikacji sieci web ze stron Razor. 
  
::: moniker range="vs-2017"

Nie należy wybierać **włączyć obsługę platformy Docker**. Później dodasz obsługę platformy Docker.

![Zrzut ekranu przedstawiający tworzenie projektu sieci web](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![Zrzut ekranu przedstawiający tworzenie projektu sieci web](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project1.png)

Nie należy wybierać **włączyć obsługę platformy Docker**. Później dodasz obsługę platformy Docker.

![Zrzut ekranu przedstawiający tworzenie projektu sieci web](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Utwórz projekt internetowego interfejsu API

Dodaj projekt do tego samego rozwiązania, a następnie wywołaj ją *MyWebAPI*. Wybierz **API** jako projekt typu, a następnie wyczyść pole wyboru **Konfigurowanie protokołu HTTPS**. W tym projekcie używamy tylko protokół SSL dla komunikacji z klientem, a nie dla komunikacji znajdujące kontenerów w ramach jednej aplikacji sieci web. Tylko `WebFrontEnd` wymaga protokołu HTTPS.

::: moniker range="vs-2017"
   ![Zrzut ekranu przedstawiający tworzenie projektu interfejsu API sieci Web](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Zrzut ekranu przedstawiający tworzenie projektu interfejsu API sieci Web](./media/tutorial-multicontainer/vs-2019/web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Dodaj kod, aby wywołać interfejs API sieci Web

1. W `WebFrontEnd` otwarty projekt *Index.cshtml.cs* plik i zastąpić `OnGet` metoda następującym kodem.

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

1. Teraz w projekcie interfejsu API sieci Web, Dodaj kod do kontrolera wartości, aby dostosować komunikat zwrócony przez interfejs API dla wywołania dodane z *webfrontend*.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

1. W `WebFrontEnd` projektu, wybierz **Dodaj > Obsługa Orkiestratora kontenerów**. **Opcje pomocy technicznej platformy Docker** zostanie wyświetlone okno dialogowe.

1. Wybierz **narzędzia Docker Compose**.

1. Wybierz docelowy system operacyjny, na przykład w systemie Linux.

   ![Zrzut ekranu przedstawiający Wybieranie docelowy system operacyjny](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Program Visual Studio tworzy *docker-compose.yml* pliku i *.dockerignore* w pliku **narzędzia docker compose** węzła w rozwiązaniu i tego projektu zawiera w pogrubiony czcionki który wskazuje, że jest projekt startowy.

   ![Zrzut ekranu Eksploratora rozwiązań z projektem docker-compose dodane](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   *Docker-compose.yml* wygląda następująco:

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   *.Dockerignore* plik zawiera typy plików i rozszerzenia, które nie mają platformy Docker do uwzględnienia w kontenerze. Te pliki są zwykle skojarzone z środowiska deweloperskiego i kontrola źródła, nie jest częścią aplikacji lub usługi, którą tworzysz.

   Przyjrzyj się **narzędzia kontenerów** sekcji okienko danych wyjściowych, aby uzyskać szczegółowe informacje o polecenia są uruchamiane.  Widać, narzędzie wiersza polecenia narzędzia docker compose służy do konfigurowania i tworzenia kontenerów środowiska wykonawczego.

1. W projekcie interfejsu API sieci Web, ponownie kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz **Dodaj** > **obsługi Orkiestratora kontenerów**. Wybierz **narzędzia Docker Compose**, a następnie wybierz ten sam element docelowy system operacyjny.  

    > [!NOTE]
    > W tym kroku programu Visual Studio będzie oferować do utworzenia pliku Dockerfile. Jeśli możesz to zrobić w projekcie, który ma już obsługuje platformy Docker, zostanie wyświetlony monit, czy chcesz zastąpić istniejący plik Dockerfile. Jeśli wprowadzono zmiany z pliku dockerfile, który chcesz zachować, wybierz przycisk nie.

    Visual Studio wprowadza pewne zmiany do swojej platformy docker compose plik YML. Teraz obie te usługi są uwzględniane.

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

1. Lokalnie, teraz (F5 lub Ctrl + F5), aby sprawdzić, czy działa zgodnie z oczekiwaniami, należy uruchomić witryny. Jeśli wszystko jest poprawnie skonfigurowane, zostanie wyświetlony komunikat "Hello webfrontend i webapi (z wartością 1)".

   Skonfigurowano pierwszy projekt, używanego podczas dodawania aranżacji kontenerów do uruchomienia podczas uruchamiania lub debugowania. Można skonfigurować w akcji uruchamiania **właściwości projektu** docker-compose projektu.  W węźle projektu docker-compose, kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe, a następnie wybierz **właściwości**, lub użyj klawisze Alt + Enter.  Poniższy zrzut ekranu przedstawia właściwości, które chcesz uzyskać rozwiązanie używane w tym miejscu.  Na przykład można zmienić strony, który jest ładowany przez dostosowanie **adres URL usługi** właściwości.

   ![Zrzut ekranu przedstawiający docker-compose właściwości projektu](media/tutorial-multicontainer/launch-action.png)

   Oto, zobacz przy uruchamianiu:

   ![Zrzut ekranu przedstawiający działającej aplikacji sieci web](media/tutorial-multicontainer/webfrontend.png)

## <a name="next-steps"></a>Następne kroki

Sprawdź opcje wdrażania usługi [kontenery na platformie Azure](/azure/containers).

## <a name="see-also"></a>Zobacz także
  
[Docker Compose](https://docs.docker.com/compose/)  
[Narzędzia kontenerów](/visualstudio/containers/)
