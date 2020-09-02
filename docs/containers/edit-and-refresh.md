---
title: Debugowanie aplikacji w lokalnym kontenerze platformy Docker | Microsoft Docs
description: Dowiedz się, jak zmodyfikować aplikację uruchomioną w lokalnym kontenerze platformy Docker, odświeżyć kontener poprzez edycję i odświeżanie, a następnie ustawić punkty przerwania debugowania.
ms.author: ghogen
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: how-to
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 26562268167abdfc5ee643618ec1610da231f9f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283167"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Debugowanie aplikacji w lokalnym kontenerze platformy Docker

Program Visual Studio zapewnia spójny sposób opracowywania kontenerów platformy Docker i lokalnego weryfikowania aplikacji. Aplikacje można uruchamiać i debugować w kontenerach systemu Linux lub Windows uruchomionych na lokalnym pulpicie systemu Windows z zainstalowanym programem Docker i nie trzeba ponownie uruchamiać kontenera przy każdym wprowadzeniu zmiany w kodzie.

W tym artykule pokazano, jak uruchomić aplikację w lokalnym kontenerze Docker przy użyciu programu Visual Studio, wprowadzić zmiany, a następnie odświeżyć przeglądarkę, aby zobaczyć zmiany. W tym artykule pokazano również, jak ustawić punkty przerwania na potrzeby debugowania dla aplikacji w kontenerze. Obsługiwane typy projektów to .NET Framework i .NET Core aplikacji internetowych i konsolowych. W tym artykule używamy ASP.NET Core aplikacji sieci Web i .NET Framework aplikacji konsolowych.

Jeśli masz już projekt obsługiwanego typu, program Visual Studio może utworzyć pliku dockerfile i skonfigurować projekt do uruchamiania w kontenerze. Zobacz [Narzędzia kontenera w programie Visual Studio](overview.md).

## <a name="prerequisites"></a>Wymagania wstępne

Aby debugować aplikacje w lokalnym kontenerze platformy Docker, należy zainstalować następujące narzędzia:

::: moniker range="vs-2017"

* [Program Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z zainstalowanym obciążeniem programowaniem w sieci Web

::: moniker-end

::: moniker range="vs-2019"

* [Program Visual Studio 2019](https://visualstudio.microsoft.com/downloads) z zainstalowanym obciążeniem programowaniem w sieci Web

::: moniker-end

Aby uruchomić kontenery platformy Docker lokalnie, musisz mieć lokalnego klienta platformy Docker. Możesz użyć [przybornika platformy Docker](https://www.docker.com/products/docker-toolbox), który wymaga wyłączenia funkcji Hyper-V. Można również użyć [Docker for Windows](https://www.docker.com/get-docker), który używa funkcji Hyper-V i wymaga systemu Windows 10.

Kontenery platformy Docker są dostępne dla projektów .NET Framework i .NET Core. Przyjrzyjmy się dwóm przykładom. Najpierw Spójrzmy na aplikację internetową platformy .NET Core. Następnie Przyjrzyjmy się .NET Framework aplikacji konsolowej.

## <a name="create-a-web-app"></a>tworzenie aplikacji internetowej

Jeśli masz projekt i dodano obsługę platformy Docker zgodnie z opisem w sekcji [Przegląd](overview.md), Pomiń tę sekcję.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Edytuj swój kod i Odśwież

Aby szybko wykonać iterację zmian, możesz uruchomić aplikację w kontenerze. Następnie Kontynuuj, aby wprowadzić zmiany, wyświetlając je tak jak IIS Express.

1. Upewnij się, że platforma Docker została skonfigurowana do korzystania z typu kontenera (Linux lub Windows), którego używasz. Kliknij prawym przyciskiem myszy ikonę platformy Docker na pasku zadań, a następnie wybierz polecenie **Przełącz do kontenerów systemu Linux** lub **Przejdź do kontenerów z systemem Windows** w zależności od potrzeb.

1. (Tylko program .NET Core 3 i nowsze) Edytowanie kodu i odświeżanie uruchomionej lokacji zgodnie z opisem w tej sekcji nie jest włączone w szablonach domyślnych w programie .NET Core >= 3,0. Aby ją włączyć, Dodaj pakiet NuGet [Microsoft. AspNetCore. MVC. Razor. RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/). W *Startup.cs*Dodaj wywołanie metody Extension `IMvcBuilder.AddRazorRuntimeCompilation` do kodu w `ConfigureServices` metodzie. Ta funkcja jest wymagana tylko w trybie debugowania, dlatego należy ją kod w następujący sposób:

    ```csharp
    public IWebHostEnvironment Env { get; set; }
    
    public void ConfigureServices(IServiceCollection services)
    {
        IMvcBuilder builder = services.AddRazorPages();
    
    #if DEBUG
        if (Env.IsDevelopment())
        {
            builder.AddRazorRuntimeCompilation();
        }
    #endif
    
        // code omitted for brevity
    }
    ```

    Zmodyfikuj `Startup` metodę w następujący sposób:

    ```csharp
    public Startup(IConfiguration configuration, IWebHostEnvironment webHostEnvironment)
    {
        Configuration = configuration;
        Env = webHostEnvironment;
    }
    ```

   Aby uzyskać więcej informacji, zobacz [kompilacja pliku Razor w ASP.NET Core](/aspnet/core/mvc/views/view-compilation?view=aspnetcore-3.1).

1. Ustaw **konfigurację rozwiązania** na **Debuguj**. Następnie naciśnij klawisz **Ctrl** + **F5** , aby skompilować obraz platformy Docker i uruchomić go lokalnie.

    Po skompilowaniu i uruchomieniu obrazu kontenera w kontenerze platformy Docker program Visual Studio uruchamia aplikację sieci Web w domyślnej przeglądarce.

1. Przejdź do strony *indeks* . Wprowadzimy zmiany na tej stronie.
1. Wróć do programu Visual Studio i Otwórz *index. cshtml*.
1. Dodaj następującą zawartość HTML na końcu pliku, a następnie Zapisz zmiany.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

1. W oknie dane wyjściowe, gdy kompilacja platformy .NET zostanie zakończona i zobaczysz następujące wiersze, przełącz się z powrotem do przeglądarki i Odśwież stronę:

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Zmiany zostały zastosowane.

### <a name="debug-with-breakpoints"></a>Debuguj z punktami przerwania

Często zmiany wymagają dalszej kontroli. Dla tego zadania można użyć funkcji debugowania programu Visual Studio.

1. W programie Visual Studio Otwórz *index.cshtml.cs*.
2. Zastąp zawartość `OnGet` metody następującym kodem:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. Na lewo od wiersza kodu Ustaw punkt przerwania.
4. Aby rozpocząć debugowanie i trafić punkt przerwania, naciśnij klawisz F5.
5. Przełącz się do programu Visual Studio, aby wyświetlić punkt przerwania. Sprawdź wartości.

   ![Punkt](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>Tworzenie aplikacji konsolowej .NET Framework

W przypadku korzystania z projektów aplikacji konsolowych .NET Framework opcja dodawania obsługi platformy Docker bez aranżacji nie jest obsługiwana. Można nadal użyć poniższej procedury, nawet jeśli używany jest tylko jeden projekt platformy Docker.

1. Utwórz nowy projekt aplikacji konsoli .NET Framework.
1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Dodaj**  >  **obsługę aranżacji kontenera**.  W wyświetlonym oknie dialogowym wybierz pozycję **Docker Compose**. Do projektu zostanie dodany pliku dockerfile i zostanie dodany projekt Docker Compose ze skojarzonymi plikami obsługi.

### <a name="debug-with-breakpoints"></a>Debuguj z punktami przerwania

1. W Eksplorator rozwiązań Otwórz *program.cs*.
2. Zastąp zawartość `Main` metody następującym kodem:

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. Ustaw punkt przerwania z lewej strony wiersza kodu.
4. Naciśnij klawisz F5, aby rozpocząć debugowanie i kliknij punkt przerwania.
5. Przełącz się do programu Visual Studio, aby wyświetlić punkt przerwania i sprawdzić wartości.

   ![Punkt](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Ponowne użycie kontenera

W cyklu programowania program Visual Studio ponownie kompiluje tylko obrazy kontenera i sam kontener po zmianie pliku dockerfile. Jeśli nie zmienisz pliku dockerfile, program Visual Studio ponownie używa kontenera z wcześniejszego uruchomienia.

Jeśli ręcznie zmodyfikowano kontener i chcesz uruchomić ponownie za pomocą czystego obrazu kontenera, użyj polecenia **Build**  >  **Clean** w programie Visual Studio, a następnie Skompiluj jako Normal.

## <a name="troubleshoot"></a>Rozwiązywanie problemów

Dowiedz się, jak [rozwiązywać problemy z programowaniem platformy Docker programu Visual Studio](troubleshooting-docker-errors.md).

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji, Przeczytaj, w [jaki sposób program Visual Studio tworzy kontenery aplikacji](container-build.md).

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Więcej informacji na temat platformy Docker z programem Visual Studio, systemem Windows i platformą Azure

* Dowiedz się więcej o [projektowaniu kontenerów za pomocą programu Visual Studio](/visualstudio/containers).
* Aby skompilować i wdrożyć kontener platformy Docker, zobacz [integracja platformy Docker dla Azure Pipelines](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker).
* Indeks artykułów systemu Windows Server i nano Server można znaleźć w temacie [Informacje o kontenerach systemu Windows](/virtualization/windowscontainers/).
* Dowiedz się więcej o [usłudze Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) i zapoznaj się z [dokumentacją usługi Azure Kubernetes](/azure/aks).
