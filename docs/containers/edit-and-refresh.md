---
title: Debugowanie aplikacji w lokalnym kontenerze platformy Docker | Microsoft Docs
description: Dowiedz się, jak zmodyfikować aplikację, która jest uruchomiona w lokalnym kontenerze platformy Docker, odświeżyć kontener za pomocą przycisku Edytuj i odśwież, a następnie ustawić punkty przerwania debugowania.
ms.author: ghogen
author: ghogen
manager: jmartens
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: how-to
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 8fb821acb48dd05aa09723fe5c6c254e7d1ca648
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306387"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Debugowanie aplikacji w lokalnym kontenerze platformy Docker

Visual Studio zapewnia spójny sposób tworzenia kontenerów platformy Docker i lokalnego weryfikowania aplikacji.
Aplikacje można uruchamiać i debugować w kontenerach systemu Linux lub Windows uruchomionych na lokalnym pulpicie systemu Windows z zainstalowaną platformą Docker i nie trzeba ponownie uruchamiać kontenera za każdym razem, gdy zmieniasz kod.

W tym artykule pokazano, jak za pomocą Visual Studio uruchomić aplikację w lokalnym kontenerze platformy Docker, wprowadzić zmiany, a następnie odświeżyć przeglądarkę, aby zobaczyć zmiany. W tym artykule pokazano również, jak ustawić punkty przerwania na potrzeby debugowania dla aplikacji konteneryzowanych. Obsługiwane typy projektów obejmują .NET Framework i aplikacje internetowe i konsolowe .NET Core. W tym artykule używamy aplikacji internetowych ASP.NET Core i .NET Framework konsoli.

Jeśli masz już projekt o obsługiwanym typie, Visual Studio utworzyć plik Dockerfile i skonfigurować projekt do uruchamiania w kontenerze. Zobacz [Narzędzia kontenerów w Visual Studio](overview.md).

## <a name="prerequisites"></a>Wymagania wstępne

Aby debugować aplikacje w lokalnym kontenerze platformy Docker, należy zainstalować następujące narzędzia:

::: moniker range="vs-2017"

* [Visual Studio 2017 z](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) zainstalowanym obciążeniem Tworzenie aplikacji internetowych

::: moniker-end

::: moniker range="vs-2019"

* [Visual Studio 2019 z](https://visualstudio.microsoft.com/downloads) zainstalowanym obciążeniem Tworzenie aplikacji internetowych

::: moniker-end

::: moniker range="vs-2022"

* [Visual Studio 2022 (wersja zapoznawcza)]() z zainstalowanym obciążeniem Tworzenie aplikacji internetowych

::: moniker-end

Aby uruchomić kontenery platformy Docker lokalnie, musisz mieć lokalnego klienta platformy Docker. Można użyć programu [Docker for Windows](https://www.docker.com/get-docker), który używa funkcji Hyper-V i wymaga Windows 10.

Kontenery platformy Docker są dostępne dla .NET Framework i .NET Core. Przyjrzyjmy się dwóch przykładom. Najpierw przyjrzymy się aplikacji internetowej .NET Core. Następnie przyjrzymy się aplikacji .NET Framework konsoli.

## <a name="create-a-web-app"></a>Tworzenie aplikacji internetowej

Jeśli masz projekt i dodano obsługę platformy Docker [](overview.md)zgodnie z opisem w przeglądzie, pomiń tę sekcję.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Edytowanie kodu i odświeżanie

Aby szybko iterować zmiany, możesz uruchomić aplikację w kontenerze. Następnie kontynuuj wprowadzać zmiany, wyświetlając je tak samo, jak w IIS Express.

1. Upewnij się, że aplikacja Docker jest ustawiona do używania typu kontenera (Linux lub Windows), z których korzystasz. Kliknij prawym przyciskiem myszy ikonę platformy Docker na pasku zadań, a następnie wybierz pozycję Przełącz na **kontenery systemu Linux** lub Przełącz na **kontenery systemu Windows** zgodnie z potrzebami.

1. (tylko program .NET Core 3 i nowsze) Edytowanie kodu i odświeżanie uruchomionej witryny zgodnie z opisem w tej sekcji nie jest włączone w domyślnych szablonach w programie .NET Core >= 3.0. Aby ją włączyć, dodaj pakiet NuGet [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/). W *pliku Startup.cs* dodaj wywołanie metody rozszerzenia `IMvcBuilder.AddRazorRuntimeCompilation` do kodu w metodzie `ConfigureServices` . Ta opcja musi być włączona tylko w trybie DEBUGOWANIE, więc należy ją zakodować w następujący sposób:

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

    `Startup`Zmodyfikuj metodę w następujący sposób:

    ```csharp
    public Startup(IConfiguration configuration, IWebHostEnvironment webHostEnvironment)
    {
        Configuration = configuration;
        Env = webHostEnvironment;
    }
    ```

   Aby uzyskać więcej informacji, zobacz [Razor file compilation in ASP.NET Core (Kompilacja plików Razor w ASP.NET Core).](/aspnet/core/mvc/views/view-compilation?view=aspnetcore-3.1&preserve-view=true)

1. Ustaw **dla opcji Konfiguracja rozwiązania** wartość **Debuguj**. Następnie naciśnij klawisz **Ctrl** + **F5,** aby skompilować obraz platformy Docker i uruchomić go lokalnie.

    Po s zbudowaniu i uruchomieniu obrazu kontenera w kontenerze platformy Docker program Visual Studio aplikację internetową w domyślnej przeglądarce.

1. Przejdź do *strony Indeks.* Na tej stronie dokonamy zmian.
1. Wróć do Visual Studio i otwórz *index.cshtml.*
1. Dodaj następującą zawartość HTML na końcu pliku, a następnie zapisz zmiany.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

1. Po zakończeniu kompilacji .NET w oknie danych wyjściowych i wyświetleniu następujących wierszy wróć do przeglądarki i odśwież stronę:

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Zmiany zostały zastosowane.

### <a name="debug-with-breakpoints"></a>Debugowanie za pomocą punktów przerwania

Często zmiany wymagają dalszej inspekcji. W tym zadaniu można użyć Visual Studio debugowania.

1. W Visual Studio otwórz *pliku Index.cshtml.cs.*
2. Zastąp zawartość metody `OnGet` następującym kodem:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. Po lewej stronie wiersza kodu ustaw punkt przerwania.
4. Aby rozpocząć debugowanie i trafić punkt przerwania, naciśnij klawisz F5.
5. Przejdź do Visual Studio, aby wyświetlić punkt przerwania. Sprawdź wartości.

   ![Zrzut ekranu przedstawiający część kodu pliku Index.cshtml.cs w pliku Visual Studio z punktem przerwania ustawionym na lewo od wiersza kodu wyróżnione kolorem żółtym.](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app&quot;></a>Tworzenie aplikacji .NET Framework konsoli

W przypadku używania .NET Framework aplikacji konsolowej opcja dodania obsługi platformy Docker bez orkiestracji nie jest obsługiwana. Nadal możesz użyć poniższej procedury, nawet jeśli używasz tylko jednego projektu platformy Docker.

1. Utwórz nowy projekt aplikacji .NET Framework Console.
1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz pozycję **Dodaj**  >  **obsługę orkiestracji kontenerów.**  W wyświetlonym oknie dialogowym wybierz pozycję **Docker Compose**. Do projektu zostanie dodany plik Dockerfile, a Docker Compose zostanie dodany projekt ze skojarzonymi plikami obsługi.

### <a name=&quot;debug-with-breakpoints&quot;></a>Debugowanie za pomocą punktów przerwania

1. W Eksplorator rozwiązań otwórz *program Program.cs.*
2. Zastąp zawartość metody `Main` następującym kodem:

   ```csharp
       System.Console.WriteLine(&quot;Hello, world!");
   ```

3. Ustaw punkt przerwania z lewej strony wiersza kodu.
4. Naciśnij klawisz F5, aby rozpocząć debugowanie i trafić punkt przerwania.
5. Przełącz się Visual Studio, aby wyświetlić punkt przerwania i sprawdzić wartości.

   ![Zrzut ekranu przedstawiający okno kodu dla programu Program.cs w Visual Studio z punktem przerwania ustawionym na lewo od wiersza kodu wyróżnione kolorem żółtym.](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Ponowne użycie kontenera

Podczas cyklu projektowania program Visual Studio tylko obrazy kontenerów i sam kontener po zmianie pliku Dockerfile. Jeśli nie zmienisz pliku Dockerfile, Visual Studio ponownie użyje kontenera z wcześniejszego uruchomienia.

Jeśli kontener został zmodyfikowany ręcznie i chcesz uruchomić go ponownie przy użyciu czystego obrazu kontenera, użyj polecenia **Build** Clean w Visual Studio, a następnie skompilowaj go w zwykły  >   sposób.

## <a name="troubleshoot"></a>Rozwiązywanie problemów

Dowiedz się, jak [rozwiązywać problemy Visual Studio docker.](troubleshooting-docker-errors.md)

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji, zobacz How Visual Studio builds containerized apps (Jak [tworzyć konteneryzowane aplikacje).](container-build.md)

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Więcej informacji na temat platformy Docker Visual Studio, systemu Windows i platformy Azure

* Dowiedz się więcej na [temat tworzenia kontenerów za pomocą Visual Studio](./index.yml).
* Aby skompilować i wdrożyć kontener platformy Docker, zobacz [Integracja platformy Docker dla Azure Pipelines](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker).
* Aby uzyskać indeks artykułów dotyczących systemów Windows Server i Nano Server, zobacz [informacje o kontenerze systemu Windows](/virtualization/windowscontainers/).
* Dowiedz się [więcej Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) i zapoznaj się z [Azure Kubernetes Service dokumentacją.](/azure/aks)
