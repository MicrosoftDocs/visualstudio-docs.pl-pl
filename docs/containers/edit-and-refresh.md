---
title: Debugowanie aplikacji w lokalnym kontenerze platformy Docker | Microsoft Docs
description: Dowiedz się, jak zmodyfikować aplikację uruchomioną w lokalnym kontenerze platformy Docker, odświeżyć kontener poprzez edycję i odświeżanie, a następnie ustawić punkty przerwania debugowania.
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: conceptual
ms.workload: multiple
ms.date: 07/25/2019
ms.author: ghogen
ms.technology: vs-azure
ms.openlocfilehash: d7a7fa83fe0976ee1e08c6c614a11f783178a285
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70179857"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Debugowanie aplikacji w lokalnym kontenerze platformy Docker

Program Visual Studio zapewnia spójny sposób opracowywania w kontenerze platformy Docker i sprawdzanie poprawności aplikacji lokalnie. Nie trzeba ponownie uruchamiać kontenera przy każdym wprowadzeniu zmiany w kodzie.

W tym artykule pokazano, jak za pomocą programu Visual Studio uruchomić aplikację sieci Web ASP.NET Core w lokalnym kontenerze Docker, wprowadzić zmiany, a następnie odświeżyć przeglądarkę, aby zobaczyć zmiany. W tym artykule pokazano również, jak ustawić punkty przerwania na potrzeby debugowania dla kontenerów ASP.NET Core aplikacje sieci Web i .NET Framework aplikacje konsolowe.

## <a name="prerequisites"></a>Wymagania wstępne

Aby debugować aplikacje w lokalnym kontenerze platformy Docker, należy zainstalować następujące narzędzia:

::: moniker range="vs-2017"

* [Program Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z zainstalowanym obciążeniem programowaniem w sieci Web

::: moniker-end

::: moniker range="vs-2019"

* [Program Visual Studio 2019](https://visualstudio.microsoft.com/downloads) z zainstalowanym obciążeniem programowaniem w sieci Web

::: moniker-end

Aby uruchomić kontenery platformy Docker lokalnie, musisz mieć lokalnego klienta platformy Docker. Możesz użyć przybornika [platformy Docker](https://www.docker.com/products/docker-toolbox), który wymaga wyłączenia funkcji Hyper-V. Można również użyć [Docker for Windows](https://www.docker.com/get-docker), który używa funkcji Hyper-V i wymaga systemu Windows 10. 

Kontenery platformy Docker są dostępne dla projektów .NET Framework i .NET Core. Przyjrzyjmy się dwóm przykładom. Najpierw Spójrzmy na aplikację internetową platformy .NET Core. Następnie Przyjrzyjmy się .NET Framework aplikacji konsolowej.

## <a name="create-a-web-app"></a>tworzenie aplikacji internetowej

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[! UWZGLĘDNIj [Create-aspnet5-App-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Edytuj swój kod i Odśwież

Aby szybko wykonać iterację zmian, możesz uruchomić aplikację w kontenerze. Następnie Kontynuuj, aby wprowadzić zmiany, wyświetlając je tak jak IIS Express.

1. Ustaw **konfigurację rozwiązania** na **Debuguj**. Następnie naciśnij kombinację klawiszy CTRL + F5, aby skompilować obraz platformy Docker i uruchomić go lokalnie.

    Po skompilowaniu i uruchomieniu obrazu kontenera w kontenerze platformy Docker program Visual Studio uruchamia aplikację sieci Web w domyślnej przeglądarce.

2. Przejdź do strony *indeks* . Wprowadzimy zmiany na tej stronie.
3. Wróć do programu Visual Studio i Otwórz *index. cshtml*.
4. Dodaj następującą zawartość HTML na końcu pliku, a następnie Zapisz zmiany.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

5. W oknie dane wyjściowe, gdy kompilacja platformy .NET zostanie zakończona i zobaczysz następujące wiersze, przełącz się z powrotem do przeglądarki i Odśwież stronę:

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
1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Dodaj** > **obsługę aranżacji kontenera**.  W wyświetlonym oknie dialogowym wybierz pozycję **Docker Compose**. Do projektu zostanie dodany pliku dockerfile i zostanie dodany projekt Docker Compose ze skojarzonymi plikami obsługi.

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

Jeśli ręcznie zmodyfikowano kontener i chcesz uruchomić ponownie za pomocą czystego obrazu kontenera, użyj polecenia **Build** > **Clean** w programie Visual Studio, a następnie Skompiluj jako Normal.

## <a name="troubleshoot"></a>Rozwiązywanie problemów

Dowiedz się, jak [rozwiązywać problemy z programowaniem platformy Docker programu Visual Studio](troubleshooting-docker-errors.md).

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Więcej informacji na temat platformy Docker z programem Visual Studio, systemem Windows i platformą Azure

* Dowiedz się więcej o [projektowaniu kontenerów za pomocą programu Visual Studio](/visualstudio/containers).
* Aby skompilować i wdrożyć kontener platformy Docker, zobacz [integracja platformy Docker dla Azure Pipelines](https://aka.ms/dockertoolsforvsts).
* Indeks artykułów systemu Windows Server i nano Server można znaleźć w temacie [Informacje o kontenerach systemu Windows](https://aka.ms/containers).
* Dowiedz się więcej o [usłudze Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) i zapoznaj się z [dokumentacją usługi Azure Kubernetes](/azure/aks).
