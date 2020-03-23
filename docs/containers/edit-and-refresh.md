---
title: Debugowanie aplikacji w lokalnym kontenerze platformy Docker | Dokumenty firmy Microsoft
description: Dowiedz się, jak zmodyfikować aplikację, która jest uruchomiona w lokalnym kontenerze platformy Docker, odświeżyć kontener za pomocą edycji i odświeżania, a następnie ustawić debugowanie punktów przerwania.
ms.author: ghogen
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: conceptual
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 9f1d80d540e9a25a3ef62ee0819c6f6655b9b3ab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75916520"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Debugowanie aplikacji w lokalnym kontenerze platformy Docker

Visual Studio zapewnia spójny sposób tworzenia kontenerów platformy Docker i sprawdzania poprawności aplikacji lokalnie. Aplikacje można uruchamiać i debugować w kontenerach systemu Linux lub Windows uruchomionych na lokalnym pulpicie systemu Windows z zainstalowanym programem Docker i nie trzeba ponownie uruchamiać kontenera przy każdej zmianie kodu.

W tym artykule pokazano, jak za pomocą programu Visual Studio, aby uruchomić aplikację w lokalnym kontenerze platformy Docker, wprowadzić zmiany, a następnie odświeżyć przeglądarkę, aby zobaczyć zmiany. W tym artykule pokazano również, jak ustawić punkty przerwania dla debugowania dla aplikacji konteneryzowanych. Obsługiwane typy projektów obejmują aplikacje sieci Web i konsoli .NET Core. W tym artykule używamy aplikacji sieci Web ASP.NET Core i aplikacji konsoli platformy .NET Framework.

Jeśli masz już projekt obsługiwanego typu, Visual Studio można utworzyć Dockerfile i skonfigurować projekt do uruchomienia w kontenerze. Zobacz [Narzędzia kontenerów w programie Visual Studio](overview.md).

## <a name="prerequisites"></a>Wymagania wstępne

Aby debugować aplikacje w lokalnym kontenerze platformy Docker, należy zainstalować następujące narzędzia:

::: moniker range="vs-2017"

* [Program Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z zainstalowanym obciążeniem web development

::: moniker-end

::: moniker range="vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) z zainstalowanym obciążeniem web development

::: moniker-end

Aby uruchomić kontenery platformy Docker lokalnie, musisz mieć lokalnego klienta platformy Docker. Można użyć [przybornika platformy Docker,](https://www.docker.com/products/docker-toolbox)który wymaga wyłączenia funkcji Hyper-V. Można również użyć platformy [Docker dla systemu Windows,](https://www.docker.com/get-docker)która używa funkcji Hyper-V i wymaga systemu Windows 10.

Kontenery platformy Docker są dostępne dla projektów platformy .NET Framework i .NET Core. Spójrzmy na dwa przykłady. Najpierw przyjrzymy się aplikacji sieci web .NET Core. Następnie przyjrzymy się aplikacji konsoli .NET Framework.

## <a name="create-a-web-app"></a>Tworzenie aplikacji internetowej

Jeśli masz projekt i dodano obsługę platformy Docker zgodnie z opisem w [przeglądzie,](overview.md)pomiń tę sekcję.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Edytowanie kodu i odświeżanie

Aby szybko iterować zmiany, można uruchomić aplikację w kontenerze. Następnie kontynuuj wprowadzanie zmian, wyświetlanie ich w sposób, który ma miejsce w uzywki usługi IIS Express.

1. Upewnij się, że docker jest skonfigurowany do używania typu kontenera (Linux lub Windows), którego używasz. Kliknij prawym przyciskiem myszy ikonę platformy Docker na pasku zadań i wybierz pozycję **Przełącz na kontenery systemu Linux** lub **Odpowiednio przełącz się do kontenerów systemu Windows.**

1. (.NET Core 3 i nowsze tylko) Edytowanie kodu i odświeżanie uruchomionej witryny zgodnie z opisem w tej sekcji nie jest włączone w domyślnych szablonach w .NET Core >= 3.0. Aby ją włączyć, dodaj pakiet NuGet [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/). W *Startup.cs*, dodaj wywołanie metody `IMvcBuilder.AddRazorRuntimeCompilation` rozszerzenia do kodu `ConfigureServices` w metodzie. To wystarczy tylko włączone w trybie DEBUG, więc kod to w następujący sposób:

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

   Aby uzyskać więcej informacji, zobacz [Kompilacja plików Razor w ASP.NET Core](/aspnet/core/mvc/views/view-compilation?view=aspnetcore-3.1).

1. Ustaw **konfigurację rozwiązania** na **Debugowanie**. Następnie naciśnij klawisz **Ctrl**+**F5,** aby utworzyć obraz platformy Docker i uruchomić go lokalnie.

    Gdy obraz kontenera jest zbudowany i uruchomiony w kontenerze platformy Docker, visual studio uruchamia aplikację sieci web w domyślnej przeglądarce.

1. Przejdź do strony *Indeks.* Zmiany wejdą na tej stronie.
1. Wróć do programu Visual Studio i otwórz *plik Index.cshtml*.
1. Dodaj następującą zawartość HTML na końcu pliku, a następnie zapisz zmiany.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

1. W oknie danych wyjściowych po zakończeniu kompilacji .NET i wyświetlonych następujących wierszy, przełącz się z powrotem do przeglądarki i odśwież stronę:

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Twoje zmiany zostały zastosowane!

### <a name="debug-with-breakpoints"></a>Debugowanie z punktami przerwania

Często zmiany wymagają dalszej kontroli. Można użyć funkcji debugowania programu Visual Studio dla tego zadania.

1. W programie Visual Studio otwórz *Index.cshtml.cs*.
2. Zastąp `OnGet` zawartość metody następującym kodem:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. Po lewej stronie wiersza kodu ustaw punkt przerwania.
4. Aby rozpocząć debugowanie i trafić w punkt przerwania, naciśnij klawisz F5.
5. Przełącz się do programu Visual Studio, aby wyświetlić punkt przerwania. Sprawdź wartości.

   ![Punkt przerwania](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>Tworzenie aplikacji konsoli platformy .NET Framework

W przypadku korzystania z projektów aplikacji konsoli platformy .NET Framework opcja dodawania obsługi platformy Docker bez aranżacji nie jest obsługiwana. Nadal można użyć poniższej procedury, nawet jeśli używasz tylko jednego projektu platformy Docker.

1. Utwórz nowy projekt aplikacji konsoli .NET Framework.
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Dodaj** > **obsługę aranżacji kontenerów**.  W wyświetlonym oknie dialogowym wybierz pozycję **Docker Compose**. Plik Dockerfile jest dodawany do projektu i docker compose projektu z skojarzonych plików pomocy technicznej jest dodawany.

### <a name="debug-with-breakpoints"></a>Debugowanie z punktami przerwania

1. W Eksploratorze rozwiązań otwórz *Program.cs*.
2. Zastąp `Main` zawartość metody następującym kodem:

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. Ustaw punkt przerwania po lewej stronie wiersza kodu.
4. Naciśnij klawisz F5, aby rozpocząć debugowanie i trafić w punkt przerwania.
5. Przełącz się do programu Visual Studio, aby wyświetlić punkt przerwania i sprawdzić wartości.

   ![Punkt przerwania](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Ponowne użycie kontenera

Podczas cyklu rozwoju Visual Studio odbudowuje tylko obrazy kontenera i sam kontener po zmianie dockerfile. Jeśli nie zmienisz pliku Dockerfile, visual studio ponownie używa kontenera z wcześniejszego uruchomienia.

Jeśli ręcznie zmodyfikowano kontener i chcesz ponownie uruchomić za pomocą czystego obrazu kontenera, użyj polecenia **Build** > **Clean** w programie Visual Studio, a następnie skompiluj go normalnie.

## <a name="troubleshoot"></a>Rozwiązywanie problemów

Dowiedz się, jak [rozwiązywać problemy z tworzeniem platformy Docker w programie Visual Studio](troubleshooting-docker-errors.md).

## <a name="next-steps"></a>Następne kroki

Uzyskaj więcej szczegółów, [czytając, jak program Visual Studio tworzy konteneryzowane aplikacje.](container-build.md)

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Więcej informacji o platformie Docker w programie Visual Studio, systemie Windows i platformie Azure

* Dowiedz się więcej o [tworzeniu kontenerów w programie Visual Studio](/visualstudio/containers).
* Aby skompilować i wdrożyć kontener platformy Docker, zobacz [Integracja platformy Docker dla potoków platformy Azure.](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker)
* Aby zapoznać się z indeksem artykułów dotyczących systemów Windows Server i Nano Server, zobacz [Informacje o kontenerze systemu Windows](/virtualization/windowscontainers/).
* Dowiedz się więcej o [usłudze Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/) i przejrzyj [dokumentację usługi Azure Kubernetes.](/azure/aks)
